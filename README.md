<h1 align="center">
  <img alt="SonarQube" src="logo.svg" width="250px" /><br>
  <b>SonarQube Community Edition: your best buddy for code quality and security</b> :white_check_mark:
</h1>

<p align="center">
  <img alt="GitHub language count" src="https://img.shields.io/github/languages/count/diegomais/sonarqube?style=for-the-badge">
  <img alt="GitHub top language" src="https://img.shields.io/github/languages/top/diegomais/sonarqube?style=for-the-badge">
  <img alt="GitHub license" src="https://img.shields.io/github/license/diegomais/sonarqube?style=for-the-badge">
  <img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/diegomais/sonarqube?style=for-the-badge">
</p>

## :seat: Getting started

These instructions will get you a copy of the SonarQube Community Edition up and running on your local machine for development and testing purposes.

### Setting up the development environment

The server is build using Docker Containers. Container is a standardized unit of software. [Download Docker Desktop](https://www.docker.com/products/docker-desktop).

### Setting up the server

#### Cloning the server

You can obtain the server by running the instruction bellow on your terminal:

`git clone https://github.com/diegomais/sonarqube.git`

#### Running the database and server

You can run the database and server by executing the instruction bellow on your terminal within the project directory:

`docker-compose up`

After the server is up, you can browse SonarQube at `http://localhost:9000`.

The default System administrator credentials are admin/admin.

### Setting up the scanner

Once the SonarQube server has been installed, you're ready to install SonarScanner and begin analyzing source code. To do that, you must install and configure the scanner that is most appropriate for your needs.

1. [Download SonarScanner](https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/).
2. Create directory `~/.sonarqube`.
3. Extract files into `~/.sonarqube/sonar-scanner-X.X.X.XXXX-macosx`.
4. Add `export PATH="$HOME/.sonarqube/sonar-scanner-X.X.X.XXXX-macosx/bin:$PATH"` into `~/.zshrc`.

### Analyzing source code

#### Configuring your project

Create a configuration file in your project's root directory called `sonar-project.properties`:

```
# must be unique in a given SonarQube instance
sonar.projectKey=my:project

# Path is relative to the sonar-project.properties file. Defaults to .
#sonar.sources=.

# Encoding of the source code. Default is default system encoding
#sonar.sourceEncoding=UTF-8

# Default SonarQube server
sonar.host.url=http://localhost:9000

# Token generated when your project is created on browser
sonar.login=46dbe7b5171c84327706e73508daffd8
```

#### Running SonarScanner

Run the following command from the project base directory to launch the analysis: `sonar-scanner`. After the task is done you can check the results on browser.

#### Multiple sub-projects

You can add a configuration file inside base directory of each sub-project and executing on parent folder: `for d in ./*/ ; do (cd "$d" && sonar-scanner); done`.

---

Made with :heart: by [Diego Mais](https://diegomais.github.io/) :wave:.
