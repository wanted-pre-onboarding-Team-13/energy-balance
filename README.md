<h1 align= "center"> 에너지 밸런스</h1>

### :house: 배포 URL
http://energybalance-team13.s3-website.ap-northeast-2.amazonaws.com

<br/>

### 🏗 프로젝트 구조도

```
│  App.css
│  App.tsx
│  index.css
│  index.tsx
│  react-app-env.d.ts
│  
├─components
│  └─Search
│          index.tsx
│          ItemList.tsx
│          MatchItem.tsx
│          ProductCard.tsx
│          Searched.tsx
│          SearchInput.tsx
│          style.scss
│          
├─types
│      db.ts
│      props.ts
│      
└─utils
    ├─constants
    │      order.ts
    │      
    ├─functions
    │      dataFilter.ts
    │      dataSortingSlice.ts
  
```

### :exclamation: 설치방법

```
1. npm install
2. npm start
```

### :palm_tree: 설계설명
<details>
    <summary>프로젝트 설계</summary>
    
### :mag_right: 문제 파악
소비자가 원하는 제품을 쉽게 찾을 수 있게 하려는 이유는 근본적으로 해당 제품을 판매해 매출을 늘리고자 하는 이유라고 생각합니다.

따라서, 소비자의 구매 행동에 대한 유형을 알아볼 필요가 있습니다.

소비자의 구매행동에는 5가지 과정이 존재합니다.
```
1. 문제인식
2. 정보탐색
3. 대안의 평가
4. 구매의사 결정
5. 구매후 행동
```
이 단계들 중에서, 사실상 구매자가 해당 플랫폼에서 제품을 찾게되는 순간은, 4~5단계에 해당한다고 생각합니다.

이 때, 소비자의 구매 행동에 관여하는 요인에는, 첨부한 표를 참고하면 알 수 있습니다.
<p><img src="https://user-images.githubusercontent.com/65812122/154698028-79fcbc27-0616-488e-8dd0-ff71d633092d.png" ></p>

<details>
    <summary>설명링크</summary>

https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=sudream2003&logNo=220220913575

</details>
<br/>

### :mag_right: 데이터 설계
기존에 제공된 데이터는 제품명과 브랜드, 두 컬럼(속성)을 가진 구조입니다.

<p><img src="https://user-images.githubusercontent.com/65812122/154698091-fbf8b844-ae17-44ec-9f67-41e75bd77d2b.png"></p>


이런 경우에는, 소비자가 어떤 것을 보고 구매를 결정할지 판단할 근거가 부족하다고 생각합니다. 

따라서, 가장 중요하다 생각하는 세가지 속성을 추가하였습니다.
```
- 평점
- 재구매 비율
- 제품 구매자가 구매한 다른 제품
```

<p><img src="https://user-images.githubusercontent.com/65812122/154698101-2e366833-3746-4d7e-ade6-ef33e4558db8.png"></p>


평점은 가장 쉽게 제품을 판단할 수 있는 근거가 될 수 있습니다. 하지만, 현재에는, 평점에 대한 신뢰도가 점점 낮아지고 있기 때문에,(마케팅 등등...) 실질적으로 구매가 되고 있다는 증거가 될 수 있는 재구매, 비율 또한 추가하였습니다.

또한, 해당 제품 구매자가 구매한 다른 제품을 노출함으로써, 다른 제품에 대한 판매도 노려볼 수 있다 생각하여 추가하였습니다.

<br/>

### :mag_right: 검색 기능

최근 검색한 내용은 LocalStorage를  사용하여, 재 방문 시, 최근 검색어를 볼 수 있게 구현 하였고, 많은 데이터가 쌓이는 것을 방지해 최근 검색한 5개의 목록만 나오도록 하고, 만일 검색한 목록에 이미 존재한다면, 기존에 있는 것은 제거하고 최신 검색이 반영되도록 설계하였습니다.

또한, 입력한 단어와 일치하는 제품이 없을 때는, 재 구매 비율이 높은 제품 5개를 노출하도록 하였고, 입력한 단어와 일치하는  제품이 있을 시에는, 재 구매 비율과, 평점 순으로 선택하여 노출하도록 하였습니다.

해당 검색어 클릭 후, 검색 시, 해당 제품 혹은, 단어가 포함 되어있는 제품 정보들이 나열 되며, 해당 제품을 구매한 사람들이, 구매한 다른 제품 또한, 노출되도록 하였습니다.

</details>

<br/>

### :clapper: 구현내용

```
- 검색어 입력시 최근 검색한 5개 이력을 출력합니다.
- 입력한 검색어와 일치하는 제품들이 존재할 시에, 기본적으로 재구매율이 높은 순으로 정보를 출력하고,
  평점이 높은 순으로 출력을 할 수 있도록 선택할 수 있는 버튼을 만들었습니다.
- 만일 검색어와 일치하는 제품이 없다면, 전체 제품중에서, 선택한 정렬 조건에 맞는 제품들을 출력합니다.
- 검색을 진행 시, 제품들이 나열 되며, 제품 카드에는, 다른 소비자가 같이 구매한 상품에 대해 정보를 표시 할 수 있도록 하였습니다.
```

