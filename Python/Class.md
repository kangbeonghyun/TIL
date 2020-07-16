# Python(ref. 점프투파이썬 172p~)

## Class

* 사용이유

  같은 일을 함수를 여러개 선언할 필요 없이(예를 들어 독립적으로 값을 저장해야 하는 경우) 클래스로 정의하여 불필요한 함수 중복을 없앨 수 있다.

  인스턴스만 생성해서 사용 가능

  Ex) def cal1:, def cal2:...가 아닌 Class Calcultor: 후 cal1=Calculator(), cal2=Calculator() # 계산기 서비스를 이용하기 위해 가입하는 느낌.

  클래스: 뽑기의 틀, 인스턴스: 클래스에 만들어진 피조물(=객체)

  Ex) a=cal() 일때 a는 객체이며 a는 cal의 인스턴스이다.

* 사용법

  도트 연산자'.'를 이용하여 클래스 내의 선언된 변수나 함수를 사용할 수 있다.

  ```python
  class Cal():
    num="here"
    def sum(self,a,b):#self를 꼭 써주자, 이렇게 해야 해당 인스턴스의 함수로 사용할 수 있다.
      result=a+b
      print("good")
    
  c=Cal()
  c.sum(1,1)# 여기서 c.sum(self,1,1)이런 식으로 사용해야 할 것 같지만 def에서 self가 자동적으로 호출한 인스턴스인 c로 대체되므로 생략 가능하다.
  # 또한 클래스명.메소드 형태로 사용 가능하긴 하지만 잘 안쓰이며 이경우 꼭 객체명을 넣어주어야 한다...Cal.sum(c,1,1)
  # c2=Cal()이 추가되었을경우 c와 c2는 서로다른 객체로 각자 고유한 저장 영역을 가지고 있으며 각 객체의 변수는 이름이 같더라도 해당 객체의 변수이기 때문에 독립적임. 
  >> good
  ```

  ```python
  class Service():
    def setname(self,name):#self는 usr1라는 아이디를 받음
      self.name=name# usr1.name=name으로 바뀌고 usr1.name="KBH"가 됨
    def sumcal(self,a,b):
      r=a+b
      print("%s야 %s+%s=%s다"%(self.name,a,b,result))
      # 여기서도 self.name은 usr1.name으로 치환되기 때문에 이름을 알 수 있음
  usr1=Service()
  usr1.setname("KBH")
  usr1.sum(1,1)
  >>KBH야 1+1=2다
  #만약 sumcal의 r 이 self.r이런식으로 되어 있다면 usr1.r 이런식으로 접근하여 사용할 수 있다.
  ## 또는
  class Service2():
    def setnum(self,frist,second):
      self.first=first
      self.second=second
    def sumcal(self):
      result self.first+self.second
      return resul
  
  ```

* "--init--"(undef bar)(=생성자)

  위의 처럼 setname을 호출하여 사용하는 것 대신 어차피 필수적으로 행해져야 될 작업이라면 init을 사용하여 인스턴스를 만들 때 항상 실행 되도록 할 수 있다.

  ```python
  class Service():
    def __init__(self,name):
      self.name=name
    ###blahblah
  
  usr1=Service("KBH") #이와 같이 사용하여 setname을 불러 사용하지 않아도 된다.
  ```

* Class 구조

  ```python
  class 클래스 이름(상속할 클래스 명):
    #pass 로 작성하면 아무것도 하지 않고 인스턴스 생성하는 용도로 쓰임 할일이 정해지면 지워줘야 함.
    <클래스 변수 1,2,...,N개>
    def 클래스 함수(self, 인수1,인수2,,,):#클래스 함수=메소드
    ### 수행할 문장
    
  ```

* Class의 상속

  ```python
  # cal1의 클래스가 이미 만들어 져있다 가정
  class cal2(cal1):
    num=2
  #이런 식으로만 설정 해 주어도 cal에 있는 cal1의 __init__메소드와 기타 메소드를 그대로 사용할 수 있다.
  ```

  메소드 오버라이딩: 상속받을 클래스의 메소드와 이름은 같지만 다른 일을 수행해야 할 경우-> 그냥 다시 구현하면 됨.

  연산자 오버로딩: 연산자를 객체끼리 사용할 수 있게 하는 기법(대체 느낌 각 연산자 자체의 의미는 없음 즉, 더하거나 빼지않고 +,- 등으로 간편하게 표현할 수 있는 장점정도)

  ```python
  class H1:
    lastname="kim"
    def __init__(self,name):
      self.fullname=self.lastname+name
    def travel(self,where):
      print("%s, %s로 여햏감"%(self.fullname,where))
    def love(self,other):
      print("%s %s 사빠"%(self.fullname,other.fullname))
    def __add__(self,other):#연산자 오버로딩
      print("%s %s 사귄다"%(self.fullname,other.fullname))
  
  class H2(H1): # H2가 H1을 상속받음
    lastname="Kang"
    def travel(self,where,day):#메소드 오버라이딩
      print("%s %s날 %s여행갔다"%(self.fullname,day,where))
  
  usr1=H1("abc")
  usr2=H2("def")
  usr2.travel("미국",3)#kang 3날 미국여행갔다
  usr1.love(usr2)# kimabc kangdef 사귄다
  usr2.love(usr1)# kangdef kimabc 사귄다
  usr1+usr2#kimabc kangdef 사귄다
  usr2+usr1#kangdef kimabc 사귄다
  
  ## - : __sub__ 
  
  ```

  

