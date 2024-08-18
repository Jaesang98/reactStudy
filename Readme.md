## part 1-1 React 배우기 전에 쓰는 이유부터 알아야
	1. 리액트를 쓰는 이유
		1) single page Application을 만들 때 쓴다
			=> 새로고침 없이 앱처럼 부드럽게 동작하는 html페이지를 만들 때 사용
				**물론 생 자바스크립로도 할 수 있지만 코드가 길어지기 때문에 react를 사용하는거임**
				
		2) html 재사용이 편리함
		
		3) 같은 문법으로 앱 개발 가능 (React Native와 유사)
		
		
## part 1-2 리액트 React 설치와 개발환경 셋팅
	1. 개발세팅
		1) node js, vscode설치
		2) 폴더 만든 후 파워쉘 창 열어서 npx create-react-app blog (react create app 라이브러리임)
			=> 허가되지 않은 스크립트 ~ 오류가 난다면 관리자로 실행 후 
				- Set-ExecutionPolicy Unrestricted 
				- 이거했는데 잘 안되면 npm install -g npm 후 npm cache clean --force해보기
				- 그래도 안되면 인생망함
				
	2. npm
		- 그냥 라이브러리를 다 모아놓은 플랫폼 같은거임
		- node.js 설치하면 딸려옴
	
	
## part 1-3 리액트에서 레이아웃 만들 때 쓰는 JSX 문법 3개
	1. jsx
		- js파일에서 쓰는 html대용품
		- 리액트는 jsx를 사용한다
		
	2. 문법
		1) className을 써야하며 다른 css파일을 사용하고 싶은 경우 import해와야함
		2) {} 데이터는 중괄호안에 써야함
			=> 웬만한 곳은 {}를 쓸수 있음, 이런걸 데이터 바인딩이라고 한다!
		3) jsx상에서 스타일을 수정할 때 {{color : 'red', ~ }} 이런식으로 써야함
			=> -기호는 쓸 수 없음
			
			
## part 1-4 중요한 데이터는 변수말고 state에 담습니다
	1. 문법 
		- return 소괄호에는 대표 태그 하나로 묶여져 있어야한다
			=> 두개의 태그를 같이 쓸 수 없다라는 뜻
			
	2. useState
		값이 변경됬을 때 자동으로 html에 렌더링 되도록 하기위해 사용
		1) useState import 해오기
		2) useState에 보관할 자료 적기
		3) let [작명1, 작명2] 으로 변수 선언
			=> 작명1은 state에 보관했던 자료, 작명2는 state를 변경해주는 함수
			
			
## part 1-5 버튼에 기능개발을 해보자 & 리액트 state변경하는 법
	1. warning 메시지
		=> 뭐 만들고 안썻다 이런것들을 알려주는건데 보기싫으면 /* eslint-disable */ 이거쓰면됨
		
	2. 클릭 이벤트
		- onClick= {}를 사용한다
		- 함수를 호출 하는 경우 onClick= {함수} 
		- 기능을 실행 하는 경우 onClick= {()=> {기능기능}}
		
	3. state변경
		- let [작명1, 작명2] = useState("0");
			작명2("1")
			=> state변경함수(새로운state) 이렇게 작성을 해야 바뀜
			
## part 1-6 array, object state 변경하는 법
	1. array object수정
		1) 원본을 보존하는게 좋음
			=> let copy = [...데이터] 이렇게 해야 카피본이 만들어짐
				배열이나 오브젝트는 변수를 지정하면 화살표가 생김
				그래서 그 상태에서 뭔 변경해도 배열이 바뀐거지 화살표가 바뀐게아니라
				기존 state에서 배열을 변경하고 넣어도 값이 바뀌지 않는거임
				... 이걸써야 화살표가 달라짐
		
## part 1-7 Component : 많은 div들을 한 단어로 줄이고 싶으면
	1. 컴포넌트 만드는법
		1) function을 만든다
		2) return()안에 html을 담는다
		3) <함수명></함수명> or <함수명/>을 쓴다
		
	2. 컴포넌트 언제 쓰는지
		1) 반복적인 html 축약
		2) 큰 페이지들
		3) 자주 변경되는 것들
		
	
## part 1-8 리액트 환경에서 동적인 UI 만드는 법 (모달창만들기)
	1. 동적 UI만드는 스텝
		1) 디자인 완성
		2) 현재 상태를 state에 저장
		3) state에 따라 UI가 어떻게 보일지 작성
	
	2. 요소 show hide처리
		{
			조건식 ? 요소 : null
		}
		=> 이렇게 요소를 show hide시킬 수 있다
		
	** useState는 작명, set작명 이렇게 적는게 관습이다 **
	
	
