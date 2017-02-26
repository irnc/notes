# [MS-DOC] File format

- https://msdn.microsoft.com/en-us/library/office/cc313153(v=office.12).aspx

# Tools

- https://github.com/elrolito/docxconv
  - doesn't provide object model for .doc
  - converts MD-DOC to HTML using unoconv
- https://github.com/gfloyd/node-unoconv
  - Node.js wrapper for converting documents with unoconv

## unoconv

- http://dag.wiee.rs/home-made/unoconv/
  - https://github.com/dagwieers/unoconv
  - Universal Office Converter
  - unoconv is written in Python
  - it needs a recent LibreOffice or OpenOffice with UNO bindings
  - makes use of the LibreOffice’s UNO bindings for non-interactive conversion of documents

## UNO bindings

- Uno stands for Universal Network Objects

## UNO

_[...] the new scripting framework offers the use of the API through several
scripting languages, such as Javascript, Beanshell or Python._ [uno-first][]

[uno-first]: https://wiki.openoffice.org/wiki/Documentation/DevGuide/FirstSteps/Programming_with_UNO

Rhino is used for JavaScript. [uno-rhino][]

[uno-rhino]: https://wiki.openoffice.org/wiki/Documentation/DevGuide/Scripting/Scripting_Framework

_JScript [...] can use OpenOffice.org to work with Office documents._ [uno-js][]

[uno-js]: https://wiki.openoffice.org/wiki/Documentation/DevGuide/FirstSteps/Fields_of_Application_for_UNO

## Scripting Framework

- https://wiki.openoffice.org/wiki/Documentation/DevGuide/Scripting/How_the_Scripting_Framework_Works

```
soffice "-accept=socket,host=localhost,port=2002;urp;"
```

Warning: `-accept=socket,host=localhost,port=2002;urp;` is deprecated.  Use `--accept=socket,host=localhost,port=2002;urp;` instead.
