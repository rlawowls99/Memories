
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>일반인이 독학한 운동 팁</title>
  <link rel="stylesheet" href="./css/style.css">
  <style>
    ul {
      list-style-type: none;
      margin: 0;
      padding: 0;
      overflow: visible;  
      /* 드롭다운메뉴가 확장될 때 메뉴 공간이 부족하여 오버플로우 발생
         overflow: visible; 은 오버클로우되는 콘텐츠를 잘라내지 않고 
         영역 범위 밖까지 콘텐츠를 출력함
         overflow: hidden은 오버클로우되는 콘텐츠를 잘라냄. */
      background-color: #333;
      position: sticky;
      top:0px;
      /* position: sticky는 미리 정의한 위치에 도달하기 전에는 
                   다른 요소와 함께 스크롤 됨
         위치를 정의하기 위해 left, right, top, bottom 속성 사용
         top:0px; 은 화면(뷰포트)의 상단 0px 위치를 지정
         ul 요소는 뷰포트의 상단 0px 위치에 도달하면 sticky가 됨. 
         sticky는 화면에 마치 붙여놓은 것처럼 위치가 고정되는 것을 의미  
         스크롤 할 때 다른 요소는 함께 스크롤되지만 
         ul요소는 상단 0px 위치에 고정되어 움직이지 않음.  */
    }

    li {
      /* float: left; */
      display: inline-block;
      /* 가로방향으로 메뉴를 만들기 위해 두가지 방법 모두 사용 가능
         float: left;  => li항목을 float(부유)시키고 왼쪽부터 차례로 배치 
         display: inline-block; => 기본적으로 li는 display: block 요소임
                                   즉, li항목 출력 후 줄바꿈이 일어남
         inline-block은 줄바꿈이 일어나지 않음
         따라서 li항목 출력 후 줄바꿈 없이 다음 li 항목이 가로방향으로 출력됨                           
         */
    }

    li a, .dropbtn {
      display: inline-block;
      /* a 요소와 .dropbtn(이것도 a 요소임)은 기본적으로 display: inline 요소임
         inline 요소는 block 요소와 달리 콘텐츠의 크기만큼만 영역을 차지함
         당연히 width, height, padding, margin 적용하지 못함. 
         아래와 같이 padding: 14px 16px;을 지정하면 보기 좋게 출력됨. 
         그러기 위해서는 display: inline-block로 바꾸어 주어야 함. 
         결과적으로 width, height, padding, margin 적용 가능함. 
         하지만 display: block 요소처럼 줄바꿈은 발생하지 않음.   
      */
      padding: 14px 16px;
      color: white;
      text-align: center;
      text-decoration: none;
    }

    li a:hover, .dropdown:hover .dropbtn {
      background-color: red;
    }
