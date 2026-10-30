# DAYS ON 메타 광고 리포트

Meta Marketing API로 DAYS ON 메타 광고계정 2개를 매일 자동 수집해 대시보드로 보여줍니다.

| 계정 | 광고계정 ID | 데이터 폴더 |
|---|---|---|
| 메타 협력광고 | 841547815503451 | `data/collab/` |
| 메타 외부링크 | 791581078215593 | `data/ext/` |

대시보드 상단 드롭다운: DAYS ON 전체(두 계정 합산·계정별 비교) / 협력광고 / 외부링크

## 처음 설정
1. Settings › Secrets and variables › Actions › New repository secret
   - `META_ACCESS_TOKEN` — 두 광고계정을 모두 할당한 시스템 사용자 토큰 (`ads_read`, `read_insights`)
   - (선택) 외부링크 계정이 다른 포트폴리오라 토큰이 따로면 `META_ACCESS_TOKEN_EXT`
2. Actions › 메타 데이터 업데이트 › Run workflow › 일수 `180`
3. 매일 05:47(KST) 자동 갱신

수집 항목·기준은 `scripts/fetch_meta.py` 주석 참고 (구매는 omni_purchase 우선, 주차는 매월 1일 시작 고정).

- 연령·성별은 광고세트 단위로 수집해 제품(광고세트명 두 번째 칸)별로 볼 수 있음
- 캠페인 목표별 메뉴는 광고세트 최적화 이벤트(`adsets.json`)로 트래픽 / 구매전환 / 기타전환(장바구니·콘텐츠 조회)을 나눔
- 기기별 데이터는 수집하지 않음
