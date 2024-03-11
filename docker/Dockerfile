FROM rocker/rstudio:4.3.2

RUN apt-get update && apt-get install -y \
	libproj-dev \
	libgdal-dev \
	libmagick++-dev \
	libglpk-dev \
	libxml2 \
	libxt6 \
	zlib1g-dev \
	libbz2-dev \
	liblzma-dev \
	libpcre3-dev \
	libicu-dev \
	libjpeg-dev \
	libpng-dev \
	libxml2-dev \
	libglpk-dev \
	libharfbuzz-dev \
  	libfribidi-dev \
	libgit2-dev \ 
	patch \
	&& rm -rf /var/lib/apt/lists/*

# Copy project files
RUN mkdir -p /home/rstudio/project
WORKDIR /home/rstudio/project
COPY renv.lock renv.lock
COPY plotting.rmd plotting.rmd
COPY section_cluster_list_obj.rds section_cluster_list_obj.rds

# Change ownership
RUN chown -R rstudio:rstudio /home/rstudio/

RUN R -e "install.packages('renv', repos = c(CRAN = 'https://cloud.r-project.org'), lib='/usr/local/lib/R/site-library')"
RUN R -e "renv::restore()"
