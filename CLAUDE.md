# 카페인 조절 기록지 (coffee-log)

커피 섭취 · 수면 · 수행도를 매일 기록하고 카페인을 조절하는 PWA. 휴대폰 홈 화면에 설치해서 사용.

- GitHub: https://github.com/sidd0262-ops/coffee-log
- 파일: index.html(화면과 로직 전부), sw.js(서비스 워커), manifest.webmanifest, 아이콘(icon.svg, icon-192/512, icon-maskable, apple-touch-icon)
- reminders/: 시간대별 캘린더 알림 파일(.ics, 144개). 캘린더에 추가하면 정해진 시각에 기록 알림
- 빌드 없음: 정적 파일 그대로 배포. 로컬 미리보기는 `python -m http.server 8765`
- 데이터는 기기 브라우저 localStorage에만 저장: 기록 `coffee-log-v1`, 목표 `coffee-goal`
  - 키 구조를 바꾸면 기존 기록이 사라질 수 있으니 반드시 마이그레이션 코드 추가
  - 기기 간 이동은 앱의 공유 시트 백업 사용 (7일 동안 백업하지 않으면 알림)

## 진행 상황
- 2026-11-05: 공유 시트로 백업, 7일 미백업 알림
- 2026-11-06: 연간 요약 차트, 매일 캘린더 알림
- 2026-11-09: 목표 수정 기능, 무섭취일 추가, 점수 1~10 동그라미 선택과 설명, 수면 점수는 높을수록 나쁨으로 안내 문구 정리, 앱 아이콘을 케멕스 라인아트(네이비·애쉬블루)로 변경

## 내 프로젝트 생태계 (모든 저장소 공통)
GitHub 계정 `sidd0262-ops` 를 기준으로 Windows PC · Mac · 아이폰(클라우드 세션)에서 같은 코드를 씁니다.

| 저장소 | 내용 |
| --- | --- |
| Short-english | 쇼츠로 배우는 영어 회화 PWA (TypeScript, Render 배포) |
| coffee-log | 카페인 조절 기록지 PWA |
| psy-Cultural-adaptation | 문화적응 여정 PWA (Firebase) |
| timebox | 나만 쓰는 한지 타임박스 PWA |
| mind-project | 마음프로젝트 소개 페이지 |

- **폴더 위치:** Windows `Desktop\클로드 코드\` · Mac `~/Desktop/클로드 코드/` (폴더 이름은 저장소 이름과 달라도 됨)
- **한 번에 최신화:** Short-english 저장소의 `workspace/sync-all.ps1`(Windows) · `workspace/sync-all.sh`(Mac). 없는 저장소는 받고, 있는 저장소는 pull
- **작업 규칙**
  1. 시작 전 `git pull` (클라우드 세션은 항상 최신으로 시작)
  2. 끝나면 커밋하고 `git push` (사용자에게 확인 후). 로컬에만 두면 다른 기기에서 안 보임
  3. 같은 저장소를 두 기기에서 동시에 수정하지 않기
  4. API 키·비밀번호는 코드와 채팅에 쓰지 않기 (`.env`, 배포 서비스 환경변수 사용)
  5. 작업이 끝나면 이 파일의 "진행 상황"을 갱신해서 다음 기기·세션이 이어받게 하기
- 사용자와는 한국어로 대화
