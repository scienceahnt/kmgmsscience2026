# 과학실 예약

과학실 1개를 여러 교사가 나눠 쓸 때, 교시를 눌러 미리 예약하는 웹앱입니다.
예약 데이터는 구글 시트에 쌓이고, 화면은 15초마다 갱신됩니다. (간격은 `index.html` 위쪽 `POLL_MS` 에서 바꿀 수 있습니다)

교내 와이파이에서 안 열리면 아래 도메인이 학교망에서 차단된 것입니다. 정보 담당자에게 접속 허용을 요청하세요.
`script.google.com`, `script.googleusercontent.com`, `scienceahnt.github.io`, `fonts.googleapis.com`, `fonts.gstatic.com`

## 파일

| 파일 | 올릴 곳 |
|---|---|
| `index.html` | 깃허브 저장소 최상단 |
| `manifest.json` | 같은 폴더 |
| `apple-touch-icon.png` | 같은 폴더 (아이폰 홈 화면 아이콘) |
| `icon-192.png` / `icon-512.png` / `icon-512-maskable.png` | 같은 폴더 (안드로이드·PWA) |
| `favicon-64.png` | 같은 폴더 (브라우저 탭) |
| `thumbnail.png` | 같은 폴더 (링크 미리보기) |
| `lab-booking-Code.gs` | 깃허브 아님 — 구글 시트의 Apps Script |

경로를 상대 주소로 잡아두었으니 `index.html`과 같은 폴더에 두어야 합니다.

## 설치

1. 구글 시트를 새로 만들고 확장 프로그램 > Apps Script 에 `lab-booking-Code.gs` 붙여넣기
2. 배포 > 새 배포 > 웹 앱 (실행: 나 / 액세스: 모든 사용자) → `/exec` 주소 복사
3. `index.html` 위쪽 `const API_URL = "..."` 에 그 주소 넣기
4. 위 파일들을 깃허브 저장소에 올리고 Settings > Pages 에서 main / (root) 지정

`예약`, `교사` 시트는 첫 요청이 들어올 때 자동으로 만들어집니다.

## 코드를 고친 뒤

- `index.html` 등은 깃허브에 커밋하면 1~2분 뒤 반영됩니다.
- Apps Script 는 **배포 관리 > 연필 > 버전 '새 버전' > 배포** 로 올려야 주소가 유지됩니다.
  '새 배포'를 누르면 주소가 새로 생겨 `API_URL` 을 다시 바꿔야 합니다.

## 쓰는 방법

- 처음 열면 이름을 입력하고 색을 고릅니다. 기기에 기억되어 다음부터 바로 열립니다.
- 빈 칸을 누르면 예약, 내 예약을 누르면 취소 확인 창이 뜹니다.
- 오른쪽 위 주 / 월 버튼으로 주간 시간표와 월간 달력을 오갑니다.
- 이름 배지를 누르면 색 바꾸기, 다른 사람으로 전환, 등록된 선생님 삭제를 할 수 있습니다.
- 아이폰은 사파리에서 공유 > 홈 화면에 추가 를 하면 앱처럼 전체 화면으로 열립니다.

## 설정 바꾸기

`lab-booking-Code.gs` 맨 위 `CONFIG` 에서 조정합니다.

- `PERIODS` — 교시 구성 (기본값 1~7교시와 방과후)
- `ALLOW_CROSS_CANCEL` — `true` 로 바꾸면 다른 교사 예약도 취소 가능
