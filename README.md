# 가구고고 백엔드

--- 

## Tech Stacks

---

- Java 17
- Spring Boot 3.2.0
    - web mvc, jpa, QueryDSL
- *DB버전*

## 폴더 구조

---

```bash
./src/main/java
    └── com.gagugogo
      └── backend
        ├── BackEndApplication.java
        ├── common
        │   ├── exception     <- 에러 처리
        │   ├── payload       <- 공통 운반 객체 //모든 API의 반환 객체 구조 통일 목적
        │   └── util          <- 유틸리티 (날짜, 검증객체 등)
        └── posts             <- 도메인 이름 (게시글, 카테고리, 유저 등 도메인 별 생성)
          ├── domain
          │   ├── constant    <- 상수 데이터 모델 //상수 변수 클래스 보다는 enum 객체 패키지로 사용하는 편이 좋지 않을까요?
          │   ├── entity      <- Persistence layer 데이터 모델
          │   ├── model       <- Buisness Layer 데이터 모델
          │   └── payload     <- End-point Layer 데이터 모델
          ├── presenter
          │   ├── controller 
          │   └── scheduler   // 예시입니다. 저희 서비스에서는 사용할 일이 없지 않을까..
          ├── repository
          │   ├── query       <- QueryDSL 클래스 패키지
          │   └── persistence <- JPA 추상화 및 구현 패키지
          │       └── impl
          └── usecase
              └── service
                  └── impl
```

## 코드 컨벤션

---

- google checkstyle 활용

1. Intellij Settings
2. Editor
3. Code Style
4. Scheme 톱니바퀴
5. Import Scheme
6. Intellij IDEA code style XML
7. 프로젝트 내 config\codestyle\intellij-java-google-style.xml 선택
8. 터미널에서 ./gradlew checkstyleMain
9. 또는 Gradle -> Tasks -> other -> checkstyleMain 실행

## 브랜치 규칙

---

> type/[issueName]#[issueNumber]
>> 예시 -> feature/게시글 작성 기능 개발#1
- 브랜치는 dev 브랜치에서 생성한다.
- 각 작업 진행 전 브랜치를 먼저 생성한다.
- 작업 영역이 겹칠 경우 상위 브랜치를 생성 후 그 하위에 작업 브랜치를 생성한다.
  - 소셜 로그인 기능의 경우 dev 브랜치에서 feature/소셜 로그인#2와 같이 생성
  - 이후 feature/소셜 로그인#2 브랜치에서 구글 로그인, 카카오 로그인, 네이버 로그인 등 생성
- 일반적으로 feature만 생성될 것으로 보이지만 기능 추가나 수정 없이 로직 수정, 구조 변경만 이루어질 경우 refactor 등을 사용

## 커밋 메시지 규칙

---

> type: Subject - #issue Number
>> 예시 -> Feat: 게시글 등록 기능 개발 - #23
- 커밋은 이슈에 대한 작업을 완료함과 무관하게 진행한다.
- 메시지의 issue Number는 생략 가능하지만 작업 추적을 위해 해당 이슈의 최종 커밋에는 포함하기를 권장한다.
### Type 종류

  | 태그 이름        | 설명                                                                      |
  | ---------------- | ------------------------------------------------------------------------- |
  | Feat             | 새로운 기능을 추가할 경우                                                 |
  | Fix              | 버그를 고친 경우                                                          |
  | Design           | CSS 등 사용자 UI 디자인 변경                                              |
  | !BREAKING CHANGE | 커다란 API 변경의 경우                                                    |
  | !HOTFIX          | 급하게 치명적인 버그를 고쳐야하는 경우                                    |
  | Style            | 코드 포맷 변경, 세미콜론 누락, 코드 수정이 없는 경우                      |
  | Refactor         | 프로덕션 코드 리팩토링                                                    |
  | Comment          | 필요한 주석 추가 및 변경                                                  |
  | Docs             | 문서를 수정한 경우                                                        |
  | Test             | 테스트 추가, 테스트 리팩토링(프로덕션 코드 변경 X)                        |
  | Chore            | 빌드 테스트 업데이트, 패키지 매니저를 설정하는 경우(프로덕션 코드 변경 X) |
  | Rename           | 파일 혹은 폴더명을 수정하거나 옮기는 작업만인 경우                        |
  | Remove           | 파일을 삭제하는 작업만 수행한 경우                                        |
