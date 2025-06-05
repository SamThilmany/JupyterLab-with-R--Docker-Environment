<a name="readme-top"></a>

<div align="center">
    <h1>JupyterLab R Environment</h1>
    <h4>A Docker Environment for Statistical Analysis using R in JupyterNotebooks</h4>
    <p>
        <img src="https://img.shields.io/badge/Version:-2.0.0-green" alt="Version 2.0.1" />
    </p>
</div>

This project provides a pre-configured Docker image to effortlessly run JupyterLab with R as the default language. The image includes essential dependencies, R installation, and popular packages like `tidyverse`, `ggplot2`, `dplyr`, and `BiocManager` for seamless data manipulation and analysis. Your notebooks will be stored in the 'notebooks' directory, ensuring organized work. Enjoy a hassle-free, reproducible, and isolated environment for your data science tasks!

## Table of Contents
<ol>
  <li>
    <a href="#getting-started">Getting Started</a>
    <ul>
      <li><a href="#prerequisites">Prerequisites</a></li>
      <li><a href="#installation">Installation</a></li>
    </ul>
  </li>
  <li><a href="#pre-installed-r-packages">Pre-installed R Packages</a></li>
  <li><a href="#versioning">Versioning</a></li>
  <li><a href="#license">License</a></li>
</ol>

## Getting Started
This guide will help you set up a running copy of **JupyterLab Environment for Statistical Analysis using R** on your machine. The Docker environment provides a seamless and isolated workspace for data science tasks, with R as the default language and popular packages pre-installed. Let's get started!

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Prerequisites
Ensure you have the following software installed on your machine. If not, download and install them from the provided official website:
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Installation
#### Step 1: Clone the Repository
Clone this Git repository to your local machine using Git:

```bash
cd /Users/your_username/path_to_install

git clone git@github.com:SamThilmany/JupyterLab-with-R--Docker-Environment.git
```

#### Step 2: Build the Docker Image
Move into the `jupyter_r` directory of the cloned project and build the container:

```bash
cd /Users/your_username/path_to_install/JupyterLab-with-R--Docker-Environment/jupyter_r

docker compose build
```

This step will take a few minutes (maybe a few minutes more than you'd like, depending on your connection speed), so make sure you grab a cup of coffee and pass the time by thinking about the big questions of humanity... ☕️

*Unfortunately, the process sometimes fails. Occasionally even several times in succession. This is usually due to a weak Internet connection; it is therefore highly advisable to be connected to the Internet via cable. 
If the process fails, you can simply enter the `build` command again. All packages that have already been downloaded were cached so that you do not have to start from scratch. If the process aborts several times, check whether packages have been successfully downloaded again in between. This indicates that it is actually due to network problems.*

#### Step 3: Run the Docker Container
Still in the `jupyter_r` directory, run:

```bash
docker compose up -d
```

#### Step 4: Access JupyterLab
Open your favourite web browser and enter the following URL into the adress bar:
- `http://127.0.0.1:8888/`

#### Step 5: Start Exploring
Congratulations! You now have a fully functional JupyterLab environment with R as the default language. Start creating new notebooks, analyzing data, and utilizing the power of R and its rich ecosystem of packages.

#### Additional Notes
- To stop the JupyterLab session, type `Ctrl + C` in the terminal where the container is running. Then type `docker compose down` to stop the Docker container.
- To start the container again in the future, repeat Step 3.
- Your notebooks will be saved in the `/Users/your_username/path_to_install/JupyterLab-with-R--Docker-Environment/notebooks/` directory on your local machine, enabling easy access and collaboration.

Enjoy your productive data science journey with the **JupyterLab Environment for Statistical Analysis using R**! If you encounter any issues or have any questions, please feel free to reach out via GitLab Issues. Happy coding!

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Pre-installed R Packages
- IRkernel
- languageserver
- devtools
- tidyverse
- showtext
- ggplot2
- ggfortify
- ggforce
- ggtext
- ggrepel
- GGally
- ggVennDiagram
- eulerr
- patchwork
- cowplot
- metR
- doParallel
- combinat
- disgenet2r (via `devtools` and GitLab)

## Pre-installed Bioconductor Packages
- fgsea
- biomaRt
- enrichplot
- DOSE
- limma
- clusterProfiler
- AnnotationDbi
- org.Hs.eg.db
- rawrr
- ComplexHeatmap
- MSstats
- MSstatsTMT

## Versioning
[Semantic Versioning](http://semver.org/) is used for versioning. For the versions
available, see the [Releases](https://github.com/SamThilmany/JupyterLab-with-R--Docker-Environment/releases).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License
This project is distributed under the Apache License 2.0. See [LICENSE](/LICENSE) for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>