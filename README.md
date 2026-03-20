**--- DevOps Project 01 ---**
**#tools**
- AWS
- Git/GitHub
- Jenkins
- Docker
- sonarqube
- OWASP
- Trivy
# Steps
**1. Launch EC2 Instance**
- t2.medium
- Disk-20Gb
- Ports - Jenkins(8080), Sonarqube(9000), App(3000)
2. Install openjdk-17-jdk
3. Install jenkins
4. Install Docker
5. give permission of docker to jenkins user
6. restart jenkins
7. set up sonarqube in following way
8. docker run -d --name sonar -p 9000:9000 sonarqube:lts
9. open http://<IP>:9000 [username:admin password:admin]
10. create project in sonarqube -
- go to projects-> create project
- choose manual
- name: devops-project
- generate token and copy it and save somewhere
11. open jenkins
- manage jenkins-> plugins->install: SonarQube scanner
- manage jenkins-> system-> SonarQube Servers
- name: sonar-server -> URL: http://<IP>:9000 -> token: paste it here
12. Install trivy on server---> test it--> trivy image nginx
13. Install OWASP Dependency check on server
14. Create Your application as follwing-
- mkdir devops-project && cd devops-project
- mkdir app && cd app
- vim index.js
- vim package.json
- cd ..
15. create Dockerfile
- vim Dockerfile
16. create sonar config file
- vim sonar-project.properties
17. now push whole directory to you github repo
- you need git to be installed on server
18. create a Jenkinsfile
- new item -> pipeline
- run a pipeline...Build Now
19. verify everything
- http://<IP>:3000
- sonarqube
- for Owasp--- ls reports/
- for Trivy -- output is visible in Jenkins console output