/*     
    li.dropdown {
      display: inline-block;
    }
*/
    .dropdown-content {
      /* .dropdown-content 클래스 요소는 구글, 유튜브, 네이버를 포함하는 
          확장되는 드롭다운 콘텐츠임. */
      display: none; /* 처음에는 드롭다운 메뉴가 보이지 않도록 설정 
                        사용자가 드롭다운 메뉴에 마우스오버하면 
                        display: block;으로 변경하여 보이게 함 
                        테스트를 할때는 메뉴가 보이지 않기 때문에
                        display: block로 하고 테스트하길 바람.  */
      position: absolute; 
      /* position: absolute; 는 출력되는 위치의 기준점을 정할 때 
         가장 가까운 조상(position: static;이 아니어야 함)을 기준점으로 사용 
         기본적으로 요소의 position 속성은 static으로 설정됨. 
         position: static은 normal flow에 따라 요소의 출력 위치가 정해짐
         html문서의 요소는 상단에서 하단으로 좌에서 우로 차례로 출력하는 것이
         normal flow(정상적인 흐름)임. 
         ***
         여기서, .dropdown-content의 아버지가 <li class="dropdown"> 요소임. 
                 <li class="dropdown"> 요소는 position 속성을 지정하지 않음
                 즉, position 속성은 기본값인 static으로 간주됨. 
         그렇다면 .dropdown-content의 할아버지를 살펴보자.     
                 할아버지는 <ul>이고 position: sticky;로 설정함.
                 따라서 <ul>요소를 기준으로 출력 위치가 결정됨       
      */
      background-color: white;
      min-width: 160px;
      box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
                /* 요소에 테두리(border)를 그리는 대신에 
                   카드 형태의 박스의 그림지 효과를 줌. 
                   오른쪽(0px), 아래(8px),
                   blur(번짐, 16px), 확산(0px)
                   그림자색 rgba(0,0,0,0.2) */
      z-index: 1; /* z-index 기본값은 0
                     요소들이 겹쳐질 때 z-index 값이 클수록 위쪽에 배치
                     아랫쪽에 배치되면 보이지 않거나 선택하지 못하게 됨. */
               
    }

    .dropdown-content a {
      color: black;
      padding: 12px 16px;
      text-decoration: none;
      display: block; 
      /* .dropdown-content a => .dropdown-content클래스의 후손인 a 
        a 요소는 기본적으로 display: inline 요소임 
         inline 요소는 block 요소와 달리 콘텐츠의 크기만큼만 영역을 차지함
         width, height, padding, margin 적용하지 못함. 
         특히, display: block 요소처럼 줄바꿈도 발생하지 않음.
         display: block로 바꾸어 주면 줄바꿈이 일어남. 
         구글
         유튜브
         네이버
         처럼 줄을 바꾸면서 드롭다운 목록이 출력됨. 
      */
      text-align: left;
    }

    .dropdown-content a:hover {background-color: #f1f1f1;}

    .dropdown:hover .dropdown-content {
      display: block; /* 마우스 오버시 드롭다운 메뉴가 보이도록 설정 */
    }

    </style>
</head>
<body>
  <ul>
    <li><a href="index.html">홈</a></li>
    <li><a href="운동전 알아야할것.html">운동전 알아야할것</a></li>
    <li><a href="분할.html">분할</a></li>
    <li><a href="다이어트.html">다이어트</a></li>
    <li><a href="스트레칭.html">스트레칭</a></li>
    <li class="dropdown">
      <a href="#" class="dropbtn">보충제</a>
      <div class="dropdown-content" >
        <a href="https://www.myprotein.co.kr/">마이프로틴</a>
        <a href="https://metree.co.kr/index/index.php?sponsor=&refere=">미트리</a>
        <a href="http://www.kookminpt.shop/?utm_source=naver&utm_medium=cpc&utm_campaign=nv_brand_search&utm_content=pc_%ED%83%80%EC%9D%B4%ED%8B%80&n_media=27758&n_query=%EB%8B%AD%EA%B3%A0%EC%95%BC&n_rank=1&n_ad_group=grp-a001-04-000000023843524&n_ad=nad-a001-04-000000214444638&n_keyword_id=nkw-a001-04-000004512057627&n_keyword=%EB%8B%AD%EA%B3%A0%EC%95%BC&n_campaign_type=4&n_contract=tct-a001-04-000000000611892&n_ad_group_type=5&NaPm=ct%3Dlavrynbs%7Cci%3D0Aa0001J3C1xt%2D%5FVR1id%7Ctr%3Dbrnd%7Chk%3D50af7a06e50f3e787c5fd13d8cfb8319866def83">닭고야</a>
      </div>
    </li>
  </ul>
   <h1 style="text-align:center;">본 사이트는 일반인이 유튜브 및 운동 선배들한테 배운 팁들을 알려주는 사이트 입니다. </h1>
   <br>
   <br>
   <br>
   <h2 style="text-align:center;">아래에 사진중 본인이 배우고 싶은 몸 부위를 클릭 하시오.<br> </h2>
   --->가슴 등 어깨 하체<br><br>
   지금부터 설명할 운동 종목은 최대한 이해하기 쉽고 간단하게 작성한 것이다.<br><br>
  더 상세한 내용은 참고영상을 보자 <br><br>
또한 헬스장에 있는 대표적인 운동기구에 대해 설명하는 것이다.<br><br>
이것 이외에 다양한 운동종목이 있다.<br><br>
설명한 운동 종목으로도 충분히 운동이 되지만 헬스장에 있는 운동종목의 경우 유튜브에 찾으면 쉽게 나온다.<br><br><br><br>
  
   <img src="https://postfiles.pstatic.net/20140810_214/ppyu112_1407660542073ekmUt_JPEG/IMG_13105354386623.jpeg?type=w3" alt="황철순 몸 사진" width="1000" height="1000" usemap="#workmap">
   <map name="workmap">
    <area shape="poly" coords="341,191,338,227,374,255,429,276,561,276,625,267,684,228,669,182,616,195,576,201,511,203,444,201,383,191," alt="가슴" href="가슴.html">
    <area shape="poly" coords="723,252,690,288,663,326,633,351,639,317,636,291,642,251,660,240,684,227" alt="등" href="등.html">
    <area shape="poly" coords="321,231,329,290,354,314,374,341,383,356,390,326,399,287,365,257,339,236,333,236" alt="등" href="등.html">
    <area shape="poly" coords="407,185,377,162,342,156,317,155,287,168,300,176,341,182,356,180,383,185" alt="어깨" href="어깨.html">
    <area shape="poly" coords="612,179,654,159,675,155,685,155,705,153,720,158,744,170,700,185,676,176,667,180,639,188,628,182" alt="어깨" href="어깨.html">
    <area shape="poly" coords="389,453,440,491,476,526,517,556,553,509,576,485,607,468,645,449,673,500,697,594,678,675,693,777,669,852,652,931,720,975,646,972,592,972,604,873,592,838,597,754,577,681,556,636,519,603,483,640,456,700,470,826,453,960,399,931,389,852,360,805,332,627,353,544,365,494,372,476" alt="하체" href="하체.html">

    
   

</body>
</html>
