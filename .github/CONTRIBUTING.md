# Git Flow & 컨벤션 가이드

## 브랜치 전략

### 주요 브랜치
- `main`: 프로덕션 배포용 브랜치 (항상 안정적)
- `develop`: 개발 통합 브랜치 (기능 개발 완료 후 병합)

### 보조 브랜치
- `feature/*`: 새로운 기능 개발
- `bugfix/*`: 버그 수정
- `hotfix/*`: 프로덕션 긴급 수정
- `release/*`: 릴리스 준비

## 브랜치 네이밍 규칙

### Feature 브랜치
```
feature/이슈번호-간단한-설명
예: feature/123-add-grpc-service
```

### Bugfix 브랜치
```
bugfix/이슈번호-간단한-설명
예: bugfix/456-fix-null-pointer
```

### Hotfix 브랜치
```
hotfix/이슈번호-간단한-설명
예: hotfix/789-fix-critical-bug
```

### Release 브랜치
```
release/버전번호
예: release/1.0.0
```

## 커밋 메시지 컨벤션

### 형식
```
<type>(<scope>): <subject>

<body>

<footer>
```

### Type
- `feat`: 새로운 기능
- `fix`: 버그 수정
- `docs`: 문서 수정
- `style`: 코드 포맷팅, 세미콜론 누락 등
- `refactor`: 리팩토링
- `test`: 테스트 추가/수정
- `chore`: 빌드 설정, 의존성 등

### 예시
```
feat(grpc): gRPC 서버 초기 구현

- ServerBuilder를 사용한 서버 구성
- 기본 서비스 인터페이스 정의

Closes #123
```

```
fix(broker): NullPointerException 수정

메시지 처리 시 null 체크 로직 추가

Fixes #456
```

## Pull Request 규칙

### PR 제목
- 커밋 메시지와 동일한 형식 사용
- 예: `feat(grpc): gRPC 서버 구현`

### PR 설명
- 변경 사항 요약
- 관련 이슈 번호
- 테스트 방법
- 체크리스트 작성


## 작업 흐름

### 기능 개발
1. `develop` 브랜치에서 최신 코드 가져오기
   ```bash
   git checkout develop
   git pull origin develop
   ```

2. Feature 브랜치 생성
   ```bash
   git checkout -b feature/123-add-feature
   ```

3. 개발 및 커밋
   ```bash
   git add .
   git commit -m "feat: 기능 추가"
   ```

4. 원격 저장소에 푸시
   ```bash
   git push origin feature/123-add-feature
   ```

5. Pull Request 생성
   - `develop` 브랜치로 PR 생성
   - 리뷰 요청

6. 머지 후 브랜치 삭제
   ```bash
   git branch -d feature/123-add-feature
   ```

### Hotfix 작업
1. `main` 브랜치에서 Hotfix 브랜치 생성
   ```bash
   git checkout main
   git checkout -b hotfix/789-fix-critical
   ```

2. 수정 및 커밋
3. `main`과 `develop` 모두에 머지
4. 태그 생성
   ```bash
   git tag -a v1.0.1 -m "Hotfix release"
   ```

