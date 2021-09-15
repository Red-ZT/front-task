## 매물정보를 출력하고 스크롤 해서 볼수 있는 화면을 제작합니다.

## 요구사항

- api가 주어집니다. (하단 참조)
- 화면에 진입하면 1페이지를 요청하여 응답받은 매물정보를 위에서부터 아래로 출력되게 리스팅 합니다.
- 화면의 끝에 다다르면 페이지를 증가시켜(최초페이지는 1) 다음 데이터를 아래에 추가합니다.
- 데이터가 더이상 없다고 판단되면 추가하는 액션을 중지합니다.
- 아이템을 클릭하면 modal에 상세정보를 출력하고 조회가 이루어졌다는 api call을 합니다.
- 주소형식은 
  - bubun이 있을 경우 `<sido> <sigungu> <dong> <bonbun>-<bubun>` 입니다.
    - 예시 (봉천동 100-1 번지) 
  - bubun이 없을 경우 `<sido> <sigungu> <dong> <bonbun>` 입니다.
    - 예시 (봉천동 100 번지)
- 가격이 여러개일 경우 보증금이 제일 높은 것을 출력합니다.

## 참고사항
- 제공되는 데이터는 테스트를 위한 가짜 데이터입니다.
- 화면에 출력되는 리스트와 상세정보는 언급되어있는 항목 이외에는 자유롭게 배치해주세요
- react, vuejs, angular 중 자유롭게 골라서 작성해주시면 됩니다.
- css preprocessor의 제약은 없습니다.
- css framework은 bootstrap 5를 이용해 주세요.
- redux나 vuex등의 상태관리는 필수사항은 아닙니다.
- 제출은 압축파일로 전달해 주시거나, 원하는 공유 git 저장소에 작성하고 공유해도 됩니다.

## 선택사항
- 디자인 감각이 있다면 뽐내주시면 감사하겠습니다.

## api 명세
### 리스트
`GET http://api.testing.zipt.cc/properties?page=1`
```
[
  {
    id: 200888,
    createdAt: '2017-12-03T12:01:29.000Z', // 등록일
    manageFee: 0, // 관리비
    floorNumber: 1, // 층수
    area: 47.52, // 면적 (제곱미터)
    isAdvertising: true, // 광고중
    prices: [{
      contract: '월세', // 계약형태
      deposit: 1000, // 보증금
      monthly: 45, // 월세
    }],
    buildingType: '일반주택', // 건물형태
    sido: '서울특별시',
    sigungu: '은평구',
    dong: '양재동',
    bonbun: 389,
    bubun: 9,
    mainPurpose: '공동주택' // 주용도
  },
]
```
  
### 조회
```
POST http://api.testing.zipt.cc/properties/<id>/hit
(status code 200, 응답본문없음)
```
