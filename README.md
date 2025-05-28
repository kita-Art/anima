🚀 도형 로딩 애니메이션 (Shape Loading Animation) - CSS 설명
이 프로젝트는 HTML과 CSS만을 사용하여 간단하면서도 시각적으로 매력적인 도형 로딩 애니메이션을 구현합니다. 세 개의 원형 요소가 순차적으로 커지고 작아지며 사라지는 효과를 통해 사용자에게 로딩 중임을 알립니다.

![bandicam 2025-05-28 13-58-41-442](https://github.com/user-attachments/assets/44ed2533-81b2-4bd4-8b07-a722776abfc7)


📁 파일 구조
index.html: 애니메이션을 표시할 기본 HTML 구조
style.css: 애니메이션의 시각적 스타일과 동작을 정의하는 CSS 파일
✨ CSS 코드 분석 (style.css)
이 섹션에서는 style.css 파일에 있는 각 CSS 규칙과 속성이 로딩 애니메이션을 어떻게 구성하는지 자세히 설명합니다.

1. Google Web Font 불러오기
CSS

@import url('https://fonts.googleapis.com/css?family=Raleway&display=swap');
이 @import 규칙은 Google Fonts에서 'Raleway' 폰트를 웹 페이지에 가져옵니다. display=swap은 폰트 로딩 시 발생할 수 있는 깜빡임을 줄여 사용자 경험을 개선하는 속성입니다.

2. body 태그 기본 스타일 설정
CSS

body {
  font-family: 'Raleway', sans-serif;
  line-height: 1.5em;
  margin: 0;
  font-weight: 300;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
font-family: 페이지 전체의 기본 글꼴을 'Raleway'로 설정하고, 폰트를 불러오지 못할 경우 'sans-serif' 계열의 기본 폰트를 사용하도록 지정합니다.
line-height: 텍스트의 줄 간격을 글꼴 크기의 1.5배로 설정하여 가독성을 높입니다.
margin: 0;: body 태그의 기본 여백을 제거하여 콘텐츠가 브라우저 가장자리부터 시작하도록 합니다.
font-weight: 300;: 글꼴의 두께를 얇게(light) 설정합니다.
display: flex;, justify-content: center;, align-items: center;: 이 세 속성은 CSS Flexbox를 활용하여 body 내부의 모든 콘텐츠(여기서는 로딩 애니메이션)를 가로 및 세로 방향으로 완벽하게 중앙에 배치합니다.
height: 100vh;: body의 높이를 뷰포트(브라우저 화면)의 전체 높이(100% of viewport height)로 설정하여 애니메이션이 화면 중앙에 나타나도록 합니다.
3. a 태그 (링크) 기본 스타일 설정
CSS

a {
  text-decoration: none;
}
HTML 문서 내 모든 <a> (하이퍼링크) 태그의 기본 밑줄을 제거합니다. 이는 시각적인 깔끔함을 위해 자주 사용되는 스타일입니다.

4. 로딩 애니메이션 <span> 요소 공통 스타일
CSS

.loading span {
  display: inline-block;
  width: 50px;
  height: 50px;
  background-color: gray;
  border-radius: 50%;
  animation: loading 1s linear infinite;
}
.loading 클래스 내부에 있는 각 <span> 요소에 적용되는 공통 스타일입니다.

display: inline-block;: <span>은 기본적으로 인라인 요소이지만, width와 height 같은 크기 속성을 적용하려면 inline-block으로 설정해야 합니다. 이렇게 하면 요소들이 한 줄에 나란히 배치되면서도 크기 조절이 가능해집니다.
width: 50px;, height: 50px;: 각 <span> 요소의 크기를 50x50 픽셀로 설정합니다.
background-color: gray;: <span>의 기본 배경색을 회색으로 지정합니다. (이 값은 나중에 :nth-child 셀렉터에 의해 개별적으로 재정의됩니다.)
border-radius: 50%;: width와 height가 같으므로 border-radius: 50%를 적용하면 각 <span>이 완벽한 원형으로 변환됩니다.
animation: loading 1s linear infinite;: loading 이라는 이름의 @keyframes 애니메이션을 이 요소에 적용합니다.
loading: 사용할 @keyframes 규칙의 이름입니다.
1s: 애니메이션이 한 번 완료되는 데 걸리는 시간입니다 (1초).
linear: 애니메이션이 시작부터 끝까지 일정한 속도로 진행됩니다.
infinite: 애니메이션이 무한히 반복되도록 설정합니다.
5. 각 <span> 요소의 개별 스타일 및 애니메이션 지연
CSS

.loading span:nth-child(1) {
  animation-delay: 0s;
  background-color: crimson;
}
.loading span:nth-child(2) {
  animation-delay: 0.2s;
  background-color: dodgerblue;
}
.loading span:nth-child(3) {
  animation-delay: 0.4s;
  background-color: royalblue;
}
여기서는 :nth-child() 의사 클래스 셀렉터를 사용하여 .loading 내부의 특정 순서에 있는 <span> 요소에 개별적인 스타일을 적용합니다.

animation-delay: 각 <span>이 loading 애니메이션을 시작하는 시점을 지연시킵니다.
첫 번째 <span>은 0초 지연 (즉시 시작).
두 번째 <span>은 0.2초 지연.
세 번째 <span>은 0.4초 지연. 이 지연 시간 덕분에 세 개의 원이 동시에 움직이지 않고 순차적으로 나타나거나 사라지는 파동 효과를 만듭니다.
background-color: 각 <span>에 다른 색상을 지정하여 시각적인 구분을 줍니다.
6. @keyframes 애니메이션 정의 (loading)
CSS

@keyframes loading {
  0%, 100% {
    opacity: 0;
    transform: scale(0.5);
  }
  50% {
    opacity: 1;
    transform: scale(1.2);
  }
}
@keyframes 규칙은 loading 이라는 이름의 애니메이션이 시간의 흐름에 따라 어떻게 변화할지를 정의합니다.

0%, 100% (애니메이션 시작과 끝 지점):
opacity: 0;: 요소의 투명도를 0으로 설정하여 완전히 보이지 않게 만듭니다.
transform: scale(0.5);: 요소의 크기를 원래 크기의 50%로 축소합니다. 이 설정은 애니메이션의 시작과 끝에서 원들이 작고 투명한 상태가 되도록 합니다.
50% (애니메이션 중간 지점):
opacity: 1;: 요소의 투명도를 1로 설정하여 완전히 보이게 만듭니다.
transform: scale(1.2);: 요소의 크기를 원래 크기의 120%로 확대합니다. 이 설정은 애니메이션의 중간 지점에서 원들이 가장 크고 선명하게 보이도록 합니다.
이러한 조합으로 각 원은 작고 투명한 상태에서 점점 커지면서 선명해졌다가, 다시 작고 투명한 상태로 돌아가는 반복적인 애니메이션을 수행하게 됩니다. animation-delay 덕분에 이 과정이 순차적으로 일어나 물결치듯 보이는 아름다운 로딩 효과가 완성됩니다.

💡 어떻게 작동하나요? (요약)
이 애니메이션은 세 개의 원형 <span> 요소를 활용합니다. 각 원은 @keyframes loading 애니메이션에 따라 투명하고 작게 시작하여, 중간 지점에서 불투명하고 크게 확대되었다가, 다시 투명하고 작게 줄어들면서 한 사이클을 마칩니다.

핵심은 각 <span>에 적용된 animation-delay 입니다. 첫 번째 원이 애니메이션을 시작한 후, 두 번째 원은 0.2초 뒤, 세 번째 원은 0.4초 뒤에 동일한 애니메이션을 시작합니다. 이 시간차 덕분에 원들이 마치 파도를 타듯이 순차적으로 나타나고 사라지는 부드러운 로딩 효과가 연출됩니다.

🛠 사용 방법
index.html 파일을 만듭니다.
style.css 파일을 만듭니다.
위에서 설명된 HTML 및 CSS 코드를 각 파일에 붙여넣습니다.
index.html 파일을 웹 브라우저에서 열면 로딩 애니메이션을 확인할 수 있습니다.
