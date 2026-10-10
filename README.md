# 엘리키친 소개 페이지

부산 해운대구 좌동의 수제 밀키트·반찬 전문점 **엘리키친**을 소개하는 웹 페이지입니다. 정식 웹사이트가 만들어지기 전까지 임시로 사용합니다.

Jekyll 정적 사이트이며 GitHub Pages로 배포합니다. Emil Baehr의 [Automatic App Landing Page](https://github.com/emilbaehr/automatic-app-landing-page) 템플릿(MIT)을 바탕으로 구조를 새로 짰습니다.

## 페이지 구성

| 섹션 | 내용 |
|---|---|
| 히어로 | 가게 외관 사진, 한 줄 소개, 네이버 지도·전화 버튼, 주소·주차·포장 한 줄 |
| 사진 띠 | 매장에서 만드는 모습 5장(모바일 4장) |
| 엘리키친 이야기 | 큰 제목, 재료·조리 사진, 소개 문단 |
| 엘리키친의 약속 | 핵심 가치 3가지 |
| 엘리키친의 음식 | 음식 사진 8장(엇갈린 배치, 이름 표기 없음) |
| 오시는 길 | 주소, 전화, 주차, 대중교통, 네이버 지도 버튼, 지도 |
| 푸터 | 상호, 대표, 사업자등록번호, 주소, 전화, 네이버 지도 링크 |

## 어디를 고치면 되나

- **문구·연락처·사진 경로·색상**: 전부 `_config.yml`에 있습니다. HTML을 건드리지 않아도 됩니다.
- **사진**: `assets/photos/`. 파일을 넣고 `_config.yml`의 `gallery.items`(음식) 또는 `strip`(사진 띠)에 한 줄 추가합니다. 음식 사진은 8장(4열×2, 모바일 2열×4) 기준으로 배치됩니다. 사진을 넣기 전에 위치 정보 같은 메타데이터를 지웁니다.
- **아이콘**: `_includes/icon.html`에 인라인 SVG로 정의돼 있습니다. 외부 아이콘 폰트는 쓰지 않습니다.

### 지도

`location.naver_map_key_id`에 네이버 지도 API 클라이언트 ID를 넣으면 네이버 지도가 표시됩니다. 비어 있으면 키가 필요 없는 구글 지도 임베드가 대신 표시됩니다.

키 발급: [네이버 클라우드 플랫폼 콘솔](https://console.ncloud.com) → AI·NAVER API → Application 등록 → Maps의 **Web Dynamic Map** 선택 → Web 서비스 URL에 `http://localhost:4000`(로컬 확인용), `https://www.ellykitchen.co.kr`, `https://ellykitchen.co.kr` 등록 → 발급된 Client ID를 설정에 입력. `_config.yml`을 고친 뒤에는 서버를 다시 시작합니다.

### 비워 둔 값 (정보가 생기면 채우기)

- `location.hours`: 영업시간. 채우면 오시는 길에 한 줄 추가됩니다.
- `location.naver_map_key_id`: 네이버 지도 API 클라이언트 ID.
- `company.email`: 문의 이메일. 푸터에 표시됩니다.
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
