## Run

```
docker run \
  -dti \
  -e PASSWORD=hurdat \
  -p 8787:8787 \
  --name hurdat \
  -v /home/timtrice/Projects/timtrice/HURDAT:/home/rstudio/HURDAT \
  timtrice/hurdat:release
```

## Shell

```
docker exec -ti hurdat /bin/bash
```
