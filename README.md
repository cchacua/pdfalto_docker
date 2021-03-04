# pdfalto_docker
Dockerfile with pdfalto


Run the container, mounting a volume with the PDF-files, and execute the following line:

```
docker exec -it <container_name> /home/pdfalto/pdfalto/pdfalto [pdfalto_options] <PDF-file> [<xml-file>]
```

You can save the xml-files in the same volume of the PDF files or you can mount a different volume to save them.


Example:

1. Run the container `pdfaltocontainer`, using the image `cchacua/pdfalto`
- Using Docker run command:

```
docker run -d -v PATHTOINPUTFOLDER:/home/jovyan/input/pdf -v PATHTOOUTPUTFOLDER:/home/jovyan/output --name pdfaltocontainer cchacua/pdfalto
```
- Using Docker compose:
```
version: '3'

services:
  pdfalto:
    image: cchacua/pdfalto
    container_name: pdfaltocontainer
    volumes:
      - PATHTOINPUTFOLDER:/home/jovyan/input/pdf
      - PATHTOOUTPUTFOLDER:/home/jovyan/output
      
```

2. Execute the container `pdfalto`, changing the options and specifying the path to your input pdf file and to your output xml file. E.g. To convert the first five pages (`-f 1 -l 5`) of `YOURPDFFILE.pdf` and save it as `YOURXMLFILE.xml`, you may write:
```
docker exec -it pdfaltocontainer /home/pdfalto/pdfalto/pdfalto -f 1 -l 5 -noImage -noImageInline -readingOrder -blocks /home/jovyan/input/pdf/YOURPDFFILE.pdf /home/jovyan/output/YOURXMLFILE.xml
```
For more information about the pdfalto options, please visit its official repository: https://github.com/kermitt2/pdfalto



