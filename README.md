# LiaScript Exporter evalution

This project provides an automated export mechanism for a LiaScript document and illustrates the current state of the exporter implementation. After committing changes related to the  [LiaScript file](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/test-exports/dev/LiaScriptCourse/LiaScript.md#1) located in `LiaScriptCourse` a Github Action generates 

| Type               | Link                                                                                                                  |
| ------------------ | --------------------------------------------------------------------------------------------------------------------- |
| `scorm2004`        | [scorm2004.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/scorm2004.zip)                           |
| `scorm2004-iframe` | [scorm2004-iframe.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/scorm2004-iframe.zip)             |
| `scorm1.2`         | [scorm12.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/scorm12s.zip)                             |
| `scorm1.2-iframe`  | [scorm12-iframe.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/scorm12-iframe.zip)                 |
| `pdf`              | [portableDocumentFormat.pdf](https://github.com/LiaPlayground/test-exports/raw/dev/export/portableDocumentFormat.pdf) |
| Webprojekt         | [webproject.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/webproject.zip)                         |

All outputs are available in the `export` folder. Feel free to clone the repository and start your ownproject.

General information about LiaScript can be found on [Project Website](https://liascript.github.io/) or in [user documentation](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaScript/docs/master/README.md#1)
                                                                                                             |

> __Currently, we improve the export functions. If you identify a problem or an interesting feature, do not hesitate to contact us. Just initiate an Issue here in Github.__

The corresponding Github Action installs the lia exporter and runs the `liaex` commands.