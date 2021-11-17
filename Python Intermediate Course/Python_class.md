# Python intermediate course 1 < Class >

<br/>

## initiate the class

<br/>

- "__init__" : class를 초기 생성해주는 생성자 (constructor)  
- 반드시 self를 인자로 가져야하고, 그 후 생성할 때 전달 받을 parameter들을 넣어준다.  
<br/>

## add new methods

<br/>

- 일반적인 함수를 선언하듯이 선언하면 된다.  
- 다만, 그 객체의 attribute에 접근하고 싶다면, parameter로 self를 붙여주면 된다.  



```python
class Quadrangle:
    def __init__(self,width,height,color): #생성자
        self.width = width
        self.height = height
        self.color = color
        
    def print_info(self): #method, attribute에 접근하기 위해 self를 parameter로 함
        print('width :',self.width)
        print('height :',self.height)
        print('color :',self.color)

Rectalge = Quadrangle(10,5,'red') #생성자로 객체 생성
Square = Quadrangle(7,7,'blue') #생성자로 객체 생성

Rectalge.print_info() #객체에서 method 호출
```

    width : 10
    height : 5
    color : red


## Inheritance

  - **추상화(abstraction)**: 여러 클래스에 중복되는 속성, 메서드를 하나의 기본 클래스로 작성하는 작업
  - **상속(inheritance)**: 기본 클래스의 공통 기능을 물려받고, 다른 부분만 추가 또는 변경하는 것
    + 이 때 기본 클래스는 부모 클래스(또는 상위 클래스), Parent, Super, Base class 라고 부름
    + 기본 클래스 기능을 물려받는 클래스는 자식 클래스(또는 하위 클래스), Child, Sub, Derived class 라고 부름
  <br><br>
  - 코드 재사용이 가능, 공통 기능의 경우 기본 클래스 코드만 수정하면 된다는 장점
  - 부모 클래스가 둘 이상인 경우는 다중 상속 이라고 부름
<br/>

<img src="https://www.fun-coding.org/00_Images/oop3.png" />
>>잔재미코딩님의 이미지 활용.

- 상속받는 방법은 클래스 생성시 클래스의 이름 옆에 (부모 클래스)를 붙이면 됨.
- 상속받는 순간 부모의 모든 attribute, method를 그대로 받음.

<br/>

## Method Override

<br/>

- 부모 클래스에서 가져온 메소드를 추가하거나 변경하고 싶으면, 그 메소드의 이름을 그대로 가져와서 재정의 하면 됨.  

<br/>


```python
class Car: # Parent class
    def __init__(self,name):
        self.name = name
    
    def get_info(self):
        print('-------------------')
        print('Name :',self.name)
        
class ElectronicCar(Car): # Child Class
    def get_info(self): ## Overide
        print('-------------------')
        print('Name :',self.name)
        print('Engine : Eletronic')
        
class GasolineCar(Car): # Child Class
    def get_info(self): ## Overide
        print('-------------------')
        print('Name :',self.name)
        print('Engine : Gasoline')

a = Car('a')
b = ElectronicCar('b')
c = GasolineCar('c')
for i in a,b,c:
    i.get_info()
```

    -------------------
    Name : a
    -------------------
    Name : b
    Engine : Eletronic
    -------------------
    Name : c
    Engine : Gasoline


## Using super and self

<br/>

### super()
 - 자식 클래스에서 부모 클래스의 method를 호출할 때 사용
   - super().부모 클래스의 method명
   


```python
class ElectronicCar(Car): # Child Class
    def get_info(self): ## Overide
        super().get_info() # Can reduce common part with parent
        print('Engine : Eletronic')
        
class GasolineCar(Car): # Child Class
    def get_info(self): ## Overide
        super().get_info()
        print('Engine : Gasoline')
        
a = Car('a')
b = ElectronicCar('b')
c = GasolineCar('c')
for i in a,b,c:
    i.get_info()
```

    -------------------
    Name : a
    -------------------
    Name : b
    Engine : Eletronic
    -------------------
    Name : c
    Engine : Gasoline


### self
 - self는 현재의 객체를 나타냄
   - self.method명 또는 attribute명 으로 호출함
 - C++/C#, Java언어에서는 this 라는 키워드를 사용함


```python
class GasolineCar(Car): # Child Class
    def get_info(self): ## Overide
        super().get_info()
        print('Engine : Gasoline')
    
    def get_just_Name(self):
        super().get_info()
    
    def get_engine_too(self):
        self.get_info()

temp = GasolineCar('temp')
temp.get_info()
temp.get_just_Name()
temp.get_engine_too()
```

    -------------------
    Name : temp
    Engine : Gasoline
    -------------------
    Name : temp
    -------------------
    Name : temp
    Engine : Gasoline