## part 1-9 map : 많은 div들을 반복문으로 줄이고 싶은 충동이 들 때
	1. map
		{
			array.map (function(item, index) {
				return (
					요소
				)
			}
		}
		=> 이런 형태
		
		
## part 1-10 자식이 부모의 state 가져다쓰고 싶을 때는 props
	1. props사용법
		1) <자식컴포넌트 작명={state}>
		2) props 파라미터 추가 후 props.작명으로 사용
			**부모에서 자식에게만 전송이 가능 (패륜 불륜안됨)**
			
			
## part 1-11 props를 응용한 상세페이지 만들기
	1. 상세에 데이터를 넘겨줄 때
		- 하나의 오브젝트 or 하나의 배열만 보내거나
		- index도 같이 보내야함
			=> 뭐가 좋을지 상황에 맞춰서 사용하자
			
		- 자식과 부모가 같이쓰는 state라면 부모에 올려놓고 자식이 props로 받아쓰는게 좋다

		
## part 1-12 input 1 : 사용자가 입력한 글 다루기
	1. input
		- 값을 가져올 때는 onChange={(e) => {e.target.value}} 이렇게 가져온다
		
	2. 이벤트 버블링
		- 이벤트가 상위요소로 퍼지는 현상
		- e.stopPropagation 사용하면 안퍼짐
		
	** state변경 시차가 있음, 그래서 변경 후 다음에 바로 콘솔찍으면 변경안된게 출력됨 **
	

## part 1-13 input 다루기 2 : 블로그 글발행 기능 만들기
	1. 배열에서 삭제
		- splice (index, 1)
		
	2. 배열에서 맨 앞에 추가
		- 변수.unshift(입력값)
		
		
## part 1-14 class를 이용한 옛날 React 문법
	오늘의 결론은 :
	컴포넌트 만들 일이 있으면 class는 복잡하니까 function 씁시다. 
	근데 개발하다보면 예전 리액트프로젝트같은거 봐야하는 경우가 있습니다.
	그럴 때 class 컴포넌트 나올텐데 당황하면 뉴비티가 나기 때문에
	고수인 척 하고 싶으면 참고로 알아둡시다. 
	
	
## part 1-15 만든 리액트 사이트 build & Github Pages로 배포해보기
	1. 빌드하기
		1) npm run build 
		2) 깃허브에서 프로젝트명..github.io 로 해줘야함
			=> 이제는 pages 들어가서 source를 main으로 바꿔주자
		3) build안에 있는거 올림
		
	
	2. 첫 페이지를 빠르게 동작시키려면
		lazy 함수 : https://reactjs.org/docs/code-splitting.html#route-based-code-splitting

-----------------------------------------------------------------

## part 2-1 새로운 프로젝트 생성 & Bootstrap 사용하기
	1. 리액트 부트스트랩 설치
		1) npm install react-bootstrap bootstrap 
		2) index.html 에 글로벌로하기
			<link
			  rel="stylesheet"
			  href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css"
			  integrity="sha384-T3c6CoIi6uLrA9TneNEoa7RxnatzjcDSCmG1MXxSR1GAsXEV/Dwwykc2MPK8M2HN"
			  crossorigin="anonymous"
			/>
			
		3) import {Button} from 'react-bootstrap' 
			=> 이런식으로 불러와야함
			
		** className넣어서 커스터마이징해도되니까 걱정 ㄴㄴ**
		
		
## part 2-2 이미지 넣는 법 & public 폴더 이용하기
	1. jsx에서 이미지 넣기
		1) import로 이미지를 가져옴
		2) style={{background : 'url(' + import로가져온이미지 + ')'}}
		
		or
		
		1) public폴더에 이미지를 넣음
		2) /이미지이름 이렇게 적으면됨
			=> 나중에 빌드할 떄 서브경로를 통해서 발행할 때 안먹을 수 있음;;
				** 그래서 img같은 경우에는 <img src={process.env.PUBLIC_URL + '/logo192.png'} /> 이렇게 해주는게좋음


## part 2-3 코드 길어지면 import export 하면 됩니다
	1. 다른 파일의 정보를 사용하는법
		1) 사용될 파일 export default 하기
			=> 여러개 쓸거면 export{a,b,c} 
		2) 사용할 페이지에서 import하기
			=> 여거래 가져올거면 import{a,b,c}
		3) 사용
		
		
## part 2-4 저번시간 숙제 해설 (Card 컴포넌트 만들기)
	1. 내가 한 실수
		return () 안에 대표 태그하나 써야됌;;;
