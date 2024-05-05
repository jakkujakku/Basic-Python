# Python(보충)

- 매개 변수(= Paramater) 와 인수(= Arguments)
  - 매개변수 : 함수에 입력으로 전달되는 값을 받는 변수를 의미
  - 인수 : 함수를 호출할 때 전달하는 입력값

------

## List

- **Count** : **현재 리스트의 특정 Value 가 몇개 있는지 알려줌.**
- **Clear : 현재 리스트에 있는 모든 Value 들을 삭제함.**
- Reverse: 현재 리스트에 있는 Value 들의 앞뒤 순서를 변경함.
- Append : 현재 리스트에 Value 을 추가할 수 있음.
- Remove : 현재 리스트에 특정 Value 를 삭제할 수 있음.

------

## URL Formatting

- startswith : 문자열이 특정문자로 시작하는지 여부를 알려줌. True 나 False 를 반환함.

```python
websites = (
    "google.com",
    "airbnb.com",
    "https://twitter.com",
    "facebook.com",
    "https://tiktok.com",
)

for website in websites:
    if website.startswith("https://"):
        print("good to go")
    else:
        print("we have to fix it")
        
# Result
we have to fix it
we have to fix it
good to go
we have to fix it
good to go
```

------

## Status Codes

- Requests Packages : URL 의 요청을 보낸 후, Status Code 를 알 수 있는 Package
- HTTP Status Code
  - 1XX : Information responses
  - 2XX : Successful responses
  - 3XX : Redirection messages
  - 4XX : Client error responses
  - 5XX : Server error reponses

```python
from requests import get

websites = (
    "google.com",
    "airbnb.com",
    "https://twitter.com",
    "facebook.com",
    "https://tiktok.com",
)

results = {

}

for website in websites:
    if not website.startswith("https://"):
        website = f"https://{website}"
    response = get(website)

    if response.status_code == 200:
        results[website] = "OK"
    else:
        results[website] = "FAILED"

print(results)
```

------

## Class 

- 생성 메서드 : 객체가 생성될 때 자동으로 호출되는 생성자 메서드, 객체의 초기화를 담당함.

```python
def __init__(self):
```

------

## Methods

- 파이썬에서 특별한 용도로 사용되는 메서드들은 양쪽에 이중 언더스코어('__')가 붙음. 특별 메서드 또는 매직 메서드라고 부르며, 이를 통해 객체에 대한 다양한 연산을 정의하고 사용할 수 있습니다.

- init 메서드 : 객체가 생성될 때 자동으로 호출되는 생성자 메서드
- Str 메서드 : 객체 자체의 내용을 출력하고 싶을 때, 형식을 지정하는 메서드

```python
class Puppy:

    def __init__(self, name, breed):
        self.name = name
        self.age = 0.1
        self.breed = breed

    def __str__(self):
        return f"Puppy named {self.name}, breed: {self.breed}"

ruffus = Puppy(
    name="Ruffus",
    breed="Beagle"
)
print(ruffus)
```

------

## Inheritance - 1

- 파이썬에서 상속할려면 **상속받을려는 클래스명(상속할려는 클래스명)** 이렇게 사용하면 됨.

```python
class Dog:
    def __init__(self, name, breed, age):
        self.name = name
        self.breed = breed
        self.age = age


class GuardDog(Dog):

    def rrrrr(self):
        print("stay away")
```

## Inheritance - 2

- Super() 함수는 파이썬에서 사용되는 특별한 함수임
- 부모 클래스의 메서드를 자식 클래스에서 호출하는 데 사용됨.
  - 자식 클래스에서 부모 클래스의 메서드를 호출하려면, super() 를 사용하여 부모 클래스의 메서드를 호출하면서 현재 클래스의 인스턴스를 전달함.

```python
class GuardDog(Dog):

    def __init__(self, name, breed):
      	# Dog 부모 클래스의 init 호출
        super().__init__(
            name,
            breed,
            5,
        )

    def rrrrr(self):
        print("stay away")
```

