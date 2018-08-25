FROM rocker/tidyverse:devel

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
		furrr \
		ggrepel \
		janitor \
		sweep \
		tibbletime \ 
		workflowr \ 
	&& installGithub.r -d TRUE \
	# No specified releases for blotter
	braverock/blotter \
	# No specified releases for quantstrat
	braverock/quantstrat \
	DavisVaughan/flyingfox \
	hadley/multidplyr \
	thomasp85/patchwork \
&& R -e "flyingfox::install_zipline()"
