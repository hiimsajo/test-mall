<h1>Try it</h1>
<div  align="center">
  <img width="24%" src="client/src/assets/logo/home_logo.png" alt="LOGO">
</div>
</br>
<h3 align="center">Spring 단기심화 2기 Ch.3 프로젝트</h3>

- **팀 명 :**  연봉1조
- **프로젝트 명 :** Try it
- **프로젝트 기간 :** 2025.01.02 - 2025.01.27
- **한줄 소개 :** 새로운 제품을 출시하는 기업과 체험하고 싶은 사용자를 연결하는 선착순 체험단 플랫폼
- **팀원 :** 손예지(리더), 신영한(부리더), 김주한, 하남규, 조승아
- **팀노션 링크 :** [💁🏻 노션 링크](https://teamsparta.notion.site/1-1-1672dc3ef51480ceb16ff07841605e7b)
- **배포 링크 :** [📮 링크](https://github.com/HERE-TRILLIONAIRES/try-and-review)

## 📝 프로젝트 개요
`Try-it` 서비스는 새로운 제품을 출시하여 고객 반응을 얻고자 하는 기업과 신제품을 체험해보고 싶어하는 다양한 사람들을 이어주는 서비스를 개발하고자 하였습니다. </br>

상품을 체험해보고 싶은 사람이라면 누구나 신청이 가능하며, SNS의 팔로워 수나 기타 영상채널의 구독자 수와는 상관없이 모두가 선착순으로 체험이 가능하여 보다 솔직한 실제 사용 후기를 플랫폼 내의 모두가 공유할 수 있는 서비스를 만들어보고자 하였습니다. </br> 
또한 고객들의 리뷰를 기반으로 하는 통계 기능을 제공하여 기업들에게 인사이트를 제공하고자 합니다. </br> 

## 🥅 프로젝트 목표
- 대규모 트래픽이 예상되는 인기 체험단 모집 시 신청자 대기열을 안정적으로 관리합니다.
- Kafka 를활용해 체험단 상태변경을 실시간으로 감지하고 이벤트 기반으로 알림을 발행하는 시스템 구축합니다.
- 자주 조회되는 정보를 캐싱해 데이터베이스의 부하를 감소시킵니다.
- 필요한 기능들에 대해 생성, 수정과 관련된 항목의 테스트코드를 작성합니다.

## 👨‍👩‍👧‍👦 Team
| 손예지<br> | 신영한<br> | 김주한<br> | 하남규<br> | 조승아<br> |
| :---: | :---: | :---: |---------| :---: |
| <img alt="예지" src="https://ca.slack-edge.com/T06B9PCLY1E-U07QEFTESGP-e2b23afd15a7-512" height="100" width="100"> | <img alt="영한" src="https://ca.slack-edge.com/T06B9PCLY1E-U07S875EUBV-g9ae29003de3-512" height="100" width="100"> | <img alt="주한" src="https://ca.slack-edge.com/T06B9PCLY1E-U06QUQQ5UU8-f0cd5f6b2a58-512" height="100" width="100"> |    <img alt="남규" src="https://ca.slack-edge.com/T06B9PCLY1E-U07RKNHN003-db789eae7cdc-512" height="100" width="100">     | <img alt="승아" src="https://ca.slack-edge.com/T06B9PCLY1E-U07QQLBVDDJ-1001a73273bb-512" height="100" width="100"> |
| [handyejee](https://github.com/handyejee) | [syhan7516](https://github.com/syhan7516) | [Hany-Kim](https://github.com/Hany-Kim) |     [Namgyu11](https://github.com/Namgyu11)    | [hiimsajo](https://github.com/hiimsajo) | 
|<p align="left">- Login <br/>- SignUp<br/>- Ledger Creat Modal</p>|<p align="left">- Header, Sidebar, Layout<br/>- Ledger Calender<br/>- Error pages</p>|<p align="left">- Home<br/>- Weather widget<br/>- Group settings modal</p>|    <p align="left">- Home<br/>- Weather widget<br/>- Group settings modal</p>     |<p align="left">- Todo CRUD<br/>- Ledger List<br/>- Hide screen<br/>- My page</p>|

## 📺 설계도
### API 명세서</br>
<img alt="" src="https://private-user-images.githubusercontent.com/125221013/404962681-733ef5a0-9df3-4194-ad59-fcf1af5ca3eb.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTQxOTAsIm5iZiI6MTczNzM5Mzg5MCwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTYyNjgxLTczM2VmNWEwLTlkZjMtNDE5NC1hZDU5LWZjZjFhZjVjYTNlYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzI0NTBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kMTg1YzYyMWI1NmM0NzdkZDVjZWJlMzY2M2M3MDY2OGRmZTViM2I0NWE4NDQxMWRjNDAwNTA4NWE2NzE5NjQ3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.ZnHyFR29QnMt613zXPn4VN9UZwHyzJHqafeR6bcA6Ms"  width="800">

### 테이블 명세서</br>
<img alt="" src="https://private-user-images.githubusercontent.com/125221013/404962681-733ef5a0-9df3-4194-ad59-fcf1af5ca3eb.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTQxOTAsIm5iZiI6MTczNzM5Mzg5MCwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTYyNjgxLTczM2VmNWEwLTlkZjMtNDE5NC1hZDU5LWZjZjFhZjVjYTNlYi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzI0NTBaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1kMTg1YzYyMWI1NmM0NzdkZDVjZWJlMzY2M2M3MDY2OGRmZTViM2I0NWE4NDQxMWRjNDAwNTA4NWE2NzE5NjQ3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.ZnHyFR29QnMt613zXPn4VN9UZwHyzJHqafeR6bcA6Ms"  width="800">

### ERD</br>
<img alt="" src="https://private-user-images.githubusercontent.com/125221013/404963868-70ada68e-f278-4e79-93a3-59fa6b1b3ee6.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTQ4OTgsIm5iZiI6MTczNzM5NDU5OCwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTYzODY4LTcwYWRhNjhlLWYyNzgtNGU3OS05M2EzLTU5ZmE2YjFiM2VlNi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzM2MzhaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05NmQyZTA4OTJhNmE3YjJkZTUzODAwNzVlMGZjNzQ2MjM2YTc3ODU4YzYwNTQ5MTVlNDI3OTk5MjlmOTRiNWI1JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9._6f_dvq4t4vu8aYTMrcSAsk5Tv5Jju_svlBTfH7cSIk"  width="800">

### 인프라 설계도</br>
<img alt="" src="https://private-user-images.githubusercontent.com/125221013/404963967-9eb6a7b6-daf0-4920-aecc-432154d788da.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTQ4OTgsIm5iZiI6MTczNzM5NDU5OCwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTYzOTY3LTllYjZhN2I2LWRhZjAtNDkyMC1hZWNjLTQzMjE1NGQ3ODhkYS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzM2MzhaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT05ZjYxNDYwOGI4MWEyZDgyNjkwYmU0MjU0NGI0ZGM5MGE0ODZmOWM4ZmM2MmI2Y2IwOWQ0YmY2NzY2ZDhiNmE5JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.gyQKLd1iezZO2aKSrmW5Zbb3sqjwE_bwCRGAHZ3B-TU"  width="800">

### 카프카 구조도</br>
<img alt="" src="https://private-user-images.githubusercontent.com/125221013/404963411-976e9fc0-0b83-41e3-bebc-8306c2e863d6.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTQ4OTgsIm5iZiI6MTczNzM5NDU5OCwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTYzNDExLTk3NmU5ZmMwLTBiODMtNDFlMy1iZWJjLTgzMDZjMmU4NjNkNi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzM2MzhaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT03MGVkNGE0NjY5ZDEzNjQ1OTA2ZThmYWIwMDcwZDQ1N2MxYTUyODU2MGRjNmVhNTI0MjQ1YjM1Y2E5NjJlY2YwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.6oRGf02jFhgTIefextMmi2-LZ8Q7fv7GPpWnUy0toC8"  width="800">

### WBS 일정관리</br>
<img alt="" src="https://private-user-images.githubusercontent.com/125221013/404966261-b26a8faa-1016-4c1e-be88-b18217e777c5.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTUwNzksIm5iZiI6MTczNzM5NDc3OSwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTY2MjYxLWIyNmE4ZmFhLTEwMTYtNGMxZS1iZTg4LWIxODIxN2U3NzdjNS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzM5MzlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yZmVkM2Q3Yzk1MDQ0OTBlZmJhNDQ5MTczMzJmM2RkMTk5MDNjZDY2MTU5NmNmYWNmMzc5MzMzMDk0OGUwMGExJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.PstbLV5Xgnvq0y1YI5dSImKG9bI0ndai-BYake-rQhc"  width="800">


## ➡️ User flow
<img width="2800" alt="User flow" src="https://private-user-images.githubusercontent.com/125221013/404963411-976e9fc0-0b83-41e3-bebc-8306c2e863d6.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MzczOTUwNzksIm5iZiI6MTczNzM5NDc3OSwicGF0aCI6Ii8xMjUyMjEwMTMvNDA0OTYzNDExLTk3NmU5ZmMwLTBiODMtNDFlMy1iZWJjLTgzMDZjMmU4NjNkNi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDEyMFQxNzM5MzlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1lYTc4OTU5MjZmNWUwYzg4MjkzYjlmNGM5MzNkNWM0M2YzN2U1OGZjYjYyN2VmYTZiM2I1YWZmOGNlODYyOTdmJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.sBxVaUFPD9YE0lMQEz4ZMX1FQarjfypjOBoiv8MVImI">

</br>

## Tech Stack
### Tools
| Git | Github | Slack |
| :---: | :---: | :---: |
| <img alt="git logo" src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.svg" width="65" height="65" > | <img alt="github logo" src="https://techstack-generator.vercel.app/github-icon.svg" width="65" height="65"> | <img alt="Slack logo" src="https://example.com/slack-logo.svg" height="65" width="65">|
### Back-end
| Java | PostgreSQL | Docker | AWS | Spring | Spring<br>Boot | Kafka | Redis | Zipkin |
| :---: | :---: | :---: | :---: | :---: | :---: |-------|-------|--------|
| <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/java-icon.svg" alt="icon" width="65" height="65" /></div> | <div style="display: flex; align-items: flex-start;"><img src="assets/postgresql-logo.svg" alt="PostgreSQL logo" width="65" height="65" /></div>| <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/docker-icon.svg" alt="icon" width="55"/></div> | <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/aws-icon.svg" alt="icon" width="65" height="65" /></div> | <img alt="spring logo" src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" height="50" width="50" > | <img alt="spring-boot logo" src="https://t1.daumcdn.net/cfile/tistory/27034D4F58E660F616" width="65" height="65" > |   <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/kafka-icon.svg" alt="Kafka logo" width="65" height="65" /></div>    |    <div style="display: flex; align-items: flex-start;"><img src="https://techstack-generator.vercel.app/redis-icon.svg" alt="Redis logo" width="65" height="65" /></div>   |   <div style="display: flex; align-items: flex-start;"><img src="assets/zipkin-logo.svg" alt="Zipkin logo" width="65" height="65" /></div>     |
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
- Microservices Architecture
- Layered Architecture + DDD
```text

```
