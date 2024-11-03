## math-env

A simple math environment for working with Python and TeX using [devcontainers](https://code.visualstudio.com/docs/devcontainers/containers). Only requires Docker and Visual Studio Code to work.

It includes support for TeX compilation from the [TeXlive](https://tug.org/texlive/) project and the [LaTeX Workshop](https://github.com/James-Yu/LaTeX-Workshop) extension by James Yu. For python development, it includes a miniconda environment with some basic libraries, which of course can be modified as the user pleases, see below.

### How do modify
- VSCode extensions: at `devcontainer.json` the extension list and their settings can be tweaked. 
- Python (miniconda) environment: at `Dockerfile` the environment is setup and the packages added, one can modify it to pre-install adequate packages, or just install them later and update the image as needed.