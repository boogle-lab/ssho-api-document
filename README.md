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
