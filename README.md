<a name="readme-top"></a>

# JupyterLab Environment for Statistical Analysis using R

This project provides a pre-configured Docker image to effortlessly run JupyterLab with R as the default language. The image includes essential dependencies, R installation, and popular packages like tidyverse, ggplot2, dplyr, and tidyr for seamless data manipulation and analysis. Your notebooks will be stored in the 'notebooks' directory, ensuring organized work. Enjoy a hassle-free, reproducible, and isolated environment for your data science tasks!

## Table of Contents
<details>
  <summary>Open the Table of Contents</summary>
  <ol>
    <li><a href="#getting-started">Getting Started</a></li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#versioning">Versioning</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

## Getting Started

This guide will help you set up a running copy of **JupyterLab Environment for Statistical Analysis using R** on your machine. The Docker environment provides a seamless and isolated workspace for data science tasks, with R as the default language and popular packages pre-installed. Let's get started!

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Prerequisites

Ensure you have the following software installed on your machine. If not, download and install them from the provided official website:
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com) or preferably [Sourcetree](https://www.sourcetreeapp.com)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Installation

#### Step 1: Clone the Repository

Clone this GitLab repository to your local machine using Git:

```bash
cd /Users/your_username/path_to_install

git clone git@github.com:SamThilmany/JupyterLab-with-R--Docker-Environment.git
```

or using Sourcetree:

    New... > Clone from URL

- **Source URL**: `git@github.com:SamThilmany/JupyterLab-with-R--Docker-Environment.git`
- **Destination Path**: `/Users/your_username/path_to_install/JupyterLab-with-R--Docker-Environment` (path on your local machine where you want the environment to be installed)
- **Name**: `JupyterLab-with-R--Docker-Environment`

If you want to change the name, you can do so as long as the **Name** is equivalent to the project folder name in **Destination Path**, *e.g.*:

- **Destination Path**: `/Users/your_username/path_to_install/Your-Awesome-Name` (path on your local machine where you want the environment to be installed)
- **Name**: `Your-Awesome-Name`

Click "Clone".

#### Step 2: Build the Docker Image

Build the Docker image:

```bash
cd /Users/your_username/path_to_install/jupyterlab-with-r-docker

docker-compose build
```

#### Step 3: Run the Docker Container

```bash
cd /Users/your_username/path_to_install/jupyterlab-with-r-docker

docker-compose up
```

#### Step 4: Access JupyterLab
Copy the URL from the terminal output into the adress bar of your favourite browser.

The URL has a format like `http://127.0.0.1:8888/lab?token=14a67f16044064336d2c86c55a48c3c44a815c080cb5584e`.

#### Step 5: Start Exploring
Congratulations! You now have a fully functional JupyterLab environment with R as the default language. Start creating new notebooks, analyzing data, and utilizing the power of R and its rich ecosystem of packages.

#### Additional Notes
- To stop the JupyterLab session and the Docker container, press `Ctrl + C` on Windows and `CMD + C` on macOS in the terminal where the container is running or click the "Stop"-button on the "Containers" pane in the Docker Desktop app.
- To start the container again in the future, repeat Step 3 or click the "Play"-button on the "Containers" pane in the Docker Desktop app.
- Your notebooks will be saved in the `/Users/your_username/path_to_install/jupyterlab-with-r-docker/notebooks/` directory on your local machine, enabling easy access and collaboration.

Enjoy your productive data science journey with the **JupyterLab Environment for Statistical Analysis using R**! If you encounter any issues or have any questions, please feel free to reach out via GitLab Issues. Happy coding!

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Versioning

[Semantic Versioning](http://semver.org/) is used for versioning. For the versions
available, see the [tags on this
repository](https://gitlab.com/SamThilmany/jupyterlab-with-r-docker/-/tags).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

This project is distributed under the Apache License 2.0. See [LICENSE](/LICENSE) for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>