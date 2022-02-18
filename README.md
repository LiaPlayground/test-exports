# LiaScript Exporter evalution

This project provides an automated export mechanism for a LiaScript document and illustrates the current state of the exporter implementation. After committing changes related to the  [LiaScript file](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/test-exports/dev/LiaScriptCourse/LiaScript.md#1) located in `LiaScriptCourse` a Github Action generates 

| Type       | Link                                                                                |
|------------|-------------------------------------------------------------------------------------|
| `scorm2004` | [scorm2004s.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/scorm2004.zip) |
| `scorm2004-iframe` | [scorm2004s.zip](https://github.com/LiaPlayground/test-exports/raw/dev/export/scorm2004-iframe.zip) |
| `scorm1.2` |   |
| `scorm1.2-iframe` |   |
| `pdf` | [portableDocumentFormat.pdf](https://github.com/LiaPlayground/test-exports/raw/dev/export/portableDocumentFormat.pdf) |
| `web` |   |

All outputs are available in the `export` folder. Feel free to clone the repository and start your project.

General information about LiaScript can be found on [Project Website](https://liascript.github.io/) or in [user documentation](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaScript/docs/master/README.md#1)
                                                                                                             |

> __Currently, we improve the export functions. If you identify a problem or an interesting feature, do not hesitate to contact us. Just initiate an Issue here in Github.__

The corresponding Github Action installs the lia exporter and runs the `liaex` commands.

```yaml
name: Execute_liascript_exporters
on: push

jobs:
  export-job:
    runs-on: ubuntu-latest

    # This 
    env:
        LIA_FILE_NAME: "LiaScript.md"
        ROOT_FOLDER_NAME: "LiaScriptCourse"
        OUTPUT_FOLDER_NAME: "export"

    steps:    
    - name: Install dependencies
      run: |
           npm install -g @liascript/exporter --unsafe-perm

    - name: Check out current repository
      uses: actions/checkout@v2
      with: 
       ref: dev

    - name: Set folders
      run: |
           echo "OUTPUT_PATH=$(echo $OUTPUT_FOLDER_NAME)" >> $GITHUB_ENV
           echo "INPUT_LIA=$(echo $ROOT_FOLDER_NAME/$LIA_FILE_NAME)" >> $GITHUB_ENV

    - name: Generate export
      run: | 
           # scorm2004
           liaex -i ${{ env.INPUT_LIA }} -f scorm2004 -o ${{ env.OUTPUT_PATH }}/scorm2004
           git add ${{ env.OUTPUT_PATH }}/scorm2004.zip
           # scorm2004-iframe
           liaex -i ${{ env.INPUT_LIA }} -f scorm2004 -o ${{ env.OUTPUT_PATH }}/c --scorm-iframe
           git add ${{ env.OUTPUT_PATH }}/scorm2004-iframe.zip
           # pdf
           liaex -i ${{ env.INPUT_LIA }} -f pdf -o ${{ env.OUTPUT_PATH }}/portableDocumentFormat
           git add ${{ env.OUTPUT_PATH }}/portableDocumentFormat.pdf

    - name: Commit all changes
      run: |
           git config --local user.email "action@github.com"
           git config --local user.name "GitHub Action"
           git status
           git commit -m "Add new version of exported LiaScript files" || echo "No changes to commit"

    - name: Push changes
      uses: ad-m/github-push-action@master
      with:
           github_token: ${{ secrets.GITHUB_TOKEN }}
           branch: dev
```