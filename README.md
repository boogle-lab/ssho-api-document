# ssho-dev-wiki
> 스쇼 개발 위키

## 프로젝트

 - ssho-core-api
   - 코어 API(Spring Boot)
   - https://github.com/ssho-lab/ssho-core-api
 - ssho-log-api
   - 로그 API(Spring Boot)
   - https://github.com/ssho-lab/ssho-log-api
 - ssho-reco-api
   - 추천 API(Flask)
   - https://github.com/ssho-lab/ssho-reco-api
 - ssho-prototype-ver2
   - 클라이언트(React Native)
   - https://github.com/ssho-lab/ssho-reco-api
 - ssho-data-analysis-server
   - 데이터 분석 및 집계 백엔드(Node.js)
   - https://github.com/ssho-lab/ssho-data-analysis-server
 - ssho-admin-web
   - 어드민 웹(React)
   - https://github.com/ssho-lab/ssho-admin-web
 - ssho-item-crawler
   - 상품 크롤러(Puppeteer)
   - https://github.com/ssho-lab/ssho-item-crawler
   
   
## 시스템 아키텍쳐
<img width="1000" alt="아키텍쳐" src="https://user-images.githubusercontent.com/23696493/103483814-29665800-4e2d-11eb-9eab-2a10432e095b.png">

 
## 인프라
  - 가상서버
    - AWS EC2(1)
      - 1GB RAM, 1vCPU
      - AWS ECS 클러스터를 가상서버 위에 설치하여 컨테이너 기반 실행
      - ssho-core-api, ssho-log-api
    - AWS EC2(2)
      - 1GB RAM, 1vCPU
      - ssho-reco-api
      - 1월중으로 해당 서버 이관 예정
    - AWS LightSail
      - 512MB RAM, 1vCPU
      - jenkins 배포를 위해 사용
 - 데이터베이스
   - MySQL
     - AWS RDB를 통한 호스팅
   - Elasticsearch
     - AWS Elasticsearch를 통한 호스팅
 - 서버리스
   - AWS Lambda
     - ssho-data-analysis-server
 - 스토리지
   - AWS S3
     - 정적 파일 저장
     - 웹 호스팅
       - ssho-admin-web

## API
 - API 명세 WIKI
   - https://github.com/ssho-lab/ssho-dev-wiki/wiki
 - 서비스별 API
   - core-api
     - http://api.ssho.tech:8080 
   - log-api
     - http://api.ssho.tech:8082 
   - reco-api
     - http://3.35.129.79:5000


## DB Table / Elasticsearch Index

#### USER (회원)(MySQL)

  | 필드   |      타입       |Default|
  |:-------------:|:-------------:|:-------------:|
  | id(PK)(AI)  |  INT(11)      |        |
  | email   |  VARCAHR(200) |        |
  | password|  VARCAHR(200) |        |
  | name    |  VARCAHR(200) |        |
  | admin   |  TINYINT(4)   |        |
  | birth   |  VARCAHR(100) |NULLABLE|
  | gender  |  VARCAHR(45)  |NULLABLE|
  | social  |  TINYINT(4)   |        |
  | channel |  VARCAHR(100) |NULLABLE|
     

#### USER CARD SET (회원 카드셋)(MySQL)

  | 필드   |      타입       |Default|
  |:-------------:|:-------------:|:-------------:|
  | id(PK)(AI)  |  INT(11)      |        |
  | userId      |  INT(11)      |        |
  | tag_id      |  VARCAHR(100) |        |
  | selected_cat  | VARCAHR(100)  |        |
  | start_price   |  VARCAHR(100) |        |
  | end_price   |  VARCAHR(100)   |        |
  | create_time  |  VARCAHR(200)  |NULLABLE|
  | title  |  TINYINT(4)          |NULLABLE|

## Jenkins
 - http://jenkins.ssho.tech:8080
 - job
    - ssho-carddeck-update-invoker
      - 회원 상품 카드덱 캐시 업데이트 invoker
      - 일정 주기마다 추천서버를 거쳐 상품 카드덱 캐시를 업데이트
    - ssho-item-crawler
      - 상품 크롤러
      - 일정 주기마다 상품 크롤링 및 상품 ES index 업데이트
