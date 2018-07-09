FROM rocker/tidyverse:devel

# Update system software
RUN apt-get update \
  && apt-get install -y \
  # For rrricanes
  libgdal-dev \
  libproj-dev \
  vim \
  curl

# Install R packages from GitHub
RUN installGithub.r eddelbuettel/drat
