FROM rocker/tidyverse:3.5.1

# Update system software
RUN apt-get update \
  && apt-get install -y \
  # For rrricanes
  libgdal-dev \
  libproj-dev \
  vim \
    curl \ 
	&& installGithub.r -d TRUE \
    eddelbuettel/drat \
    ropensci/rrricanes \
    ropensci/rrricanesdata
