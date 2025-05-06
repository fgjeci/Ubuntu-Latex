<h1 align="center">Compiling Latex thesis style documents using VS Code (tested in Ubuntu)</h1>
<p align="center">
  <em>Don't forget to give this repo a star ⭐️</em>
  <br>
</p>

<!-- <p align="center">
  <em>The configuration steps to use Visual Studio Code
    <br>to compile thesis style documents in LaTeX</em>
  <br>
</p> -->

This repository contains the configuration steps that are necessary to compile Latex documents in a local environment. It has been tested in Ubuntu and can be used to generate from simple documents, to publications articles. It supports <b>citations</b> for <b>Research</b> related documents.



<hr>

<h2>Features</h2>
<ul>
<li>Works fully offline</li>
<li>Bibliography support with citations</li>
<li>Auxiliary files are hidden in subfolders</li>
<li>Only the Main file is shown in the main directory of the project</li>
</ul>


<h2>VS Code setup</h2>

In order to use it, you need to do the following

<h3>Install Visual Studio Code</h3>

VS Code is the IDE that you will use to edit and compile your LaTeX files. You can download it from the official source [here](https://code.visualstudio.com/download "Visual Studio Code - Download")

<h3>Install MikTex</h3>

Ubuntu users can use the command
```
sudo apt-get install miktex
```

<h3>Install the LaTeX Workshop extension in VS Code </h3>

The Publisher of this extension is James Yu. You can find it by searching for <b>LaTeX Workshop</b> in the <i>Extensions</i> option in the menu on the left of the VS Code IDE. The <i>Extensions</i> option is also activated by using the keyboard shortcuts <b>Ctrl+Shift+X</b> in Ubuntu. 

After installing, restart the VS Code and you will see a new added extension to the VS Code menu on the left, with the text TEX as icon.



<h3>Edit the User Setting in VS Code</h3>

You have to open the JSON version of <i>User Settings (JSON)</i> using the keyboard shortcuts <b>Ctrl+Shift+P</b> in Ubuntu. Once inside you have to add the following components


```
"latex-workshop.latex.tools": [
    {
        "name": "lualatex",
        "command": "lualatex",
        "args": [
            "--interaction=nonstopmode",
            "--recorder",
            "--output-directory=%DOCFILE%",
            "--aux-directory=%DOCFILE%",
            "%DOCFILE%"
        ]
    },
    {
        "name": "bibtex",
        "command": "bibtex",
        "args": [
            "%DOCFILE%/%DOCFILE%"
        ],
    },
    {
        "name": "pdflatex",
        "command": "pdflatex",
        "args": [
            "-interaction=nonstopmode",
            "-synctex=1",
            "-include-directory=%DOCFILE%",
            "-jobname=%DOCFILE%",
            "-aux-directory=%DOCFILE%",
            "%DOCFILE%"
        ]
    },
],
"latex-workshop.latex.recipes": [
    {
        "name": "pdflatex",
        "tools": [
            "pdflatex"
        ]
    },
    {
        "name": "lualatex -> bibtex -> lualatex",
        "tools": [
            "lualatex",
            "bibtex",
            "lualatex",
            "pdflatex"
        ]
    },
],
```

<h3>Build Latex projects</h3>

To build a latex project go into the new TEX added extension, and as a fist item you will see a list titled <i>Build LaTeX project</i>. Inside the list are listed the latex compilation recipes we defined in the previous step, namely <b>pdflatex</b> and <b>lualatex -> bibtex -> lualatex</b>. In case the latex document you create has only text and figure, you can use <b>pdflatex</b>, whereas if you have a <b>bibliography</b> and <b>citations</b> use <b>lualatex -> bibtex -> lualatex</b>. 



