# javascript_game
lets get it 자바스크립트 프로그래밍 책 공부 용 리파지토리
자바스크립트를 사용하여 게임을 만들어 본다

# 01월 03일
## 끝말잇기 게임
### 게임 방식
```
1. 시작
2. 몇명이 게임에 참가할지 입력 받는다
3. 첫번째 참가자가 제시어를 입력한다
4. 확인 버튼을 클릭한다
5. 다음사람이 입력할 차례가 된다
6. 제시어를 입력한다
7. 참가자 차례 검사 및 끝말잇기 규칙에 맞는 제시어인지 검사한다
    0. 제시어가 없는 경우 첫번째 사람이 입력한 것이다
    1. 맞는 경우 - 다음사람으로 차례가 넘어간다
    2. 틀린 경우 - 다시 제시어를 입력한다
```


### 주요 로직 정리
#### 설명
+ 제시어 입력후 버튼 클릭시 
+ 첫번째 사람이 입력한 것인지 검사
+ 첫번째 사람이 아닌 경우 끝말잇기 규칙에 어긋나지 않는 지 검사
+ [끝말있기 상세 정리 내용](https://unique-wandflower-4cc.notion.site/20d93fcbb70f465fabd045214dd9a31e)
```
function buttonClicked() {
	1. 사용자가 입력한 제시어를 input 태그에서 가져온다
    2. 제시어를 변수에 저장한다
	let inputWord = "";
    inputWord = $input.value;


    3. 이전 사용가가 입력한 기존 제시어를 저장할 변수를 초기화 한다
    4. 기존 제시어를 comWord 변수에 저장해 둔다 
     let comWord = "";

    5.
    목적: 제시어를 입력한 사람이 첫번째 사람인지 판단 하기 위한 
          분기문
    역할: 
    - 제시어 변수에 제시어가 없는 경우 첫번쨰 사람이 입력한 것이다
    - 기존 제시어의 첫번째 글자와 사용자가 입력한 제시어의 마지막 글자가
      같지 않으면 끝말잇기 규칙에 위배되었다
    if (!newWord ||  comWord[comWord.length - 1] === inputWord[0]) {
        5-1. 사용자가 입려한 단어를 제시어를 보여줄 변수에 저장한다
				newWord = inputWord;		

        5-2. 제시어를 보여줄 html 요소에 값을 넣어준다
        $word.textContent = newWord;


        5-3. 제시어가 끝말잇기 규칙에 위배되지 않은 경우 다음 차례로 순서를 바꿔준다
				a. 게임에 참가하는 전체 인원수를 변수에 저장한다
        b. 현재 순서를 가져온다
        c. 현재 순서 + 1 > 전체 인원수
           c-1. 순서가 다시 첫번째 사람으로 돌아간다
        c-else 
           c-2. 다음순서를 지정해 준다
           c-3. 현재 순서 += 1;
           c-4. 현재 순서를 담고 있는 html 태그에 값을 넣어준다
     
    } else {

			6. 사용자가 입력한 단어가 끝말잇기 규칙에 위배된 경우
      6-1. "올바르지 않은 단어 입니다."


	  }


}


$button.addEventListener('click' , buttonClicked);


```


### 배운점
+ 자바스크립트 태그 내부 값 가져오기
	+ innerHTML innerText textContent 차이
+ 발생 된 에러 
+ Uncaught TypeError: Cannot read properties of undefined (reading 'length')
	+ 발생이유 : 변수에 값이 할딩되지 않은 상태인데 데이터의 길이를 구하려고 하니 에러가 발생했다
+ 자바스크립트 문자열 길이 체크
	+ 문자열[index] 형식
+ null , undefined 차이




## 쿵쿵따 게임
+ 제시어가 쿵쿵따 규칙에 어긋나지 않는지 검사
    + 제시어 길이가 3인지
    + 제시어의 마지막 글자 와 입력받은 문자열의 첫번째 글자가 일치하는지  
+ 입력한 사람의 순서 검사
+ [쿵쿵따 상세 정리 내용](https://unique-wandflower-4cc.notion.site/dcd8df52d6e7426eaaab400004d65a24)

### 진행 방식
1. 시작
2. 몇명이 게임에 참가할지 입력 받는다
3. 첫번째 참가자가 제시어를 입력한다
4. 확인 버튼을 클릭한다
5. 다음사람이 입력할 차례가 된다
6. 제시어를 입력한다
7. 제시어 길이가 3글자 인자 그리고 첫번째 사람이 입력 했는지 또는 쿵쿵따 규칙에 맞는 제시어 인지 검사한다
    0. 제시어 길이 검사
    1. 첫번째 사람이 입력했는지 검사
    2. 쿵쿵따 규칙에 맞는 제시어 인지 검사
        a. 맞는 경우 - 다음사람으로 차례가 넘어간다
        b. 틀린 경우 - 다시 제시어를 입력한다

### 주요 로직 정리
#### 설명

```
			
	function buttonClicked() {
				1. 사용자가 입력한 제시어를 input 태그에서 가져온다
		    2. 제시어를 변수에 저장한다
				let inputWord = "";
		    inputWord = $input.value;
		
		
		    3. 이전 사용가가 입력한 기존 제시어를 저장할 변수를 초기화 한다
		    4. 기존 제시어를 comWord 변수에 저장해 둔다 
		     let comWord = "";
		
		    5.
		    목적:
		         a. 제시어가 3글자 인지 검사
		         b. 첫번째 사람이 입력한 제시어 인지 검사
		         c. 제시어가 쿵쿵따 규칙에 위배되지 않는지 검사
		        
		    역할: 
		    - 제시어 길이가 3글자 인지 검사한다
		    - 제시어 변수에 제시어가 없는 경우 첫번쨰 사람이 입력한 것이다
		    - 기존 제시어의 첫번째 글자와 사용자가 입력한 제시어의 마지막 글자가
		      같지 않거나 길이가 3글자가 아닌 경우 쿵쿵따 규칙에 위배되었다
		    if (inputWord.length === 3 && (!newWord ||  comWord[comWord.length - 1] === inputWord[0]) ) {
		        5-1. 사용자가 입려한 단어를 제시어를 보여줄 변수에 저장한다
						newWord = inputWord;		
		
		        5-2. 제시어를 보여줄 html 요소에 값을 넣어준다
		        $word.textContent = newWord;
		
		
		        5-3. 제시어가  쿵쿵따  규칙에 위배되지 않은 경우 다음 차례로 순서를 바꿔준다
						a. 게임에 참가하는 전체 인원수를 변수에 저장한다
		        b. 현재 순서를 가져온다
		        c. 현재 순서 + 1 > 전체 인원수
		           c-1. 순서가 다시 첫번째 사람으로 돌아간다
		        c-else 
		           c-2. 다음순서를 지정해 준다
		           c-3. 현재 순서 += 1;
		           c-4. 현재 순서를 담고 있는 html 태그에 값을 넣어준다
		     
		    } else {
		
					6. 사용자가 입력한 단어가 끝말잇기 규칙에 위배된 경우
		      6-1. "올바르지 않은 단어 입니다."
		
		
			  }
		
		
		}
		
		
		$button.addEventListener('click' , buttonClicked);


```

### 배운점
+ undefined vs null 차이
+ 문자열에서 특정 인덱스에 해당하는 문자 추출하는 방법
+ 문자열의 길이를 체크하는 방법


# 01월 04일
## 끝말잇기 게임 

### 잘된점
+ 끝말잇기 게임 구조도 세분화
+ 구조도를 보고 코딩 진행
+ 코드리뷰 하면서 정리
+ [상세 정리 내용](https://unique-wandflower-4cc.notion.site/20d93fcbb70f465fabd045214dd9a31e)
+ 중복되는 코드 제거


### 구조도 
```
1. 시작 
2. 몇명이 게임에 참가할지 입력 받는다 prompt()
3. 첫번째 참가자가 제시어를 입력한다
    1. 입력 한 제시어를 변수 (임시변수)에 저장해 둬야 한다
        1. 확인 버튼을 클릭한다
        2. 첫번째 사람인지
            1. 제시어를 저장한 변수에 값이 없을 것이다 (즉 , 제시어가 없다)
        3. 첫번째 사람이 아닌 경우
            1. 제시어를 저장하는 변수에 값이 있을 것이다 (즉 , 제시어가 있다)
        4. 어떤 제시어를 입력했는지
            1. 첫번째 사람의 경우
                1. 입력한 단어를 제시어 변수에 저장한다
                2. 값을 html 태그에 넣어준다
            2. 첫번째 사람이 아닌 경우 (두번째 사람부터)
                1. 제시어의 마지막 글자와 입력한 제시어의 첫번째 글자가 일치하는 지 검사한다
                2. 일치하는 경우 
                    1. 값을 html 태그에 넣어준다
                    2. input 태그에 남아있는 값은 지워 준다
                3. 일치하지 않는 경우
                    1. 값을 다시 입력하라고 경고창을 띄운다
                    2. input 태그에 남아있는 값은 지워 준다
4. 다음사람이 입력할 차례가 된다
5. 제시어를 입력한다
6. 끝말잇기 규칙에 맞는 제시어인지 검사한다
    1. 맞는 경우 
        1. 다음사람으로 차례가 넘어간다
    2. 틀린 경우  
        1. 다시 제시어를 입력한다

```

### 중요코드 
+ 제시어를 입력한 사람이 첫번째 사람인지 확인 하는 방법에 대한 고민
+ 입력한 제시어가 끝말잇기 규칙에 맞는지 검사하는 방법에 대한 고민
+ 규칙에 맞는 경우 다음 순서로 어떻게 넘길것인지에 대한 고민
+ 고민 결과
```
const buttonClick = () => {

	// 첫번째 사람이 입력하는 경우
    if (제서어가 없는 경우) {
        
				1. 입력한 제시어를 임시변수에 담아 놓는다
        savedWord = inputWord;

        2. 임시변수 데이터를 제시어를 보여줄 HTML 요소에 넣어준다
        $word.textContent = savedWord;

				3. 현재 순서를 담고 있는 HTML 요소의 값을 가져와서 nowOrder 변수에 담는다
        nowOrder = Number($order.textContent);

				4. 현재 순서 + 1 한 값이 전체 참여인원 보다 큰경우         
        if (nowOrder + 1 > players) {
            
            4-1. 다시 첫번째 사람으로 순서가 돌아간다
						nowOrder = 1;

            4-2. 다음 순서를  HTML 의 순서보여주는 태그에 넣어준다
            $order.textContent = Number(nowOrder);

            4-3. 다음사람이 입력을 편하게 하기 위해 input 태그의 값을 초기화 해준다
            $input.value = "";
        } 
         5. 현재 순서 + 1 한 값이 전체 참여인원 보다 작은 경우
				else  { 
						
            5-1. 현재 순서 + 1을 해준다 (다음 사람으로 순서가 넘어간다)
            nowOrder = Number($order.textContent);
            nowOrder += 1;
            
            5-2. 다음 순서 값을 HTML 의 순서 보여주는 태그에 넣어준다
            $order.textContent = Number(nowOrder);

            5-3. 다음 사람이 입력을 편하게 하기 위해 input 태그의 값을 초기화 해준다
            $input.value = "";
        }


    } 
			// 첫번째 사람이 아닌 경우
			else {
            6. 제시어를 보여주는 태그 내부 데이터를 변수 (comWord)에 저장한다
            comWord = $word.textContent;
        
            7. 제시어의 마지막 글자와 입력한 제시어의 첫번째 글자가 같은 지 검사한다
            if (comWord[comWord.length - 1] === inputWord[0]) {
							
              7-1. 맞는 경우 입력한 제시어를 변수(saveWord)에 저장한다                
	            savedWord = inputWord;
              
              7-2. 임시변수의 데이터를 제시어를 보여주는 HTML 태그에 넣어준다
	            $word.textContent = savedWord;

              7-3. 현재 순서 데이터를 담고 있는 HTML 태그에서 데이터를 가져와서 변수(nowOrder)에 저장한다	
	            nowOrder = Number($order.textContent);
	
						  7-4. 현재 순서 + 1 한 값이 전체 참여인원 보다 큰경우 
	            if (nowOrder + 1 > players) {
									다시 첫번째 사람으로 순서가 돌아간다
	                nowOrder = 1;

									다음 순서를  HTML 의 순서보여주는 태그에 넣어준다
	                $order.textContent = Number(nowOrder);

									다음 사람이 입력을 편하게 하기 위해 input 태그의 값을 초기화 해준다
	                $input.value = "";
	            } 
								8. 현재 순서 + 1 한 값이 전체 참여인원 보다 작은 경우
								else  { 
										
				            8-1. 현재 순서 + 1을 해준다 (다음 사람으로 순서가 넘어간다)
				            nowOrder = Number($order.textContent);
				            nowOrder += 1;
				            
				            8-2. 다음 순서 값을 HTML 의 순서 보여주는 태그에 넣어준다
				            $order.textContent = Number(nowOrder);
				
				            8-3. 다음 사람이 입력을 편하게 하기 위해 input 태그의 값을 초기화 해준다
				            $input.value = "";
				        }							
        }
        
        // 끝말잇기 규칙에 어긋난 제시어를 입력한 경우 
				else {
            alert('다시 입력 하세요');
            $input.value = "";
        }
    }
}

$button.addEventListener('click' , buttonClick);


```

### 배운내용
+ prompt () vs alert() vs confirm() 차이
+ Number() vs parseInt() 차이
+ html 요소를 자바스크립트로 조작하는 방법
	+ querySelector() vs querySelectorAll()
+ html 요소에 이벤트를 다는 방법
  + addEventListener('이벤트 이름' , 콜백함수)
  + 콜백함수 목적
  + event.target
   + 실제로 이벤트가 발생된 html 요소
  + 이벤트가 발생된 태그에서 값을 가져오는 방법
   + event.target.value
   + event.target.textContent
+ 화살표 함수
  + 화살표 함수 형식
  ```
	() => {

	}

  ```
+ 유사배열
  + 문자열의 경우 배열처럼 인덱스를 통해 접근할 수 있다
  + 이와 같은 특성을 갖는 데이터를 유사배열 이라 한다


### 코드리펙토링
+ 제시어를 입력했을떄 순서가 다음사람으로 넘어가는 부분이 코드상에서 중복된다
+ 이를 한번만 사용하기 위해
+ 조건문에 || (OR) 연산자를 사용하였다
+ 제시어를 저장하는 변수에 값이 없거나 또는 제시어의 마지막 글자와 입력한 제시어의 첫번째 글자가 같이 않은 경우
+ OR 연산자를 통해 첫번째 사람과 그외 사람들을 구분할 수 있다
```
 if (!savedWord || inputWord[0] === comWord[comWord.length - 1]) {                   
      savedWord = inputWord;
      $word.textContent = savedWord;

      nowOrder = Number($order.textContent);
      
      if (nowOrder + 1 > players) {
          nowOrder = 1;
          $order.textContent = Number(nowOrder);
      } else  {
          nowOrder = Number($order.textContent);
          nowOrder += 1;
          $order.textContent = Number(nowOrder);
      }

      $input.value = "";

  } else {
      alert("제시어가 올바르지 않습니다.");
}


```


