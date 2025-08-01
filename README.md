# 🛠️ User Service Setup Guide

## ✅ 1. MySQL 데이터베이스 복원

- 이 프로젝트에는 `user_db` 관련 SQL 덤프 파일들이 포함되어 있습니다.
- 아래 `.sql` 파일들을 MySQL에 import 해주세요: <ueers 과 post는 필수가 아닙니다.>
  - `user_db_users.sql`
  - `user_db_spot_image.sql`
  - `user_db_post.sql`
  - `user_db_tourist_spot.sql`

### 💡 Import 방법 (MySQL Workbench 기준)
1. MySQL Workbench 실행
2. 상단 메뉴 → `Server > Data Import`
3. 각 파일을 `Import from Self-Contained File`로 선택
4. 대상 스키마는 `user_db`
5. `Start Import` 클릭

또는 커맨드라인에서:
bash
mysql -u root -p user_db < user_db_users.sql

## ✅ 2. 서버 URL 및 Gateway URL 설정

서비스가 서로 통신하기 위해 다음 두 가지 환경변수를 반드시 설정해야 합니다:

---
[결과물_22012231_김동하.pdf](https://github.com/user-attachments/files/21539722/_22012231_.pdf)

### 🔗 GATEWAY_URL (API Gateway 주소)

`UserController` 등에서는 Gateway 주소를 아래와 같이 사용합니다:
실행 컴퓨터에 맞게 설정하여야 합니다 
ex)  로컬 실행 시 : GATEWAY_URL=http://localhost:8080
```kotlin 
@Value("\${GATEWAY_URL:http://gyetrip.iptime.org:8080}")
