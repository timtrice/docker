FROM rocker/tidyverse:3.4.4

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