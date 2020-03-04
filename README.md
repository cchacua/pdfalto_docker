# pdfalto_docker
Dockerfile with pdfalto


Run the container, mounting a volume with the PDF-files, and execute the following line:

```
docker exec -it <container_name> /home/pdfalto/pdfalto/pdfalto [pdfalto_options] <PDF-file> [<xml-file>]
```

You can save the xml-files in the same volume of the PDF files or you can mount a different volume to save them.


