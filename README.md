# LiaScript Exporter evalution

This project provides an automated export mechanism for a LiaScript document and illustrates the current state of the exporter implementation. A Github Action generates 

| Type       | Link                                                                                |
|------------|-------------------------------------------------------------------------------------|
| 'scorm2004' | [scorm2004s.zip](https://github.com/LiaPlayground/test-exports/blob/dev/export/scorm2004.zip) |


for a [LiaScript file](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/test-exports/dev/LiaScriptCourse/LiaScript.md#1) locate in `LiaScriptCourse` repository root. The output is available in `export`. All parameters can be adapted to your needs. Feel free to clone the repository and start your project.

General information about LiaScript can be found on [Project Website](https://liascript.github.io/) or in [user documentation](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaScript/docs/master/README.md#1)
                                                                                                             |

> __Currently, we improve the export functions. If you identify a problem or an interesting feature, do not hesitate to contact us. Just initiate an Issue here in Github.__





## SCORM1.2

``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md --path LiaScriptProject -f scorm1.2 -o scorm12
```

[output](scorm12.zip)

## SCORM1.2 within an iframe


``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md --path LiaScriptProject -f scorm1.2 -o scorm12 --scorm-iframe
```

[output](scorm12-iframe.zip)

## SCORM2004

``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md --path LiaScriptProject -f scorm2004 -o scorm2004
```

[output](scorm2004.zip)


## SCORM2004 within an iframe

``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md --path LiaScriptProject -f scorm2004 -o scorm2004 --scorm-iframe
```

[output](scorm2004-iframe.zip)

## PDF


``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md -f pdf
```

[output](./output.pdf)