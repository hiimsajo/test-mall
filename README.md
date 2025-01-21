<h1>Try it</h1>
<div  align="center">
  <img width="50%" src="https://github.com/user-attachments/assets/b2992947-940a-40b5-a424-4f8005d95f71" alt="LOGO">
</div>
</br>
<h3 align="center">Try it 선착순 체험단 플랫폼</h3>

`Try-it` 서비스는 **대규모 트래픽 환경**에서도 안정적으로 작동하는 **MSA 기반**의 **선착순** 체험단 플랫폼 입니다. 
새로운 제품을 출시하는 기업과 체험하고 싶은 사용자를 **연결하는 서비스**를 만들었습니다. </br>

---

- **팀 명 :**  연봉1조
- **프로젝트 명 :** Try it
- **프로젝트 기간 :** 2025.01.02 - 2025.01.27
- **한줄 소개 :** 새로운 제품을 출시하는 기업과 체험하고 싶은 사용자를 연결하는 선착순 체험단 플랫폼
- **팀원 :** 손예지(리더), 신영한(부리더), 김주한, 하남규, 조승아
- **팀노션 링크 :** [💁🏻 노션 링크](https://teamsparta.notion.site/1-1-1672dc3ef51480ceb16ff07841605e7b)
- **배포 링크 :** [📮 링크](http://gateway-lb-1883933206.ap-northeast-2.elb.amazonaws.com)

## 📝 프로젝트 개요
`Try-it` 서비스는 새로운 제품을 출시하는 기업과 체험하고 싶은 사용자를 연결하는 선착순 체험단 플랫폼 입니다.</br>

## 🥅 프로젝트 목표
1. **대규모 트래픽 대응**
   - Redis와 Kafka를 활용한 비동기 처리를 통해 API 요청 200req/sec 이상 처리.
   - 동시성 문제를 해결하며 안정적인 쿠폰 발급 서비스 제공.

2. **성능 최적화**
   - Redis 기반 캐싱으로 가장 빈번하게 호출되는 api의 조회 성능을 2배 이상 향상.
   - 응답속도 개선과 함께 데이터베이스 부하 감소

3. **운영 및 배포 효율화**
   - Docker와 Github Actions를 이용한 CI/CD 파이프라인 구축으로 배포 자동화.
   - Prometheus와 Grafana를 활용한 실시간 모니터링으로 시스템 안정성 확보.

4. **데이터 일관성 및 트랜잭션 관리**
   - Kafka 를활용해 체험단 상태변경을 실시간으로 감지하고 이벤트 기반 트랜잭션 처리.
   - 대규모 트래픽이 예상되는 인기 체험단 모집 시 신청자 대기열을 안정적으로 관리
   - 중복 및 데이터 손실을 방지하는 Kafka Batch Listener 구현.
  
## KEY Summary

### 🍁 **성능 개선 : 최저가 상품 조회 성능, Redis 도입으로 3배 이상 향상**

---

1. **한 줄 요약**  
   - Redis 도입으로 기존 DB 조회보다 **348% 성능 개선**  
   - 대규모 트래픽 환경에서도 안정적인 서비스 유지  

   ![성능 개선 이미지]

2. **도입 배경**  
   - 상품의 최저가를 제공하기 위해 외부 서버에서 제공하는 타임세일 상품의 할인율과  
     상품 자체의 할인율을 비교하는 기능이 필요  

3. **기술적 선택지**  

   1. **DB 데이터 적재**  
      - 스케줄링 작업으로 짧은 시간 내 대량의 데이터를 수정하는 것은 데이터베이스에 과도한 부하 발생  
      - 상품 자체의 할인율과 타임세일 할인율을 분리하여 별도 컬럼 저장 필요  

   2. **Redis 캐싱**  
      - 실시간 최저가 할인율로 최신 정보와 가격 제공  
      - TTL 설정으로 타임세일 종료 시 자동 데이터 삭제  

   **결론:** Redis 도입을 결정하여 성능 및 효율성을 크게 개선  

---

### 🍁 **트러블 슈팅 : LazyConnectionDataSourceProxy - 불필요한 커넥션 점유 해결**

---

1. **배경**  
   - **스프링 배치 5버전 도입**  
     - 정산은 실시간이 아닌, 이용자가 적은 시간에 일괄 처리하도록 배치 선택  
     - 메인 DB와 배치 메타데이터 DB 분리 필요  
   - **배치 메타데이터 테이블 생성 필수화**  
     - 메타데이터 전용 DB를 나누는 구조로 전환  
   - **멀티 DataSource 구성**  
     - 메인 DataSource와 배치 DataSource로 데이터베이스 모듈 구분  

2. **문제**  
   - 실제 DB 요청 없이도 불필요한 커넥션 점유 발생  
     - 스프링은 트랜잭션 진입 시 커넥션 풀에서 커넥션을 점유  
     - 멀티 DataSource로 인해 두 DataSource 모두 커넥션 점유  

3. **해결 방안**  
   - **LazyConnectionDataSourceProxy 클래스 사용**  
     - 실제 DB 요청 전까지 커넥션 점유를 지연시키는 프록시 DataSource 활용  

   ![LazyConnectionDataSourceProxy 이미지]

   - 이를 통해 **실제 DB 요청 시에만 커넥션 점유**로 불필요한 리소스 낭비를 해결

## 📺 프로젝트 설계
### 🔗API 명세서 확인하기</br> -> 링크
<details>
  <summary>사용자 API</summary>
  <img alt="" src="https://github.com/user-attachments/assets/b3b42806-0558-4764-98ab-35a2a1400e46"  width="800">
</details>
<details>
  <summary>상품 API</summary>
  <img alt="" src="https://github.com/user-attachments/assets/b3b42806-0558-4764-98ab-35a2a1400e46"  width="800">
</details>

### 🔗테이블 명세서</br> -> 링크
<img alt="" src="https://github.com/user-attachments/assets/b3b42806-0558-4764-98ab-35a2a1400e46"  width="800">

### 🔗ERD</br>
<img alt="" src="https://github.com/user-attachments/assets/0afea585-b5d6-4c56-a7a2-7341f1075f67"  width="800">

### 🔗인프라 설계도</br>
<img alt="" src="https://github.com/user-attachments/assets/7f469c41-4999-444f-94cf-96441c8f1e43"  width="800">

### 🔗카프카 구조도</br>
<img alt="" src="https://github.com/user-attachments/assets/346a7fe1-f7a3-4bc4-abb4-13b28b3a8f66"  width="800">

### 🔗WBS 일정관리</br> -> 링크
<img alt="" src="https://github.com/user-attachments/assets/b3b42806-0558-4764-98ab-35a2a1400e46"  width="800">

### ➡️User flow
<img width="2800" alt="User flow" src="https://github.com/user-attachments/assets/cd22c0d1-8f4a-44e7-aea0-35a53ebd0f64">

</br>

## 🔧Tech Stack
### Tools
| Git | Github | Slack |
| :---: | :---: | :---: |
| <img alt="git logo" src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.svg" width="65" height="65" > | <img alt="github logo" src="https://techstack-generator.vercel.app/github-icon.svg" width="65" height="65"> | <img alt="Slack logo" src="https://github.com/user-attachments/assets/708bcf8f-f064-40e9-b060-a7b3438107da" height="65" width="65">|
### Back-end
| Java | PostgreSQL | Docker | AWS | Spring | Spring<br>Boot | Kafka | Redis | Zipkin |
| :---: | :---: | :---: | :---: | :---: | :---: |-------|-------|--------|
| <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/java-icon.svg" alt="icon" width="65" height="65" /></div> | <div style="display: flex; align-items: flex-start;"><img src="https://github.com/user-attachments/assets/3a2dd96d-0989-4ce0-b178-84bf23b2e60c" alt="PostgreSQL logo" width="65" height="65" /></div>| <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/docker-icon.svg" alt="icon" width="55"/></div> | <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/aws-icon.svg" alt="icon" width="65" height="65" /></div> | <img alt="spring logo" src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" height="50" width="50" > | <img alt="spring-boot logo" src="https://t1.daumcdn.net/cfile/tistory/27034D4F58E660F616" width="65" height="65" > |   <div style="display: flex; align-items: flex-start;"><img src="https://github.com/user-attachments/assets/6f1f5691-2609-4e77-a628-e84f3a54854fc" alt="Kafka logo" width="65" height="65" /></div>    |    <div style="display: flex; align-items: flex-start;"><img src="https://github.com/user-attachments/assets/88e14b10-c73e-491c-8f9a-dd43abf49b8f" alt="Redis logo" width="65" height="65" /></div>   |   <div style="display: flex; align-items: flex-start;"><img src="https://github.com/user-attachments/assets/66d6cfd6-6b67-4ecc-b9f9-5ea6c7cb4352" alt="Zipkin logo" width="65" height="65" /></div>     |
<br/>

## 🌲 Git
### Branch
- `main` : 서비스 운영 브랜치입니다.
- `dev` : 개발 환경 브랜치입니다. 개별적으로 작업했던 내용을 합치고 검토합니다.
- `feat/(서비스명)/...` : (서비스이름) 서비스별 세부 브랜치입니다.
### Commit & Pull-Request Message
|    Division    | Message |
|:--------------:| :--- |
|   "feat: ~ "   | 새로운 기능 추가 |
|   "fix: ~ "    | 버그 수정 |
| "refactor: ~ " | 기능이나 성능 개선 및 수정 |
|   "add: ~ "    | 파일이나 코드 추가 |
|  "remove: ~ "  | 파일을 삭제만 한 경우 |

## 📁 프로젝트 파일 구조
1. 마이크로서비스 아키텍처 구조<br>
프로젝트는 Microservices Architecture와 DDD(Domain-Driven Design) 기반의 Layered Architecture를 적용하여 구성되어 있습니다.
```text
├─ com.trillionares.tryit.*  // 각 마이크로서비스
│  ├─ auth                   // 인증/인가 서비스
│  ├─ config                 // Config server
│  ├─ gateway                // API Gateway
│  ├─ image-manage          // 이미지 관리 서비스
│  ├─ notification          // 알림 서비스
│  ├─ product               // 상품, 체험단 신청 서비스
│  ├─ review                // 리뷰 서비스
│  ├─ server                // Eureka Server
│  ├─ statistics            // 통계 서비스
│  └─ trial                 // 체험단 등록 
│
├─ environment              // 환경 설정
├─ loki                     // 로깅 시스템
└─ prometheus              // 모니터링 시스템
```

2. 계층형 아키텍처 구조<br>
각 마이크로서비스는 DDD 기반의 계층형 아키텍처로 구성되어 있습니다.
``` text
com.trillionares.tryit.[service-name]
├─ application             // 비즈니스 처리 계층
│  ├─ dto                 // 서비스 간 데이터 전달 객체
│  └─ service             // 비즈니스 로직 처리
│
├─ domain                 // 핵심 비즈니스 규칙 계층
│  ├─ model              // 도메인 모델/엔티티
│  └─ repository         // 레포지토리 인터페이스
│
├─ infrastructure        // 인프라스트럭처 계층
│  ├─ config            // 설정 클래스
│  └─ persistence       // 영속성 관리
│
└─ presentation         // 프레젠테이션 계층
    ├─ controller       // 컨트롤러
    └─ dto             // API 요청/응답 DTO
```
## 역할 분담 및 협업 방식
| 손예지<br> | 신영한<br> | 김주한<br> | 하남규<br> | 조승아<br> |
| :---: | :---: | :---: |:---:| :---: |
| <img alt="예지" src="https://ca.slack-edge.com/T06B9PCLY1E-U07QEFTESGP-e2b23afd15a7-512" height="100" width="100"> | <img alt="영한" src="https://ca.slack-edge.com/T06B9PCLY1E-U07S875EUBV-g9ae29003de3-512" height="100" width="100"> | <img alt="주한" src="https://ca.slack-edge.com/T06B9PCLY1E-U06QUQQ5UU8-f0cd5f6b2a58-512" height="100" width="100"> | <img alt="남규" src="https://ca.slack-edge.com/T06B9PCLY1E-U07RKNHN003-db789eae7cdc-512" height="100" width="100"> | <img alt="승아" src="https://ca.slack-edge.com/T06B9PCLY1E-U07QQLBVDDJ-1001a73273bb-512" height="100" width="100"> |
| [handyejee](https://github.com/handyejee) | [syhan7516](https://github.com/syhan7516) | [Hany-Kim](https://github.com/Hany-Kim) |     [Namgyu11](https://github.com/Namgyu11)    | [hiimsajo](https://github.com/hiimsajo) | 
|<p align="left">- 알림기능 <br/>- 아키텍쳐 설계 및 초기구성<br/>- 일정관리</p>|<p align="left">- 리뷰기능<br/>- 통계기능</p>|<p align="left">- 상품, 이미지 업로드 기능<br/>- 체험단 신청기능<br/>- AWS 배포</p>|<p align="left">- 체험단 모집<br/>- 모집상태 관리</p>|<p align="left">- 사용자 기능<br/>- JWT 기반 인증 기능<br/>- Gateway 설정</p>|

---

### **Ground Rule**

🍁 **문제 발생 시 즉시 공유**  
- 문제가 발생하면 팀원들에게 빠르게 상황을 공유하여 협력 해결.


## 성과 및 회고

### 잘된 점
- **제목**  
  - 내용

---

### 아쉬운 점
- **제목**  
  - 내용
---

### 향후 계획
- **제목**  
  - 내용

