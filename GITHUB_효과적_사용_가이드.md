# GitHub 효과적 사용 가이드

## 1. 저장소(Repository) 설정

### 1.1 저장소 생성 및 초기화
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/username/repository.git
git push -u origin main
```

### 1.2 .gitignore 설정
- 버전 관리가 필요 없는 파일 지정 (node_modules/, .env, 캐시 파일 등)
- 프로젝트 타입에 맞는 .gitignore 템플릿 사용

### 1.3 README.md 작성
- 프로젝트 설명과 목표
- 설치 및 사용 방법
- 기여 방법
- 라이선스 정보

---

## 2. 커밋(Commit) 관리

### 2.1 커밋 메시지 작성 규칙
```
[Type]: 한 줄 요약 (50자 이내)

상세 설명 (선택사항)
- 무엇을 했는지
- 왜 했는지
- 부작용이 있는지

Type:
- feat: 새로운 기능
- fix: 버그 수정
- docs: 문서 변경
- style: 코드 스타일 변경
- refactor: 코드 리팩토링
- perf: 성능 개선
- test: 테스트 추가
- chore: 빌드, 패키지 변경
```

### 2.2 커밋 주기
- 작은 단위로 자주 커밋하기 (한 기능당 하나의 커밋)
- 관련 없는 변경사항을 섞지 않기
- 테스트 후 커밋하기

---

## 3. 브랜치(Branch) 전략

### 3.1 브랜치 명명 규칙
```
- main: 배포 가능한 안정 버전
- develop: 개발 중인 버전
- feature/기능이름: 새로운 기능
- bugfix/버그이름: 버그 수정
- hotfix/긴급수정: 긴급 버그 수정
```

### 3.2 브랜치 생성 및 관리
```bash
# 새 브랜치 생성 및 전환
git checkout -b feature/새기능

# 원격 브랜치 추적
git checkout --track origin/develop

# 로컬 브랜치 목록
git branch -l

# 원격 브랜치 목록
git branch -r

# 브랜치 삭제
git branch -d feature/완료된기능
```

### 3.3 Git Flow 전략
```
main (배포)
  ↑
release branch (최종 테스트)
  ↑
develop (개발 통합)
  ↑
feature branches (기능 개발)
```

---

## 4. Pull Request(PR) 활용

### 4.1 PR 생성 전 체크리스트
- [ ] 최신 코드로 동기화 (`git pull`)
- [ ] 코드 리뷰 가능하도록 정리
- [ ] 테스트 완료 및 통과
- [ ] 문서 업데이트
- [ ] 불필요한 커밋 정리 (rebase)

### 4.2 효과적인 PR 설명
```markdown
## 설명
이 PR은 [무엇을] 변경합니다.

## 타입
- [ ] 새 기능
- [ ] 버그 수정
- [ ] 문서 변경

## 변경 사항
- 변경사항 1
- 변경사항 2

## 테스트 방법
1. 단계 1
2. 단계 2

## 스크린샷 (필요시)
[이미지 첨부]

## 관련 이슈
Closes #123
```

### 4.3 PR 리뷰 받기
- 리뷰어에게 명확한 설명 제공
- 피드백을 건설적으로 받아들이기
- 요청된 변경사항 적용 후 재요청

---

## 5. 코드 리뷰

### 5.1 리뷰 시 확인 사항
- [ ] 코드가 요구사항을 충족하는가?
- [ ] 코드 스타일이 일관성 있는가?
- [ ] 버그나 보안 취약점이 있는가?
- [ ] 테스트가 충분한가?
- [ ] 문서가 업데이트되었는가?

### 5.2 효과적인 피드백
- 구체적이고 친절하게 작성
- 개선할 점만 지적하기
- 대안 제시하기
- 칭찬할 점도 언급하기

---

## 6. 이슈(Issues) 관리

### 6.1 이슈 작성
```markdown
## 문제 설명
명확하고 간결하게 설명

## 재현 방법
1. 단계 1
2. 단계 2

## 예상 결과
어떻게 동작해야 하는가?

## 실제 결과
실제 동작 결과

## 환경
- OS: [예: macOS 12.0]
- 버전: [예: 1.0.0]
```

### 6.2 이슈 라벨 활용
- bug: 버그 보고
- enhancement: 기능 개선
- documentation: 문서
- help wanted: 도움이 필요한 작업
- good first issue: 초보자 친화적

---

## 7. 병합(Merge) 및 충돌 해결

### 7.1 Merge 전 확인
```bash
# 최신 변경사항 동기화
git fetch origin
git rebase origin/main

