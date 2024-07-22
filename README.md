# 2024-07-18 ~ 2024-07-23 DS2기 DataThon<br>
1조 김학준, 김찬영, 이찬우

DATASET
https://www.kaggle.com/competitions/airbnb-recruiting-new-user-bookings/data

- 데이터셋 설명
    - **신규 회원의 첫 여행 국가 예측 데이터셋**
    1. **train_users_2.csv, test_users.csv(country_destination 목표 변수 이므로 없음)**
    - ID :  사용자 id
    → session 데이터셋과 연동할 때 필요
    → 연동 후 학습할 때는 필요가 없는 컬럼 이므로 drop
    - date_account_created : 계정 생성 날짜
    → 계정 생성부터 첫 예약 까지의 시간은 어느 정도인가?
    - **timestamp_first_active**: 첫 활동 타임스탬프 (20100101215619 - 2010년 1월 1일 21시 56분 19초)
    - **date_first_booking**: 첫 예약 날짜
    → 계절 또는 월에 따라 특정 나라에 대한 수요 급증을 예측할 수도 있음
    → 이를 바탕으로 프로모션 전략을 개발할 수 있음
    - gender : 성별
    → 성별에 따른 선호 국가를 알 수 있음
    → 성별과 목적지 국가의 관계를 카이제곱 검정을 통해 분석
    - age : 나이
    → 나이에 따른 선호 국가를 알 수 있음
    → 나이와 목적지 국가의 관계를 회귀 분석
    - **signup_method**: 가입 방법
    → basic, facebook, goolge 3가지가 존재 해당 컬럼은 광고 또는 프로모션 부분과 연관 지을 수 있음
    - **signup_flow**: 사용자가 가입하기 위해 온 페이지
    → 해당 컬럼은 광고 또는 프로모션 부분과 연관 지을 수 있으나 숫자에 대한 자세한 정보가 부족함.
    - **language**: 국제 언어 선호도
    → 국제 언어 선호도와 목적지 국가의 관계를 카이제곱 검정을 통해 분석
    - **affiliate_channel**: 유입 경로
    → 어떠한 경로를 통해 들어왔는가?
    1. direct : URL 또는 북마크를 통해 사이트에 유입된 경우
    2. sem-brand : 브랜드 키워드를 포함한 검색 엔진을 통해 유입된 경우
    3. sem-non-brand : 브랜드 키워드가 아닌 검색 엔진을 통해 유입된 경우
    4. other : 다양한 경로로 유입된 경우
    5. seo : 검색엔진 최적화를 통해 유입된 경우
    6. content : 블로그, 기사, 리뷰 등 콘텐츠 마케팅을 통해 유입된 경우
    7. remarketing : 이전에 사이트를 방문한 사용자를 대상으로 한 마케팅을 통해 유입된 경우
    - **affiliate_provider**: 광고 출처 예: google, craigslist, other
    → 어느 사이트를 통해 유입이 되는지 분석할 수 있음
    → 사이트 광고를 기획할 수 있음
    - **first_affiliate_tracked**: 사용자가 가입 전에 처음으로 상호작용한 마케팅
    → 에어비앤비에 처음으로 접한 마케팅을 나타냄
    → 해당 데이터를 통해 어떠한 마케팅이 효과적인지 알 수 있음
    - **signup_app**: 가입에 사용된 앱
    - **first_device_type**: 첫 기기 유형
    - **first_browser**: 첫 브라우저
    - **country_destination**: 예측할 목표 변수 (목적지 국가)
    
    1. **sample_submission.csv_NDF.csv - 제출 양식 예시**
    - ID : 사용자 id
    - country : 사용자의 목적지 국가 (해당 파일의 경우 NDF를 목적지로 한 사용자 예측)
    
    **3. sessions.csv - 사용자 웹 세션 로그**
    
    - **user_id**: 사용자 ID (users 테이블의 'id'와 연결)
    - **action**: 사용자의 행동
    - **action_type**: 행동 유형
    - **action_detail**: 행동 세부사항
    - **device_type**: 기기 유형
    - **secs_elapsed**: 경과 시간 (초)
    
    1. **countries.csv [파일] - 목적지 국가(목표 변수)의 정보 (해당 데이터 셋은 참고 사항)**
    - **country_destination**: 목적지 국가의 코드
    - **lat_destination**: 목적지 국가의 위도
    - **lng_destination**: 목적지 국가의 경도
    - **distance_km**: 출발지(미국)로부터 목적지 국가까지의 거리(킬로미터 단위).
    - **destination_km2**: 목적지 국가의 면적(제곱 킬로미터 단위).
    - **destination_language**: 목적지 국가의 주요 언어
    - **language_levenshtein_distance**: 목적지 국가의 주요 언어와 사용자의 언어(영어) 간의 레벤슈타인 거리. 
    레벤슈타인 거리는 두 문자열 사이의 편집 거리로, 문자열을 같게 만들기 위해 필요한 삽입, 삭제, 대체 연산의 최소 개수를 나타냅니다. 값이 낮을수록 언어가 더 유사함을 의미합니다.
    
    1. **age_gender_bkts.csv [파일] - 연령대, 성별별 인구 수 (해당 데이터 셋은 참고 사항)**
    - **age_bucket**: 연령대 그룹
    - **country_destination**: 국가
    - **gender**: 성별
    - **population_in_thousands**: 해당 연령대와 성별의 인구 수를 천 명 단위로 나타냅니다.
    - **year**: 2015년
