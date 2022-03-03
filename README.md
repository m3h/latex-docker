# LaTeX Docker image
This repo provides a docker image, based on the latest ubuntu image, with a current LaTeX installation (installed using the install-tl script).

```
cd ./latex
sudo docker build --build-arg LATEX_UPDATE_TIME="$(date)" -t m3hh/latex:latest .
```
