# Python(ref. 점프 투 파이썬 P228~)

## 예외처리

* try,except 문

  ```python
  #1. 오류의 종류와 상관없이 오류가 발생하기만 하면 except 블록 수행
  try:
    ...
  except:
    ...
  #2. except문에 정해놓은 오류 이름과 일치하는 오류인 경우에만 except 블록수행
  try:
    ...
  except 발생 오류:
    ...
  #3. 오류 이름과 일치하고 오류 내용 까지 알고 싶을 때
  try:
    ...
  except 발생오류 as 오류 메시지 변수: ## 또는 except 발생오류,e
    ...
   
  ```

* Try,except,else

  except이후에 위치해야 하며 예외가 발생하지 않은 경우 실행

* Try...finally

  예외 발생 여부에 상관없이 항상 수행, 보통 파일 close()문이 많이 쓰임

* 오류 회피 시키기

  의도적으로 오류를 통과시키기 위함, except안에 pass만 넣어주면 된다.

* 오류를 발생시키기

  오류를 일부러 발생시켜야 하는 경우 raise 명령어 수행

  ```python
  class Bird:
    def fly(self):
      raise NotImplementedError
  
  class Eagle(Bird):
    pass
  eagle=Eagle()
  eagle.fly
  ## 이경우 fly가 구현되지 않았기 때문에 raise문에 의해 NotImplementedError가 발생한다
  # 따라서 이후 반드시 구현해야 한다.
  ```

  