# 로컬에서 테스트
npm test
```

### 7.2 충돌 해결
```bash
# 충돌 파일 확인
git status

# 텍스트 에디터에서 수정
# <<<<<<< HEAD
# ======= 
# >>>>>>> branch-name

# 수정 후 추가 및 커밋
git add .
git commit -m "Resolve merge conflict"
```

### 7.3 Merge 전략
- **Fast-forward merge**: 선형 히스토리
- **Three-way merge**: 병합 커밋 생성
- **Squash merge**: 커밋 합치기 (린 히스토리)

---

## 8. 협업 베스트 프랙티스

### 8.1 커뮤니케이션
- 이슈나 디스커션에서 먼저 논의
- PR 템플릿 활용으로 일관성 유지
- 명확한 코드 리뷰 피드백

### 8.2 코드 품질
- 자동화 도구 활용 (Linter, Formatter)
- CI/CD 파이프라인 설정
- 테스트 커버리지 유지

### 8.3 문서화
- 코드 주석 작성
- API 문서 작성
- CONTRIBUTING.md 작성

### 8.4 보안
- 민감한 정보 버전 관리 금지 (.env)
- 강한 인증 설정 (2FA)
- 규칙적인 의존성 업데이트

---

## 9. 유용한 Git 명령어

### 9.1 일상적인 명령어
```bash
# 상태 확인
git status

# 변경사항 확인
git diff
git diff --staged

# 커밋 히스토리 보기
git log --oneline --graph --all

# 특정 파일 히스토리
git log -p filename

# 원격 저장소와 동기화
git fetch origin
git pull origin main
```

### 9.2 커밋 수정
```bash
# 마지막 커밋 메시지 수정
git commit --amend -m "새 메시지"

# 마지막 커밋에 파일 추가
git add forgotten_file
git commit --amend --no-edit

# 커밋 히스토리 정리
git rebase -i HEAD~3
```

### 9.3 되돌리기
```bash
# 작업 디렉토리 변경 취소
git checkout -- filename

# 스테이징 취소
git reset HEAD filename

# 커밋 취소 (히스토리 유지)
git revert commit-hash

# 커밋 취소 (히스토리 변경)
git reset --hard commit-hash
```

---

## 10. 자동화 도구

### 10.1 GitHub Actions
- CI/CD 자동화
- 테스트 자동 실행
- 배포 자동화

### 10.2 Branch Protection Rules
- 리뷰 승인 필수
- 상태 확인 필수 (테스트 통과)
- 최신 브랜치 유지 필수

### 10.3 자동 포맷팅 도구
- Prettier: 코드 포맷팅
- ESLint: 코드 스타일 검사
- Husky + pre-commit hooks: 자동 검사

---

## 11. 오픈소스 프로젝트 기여

### 11.1 기여 전 단계
1. 프로젝트 문서 읽기
2. CONTRIBUTING.md 확인
3. 이슈 또는 디스커션 먼저 확인
4. Fork하여 로컬에서 작업

### 11.2 기여 절차
```bash
# Fork 저장소를 로컬에 클론
git clone https://github.com/yourname/repository.git
git remote add upstream https://github.com/original/repository.git

# 기능 브랜치 생성
git checkout -b feature/새기능

# 변경사항 커밋
git commit -m "feat: 새 기능 추가"

# 원본 저장소 동기화
git fetch upstream
git rebase upstream/main

# Push 후 PR 생성
git push origin feature/새기능
```

---

## 12. 문제 해결

### 12.1 자주 발생하는 문제
- **푸시 거부**: `git pull` 후 다시 시도
- **병합 충돌**: 수동으로 파일 편집 후 해결
- **잘못된 커밋**: `git revert` 또는 `git reset` 사용
- **분리된 HEAD**: `git checkout main` 으로 돌아가기

### 12.2 디버깅
```bash
# 특정 행 변경 추적
git blame filename

# 특정 커밋 내용 보기
git show commit-hash

# 손실된 커밋 복구
git reflog
git checkout lost-commit-hash
```

---

## 참고 자료
- [Git 공식 문서](https://git-scm.com/doc)
- [GitHub 가이드](https://guides.github.com/)
- [Git 한국어 완벽 가이드](https://git-scm.com/book/ko/v2)
- [Conventional Commits](https://www.conventionalcommits.org/ko/)
