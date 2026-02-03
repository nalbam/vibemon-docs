# vibemon-docs

Vibemon 문서 사이트

## GitHub Pages 설정

이 저장소는 `docs` 폴더를 GitHub Pages로 서빙합니다.

### 설정 방법

1. GitHub 저장소 Settings로 이동
2. 왼쪽 메뉴에서 "Pages" 선택
3. "Source" 섹션에서:
   - Branch: `main` (또는 현재 브랜치) 선택
   - Folder: `/docs` 선택
4. "Save" 클릭

### 커스텀 도메인 설정

`docs/CNAME` 파일에 `docs.vibemon.io` 도메인이 설정되어 있습니다.

DNS 설정에서 다음을 추가해야 합니다:
- CNAME 레코드: `docs.vibemon.io` → `nalbam.github.io`

또는 GitHub IP 주소를 사용한 A 레코드:
```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

### 접속

설정 완료 후 https://docs.vibemon.io 에서 접속 가능합니다.