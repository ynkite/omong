<div align="center">

<img src="docs/images/hero_flow.jpg" alt="오몽 휴대폰 화면 네 장: 첫 화면(말하기, 사진찍기, 제보하기), 사진찍기, 누를 메뉴 안내, 직원에게 보여 줄 주문서" width="100%">

# 오몽 OMONG

키오스크를 찍으면 그 가게 메뉴에서 무엇을 누를지 5개 국어 음성과 큰 글씨로 알려 주고, 막히면 「직원에게 보여주기」 로 주문서를 띄우는 키오스크 주문 도우미

[![Java](https://img.shields.io/badge/Java-21-007396?logo=openjdk&logoColor=white)](#기술-스택)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-4.1-6DB33F?logo=springboot&logoColor=white)](#기술-스택)
[![Spring AI](https://img.shields.io/badge/Spring_AI-6DB33F?logo=spring&logoColor=white)](#기술-스택)
[![Spring Data JPA](https://img.shields.io/badge/Spring_Data_JPA-6DB33F?logo=spring&logoColor=white)](#기술-스택)
[![MariaDB](https://img.shields.io/badge/MariaDB-003545?logo=mariadb&logoColor=white)](#기술-스택)
[![Thymeleaf](https://img.shields.io/badge/Thymeleaf-005F0F?logo=thymeleaf&logoColor=white)](#기술-스택)
[![Web Speech API](https://img.shields.io/badge/Web_Speech_API-4285F4?logo=googlechrome&logoColor=white)](#기술-스택)

[서비스 열기](https://omong.r-e.kr)  |  [시연 영상](https://ynkite.github.io/portfolio/assets/omong-intro.mp4)  |  [보도](https://www.newsnjeju.com/news/articleView.html?idxno=291702)

</div>

---

## 목차

- [소개](#소개)
- [화면](#화면)
- [주요 기능](#주요-기능)
- [전체 구조](#전체-구조)
- [주문까지의 흐름](#주문까지의-흐름)
- [ERD](#erd)
- [담당 작업과 팀](#담당-작업과-팀)
- [AI 활용](#ai-활용)
- [트러블슈팅](#트러블슈팅)
- [보안 점검](#보안-점검)
- [기술 스택](#기술-스택)
- [실행 방법](#실행-방법)
- [폴더 구조](#폴더-구조)

## 소개

| 항⁠목 | 내용 |
|---|---|
| 한⁠ ⁠줄 | 키오스크 주문 도우미 |
| 만⁠든⁠ ⁠이⁠유 | 화면을 읽기 어려운 외국인과 어르신도 실물 키오스크로 주문을 끝내게 하기 위해 |
| 대⁠회 | 빛나는 인재 AI Re-Local 해커톤(제주), 다문화와 배리어프리 트랙 |
| 기⁠간⁠과⁠ ⁠팀 | 2026.06.30~07.03, 팀 프로젝트 6인(개발 2명) |
| 결⁠과 | 해커톤 아이디어상, 팀원 투표 MVP |
| 서⁠비⁠스 | https://omong.r-e.kr |

## 화면

맨 위 그림은 왼쪽부터 첫 화면, 사진 찍기, 누를 메뉴 안내, 직원에게 보여 줄 주문서다.

| 단⁠계 | 화면에서 하는 일 |
|---|---|
| 1⁠.⁠ ⁠첫⁠ ⁠화⁠면 | 말하기, 사진찍기, 제보하기 중 편한 방법 선택. 글자 크게, 소리 크게 단추와 5개 국어 단추가 늘 보임 |
| 2⁠.⁠ ⁠사⁠진⁠ ⁠찍⁠기 | 키오스크 화면이나 메뉴판을 찍어 올리면 어느 가게인지 알아봄 |
| 3⁠.⁠ ⁠메⁠뉴⁠ ⁠안⁠내 | 「꿀아메리카노(HOT) 를 눌러주세요」 처럼 누를 곳을 키오스크와 같은 배치 위에 짚고 소리로도 읽음 |
| 4⁠.⁠ ⁠주⁠문⁠서 | 막히면 「직원에게 보여주기」 로 고른 메뉴와 합계를 큰 글씨로 띄움 |

<details>
<summary>데스크톱 화면 보기</summary>

<br>

<img src="docs/images/desktop.jpg" alt="데스크톱에서 연 오몽 첫 화면" width="100%">

</details>

## 주요 기능

| 기⁠능 | 설명 |
|---|---|
| 네⁠ ⁠가⁠지⁠ ⁠입⁠력 | 말하기(음성), 누르기, 사진 찍기, 제보하기 |
| 가⁠게⁠ ⁠알⁠아⁠보⁠기 | 키오스크를 찍으면 어느 가게인지 알아보고, 말로 하면 가게를 짐작해 「○○ 맞을까요?」 하고 되물음 |
| 메⁠뉴⁠ ⁠좁⁠혀⁠ ⁠가⁠기 | 「커피 맛으로 드릴까요?」 처럼 쉬운 질문으로 메뉴를 좁히고 누를 곳을 짚어 줌 |
| 5⁠개⁠ ⁠국⁠어⁠와⁠ ⁠큰⁠ ⁠글⁠씨 | 한국어, English, Tiếng Việt, 中文, 日本語. 글자 크게, 소리 크게 |
| 직⁠원⁠에⁠게⁠ ⁠보⁠여⁠주⁠기 | 고른 메뉴와 합계를 주문서로 띄움 |
| 제⁠보⁠하⁠기 | 등록되지 않은 가게의 키오스크 사진을 올리면 AI 가 메뉴를 읽고, 관리자가 확인한 뒤 등록 |
| 카⁠카⁠오⁠ ⁠로⁠그⁠인 | 카카오 계정이나 휴대폰 번호로 가입 |

## 전체 구조

AI 서버에 닿지 않아도 등록해 둔 메뉴 분류로 주문을 이어 간다. 파란 칸이 AI 다.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/diagram_arch_dark.svg">
  <img src="docs/images/diagram_arch_light.svg" alt="전체 구조: 휴대폰 브라우저(Thymeleaf, Web Speech API)가 Spring Boot 서버(가게 알아보기, 메뉴 좁혀 가기와 번역, 제보 처리, AI 호출)를 부르고, 서버는 MariaDB, 기본 데이터 JSON, AI 게이트웨이와 로컬 모델 Ollama, 카카오 로그인을 쓴다">
</picture>

## 주문까지의 흐름

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="docs/images/diagram_flow_dark.svg">
  <img src="docs/images/diagram_flow_light.svg" alt="주문 흐름: 1 입력(사진, 말하기, 누르기), 2 AI 가게 알아보기, 3 AI 메뉴 좁혀 가기, 4 누를 곳 안내, 5 막히면 직원에게 보여주기. AI 서버가 안 되면 등록해 둔 메뉴 분류를 차례로 물음. 제보는 사진에서 AI 가 메뉴를 읽고 개인정보를 가린 뒤 관리자가 승인해야 등록">
</picture>

## ERD

가게 메뉴는 브랜드마다 JSON 한 덩어리(`spec_json`)로 저장한다. 제보는 바로 등록하지 않고 `PENDING_REPORT` 에 쌓았다가 관리자가 승인하면 `KIOSK_SPEC` 으로 옮긴다.

```mermaid
erDiagram
    PENDING_REPORT }o..|| KIOSK_SPEC : "승인되면 등록"
    APP_USER ||--o{ PENDING_REPORT : "제보"

    APP_USER {
        bigint id PK
        varchar kakao_id "카카오 로그인"
        varchar provider
        varchar role "USER, ADMIN"
        datetime created_at
    }
    KIOSK_SPEC {
        varchar brand_id PK
        varchar brand_name
        longtext spec_json "화면, 메뉴, 버튼 위치"
        datetime updated_at
    }
    PENDING_REPORT {
        bigint id PK
        varchar brand_id
        varchar brand_name
        longtext spec_json "AI 가 읽은 메뉴"
        varchar reporter_name
        datetime created_at
    }
```

`APP_USER` 와 `PENDING_REPORT` 사이에는 외래 키가 없고 제보자 이름만 남기므로, 위 관계는 의미상의 관계다.

## 담당 작업과 팀

| 구⁠분 | 내용 |
|---|---|
| 담⁠당⁠ ⁠작⁠업 | 아이디어 제안과 기획, AI 연동, 대회 취지에 맞춰 AI 도구로 디자인과 기능 구현 |
| 팀 | 6인 팀(개발 2명) |

## AI 활용

### 서비스 안에서 AI 가 하는 일

| 기⁠능 | AI 가 하는 일 | AI 에 맡기지 않은 일 |
|---|---|---|
| 가⁠게⁠ ⁠알⁠아⁠보⁠기 | 사진 속 키오스크가 어느 가게인지, 말로 한 가게가 어디인지 짐작 | 메뉴와 버튼 위치(등록해 둔 가게 메뉴 데이터) |
| 메⁠뉴⁠ ⁠좁⁠혀⁠ ⁠가⁠기 | 메뉴 목록을 보고 쉬운 질문과 보기 만들기 | 실제 메뉴 이름과 가격(가게 메뉴 데이터), AI 가 안 될 때는 규칙으로 |
| 번⁠역 | 안내 문장을 사용자 언어로 | 메뉴 이름 사전(`i18n-menu.json`) |
| 제⁠보⁠ ⁠사⁠진⁠ ⁠읽⁠기 | 사진에서 메뉴 이름과 가격 읽기 | 등록 여부(관리자가 확인한 뒤에만) |

### AI 로 만든 방식

대회 취지대로 화면과 기능은 AI 도구로 만들었다. 사진 인식 모델이 메뉴를 지어내지 않도록 지시문에 「보이는 대로 읽고, 모르면 비워 두기」 조건을 넣었다.

## 트러블슈팅

<details>
<summary>1. 사진 인식 모델이 없는 메뉴를 지어낼 수 있음</summary>

<br>

| 구⁠분 | 내용 |
|---|---|
| 문⁠제 | 사진 인식 모델은 사진에 없는 메뉴 이름도 그럴듯하게 채워 넣을 수 있음 |
| 원⁠인 | 「모를 때 어떻게 할지」 를 정해 주지 않으면 모델이 빈칸을 추측으로 채움 |
| 해⁠결 | 지시문에 「보이는 대로 읽고, 확실하지 않으면 비워 두고, 항목을 지어내지 말 것」 조건을 넣음. 읽은 결과가 정해진 꼴이 아니면 쓰지 않고 다른 길로 넘김 |
| 결⁠과 | 모르는 칸은 비어서 돌아오고, 제보로 들어온 메뉴는 관리자가 확인한 뒤에만 등록 |

</details>

<details>
<summary>2. AI 모델 하나가 답을 거절하면 안내가 멈출 수 있음</summary>

<br>

| 구⁠분 | 내용 |
|---|---|
| 문⁠제 | 모델 하나가 답을 거절하거나 실패하면 그 자리에서 안내가 멈출 수 있음 |
| 원⁠인 | 안내 한 단계가 AI 답 하나에 기대는 구조 |
| 해⁠결 | 한 모델이 거절하면 다음 모델로 넘김 |
| 결⁠과 | 모델 하나가 실패해도 안내가 이어짐 |

</details>

<details>
<summary>3. AI 서버에 연결되지 않을 때도 주문을 이어 가야 함</summary>

<br>

| 구⁠분 | 내용 |
|---|---|
| 문⁠제 | AI 서버에 닿지 않으면 메뉴를 좁혀 가는 질문을 만들 수 없음 |
| 원⁠인 | 질문과 보기를 AI 가 만듦 |
| 해⁠결 | AI 서버에 연결되지 않으면 등록해 둔 메뉴 분류를 차례로 물어 고르게 하고, 그래도 막히면 「직원에게 보여주기」 로 주문서를 띄움 |
| 결⁠과 | AI 없이도 주문서까지 갈 수 있음 |

</details>

## 보안 점검

4일 동안 만든 해커톤 MVP 다. TripLinker, COGI 에 썼던 직접 만든 점검 가이드(KISA 웹 항목, OWASP Top 10, AI 기능 항목)로 코드를 다시 읽은 결과다.

### 들어 있는 보호 장치

| 기⁠준 | 지금 상태 |
|---|---|
| 개⁠인⁠정⁠보⁠(⁠책⁠임⁠ ⁠있⁠는⁠ ⁠A⁠I⁠) | 제보 사진에서 읽어 낸 글자 중 카드번호와 주민번호로 보이는 숫자를 가림(`PrivacyMaskingService`, 글자 단계) |
| AI 답 검증(LLM 지어내기) | 사진 인식 지시문에 지어내지 말라는 조건, 정해진 꼴이 아닌 답은 버림 |
| A⁠I⁠ ⁠실⁠패⁠(⁠L⁠L⁠M⁠ ⁠가⁠용⁠성⁠) | 한 모델이 거절하면 다음 모델로, AI 서버에 닿지 않으면 규칙으로 이어 감 |
| 데⁠이⁠터⁠ ⁠무⁠결⁠성 | 제보는 검수 대기함에 쌓았다가 관리자가 승인해야 등록 |
| 파일 업로드(KISA FU) | 제보 사진은 서버가 이미지로 읽어 jpg 로 다시 저장, 폴더와 파일 이름은 서버가 만듦(영문과 숫자만) |
| 비⁠밀⁠ ⁠값 | 키는 설정 파일과 환경 변수로만 넣고, 설정 파일은 저장소에서 추적하지 않음 |

### 남긴 것

| 남⁠긴⁠ ⁠것 | 이유 |
|---|---|
| 사진 속 얼굴과 번호 가리기 | 이미지 단계 가림은 자리(`maskImage`)만 있고 아직 만들지 않음 |
| 운⁠영⁠ ⁠전⁠환⁠ ⁠전⁠ ⁠정⁠리 | 해커톤 시연용으로 둔 설정을 운영용으로 바꾸는 일이 남음. 세부는 공개하지 않음 |

## 기술 스택

| 영⁠역 | 기술 |
|---|---|
| 백⁠엔⁠드 | Java 21, Spring Boot 4.1, Spring AI, Spring Data JPA |
| 화⁠면 | Thymeleaf, JavaScript, Web Speech API(음성 인식과 읽어 주기) |
| D⁠B | MariaDB |
| A⁠I | AI 게이트웨이로 여러 모델 호출, 로컬 모델 Ollama |
| 외⁠부⁠ ⁠서⁠비⁠스 | 카카오 로그인 |

## 실행 방법

설정 값은 저장소에 없다. 아래 키를 설정 파일이나 환경 변수로 넣은 뒤 실행한다.

<details>
<summary>필요한 설정 키 이름</summary>

<br>

| 묶⁠음 | 키 이름 |
|---|---|
| D⁠B | `spring.datasource.*` |
| A⁠I | `kiosk.ai.provider`, `kiosk.ai.models`, `kiosk.ai.fast-models`, `mindlogic.base-url`, `mindlogic.api-key`, `spring.ai.anthropic.*`, `spring.ai.ollama.*` |
| 카⁠카⁠오⁠ ⁠로⁠그⁠인 | `kakao.rest-api-key`, `kakao.client-secret`, `kakao.redirect-uri` |
| 제⁠보⁠ ⁠사⁠진 | `kiosk.upload-dir` |

</details>

```bash
./gradlew bootRun
# 도우미 앱: http://localhost:8080/
```

## 폴더 구조

```text
src/main/java/com/jingdari/omong
├── controller        화면, API, 로그인, 관리자
├── service
│   ├── AiService             AI 호출(한 모델이 거절하면 다음 모델)
│   ├── RecognitionService    가게 알아보기(사진, 말)
│   ├── FunnelService         메뉴 좁혀 가기
│   ├── VisionService         사진에서 메뉴 읽기
│   ├── ReportService         제보 처리
│   ├── PrivacyMaskingService 개인정보 가림
│   └── TranslationService    번역
├── model             가게, 메뉴, 언어, 회원, 제보
└── dto               요청과 응답
src/main/resources
├── templates         Thymeleaf 화면
├── static/js         app.js(화면 흐름, 규칙 대체), i18n.js(5개 국어)
└── data              kiosks.json(기본 가게), i18n-menu.json(메뉴 이름 사전)
```
