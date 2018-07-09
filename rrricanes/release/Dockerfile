FROM rocker/tidyverse:latest

RUN apt-get update \ 
  && apt-get install -y \ 
    libgdal-dev \ 
    libproj-dev \
  && install2.r -e \
    crul \
    rgdal \
    rgeos \
    rnaturalearthdata \ 
  && installGithub.r \ 
    r-lib/fs \
    r-lib/pkgdown
