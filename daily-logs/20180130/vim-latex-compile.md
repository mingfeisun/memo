
## Compiling latex file within vim
``` bash
# install texlive in ubuntu 
sudo apt-get install texlive-full

# compile under personal vimrc file
[space key] + ll
```

Procedure:

1. Compile with pdfLaTeX to get know which pieces you cite and store it in .aux file.
2. Compile with BibTeX to create the .bbl file (which contains the formatted references) from information stored in the .aux and .bib files.
3. Compile with pdfLaTex to incorporate the .bbl file in the typeset document (to include references list in the document).
4. Compile with pdfLaTex to rid of ? marks and get citations in your text.
