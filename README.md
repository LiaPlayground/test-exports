# test-exports


https://www.npmjs.com/package/@liascript/exporter

Install the exporter via:

``` bash
npm install -g --verbose @liascript/exporter
```

## SCORM1.2

``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md --path LiaScriptProject -f scorm1.2 -o scorm12
```

[output](scorm12.zip)

## SCORM2004

``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md --path LiaScriptProject -f scorm2004 -o scorm2004
```

[output](scorm2004.zip)
## PDF


``` bash
liaex -i LiaScriptProject/markdown/LiaScript.md -f pdf
```

[output](./output.pdf)