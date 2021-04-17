> Route53

- 높은 가용성과 확장성이 뛰어난 클라우드 DNS 웹서비스
- 인터넷 애플리케이션으로 라우팅 할수 있게 해줌
```
  www.examples.com 과 같은 주소를 IPV4 주소나 IPV6 로 변환한다.
```

> EC2
- 서버 클라우드 서비스 (메모리) 제공
- 서버 라이선스 제공
RDS
ELB
VPC
Cloud Front
S3
IAM => AWS 계정 분배
가용성 => 가용 영역
watchcloud


엘라스틱 빈스톡 구조
: EC2 + RDS + watchcloud + 
(t2.xlarge) + (?요금측정 실행)


or 

오토 스케일링       +       WatchCloud    +     
(EC2 + RDS)              ()