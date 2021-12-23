# Personal VS Code Configurations

> I use Windows OS but the shell/terminal commands i use it can be changed for the command in the correspondig OS.

## Finding the file

This is the file where you can overwrite the default configurations of the editor. 

You can access it with `Ctrl + ,` and writing ***settings*** in the search settings bar. After that,  search the sentence `Edit in settings.json` and click on it.![image](https://user-images.githubusercontent.com/44256569/147283853-70b43234-d9c1-49bf-9d1a-a54631ff83a4.png)

But if you can find it with this way, just search for the ruler of the editor.
You need to do the same process: `Ctrl + ,` and writing ***rulers*** in the search settings bar. After that,  search the sentence `Edit in settings.json` and click on it.![image](https://user-images.githubusercontent.com/44256569/147286691-42e83be0-27ff-4431-822b-740aef96e926.png)


## settings.json

The most important part for me is the code-runner configuration due to any bugs i found trying to compile codes:

```javascript
{
    "code-runner.executorMap": {

        // esto evita que las clases en C++ no compilen
        "c": "cls && cd $dir && gcc *.c -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
        // esto evita que las clases en C++ no compilen
        "cpp": "cls && cd $dir && g++ -std=c++14 *.cpp -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
        // esto obtiene la ultima versión de python para compilar
        "python": "cls && python3 -u $fileName",
        // reescribe el formato de fortran para compilarse
        "fortran": "cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
        "FortranFreeForm": "cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
        "fortran-modern":"cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
        "fortran_fixed-form":"cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe ",
        // run Scilab from VSCode
        // "scilab": "cls && cd $dir && D:\\Programs\\scilab-6.1.0\\bin\\Scilex.exe -nb -quit -f $fileName",
        // run Scilab with graphic Functions
        "scilab": "cls && cd $dir && D:\\Programs\\scilab-6.1.0\\bin\\WScilex-cli.exe -nb -f $fileName",
        // for processing execution
        "pde": "cls && cd $dir && processing-java --sketch=$dir --force --run"
    },
    "workbench.editorAssociations": {
        "*.ipynb": "jupyter.notebook.ipynb"
    },
    "editor.fontLigatures": true,
    "editor.fontFamily": "Fira Code",
    // "terminal.integrated.shell.windows": "C:\\WINDOWS\\System32\\WindowsPowerShell\\v1.0\\powershell.exe",
    "code-runner.saveAllFilesBeforeRun": true,
    "code-runner.runInTerminal": true,
    "code-runner.clearPreviousOutput": true,
    "fortran-ls.enableCodeActions": true,
    "fortran-ls.executablePath": "",
    "workbench.iconTheme": "vscode-icons",
    "latex-workshop.view.pdf.viewer": "tab",
    "git.autofetch": true,
    "git.confirmSync": false,
    "C_Cpp.updateChannel": "Insiders",
    "vsicons.dontShowNewVersionMessage": true,
    "latex-workshop.message.update.show": false,
    "editor.suggestSelection": "first",
    "vsintellicode.modify.editor.suggestSelection": "automaticallyOverrodeDefaultValue",
    "security.workspace.trust.untrustedFiles": "open",
    "workbench.colorTheme": "One Dark Pro Darker"

}
```

## Code-Runner Configurations

I try to work with all the languages i know in the same environment, so code-runner made me able to add the shell/terminal configurations to run/compile the languagues i need.

### C/C++

For this languages, i had a problem which the C files works but when i was working with headers and classes i got weird error, so i fixed it.
```javascript
"c": "cls && cd $dir && gcc *.c -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
"cpp": "cls && cd $dir && g++ -std=c++14 *.cpp -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
```

### Scilab

I rather scilab to matlab but the Scilab Editor is old and ugly, so, the compiler of Scilab is `scilex`, just search for the way to compile from batch in Scilab and i added it to code-runner options as a new language. Scilab have plot windows that can be plotting with the second way to run, but ***NOTE: you can just choose one of them.***
```javascript
// run Scilab from VSCode (just printing, not plots)
"scilab": "cls && cd $dir && D:\\Programs\\scilab-6.1.0\\bin\\Scilex.exe -nb -quit -f $fileName",
// or run Scilab with graphic Functions
"scilab": "cls && cd $dir && D:\\Programs\\scilab-6.1.0\\bin\\WScilex-cli.exe -nb -f $fileName",
```

### Fortran

I don't really remember why i added 4 different types of fortran languages, but it works for me.
```javascript
"fortran": "cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
"FortranFreeForm": "cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
"fortran-modern":"cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe",
"fortran_fixed-form":"cls && cd $dir && gfortran $fileName -o $fileNameWithoutExt && $dir$fileNameWithoutExt && del $dir$fileNameWithoutExt.exe ",
```

### Processing

Processing is a flexible software sketchbook and a language for learning how to code within the context of the visual arts. For that reason, the compile result is a prompt window that also can be compiled from terminal.
```javascript
"pde": "cls && cd $dir && processing-java --sketch=$dir --force --run"
```

---

>It's just a basic control of VS Code but it can be useful for someone.
