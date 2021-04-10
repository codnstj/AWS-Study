# Installing Docker in EC2
[ec2-user@ip---]$ sudo yum install docker.io
[ec2-user@ip---]$ docker ps -a

Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?

[ec2-user@ip---]$ sudo systemctl start docker

[ec2-user@ip---]$ docker ps -a

Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get http://%2Fvar%2Frun%2Fdocker.sock/v1.40/containers/json?all=1: dial unix /var/run/docker.sock: connect: permission denied

[ec2-user@ip---]$ sudo setfacl -m user:ec2-user:rw /var/run/docker.sock
