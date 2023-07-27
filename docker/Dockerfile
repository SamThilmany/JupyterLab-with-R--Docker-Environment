# Use the jupyter/base-notebook image as the base
FROM jupyter/base-notebook

# Set the working directory to /app
WORKDIR /app

# Switch to the root user
USER root

# Install R and necessary system dependencies
RUN apt-get update && apt-get install -y \
    libssl-dev \
    libxml2-dev \
    libcurl4-openssl-dev \
    libfontconfig1-dev \
    libharfbuzz-dev libfribidi-dev \
    libfreetype6-dev libpng-dev libtiff5-dev libjpeg-dev \
    r-base \
    r-base-dev

# Install R kernel for JupyterLab
RUN R -e "install.packages('IRkernel', repos = 'http://cran.us.r-project.org')" && \
    R -e "IRkernel::installspec()"

# Install JupyterLab packages
RUN R -e "install.packages('IRdisplay')"

# Install some common R packages for statistical analysis
RUN R -e "install.packages('tidyverse')" && \
    R -e "install.packages('ggplot2')" && \
    R -e "install.packages('showtext')" && \
    R -e "install.packages('dplyr')" && \
    R -e "install.packages('tidyr')" && \
    R -e "install.packages('stringr')" && \
    R -e "install.packages('BiocManager')"

# Expose the Jupyter Notebook port
EXPOSE 8888

# Create JupyterLab configuration directory
RUN mkdir -p /etc/jupyter

# Add JupyterLab configuration to save notebooks in /app/notebooks
RUN echo "c.NotebookApp.notebook_dir = '/app/notebooks'" >> /etc/jupyter/jupyter_lab_config.py

# Command to run Jupyter Notebook
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]