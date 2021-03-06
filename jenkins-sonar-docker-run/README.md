# A custom image and docker-compose files for running Jenkins, SonarQube

Creates a new image based on Jenkins with Docker installed and the proper docker group created.  
Also adds the 'jenkins' user to the docker group.
Runs a Jenkins container with https on port 8443.
It also enables Docker within the container.

Nexxt, the Compose file starts up SonarQube container with an embedded database.

## Running the containers
1) Clone this repo
2) Navigate to this subfolder in your local copy
3) Before running the container, create a host location folder to map to jenkins home:
```
mkdir -p /var/jenkins_home
chown -R 1000:1000 /var/jenkins_home/
```
3) Run ```docker-compose up -d```
4) Gradle is problematic in this case.  Make sure that /var/jenkins_home/.gradle is owned by the jenkins user, and not root:
```sudo chown devuser:devuser /var/jenkins_home/.gradle```