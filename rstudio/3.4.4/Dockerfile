FROM rocker/tidyverse:3.4.4

# Update system software
RUN apt-get update \
  && apt-get install -y \
    # For rrricanes
    libgdal-dev \
    libproj-dev \
    # For the littler R package
    r-cran-littler \
    # These next two are for XLConnect (a dependency of tidyquant)
    openjdk-8-jdk \
		r-cran-rjava \
    # Database drivers
    unixodbc  \
    unixodbc-dev \
    tdsodbc \
    odbc-postgresql \
    libsqliteodbc \
    # Needed to add the Microsoft sources below.
    apt-transport-https \
    # This is for me.
    vim \
    curl \
		wget \
		# Python stuff
		python-pip \
		python3-pip \
		python-numpy \ 
		python-scipy \ 
		python-pandas \
    # For MS SQL Server \ need to install ODBC 13 Driver (17 not avail as of now).
  && curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add - \
  && curl https://packages.microsoft.com/config/debian/8/prod.list > /etc/apt/sources.list.d/mssql-release.list \
  && apt-get update \
  && ACCEPT_EULA=Y apt-get install msodbcsql \
  # Set java conf
  && R CMD javareconf \
	# Install virtualenv
	&& pip install virtualenv \ 
  && install2.r -e \
    blogdown \
    corrplot \
		crul \
    ggrepel \
		Hmisc \
    miniUI \
    pander \
    PKI \
    RCurl \
		rgdal \
		rgeos \
    RJSONIO \
    rnaturalearthdata \
    rsconnect \
		servr \
    skimr \
    sweep \
    tibbletime \
    tidyquant \
    timetk \
  && install2.r -e -r https://timtrice.github.io/drat/ \
    rrricanesdata \
  && installGithub.r \
    DavisVaughan/flyingfox \
		DavisVaughan/furrr \ 
		eddelbuettel/drat \
		r-dbi/DBI \
    r-dbi/odbc \
    r-dbi/RMariaDB \
    r-dbi/RPostgres \
		r-lib/fs \
		r-lib/pkgdown \
    ropensci/rrricanes \
		timtrice/HURDAT \
    timtrice/NCDCStormEvents \
    yihui/xfun \
	# tinytex
	&& wget -q0- "https://github.com/yihui/tinytex/raw/master/tools/install-unx.sh" | sh \
  && echo "# set CRAN mirrors\n \
    options(blogdown.hugo.dir = '/home/rstudio/bin/')\n" \
    >> /usr/local/lib/R/etc/Rprofile.site \
  && R -e "blogdown::install_hugo()" \
	&& R -e "flyingfox::install_zipline()" \
  && mkdir -p /home/rstudio/.rstudio/monitored/user-settings \
  && git config --global user.email "tim.trice@gmail.com" \
  && git config --global user.name "Tim Trice"

# Set RStudio preferences
RUN mkdir -p .rstudio/monitored/user-settings
WORKDIR /home/rstudio/.rstudio/monitored/user-settings
RUN wget https://gist.githubusercontent.com/timtrice/94a679b51388faf99ef7918c7bdaff8d/raw/9a52ffebd1e2e8587918a31ff8e962110b816936/user-settings
# Change ownership of rstudio dir
WORKDIR /home/rstudio
RUN chown -R rstudio:rstudio /home/rstudio/.rstudio
