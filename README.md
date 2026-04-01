# syscall 어셈블리 데모 — User ↔ Kernel Mode Switch

x86-64 Linux에서 `sys_read` 시스템 콜이 호출될 때 CPU 내부에서 벌어지는 일을 단계별로 보여주는 인터랙티브 데모입니다.

## 데모

👉 **[라이브 데모 보기](https://USERNAME.github.io/syscall-demo/)** ← 배포 후 USERNAME을 자신의 GitHub 아이디로 바꿔주세요

## 다루는 내용

- **유저 모드 (ring 3)**: `mov` 명령어로 syscall 인자 세팅 → `syscall` 트랩
- **모드 전환**: CPU가 자동으로 RIP/RFLAGS 백업, 커널 핸들러로 점프
- **커널 모드 (ring 0)**: `swapgs`, 커널 스택 교체, 유저 상태 저장, 실제 I/O 처리
- **복귀**: 상태 복원 → `sysret`으로 유저 모드 복귀

## 사용법

| 조작 | 동작 |
|------|------|
| `Space` / step 버튼 | 한 단계씩 진행 |
| `R` / reset 버튼 | 처음으로 되돌리기 |
| auto play 버튼 | 자동 재생 (1.4초 간격) |

## GitHub Pages 배포 방법

1. 이 레포를 GitHub에 push
2. **Settings → Pages → Source** 에서 `main` 브랜치, `/ (root)` 선택
3. Save → 1분 내 `https://USERNAME.github.io/syscall-demo/` 에서 접근 가능

```bash
git init
git add .
git commit -m "syscall assembly demo"
git branch -M main
git remote add origin https://github.com/USERNAME/syscall-demo.git
git push -u origin main
```

## 로컬 실행

외부 의존성이 없는 단일 HTML 파일이라 브라우저에서 바로 열면 됩니다.

```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

## 기술 스택

- 순수 HTML/CSS/JS (프레임워크 없음)
- 다크 모드 자동 지원 (`prefers-color-scheme`)
- 모바일 반응형 레이아웃

## 라이선스

강의/교육 목적 자유 사용. 출처 표기 환영합니다.
