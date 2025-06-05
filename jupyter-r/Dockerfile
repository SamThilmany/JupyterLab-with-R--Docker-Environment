# The version has to be explicitely defined as the :latest tag does not define the ARM64 image
FROM bioconductor/bioconductor_docker:RELEASE_3_21 

## Install system dependencies
RUN apt-get update --fix-missing

RUN apt-get install -y --no-install-recommends \
        ca-certificates \
        curl && \
    update-ca-certificates

RUN apt-get install -y --no-install-recommends \
        mono-mcs \
        mono-xbuild \
        mono-devel \
        mono-complete \
        nodejs \
        npm

RUN apt-get clean
RUN apt-get autoremove -y
RUN apt-get autoclean -y
RUN rm -rf /var/lib/apt/lists/*

## Select CRAN Mirror
RUN R -e "options(download.file.method = 'libcurl', url.method = 'libcurl', BioC_mirror = 'http://bioconductor.statistik.tu-dortmund.de/', repos = c(CRAN = 'https://ftp.fau.de/cran/'))"

## Install JupyterLab
RUN pip3 install jupyter --break-system-packages

RUN R -e "if (!requireNamespace('IRkernel')) { install.packages(c('repr', 'IRdisplay', 'IRkernel')); if (!requireNamespace('IRkernel')) stop('Package "IRkernel" failed to install') }"
RUN R -e "IRkernel::installspec(user = FALSE)"
RUN R -e "if (!requireNamespace('languageserver')) { install.packages('languageserver'); if (!requireNamespace('languageserver')) stop('Package "languageserver" failed to install') }"

# Install R packages
RUN R -e "if (!requireNamespace('devtools')) { install.packages('devtools'); if (!requireNamespace('devtools')) stop('Package "devtools" failed to install') }"
RUN R -e "if (!requireNamespace('tidyverse')) { install.packages('tidyverse'); if (!requireNamespace('tidyverse')) stop('Package "tidyverse" failed to install') }"
RUN R -e "if (!requireNamespace('showtext')) { install.packages('showtext'); if (!requireNamespace('showtext')) stop('Package "showtext" failed to install') }"
RUN R -e "if (!requireNamespace('ggplot2')) { install.packages('ggplot2'); if (!requireNamespace('ggplot2')) stop('Package "ggplot2" failed to install') }"
RUN R -e "if (!requireNamespace('ggfortify')) { install.packages('ggfortify'); if (!requireNamespace('ggfortify')) stop('Package "ggfortify" failed to install') }"
RUN R -e "if (!requireNamespace('ggforce')) { install.packages('ggforce'); if (!requireNamespace('ggforce')) stop('Package "ggforce" failed to install') }"
RUN R -e "if (!requireNamespace('ggtext')) { install.packages('ggtext'); if (!requireNamespace('ggtext')) stop('Package "ggtext" failed to install') }"
RUN R -e "if (!requireNamespace('ggrepel')) { install.packages('ggrepel'); if (!requireNamespace('ggrepel')) stop('Package "ggrepel" failed to install') }"
RUN R -e "if (!requireNamespace('GGally')) { install.packages('GGally'); if (!requireNamespace('GGally')) stop('Package "GGally" failed to install') }"
RUN R -e "if (!requireNamespace('ggVennDiagram')) { install.packages('ggVennDiagram'); if (!requireNamespace('ggVennDiagram')) stop('Package "ggVennDiagram" failed to install') }"
RUN R -e "if (!requireNamespace('eulerr')) { install.packages('eulerr'); if (!requireNamespace('eulerr')) stop('Package "eulerr" failed to install') }"
RUN R -e "if (!requireNamespace('patchwork')) { install.packages('patchwork'); if (!requireNamespace('patchwork')) stop('Package "patchwork" failed to install') }"
RUN R -e "if (!requireNamespace('cowplot')) { install.packages('cowplot'); if (!requireNamespace('cowplot')) stop('Package "cowplot" failed to install') }"
RUN R -e "if (!requireNamespace('metR')) { install.packages(c('s2', 'metR')); if (!requireNamespace('metR')) stop('Package "metR" failed to install') }"
RUN R -e "if (!requireNamespace('doParallel')) { install.packages('doParallel'); if (!requireNamespace('doParallel')) stop('Package "doParallel" failed to install') }"
RUN R -e "if (!requireNamespace('combinat')) { install.packages('combinat'); if (!requireNamespace('combinat')) stop('Package "combinat" failed to install') }"

# Install GitLab packages
RUN R -e "if (!requireNamespace('disgenet2r')) { devtools::install_gitlab('medbio/disgenet2r'); if (!requireNamespace('disgenet2r')) stop('Package "disgenet2r" failed to install') }"

# Install Bioconductor packages
RUN R -e "if (!requireNamespace('fgsea')) { BiocManager::install('fgsea', ask = FALSE); if (!requireNamespace('fgsea')) stop('Package "fgsea" failed to install') }"
RUN R -e "if (!requireNamespace('biomaRt')) { BiocManager::install('biomaRt', ask = FALSE); if (!requireNamespace('biomaRt')) stop('Package "biomaRt" failed to install') }"
RUN R -e "if (!requireNamespace('enrichplot')) { BiocManager::install('enrichplot', ask = FALSE); if (!requireNamespace('enrichplot')) stop('Package "enrichplot" failed to install') }"
RUN R -e "if (!requireNamespace('DOSE')) { BiocManager::install('DOSE', ask = FALSE); if (!requireNamespace('DOSE')) stop('Package "DOSE" failed to install') }"
RUN R -e "if (!requireNamespace('limma')) { BiocManager::install('limma', ask = FALSE); if (!requireNamespace('limma')) stop('Package "limma" failed to install') }"
RUN R -e "if (!requireNamespace('clusterProfiler')) { BiocManager::install('clusterProfiler', ask = FALSE); if (!requireNamespace('clusterProfiler')) stop('Package "clusterProfiler" failed to install') }"
RUN R -e "if (!requireNamespace('AnnotationDbi')) { BiocManager::install('AnnotationDbi', ask = FALSE); if (!requireNamespace('AnnotationDbi')) stop('Package "AnnotationDbi" failed to install') }"
RUN R -e "if (!requireNamespace('org.Hs.eg.db')) { BiocManager::install('org.Hs.eg.db', ask = FALSE); if (!requireNamespace('org.Hs.eg.db')) stop('Package "org.Hs.eg.db" failed to install') }"
RUN R -e "if (!requireNamespace('rawrr')) { BiocManager::install('rawrr', ask = FALSE); if (!requireNamespace('rawrr')) stop('Package "rawrr" failed to install') }"
RUN R -e "if (!requireNamespace('ComplexHeatmap')) { BiocManager::install('ComplexHeatmap', ask = FALSE); if (!requireNamespace('ComplexHeatmap')) stop('Package "ComplexHeatmap" failed to install') }"
RUN R -e "if (!requireNamespace('MSstats')) { BiocManager::install('MSstats', ask = FALSE); if (!requireNamespace('MSstats')) stop('Package "MSstats" failed to install') }"
RUN R -e "if (!requireNamespace('MSstatsTMT')) { BiocManager::install('MSstatsTMT', ask = FALSE); if (!requireNamespace('MSstatsTMT')) stop('Package "MSstatsTMT" failed to install') }"

RUN R -e "tools::R_user_dir('rawrr', which = 'cache')"
RUN R -e "rawrr::installRawFileReaderDLLs()"
RUN R -e "rawrr::installRawrrExe()"

# Expose the Jupyter Notebook port
EXPOSE 8888

# Create JupyterLab configuration directory
RUN mkdir -p /etc/jupyter

# Add JupyterLab configuration to save notebooks in /app/notebooks
RUN echo "c.ServerApp.root_dir = '/app/notebooks'" >> /etc/jupyter/jupyter_server_config.py

# Add JupyterLab configuration to remove token
#
# Caution: This is a security hazard.
# Remove these lines if you're running the container remotely!
RUN echo "c.ServerApp.token = ''" >> /etc/jupyter/jupyter_server_config.py && \
    echo "c.ServerApp.password = ''" >> /etc/jupyter/jupyter_server_config.py

# Command to run Jupyter Notebook
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]