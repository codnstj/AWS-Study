# Installing Docker in EC2
//도커 설치
[ec2-user@ip---]$ sudo yum install docker.io
//도커 리스트 확인
[ec2-user@ip---]$ docker ps -a

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

//해결
```
[ec2-user@ip---]$ sudo systemctl start docker

[ec2-user@ip---]$ docker ps -a

Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http:// %2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json?all=1: dial unix /var/run/docker.sock: connect: permission denied

[ec2-user@ip---]$ sudo setfacl -m user:ec2-user:rw /var/run/docker.sock
```
// 기존 지라 도커 컨테이너 삭제 
[ec2-user@ip---]$ docker rm --volumes --force "jira-container"

// 지라 도커 컨테이너 설치
[ec2-user@ip---]$ docker pull cptactionhank/atlassian-jira-software:latest

// 지라 도커 컨테이너 생성
[ec2-user@ip---]$ docker create --restart=no --name "jira-container" \ --publish "8080:8080" \ --volume "hostpath:/var/atlassian/jira" \ --env "CATALINA_OPTS= -Xms1024m -Xmx1024m -Datlassian.plugin.enable.wait=300" \ cptactionhank/atlassian-jira-software:latest

//지라 도커 컨테이너 실행
[ec2-user@ip---]$ docker start --attach "jira-container"