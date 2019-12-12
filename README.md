# jenkins2-with-docker
Learning :: How to install/config the Continuous Integration Server with Jenkins on Docker 

* Jenkins master 
* Jenkins data to keep all configuration such as plugins and jobs of Jenkins

# build image
* docker build -t jenkins-data -f data/Dockerfile .
* docker build -t <you tag jenkins2> -f master/Dockerfile .

# get jenkins admin password
docker exec <container id> cat /var/jenkins_home/secrets/initialAdminPassword

# use docker compose 
docker-compose up -d 

# use docker command line
mkdir /var/log/jenkins
docker run -p 8080:8080 -p 50000:50000 --name=jenkins-master -v /var/log/jenkins:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock  -d <limweb/jenkins-dind or you tag image id>
