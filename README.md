<h1 align= "center"> 에너지 밸런스 검색</h1>

### :house: 배포 URL


<br/>

### 🏗 프로젝트 구조도

```

```

### :exclamation: 설치방법

```
1. npm install
2. npm start
```

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

### :clapper: 구현내용

#### 1. 대화목록 데이터 모델 구성

```
- 메시지의 데이터 모델에는 userId, userName, profileImage, content, date
- typescript를 이용하여 각각 데이터 모델에 type을 지정해 주었습니다.
```
#### 2. 로그인 유저 관리

```
- redux를 이용하여, 로그인 유저 상태 관리
- 현재 로그인된 유저, 채팅창에서 *표시
```
#### 3. 채팅 기능

```
- redux를 이용하여, 메시지 Post,Delete 기능 구현
- shift + enter는 줄바꿈 , enter는 메시지 보내기 기능 구분
- 입력창이 빈칸일시 메시지 보내기 기능 작동안함.
- 답장 버튼 누를시, 회신 메시지 
- 채팅 입력 컴포넌트 UI 구현
- textarea 글자 입력 길이에 따라 textarea의 height 값이 변경되는 기능.
- 텍스트 줄바꿈 또는 작성한 텍스트 수정할 때 textarea의 높이 값이 변경됩니다.
```
![채팅 기능](https://user-images.githubusercontent.com/77766718/153698875-9bcf2d93-435a-472c-882f-37c6df39ed77.gif)





#### 4. nav바 및 side바 UI 구현

```
- nav바 및 aside바 전체 UI 구현
- nav바에 로그인한 유저의 프로필 이미지가 표시됩니다.
```

