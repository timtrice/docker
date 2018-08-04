FROM rocker/tidyverse:3.4.4

RUN apt-get update \
  && apt-get install -y \
		libglu1-mesa-dev \
		libmagick++-dev \
		python-pip \
	&& pip install virtualenv \
	&& install2.r -e -d TRUE \
		blogdown \
		bookdown \
		DT \
		ggrepel \
		janitor \
		sweep \
		tibbletime \ 
		workflowr \ 
	&& installGithub.r -d TRUE \
		DavisVaughan/flyingfox \
		DavisVaughan/furrr \
&& R -e "flyingfox::install_zipline()"
