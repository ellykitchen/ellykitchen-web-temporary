# 엘리키친 소개 페이지

부산 해운대구 좌동의 수제 밀키트·반찬 전문점 **엘리키친**을 소개하는 웹 페이지입니다. 정식 웹사이트가 만들어지기 전까지 임시로 사용합니다.

Jekyll 정적 사이트이며 GitHub Pages로 배포합니다. Emil Baehr의 [Automatic App Landing Page](https://github.com/emilbaehr/automatic-app-landing-page) 템플릿(MIT)을 바탕으로 구조를 새로 짰습니다.

## 페이지 구성

메인 한 페이지에 섹션 8개가 이어집니다(2026-11-24 리뉴얼, Figma "엘리키친 앱 (개편)" 페이지 "17 소개 웹 · 리뉴얼 시안"). 섹션마다 화면 높이를 채우고, 데스크톱에서는 휠 한 번에 한 섹션씩 넘어가며 오른쪽 섹션 표시로 바로 갈 수 있습니다. 섹션 내용이 창보다 길면(글자 확대·작은 창) 보통 스크롤이 되고, 움직임 줄이기 설정이면 나타나는 움직임을 끕니다. 문구는 앱(`lib/i18n/ko.i18n.json`)의 홈·온보딩 문구와 같게 맞춥니다.

| 섹션 (id) | 내용 |
|---|---|
| 앱 다운로드 (`home`) | 전골 밀키트 사진, 앱 홈 소개 문구, App Store·Google Play 배지 |
| 엘리키친 (`story`) | 큰 이름, 소개 문단, 원형 음식 사진 6장 |
| 가입 (`signup`) | 가입 뒤 매장 확인 안내, 앱과 같은 단계 표시(가입 완료 → 매장 준비 → 주문 가능) |
| 주문서 (`ordersheet`) | 주문서 안내(1인 주방이라 수량이 정해져 있음), 앱 홈 화면 |
| 주문 과정 (`howto`) | 앱 화면 4장(메뉴 상세·주문하기·주문 상세·찜), 모바일은 가로로 넘김 |
| 픽업 (`pickup`) | 픽업 안내, 매장 사진 |
| 메뉴 (`menu`) | 메뉴 사진 8장(이름 표기 없음), 사진 유의사항 |
| 오시는 길 (`location`) | 매장 위치·주차·오시는 길·문의, 네이버 지도 버튼, 바닥글(사업자 정보·약관 링크) |

예전 주소 `/about`·`/food`·`/location`은 같은 페이지의 엘리키친·메뉴·오시는 길 섹션으로 이어집니다(`about.html` 등의 `section` 값과 `_layouts/default.html` 스크립트).

### 약관 페이지

| 주소 | 파일 | 내용 |
|---|---|---|
| `/terms` | `terms.html` | 이용약관 (레이아웃 `_layouts/legal.html`, 스타일 `_sass/legal.scss`) |
| `/privacy` | `privacy.html` | 개인정보 처리방침 (같은 레이아웃·스타일). 앱의 "[필수] 개인정보 수집 이용 동의"는 `/privacy#consent`(회원 정보 동의 표)로 연결합니다. |

`terms.html`·`privacy.html`의 본문은 검토를 마친 원본(Markdown)을 변환 스크립트로 만듭니다. 손으로 고치지 말고 원본을 고친 뒤 다시 만듭니다.

## 어디를 고치면 되나

- **문구·연락처·사진 경로·색상**: 전부 `_config.yml`에 있습니다. HTML을 건드리지 않아도 됩니다.
- **이용약관·개인정보 처리방침의 연락처**: `terms.html`·`privacy.html` 본문에 들어 있어 `_config.yml`을 고쳐도 바뀌지 않습니다. 원본(Markdown)을 고친 뒤 다시 만듭니다.
- **사진**: 메뉴 사진은 `assets/menu/`, 매장 사진은 `assets/photos/`. 파일을 넣고 `_config.yml`의 해당 섹션(`story.photos`·`menu.items` 등)에 한 줄 추가합니다. 메뉴 사진은 8장(4열×2, 모바일 2열×4) 기준으로 배치됩니다. 사진을 넣기 전에 위치 정보 같은 메타데이터를 지웁니다.
- **앱 화면**: `assets/app/`. Figma "00 스토어 · 스크린샷"의 App Store 기기 화면을 내보낸 것입니다. 앱 화면이 바뀌면 다시 내보냅니다.
- **스토어 배지·링크**: 배지 그림은 `assets/badges/`(App Store·Google Play 배지 이미지), 링크는 `_config.yml`의 `app`.
- **아이콘**: `_includes/icon.html`에 인라인 SVG로 정의돼 있습니다. 외부 아이콘 폰트는 쓰지 않습니다.

### 지도

메인에는 지도를 직접 띄우지 않고 [네이버 지도에서 보기] 버튼(`location.naver_map_url`)으로 연결합니다. `_config.yml`의 `lat`·`lng`·`naver_map_key_id`는 지금 쓰지 않습니다(지도를 다시 넣을 때 씀).

### 비워 둔 값 (정보가 생기면 채우기)

- `location.hours`: 영업시간. 채우면 오시는 길에 한 줄 추가됩니다.
- `location.naver_map_key_id`: 네이버 지도 API 클라이언트 ID.
- `company.kakao_channel`: 카카오톡 채널 URL.

## 로컬 실행

Ruby와 Bundler가 필요합니다.

```bash
bundle install
bundle exec jekyll serve
```

브라우저에서 http://localhost:4000 을 엽니다. `_config.yml`을 고친 뒤에는 서버를 다시 시작해야 반영됩니다.

## 배포

GitHub Pages에서 `main` 브랜치를 빌드·배포합니다. 대표 주소는 `CNAME`의 `www.ellykitchen.co.kr`이고, `ellykitchen.co.kr`로 들어오면 대표 주소로 이동합니다. DNS(가비아)에는 루트 도메인 A 레코드 4개(GitHub Pages IP)와 `www` CNAME(`ellykitchen.github.io`)이 있으며, 메일(하이웍스) MX·SPF 레코드는 그대로 둡니다.

## 사진 출처

- 가게 외관 2장: 엘리키친 제공
- 음식·재료 사진(`gallery-*`, `about-*`): 엘리키친이 네이버 플레이스에 올린 업체 사진. 웹용으로 크기를 줄여 넣었습니다.
- 사진 띠(`strip-*`): 엘리키친 인스타그램 게시물 사진.

## 라이선스

[MIT License](LICENSE)
