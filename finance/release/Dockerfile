FROM rocker/tidyverse:3.5.1

RUN apt-get update \
  && apt-get install -y \
		libglu1-mesa-dev \
		libmagick++-dev \
		python-pip \
	&& pip install virtualenv \
	&& install2.r -e -d TRUE \
		blogdown \
		bookdown \
		furrr \
		ggrepel \
		sweep \
		tibbletime \ 
		workflowr \ 
	&& installGithub.r -d TRUE \
	# No specified releases for blotter
	braverock/blotter \
	# No specified releases for quantstrat
	braverock/quantstrat \
	DavisVaughan/flyingfox \
&& R -e "flyingfox::install_zipline()"
