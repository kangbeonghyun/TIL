# Python(ref. 점프 투 파이썬 P212~)

## Module 과 Package

### Module

* 모듈이란 함수나 변수 또는 클래스 들을 모아놓은 파일

* 사용 시 경로 주의!

* import 모듈 명(=파일 명 ,not 파일명.py)

  ```python
  #module1.py
  def sumcal(a,b):
    result=a+b
    return result
  
  #module2.py
  import module1
  print(module1.sumcal(1,3))
  >>4
  
  #또는 
  
  from module1 import sumcal
  print(sumcal(1,3))
  >>4
    
  ```

* if --name--=="--main--":(언더바)

  이 부분이 없으면 import할 시 해당 파일을 그냥 실행한다. 따라서 이 구문을 사용하면 실행하는 파일이 main이면 참이 되어 실행하고 대화형 인터프리터나 다른 파일에서 해당 모듈을 부른 경우 조건문이 거짓이 되어 이하 문장들이 수행되지 않는다.

* 모듈에 포함된 변수, 클래스, 함수도 사용할 수 있다

  ```python
  #module2.py
  PI=3.14
  class Math():
    def solve(self,r):
      return PI*(r**2)
  if __name__=="__main__":
    #blahblah
    
  #test.py
  import module2
  print(module2.PI)#3.14
  a=module2.Math()
  print(a.solve(2))#12.5663
  
  ```

* 같은 디렉토리 내가 아닌 모듈을 불러와서 사용하는 방법

  1. sys.path.append(모듈을 저장한 디렉토리) 사용

     Sys.path는 파이썬 라이브러리들이 설치되어 있는 디렉토리를 보여줌, 만일 조회된 디렉토리에 사용하고 싶은 모듈이 있다면 디렉토리 이동없이 바로 사용 가능

     따라서 sys.path에 사용하고 싶은 모듈을 추가해주면 해당 모듈을 사용할 수 있다.

     Ex) 모듈이 C:/python/Mymodule 디렉토리에 위치한다면,sys.path.append("C:/python/Mymodule")해서 추가시키면 된다.

  2. PYTHONPATH 환경 변수 이용

     Set 도스 명령어를 이용해 PYTHONPATH 환경변수에 모듈이 있는 디렉토리를 설정시키면 된다.

     Ex) set PYTHONPATH=C:\python\Mymodule

### Package

* 도트(.)를 이용해서 파이썬 모듈을 계층적(디렉토리 구조)으로 관리할 수 있게 해줌. 계층적 관리를 통해 공동 작업이나 유지보수가 쉽다.

* Ex) A.B이면 A는 패키지, B는 A패키지의 모듈이다.

* 사용 전에 set 도스 명령어를 사용하여 PYTHONPATH 환경변수에 최상위 패키지를 참조할 수 있는 디렉토리를 설정하자. ex) set PYTHONPATH=C:\python

  ```python
  #디렉토리 구조
  #game# C:/python에 있음
  # __init__.py
  # sound/
  #   __init__.py
  #   echo.py
  #   wav.py
  # graphic/
  #   __init__.py
  #   screen.py
  #   render.py
  # play/
  #   __init.py
  #   run.py
  #   test.py
  ```

  ```python
  #패키지를 활용하여 echo.py 파일의 echo_test함수 실행시키기
  #1.
  import game.sound.echo
  game.sound.echo.echo_test()
  #2.
  from game.sound import echo
  echo.echo_test()
  #3.
  from game.sound.echo import echo_test
  echo_test()
  #아래의 경우는 불가능, 왜냐하면 game 디렉토리의 모듈 또는 game 디렉토리의 __init__.py에 정의된 것들만 참조할 수 있기 때문
  import game
  game.sound.echo.echo_test()
  #아래의 경우는 불가능, 왜냐하면 import . . 의 가장 마지막 항목은 반드시 모듈 또는 패키지여야만 한다.
  import game.sound.echo.echo_test()
  ```

* --init--.py의 용도

  해당 디렉터리가 패키지의 일부임을 알려주는 용도. 만약 없으면 패키지로 인식하지 않는다. 따라서 다 있는게 좋다

* --all--의 용도

  ```python
  from game.sound import *
  echo.echo_test()
  # from game.sound.echo import *은 당연히 __all__과 상관없이 된다
  # __all__과 상관없이 무조건 import 되는 경우는 from a.b.c import *에서 c가 모듈인 경우이다.
  ```

  위와 같이 사용할 수 없다. 이러한 목적으로 사용하기 위해서는 해당 디렉토리의 init.py파일에 --all--=['echo'] 와 같이 선언하여 import할 수 있는 모듈을 정의해 주어야 한다.

  (여기서 --all--은 sound 디렉토리에서 *를 이용하여 import하는 경우 이곳에 정의된 echo모듈만 import된다는 것이다)

* relative 패키지

  위의 경우에서 graphic 디렉토리의 render.py 모듈이 sound 디렉토리의 echo.py모듈을 사용하고 싶다면, render.py를 다음과 같이 수정한다

  ```python
  #render.py
  from game.sound.echo import echo_test
  #blahblah
  ```

  이렇게 되면 외부에서 render모듈을 실행할 때 render모듈은 echo_test()를 사용할 수 있다. 또는,

  ```python
  #render.py
  from ..sound.echo import echo_test
  #blahblah
  ## python 2.5부터 지원
  ```

  이러한 식으로도 가능하다. 여기서 ..은 부모 디렉터리를 의미한다. (Cf '.'은 현재 디렉토리를 의미), 또한 여기서는 graphic과 sound의 디렉토리가 같은 depth여서 이렇게 표현이 가능하다.(relative한 접근자 사용,반드시 모듈 안에서 사용해야 한다,인터프리터 단에서는 불가능)

