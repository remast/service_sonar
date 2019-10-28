[![SonarCloud](https://sonarcloud.io/images/project_badges/sonarcloud-white.svg)](https://sonarcloud.io/dashboard?id=de.red6%3Aservice_sonar) ![](https://github.com/remast/service_sonar/workflows/Main%20%Workflow/badge.svg)
# Example for SonarQube with Go

Example on static analysis of Go code using SonarQube for the blog post [Go for SonarQube](https://medium.com/@remast/go-for-sonarqube-ffff5b74f33a).
This example uses Go Modules so you need to set `GO_MODULES="on"`.

## Start SonarQube

    docker run -d --name sonarqube -p 9000:9000 sonarqube


## Run SonarQube analysis

    docker run --rm --network host --mount type=volume,src="$(pwd)",dst=/opt/app,type=bind -w=/opt/app red6/docker-sonar-scanner:latest sonar-scanner -Dsonar.login=**SECRET**

## Github Action

This project also uses Github Actions as documented in [Scan your code with SonarCloud](https://github.com/SonarSource/sonarcloud-github-action).

Code coverage is analyzed during the test and then reported to SonarCloud using [upload-artifact](https://github.com/actions/upload-artifact) and [download-artifact](https://github.com/actions/download-artifact).