## Order of properties in JSON does matter

Prerequisites:
- stream records into Kinesis Firehose
- put one JSON serialized object per record

Streaming one JavaScript object serialized using JSON to Kinesis Firehose works
just fine.

Next step we connect Kinesis Analytics to analyze the stream. First step, the
schema discovery, fails right away with unexpected results.

[![][dup]][dup]

[dup]: 2016-10-11-kinesis-analytics-duplicate-arrays.png

Seems that property with array value breaks the JSON parser and it starts to
duplicate that value in all consecutive properties. While it was not obvious on
complex real data structure, simplified test case confirmed that assumption.

In order to workaround that issue, we could sort object keys and place
primitive values and nested objects before array values. It is an ugly
workaround, as order of object properties is not guaranteed by ECMAScript, but
we know that all major implementations store then in order of addition, so we
could sort them.

Correct and expected output after workaround:

[![][right]][right]

[right]: 2016-10-11-kinesis-analytics-expected-results.png

## Column names in schema should be ALL UPPER CASE

Which was not obvious at all.

Automatically discovered schema for real data with nested objects and arrays
was awful because it is hard to map nested properties to single namespace.

_Analytics_ does this by adding `_0` and `_1` to the end of column name, but is
uses property names as is, e.g. `camelCase` as seen in JSON.

Simplified input looked like:

```js
{
  ticker_symbol: 'AMZN',
  sector: 'TECHNOLOGY',
  change: 0.11,
  price: 200.31,
}
```

This is a data structure used in SQL examples at a next step. All good from
_stream sample_ view, but it fails to work with any SQL of examples. Error is
`Column 'SECTOR' not found in any table`.

Trial and error showed that _Analytics_ converts SQL column names to be all
upper case because it reaches some query execution engine. Thus no luck looking
for `SECTOR` when `sector` is provided.

Workaround: define schema manually and use `UPPER_CASE` for column names.

## What syntax is it?

I have no understanding why there is `0:` in `$.emails[0:]`.

## Don't use JSON array as data record

TODO

## Don't use JSON object with single property as data

TODO

## Follow a strict procedure updating SQL query and changing schema

TODO
