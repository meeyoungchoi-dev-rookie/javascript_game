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

# 01월 06일

## 계산기 리펙토링
### 레펙토링 내용
+ 1. 숫자를 클릭한후 저장하는 변수를 재사용하지 않았다
+ 2. 하나의 함수는 하나의 기능만 담당해야 하는데 여러개의 기능을 담당하고 있다
  + 연산자를 클릭하는 함수가 = 을 클릭했을때 계산결과 까지 같이 계산해준다
  + 이로 인해 함수 내부 로직이 복잡해진다
  + 연산자를 클릭했을때 실행되는 함수는 연산자 앞뒤 숫자와 연산자를 연결해 주는 역할만을 해야한다
  + 따라서 연산자를 변수에 저장만 하도록 바꿨다
  + 실제 계산 결과는 = 을 클릭했을때 실행되는 함수에서 처리하도록 따로 함수를 만들어 줬다
+ 4. clear (c) 버튼을 클릭했을때
  + 지금까지 입력된 숫자와 연산자 변수에 저장된 모든 데이터를 초기화 시켜준다
  + 다음 계산식을 만들고 계산을 진행할때 페이지를 새로고침 하지 않고 계속 작업을 진행할 수 있게 하기 위함이다
+ [코드 리펙토링 진행 및 정리 내용](https://unique-wandflower-4cc.notion.site/23a9feee4f864226a0436efd962fa554)



# 01월 07일

## 계산기 리펙토링

### 잘된점
+ 고차함수의 사용방법을 이해하고 적용할 수 있었다
+ 고차함수와 event 객체를 사용한 콜백함수의 차이를 이해할 수 있었다
+ [리펙토링 상세 정리 내용](https://unique-wandflower-4cc.notion.site/445bbba94df041799e07badfdc7ef2e5)

### 리펙토링 내용
+ 숫자를 클릭할때 고차함수 적용
```
const numberClick = (number) => () => {
      
    if (!operator) {
        num += number;
        numberOne = num;
        $cal_show_num.textContent = numberOne;
        return;
    }


    if (!numberTwo) {
        $cal_show_num.textContent = "";
        num = "";   
    }    


    num += number;
    numberTwo = num;
    $cal_show_num.textContent = numberTwo;                
}


```
+ = 연산자를 클릭할때 event 객체를 사용한 콜백함수 적용
```
const operClick = (event) => {
    if (numberOne) {
        operator = event.target.textContent;
        $cal_operator.textContent = operator;
    }
}
```
+ C 버튼 클릭시 변수에 저장된 모든 값과 화면에 표시되는 모든 값 초기화
```

$clear.addEventListener('click' , () => {
    $cal_show_num.textContent = "";
    $cal_operator.textContent = "";
    num = "";
    numberOne = "";
    numberTwo = "";
    operator = "";
    result = "";
})


```



# 01월 08일
## 계산기 리펙토링
### 리펙토링 방향
+ 연속 계산이 가능하도록 수정
+ 첫번째 결과값을 resultNum이라는 변수에 담아놓는다
+ 첫번째 숫자를 저장하는 변수에 resultNum을 저장한다
+ 연산자 변수와 두번째 숫자를 저장하는 변수를 초기화 시켜준다
+ 연산자와 두번째 숫자를 클릭한다
+ 그러면 = 연산자를 클릭했을때 resultNum을 담고있는 numberOne 변수와 두번째 숫자가 연산이 된다
```
const numberClick = (number) => () => {
    if (!operator) {
        num += number;
        numberOne = num;
        $cal_show_num.textContent = numberOne;
        return;
    }

    if (!numberTwo) {
        $cal_show_num.textContent = "";
        num = "";   
    }    

    num += number;
    numberTwo = num;
    $cal_show_num.textContent = numberTwo;                
}


```


```
$result.addEventListener('click' , () => {
          switch(operator) {
              case '+':
                  result = parseInt(numberOne) + parseInt(numberTwo);                       
                  break;
              case '-':
                  result = parseInt(numberOne) - parseInt(numberTwo);
                  break;
              case 'X':
                  result = parseInt(numberOne) * parseInt(numberTwo);                        
                  break;
              case '/':
                  result = parseInt(numberOne) / parseInt(numberTwo);
                  break;
          }

          resultNum = parseInt(result);
          $cal_show_num.textContent = resultNum;
          $cal_operator.textContent = "=";
          num = "";
          numberOne = resultNum;
          numberTwo = "";
          result = "";
          operator = "";
})  
```


# 01월 10일
## 숫자야구
### 로직 정리
- 4자리 숫자를 입력받는다
    - 전송버튼 클릭
    - 4자리 숫자인지 검사
        - 아닌경우 4자리숫자를 입력하라고 경고창 띄움
        - 맞는 경우 데이터를 배열에 저장
            - String 타입의 데이터는 유사배열로 사용할 수 있기 때문에 요소를 하나씩 꺼내서 배열에 담는다
- 컴퓨터가 랜덤으로 4자리 숫자를 뽑는다
    - 숫자들이 중복되지 않게 뽑는다
        - 중복된 값이 존재하는 경우 다시 뽑는다
    - 뽑은 숫자를 배열에 저장한다
- 컴퓨터가 뽑은 숫자가 저장된 배열과 사용자가 입력한 숫자가 저장된 배열을 비교하면서 체크한다
    - 홈런
        - 컴퓨터가 뽑은 데이터가 들어있는 배열에서 요소들을 하나씩 꺼내 문자열에 저장한다
        - 사용자가 뽑은 데이터가 들어있는 배열에서 요소들을 하나씩 꺼내 문자열에 저장한다
        - 문자열을 비교한다
        - 값이 같은 경우 홈런
    - strike
        - 컴퓨터가 뽑은 데이터가 들어있는 배열을 기준으로 바깥쪽 반복문을 돌린다
        - 사용자가 뽑은 데이터가 들어있는 배열을 기준으로 안쪽 반복문을 돌린다
        - 두 배열 요소의 값이 같고 인덱스 까지 같은 경우 strike 이다
        - strike가 될때 마다 strikeCount 변수의 값을 1씩 증가시킨다
    - ball
        - 컴퓨터가 뽑은 데이터가 들어있는 배열을 기준으로 바깥쪽 반복문을 돌린다
        - 사용자가 뽑은 데이터가 들어있는 배열을 기준으로 안쪽 반복문을 돌린다
        - 두 배열 요소의 값은 같지만 인덱스가 다른경우 ball이다
        - ball이 될때 마다 ballCount 변수의 값을 1씩 증가시킨다
    - out
        - strikeCount가 0이고 동식에 ballCount도 0인 경우
        - outCount를 저장하는 변수가 1 증가 된다
        - 왜? strike 와 ball이 아닌 경우 고객이 뽑은 숫자 4자리와 컴퓨터가 뽑은 숫자 4자리의 값이 일치하지 않기 때문에 out으로 처리할 수 있다

## 고민한 부분
+ ball을 어떻게 판단할 것인가
+ strike을 어떻게 판단할 것인가
+ out을 어떻게 판단할 것인가
+ 숫자가 랜덤으로 저장될때 중복되지 않게 저장하는 방법

## 개선해야 하는 부분
+ 숫자를 랜덤으로 저장하면서 값이 중복되지 않게 처리
+ 한번 결과가 나오면 홈런을 치거나 아웃 카운트가 다 차서 게임이 종료될때
+ 까지 랜덤숫자가 계속 바뀌지 않게 처리하기


## 숫자야구 리펙토링 진행
+ 


## 상세 정리 내용
+ [숫자야구 정리 내용](https://unique-wandflower-4cc.notion.site/399b8c1d9a0f4a8d8d147979ff79f2c3)



# 01월 11일

## 숫자야구 구조도 다시 설계
### 설계 방향
+ 숫자 4자리를 입력받는다
 + 예외를 체크한다
 1. 입려값이 없는 경우
 2. 4자리보다 많은 경우
 3. 4자리보다 적은 경우
 4. 중복된 값이 있는 경우
+ 컴퓨터도 랜덤으로 숫자 4개를 뽑는다
 + 예외를 체크한다
 1. 중복된 값이 있는 경우
+ 사용자가 입력한 숫자와 컴퓨터가 랜덤으로 뽑은 숫자 값을 비교한다
 + 홈런이 될 조건
 1. 숫자가 서로 일치하는 경우
 + strike가 될 조건 
 1. 숫자를 배열에 담아서 비교한다
 2. 숫자는 같지암 배열의 인덱스가 다른 경우 
 + ball이 될 조건
 1. 숫자만 같고 인덱스는 다르다
 + out이 될 조건
 1. strike 개수와 ball 개수의 결과 값이 0인 경우

 ### 고려한 사항
 + 게임이 계속 유지될 수 있는 조건
 1. 홈런 또는 3out으로 게임이 끝나지 않았을때
 + 게임을 초기화 시켜야 하는 조건
 1. 홈런 또는 3out으로 게임이 끝났을때

 ### 배운점
 + 배열에 중복된 요소가 있는 지 체크하는 방법
 1. Set
 2. indexOf
 
 + out을 만들어 내는 방법



