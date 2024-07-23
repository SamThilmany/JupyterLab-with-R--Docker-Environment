FROM debian:bookworm

# Install requirements
RUN apt-get clean && apt-get update \
    && apt-get install -y --no-install-recommends \
        # Libraries
        build-essential \
        libssl-dev \
        libxml2-dev \
        # libcurl4-openssl-dev \
        libcurl4-gnutls-dev \
        libfontconfig1-dev \
        libharfbuzz-dev \
        libfribidi-dev \
        libproj-dev \
        libglpk-dev \
        libgit2-dev \
        # Graphics
        libfreetype6-dev \
        libpng-dev \
        libtiff5-dev \
        libjpeg-dev \
        # Mono
        mono-mcs \
        mono-xbuild \
        # Locales
        locales \
    && rm -rf /var/lib/apt/lists/*

# Configure the default locale
RUN echo "en_US.UTF-8 UTF-8" >> /etc/locale.gen \
    && locale-gen en_US.UTF-8 \
    && /usr/sbin/update-locale LANG=en_US.UTF-8 \
    && rm -rf /var/lib/apt/lists/*

ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US.UTF-8

# Use Debian unstable via pinning
RUN echo "deb http://http.debian.net/debian sid main" > /etc/apt/sources.list.d/debian-unstable.list \
    && echo 'APT::Default-Release "bookworm";' > /etc/apt/apt.conf.d/default \
    && echo 'APT::Install-Recommends "false";' > /etc/apt/apt.conf.d/90local-no-recommends

# Install R and littler, Create a link for littler in /usr/local/bin
ENV R_BASE_VERSION 4.2.2

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        r-base=${R_BASE_VERSION}.* \
        r-base-dev=${R_BASE_VERSION}.* \
        r-base-core=${R_BASE_VERSION}.* \
        r-recommended=${R_BASE_VERSION}.* \
        libopenblas0-pthread \
        littler \
        r-cran-docopt \
        r-cran-littler \
    && chown root:staff "/usr/local/lib/R/site-library" \
    && chmod g+ws "/usr/local/lib/R/site-library" \
    && ln -s /usr/lib/R/site-library/littler/examples/install.r /usr/local/bin/install.r \
    && ln -s /usr/lib/R/site-library/littler/examples/install2.r /usr/local/bin/install2.r \
    && ln -s /usr/lib/R/site-library/littler/examples/installBioc.r /usr/local/bin/installBioc.r \
    && ln -s /usr/lib/R/site-library/littler/examples/installDeps.r /usr/local/bin/installDeps.r \
    && ln -s /usr/lib/R/site-library/littler/examples/installGithub.r /usr/local/bin/installGithub.r \
    && ln -s /usr/lib/R/site-library/littler/examples/testInstalled.r /usr/local/bin/testInstalled.r \
    && rm -rf /tmp/downloaded_packages/ /tmp/*.rds \
    && rm -rf /var/lib/apt/lists/*

## Install JupyterLab
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        python3-full \
        python3-dev \
        python3-pip \
    && pip3 install jupyter --break-system-packages \
    && rm -rf /var/lib/apt/lists/*

RUN R -e "install.packages('IRkernel')"
RUN R -e "IRkernel::installspec(user = FALSE)"

# Install R packages
RUN R -e "install.packages('devtools')"

RUN R -e "install.packages(c( \
    'tidyverse', \
    'showtext', \
    'ggplot2', \
    'GGally', \
    'ggVennDiagram', \
    'cowplot', \
    'ggrepel', \
    'doParallel', \
    'combinat', \
    'BiocManager' \
))"

RUN R -e "devtools::install_github('YuLab-SMU/ggtree')"
RUN R -e "devtools::install_gitlab('medbio/disgenet2r')"

# Install Bioconductor packages
RUN R -e "BiocManager::install(c( \
    'limma', \
    'clusterProfiler', \
    'AnnotationsDbi', \
    'org.Hs.eg.db', \
    'enrichplot', \
    'rawrr' \
), update = TRUE, ask = FALSE)"

RUN R -e "tools::R_user_dir('rawrr', which = 'cache')" &&\
    R -e "rawrr::installRawFileReaderDLLs()" &&\
    R -e "rawrr::buildRawrrExe()"

# Expose the Jupyter Notebook port
EXPOSE 8888

# Create JupyterLab configuration directory
RUN mkdir -p /etc/jupyter

# Add JupyterLab configuration to save notebooks in /app/notebooks
RUN echo "c.NotebookApp.notebook_dir = '/app/notebooks'" >> /etc/jupyter/jupyter_lab_config.py
RUN echo "c.MappingKernelManager.kernel_cmd_timeout = 3600" >> /etc/jupyter/jupyter_notebook_config.py

# Command to run Jupyter Notebook
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]