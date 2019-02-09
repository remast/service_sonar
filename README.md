# Example for SonarQube with Go

Example on static analysis of Go code using SonarQube.

## Start SonarQube

    docker run -d --name sonarqube -p 9000:9000 sonarqube


## Run SonarQube analysis

    docker run --rm --network host --mount type=volume,src="$(pwd)",dst=/opt/app,type=bind -w=/opt/app red6/docker-sonar-scanner:latest sonar-scanner -Dsonar.login=**SECRET**