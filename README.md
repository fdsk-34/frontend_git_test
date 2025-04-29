좋습니다! 아래는 **Spring Boot, MySQL, React**를 사용하여 구현한 **자바 기반 프로젝트 설명서**입니다. 이 문서는 실제 발표, 보고서 제출, README 등에 활용할 수 있도록 구성되어 있습니다.

---

## 📄 Java Full-Stack 프로젝트 설명서  
**프로젝트명: 자동차 쇼핑몰 시스템**

---

### 1. 📌 프로젝트 개요

- **프로젝트 이름**: 자동차 쇼핑몰 시스템 (CarShop)
- **개발 기간**: 2025.03.01 ~ 2025.04.20
- **개발 목적**: 사용자가 웹에서 자동차를 조회하고, 장바구니에 담아 주문까지 할 수 있는 온라인 자동차 쇼핑몰 시스템을 구축
- **특징**:
  - 백엔드: Java + Spring Boot 기반의 REST API
  - 프론트엔드: React를 이용한 동적 웹 UI
  - DB: MySQL 기반의 관계형 데이터 관리
  - 배포: Docker, AWS EC2

---

### 2. 🛠️ 기술 스택

| 구분         | 기술 상세                                     |
|--------------|-----------------------------------------------|
| Frontend     | React, Axios, React Router, Tailwind CSS 등   |
| Backend      | Java 17, Spring Boot 3.x, Spring Security, JPA|
| Database     | MySQL 8.x, Spring Data JPA                    |
| 배포         | Docker, AWS EC2, RDS                          |
| 개발 도구    | VSCode, IntelliJ, GitHub, MySQL Workbench     |

---

### 3. ⚙️ 주요 기능

#### 🧑 사용자 측 기능
- 회원가입 / 로그인 (JWT 인증 방식)
- 자동차 목록 조회 및 검색
- 자동차 상세 정보 확인
- 장바구니 담기 및 주문하기
- 마이페이지에서 주문 내역 확인

#### 🔐 관리자 측 기능
- 자동차 등록, 수정, 삭제
- 주문 상태 변경 (배송 준비, 배송 완료 등)
- 사용자 계정 및 권한 관리

---

### 4. 🗃️ 데이터베이스 설계 (ERD 요약)

#### 주요 테이블

- **Users**
  - id, username, email, password, role
- **Cars**
  - id, model, brand, year, price, image_url, stock
- **Orders**
  - id, user_id (FK), order_date, status
- **OrderItems**
  - id, order_id (FK), car_id (FK), quantity

> 설계 도구: MySQL Workbench

---

### 5. 🧩 시스템 아키텍처

```
[ React (Frontend) ]
        |
        ↓
[ Spring Boot REST API ]
        |
        ↓
[ MySQL Database ]
```

- **프론트엔드**: React에서 Axios를 통해 백엔드 API 호출
- **백엔드**: Spring Boot가 REST API 제공 및 인증/인가 처리
- **DB**: MySQL에서 데이터 저장 및 쿼리 처리
- **보안**: Spring Security + JWT 토큰 기반 로그인 처리

---

### 6. 🔧 주요 구현 예시

#### 1) Spring Boot – 로그인 API
```java
@PostMapping("/login")
public ResponseEntity<?> login(@RequestBody LoginRequest request) {
    String token = userService.authenticate(request);
    return ResponseEntity.ok(new JwtResponse(token));
}
```

#### 2) React – 자동차 목록 컴포넌트
```javascript
useEffect(() => {
  axios.get("/api/cars")
    .then(res => setCars(res.data))
    .catch(err => console.error(err));
}, []);
```

---

### 7. 📦 프로젝트 폴더 구조

#### 📁 Backend (Spring Boot)
```
com.carshop
├── controller
├── service
├── repository
├── entity
├── dto
└── config
```

#### 📁 Frontend (React)
```
src/
├── components
├── pages
├── api
├── store (Redux or Zustand)
└── App.js
```

---

### 8. ☁️ 배포 환경

- **Docker**
  - Spring Boot 애플리케이션과 MySQL을 컨테이너로 실행
- **AWS**
  - EC2: 백엔드 서버 호스팅
  - RDS: MySQL 호스팅
  - S3 (옵션): 이미지 파일 저장

> CI/CD는 GitHub Actions로 자동화 가능 (선택적 적용)

---

### 9. 🧪 테스트 및 검증

- **단위 테스트**: JUnit, Mockito로 서비스 계층 테스트
- **통합 테스트**: Spring Boot Test 사용
- **프론트엔드 테스트**: Cypress 또는 React Testing Library로 컴포넌트 테스트 (선택)

---

### 10. 🔮 향후 개선 방향

- 결제 API 연동 (KakaoPay, Toss 등)
- 관리자용 대시보드 UI 개선
- 사용자 리뷰/별점 기능 추가
- 검색 자동완성 및 추천 알고리즘 적용
- 모바일 앱 연동 (React Native)

---


