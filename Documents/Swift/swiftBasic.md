# 스위프트 기초

> 참조: 네이버 [부스트코스] iOS 프로그래밍을 위한 스위프트 기초. by yagom님  
> [네이버 부스트코스 링크](https://www.edwith.org/boostcamp_ios/joinLectures/38564)  
> [야곰 닷넷 링크](https://yagom.net/courses/swift-basic/)

---

강의를 들으며 Notion에 기록한 것을 복사/붙여넣기 하는 방식으로 작성하고 있다.

---

## 1. 명명법 / 콘솔로그 / 문자열 보간법

### 이름짓기 규칙

기본적으로 Camel Case 사용

- Lower Camel Case: function, method, variable, constant

  ex) soemVariableName

- Upper Camel Case: type(class struct, enum, extension ...)

  ex) Person, Point, Week

- 대소문자를 구분!

### 콘솔로그

- print

  단순 문자열 출력

- dump

  인스턴스의 자세한 설명(description 프로퍼티)까지 출력

### 문자열 보간법 (파이썬에서 문자열 포매팅)

- String Interpolation
- 프로그램 실행 중 문자열 내에 변수 또는 상수의 실질적인 값을 표현하기 위해 사용
- \()

## 2. 상수와 변수

### 상수와 변수 선언

- let: 상수 선언 키워드
  - let 상수이름: 타입 = 값
  - 차후에 값 변경이 불가능
- var: 변수 선언 키워드
  - var 변수이름: 타입 = 값
  - 차후에 값 변경이 가능
- 값의 타입이 명확하다면 타입 생략 가능

  - let 상수이름 = 값
  - var 변수이름 = 값

### 상수 선언 후 값 할당하기

선언을 먼저 한 뒤, 나중에 값을 할당하려는 상수나 변수는 반드시 타입을 명시해야 한다.

- let sum: Int

선언 후 할당

- sum = 100 + 200
- (상수는 값 할당 이후에 다시 값을 바꿀 수 없음. 오류발생)

변수도 물론 차후에 할당하는 것이 가능함

- var nickName: String
- nickName = 'yagom'
- nickName = '야곰' # 변수는 차후에 다시 다른 값을 할당해도 문제가 없음

## 3. 기본 데이터 타입

스위프트는 데이터 타입에 굉장히 엄격한 언어.  
다른 데이터 타입끼리 값의 교환이 불가능

### Swift의 기본 데이터 타입

### Bool

- true와 false만을 값으로 가지는 타입
  - 파이썬과 달리, 0이나 1을 값으로 가지지 못한다.
- var someBool: Bool = true
- someBool = false

### Int, UInt

- Int: 정수 타입. 기본적으로 64비트 정수형
- UInt: 양의 정수 타입. 기본적으로 64비트 양의 정수형.

### Float, Double (정수 입력 가능, 정수 타입인 변수 입력 불가능)

- Float: 실수 타입. 32비트 부동소수형
- Double: 실수 타입. 64비트 부동소수형

### Character, String

- Character: 문자 타입. 유니코드 사용(이모티콘 가능). 큰따옴표("") 사용. 한 글자만 가능
- String: 문자열 타입. 유니코드 사용. 큰따옴표("")사용. 문자열

### 타입 확인하는 법

```swift
type(of: )
```

## 4. Any, AnyObject, nil

### 생각해보기

- 사람이 사용하는 숫자 0은 '없음'이라는 의미를 갖고 있다. 프로그래밍에서 0은 없음을 나타낼 수 있을까?
- 0이 있는데 nil이라는 표현은 왜 존재하는 것일까?

### Any

- Swift의 모든 타입을 지칭하는 키워드
  - var someAny: Any = 3.14
- Any 타입에 Double 자료를 넣어두었더라도, Any는 Double 타입이 아니기 때문에 Double 타입의 변수에 할당할 수 없다.
  - 명시적으로 타입을 변환해 주어야 한다.

### AnyObject

- 모든 클래스 타입을 지칭하는프로토콜
  - class SomeClass {}
  - var someAnyObject: AnyObject = SomeClass()
- AnyOjbect는 클래스의 인스턴스만 수용 가능하기 때문에 클래스의 인스턴스가 아니면 할당할 수 없다.

### nil

- 없음을 의미하는 키워드
- 다른 언어의 NULL, Null, null 등과 유사한 표현이다.
  - Any와 AnyObject에는 nil을 할당할 수 없다.

## 5. 컬렉션 타입(Array, Dictionary, Set)

#### Array

- 멤버가 순서(인덱스)를 가진 리스트 형태의 타입
- 여러가지 리터럴 문법을 활용할 수 있어 표현 방법이 다양하다.

Array 선언 및 생성

```swift
var integers: Array<Int> = Array<Int>()
var integers: Array<Int> = [Int]()
var integers: Array<Int> = []
var integers: [Int] = Array<Int>()
var integers: [Int] = [Int]()
var integers: [Int] = []
var integers = [Int]()
```

#### Array 활용

멤버 추가

```swift
integers.append(1) # 멤버 추가
```

멤버 포함 여부 확인

```swift
integers.contrains(100) # 멤버 포함 여부 확인
```

멤버 삭제

```swift
integers.remove(at: 0) # 멤버 삭제
integers.removeLast()
integers.removeAll()
```

멤버 수 확인

```swift
integers.count  # 멤버 수 확인
```

#### 불변 Array: let을 사용하여 Array 선언

```swift
let immutableArray = [1, 2, 3]
```

만약 빈 Array를 주고 싶으면 explicit 하게 선언해야 한다.

```swift
let immutableArray: Array<Any> = Array<Any>()
```

### Dictionary

- '키'와 '값'의 쌍으로 이루어진 컬렉션 타입
- Array와 비슷하게 여러가지 리터럴 문법을 활용할 수 있어 표현 방법이 다양하다.

#### Dictionary의 선언과 생성

```swift
var anyDictionary: Dictionary<String, Any> = [String: Any]()
var anyDictionary: Dictionary<String, Any> = Dictionary<String, Any>()
var anyDictionary: Dictionary<String, Any> = [:]
var anyDictionary: [String: Any] = Dictionary<String, Any>()
var anyDictionary: [String: Any] = [String: Any]()
var anyDictionary: [String: Any] = [:]
var anyDictionary: [String: Any]()
```

#### Dictionary 활용

키에 해당하는 값 할당

```swift
aniDictionary["someKey"] = "value" # 키에 해당하는 값 할당
anyDictionary["anotherKey"] = 100
```

키에 해당하는 값 변경

```swift
anyDictionary["someKey"] = "dictionary" # 키에 해당하는 값 변경
```

키에 해당하는 값 삭제

```swift
anyDictionary.removeValue(forKey: "anotherKey") # 키에 해당하는 값 삭제
anyDictionary["anotherKey"] = nil
```

#### 불변 Dictionary: let 을 사용하여 Dictionary 선언

```swift
let emptyDictionary: [String: String] = [:]
let initializedDictionary: [String: String] = ["name": "yagom", "gender": "male"]

//불변 Dictionary이므로 값 변경 불가!불변 Dictionary이므로 값 변경 불가!
```

키에 해당하는 값을 다른 변수나 상수에 할당하고자 할 때는 옵셔널과 타입 캐스팅 파트에서 다룸.

"name"이라는 키에 해당하는 값이 없을 수 있으므로, Sting 타입의 값이 나올 것이라는 보장이 없다.

```swift
let someValue: String = initializedDictionary["name"]
// 컴파일 오류 발생!
```

### Set

- 중복되지 않는 멤버가 순서없이 존재하는 컬렉션
- Array, Dictionary와 다르게 축약형이 존재하지 않음

#### Set 생성 및 선언

```swift
var integerSet: Set<Int> = Set<Int>()
```

멤버 추가 - 동일한 값을 여러번 Insert 해도 한 번만 저장됨

```swift
integerSet.insert(1)
```

멤버 포함 여부 확인

```swift
integerSet.contains(1)
```

멤버 삭제

```swift
integerSet.remove(1)
integerSet.removeFirst()
```

멤버 개수

```swift
integerSet.count
```

#### Set의 활용

멤버의 유일성이 보장되기 때문에 **집합 연산**에 활용하면 유용하다.

```swift
let setA: Set<Int> = [1, 2, 3, 4, 5]
let setB: Set<Int> = [3, 4, 5, 6, 7]
```

합집합 **(union)**

```swift
let union: Set<Int> = setA.union(setA)
```

합집합 오름차순 정렬 **(sorted) - Array로 반환됨**

```swift
let sortedUnion: [Int] = union.sorted()
```

교집합 **(intersection)**

```swift
let intersection: Set<Int> = setA.intersection(setB)
```

차집합 **(subtracing)**

```swift
let subtracting: Set<Int> = setA.subtracting(setB)
```

## 6. 함수 기본

### 함수 선언의 기본 형태

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
  /*함수 구현부*/
}

// 예시
fnc sum(a: Int, b: Int) -> Int {
	return a + b
}
```

### 반환 값이 없는 함수

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> Void {
  /*함수 구현부*/
}
// 예시
func printMyName(name: String) -> Void {
  print(name)
}
// 반환 값이 없는 경우, 반환 타입(Void)을 생략해줄 수 있다.
func printYourName(name: String) {
  print(name)
}
```

### 매개변수가 없는 함수

```swift
func 함수이름() -> 반환타입 {
  /*함수 구현부*/
}
// 예시
func maximumIntegerValue() -> Int {
  return Int.max
}
```

### 매개변수와 반환값이 없는 함수

```swift
func 함수이름() -> Void {
  /*함수 구현부*/
  return
}

/* 함수 구현이 짧은 경우
가독성을 해치지 않는 범위에서
줄바꿈을 하지 않고 한 줄에 표현해도 무관하다.*/
func hello() -> Void {print("hello")}

// 반환 값이 없는 경우, 반환 타입(Void)을 생략해줄 수 있다.
func 함수이름() {
  /*함수 구현부*/
  return
}

func bye() {print("bye")}
```

### 함수의 호출

```swift
sum(a: 3, b:5) //8

printMyName(name: "yagom") //yagom

printYourName(name: "haha") //haha

maximumIntegerValue() //Int의 최댓값

hello() //hello

bye() //bye
```

## 7. 함수 고급

### 함수 선언의 기본 형태

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> 반환타입 {
  /*함수 구현부*/
}

// 예시
fnc sum(a: Int, b: Int) -> Int {
	return a + b
}
```

### 반환 값이 없는 함수

```swift
func 함수이름(매개변수1이름: 매개변수1타입, 매개변수2이름: 매개변수2타입 ...) -> Void {
  /*함수 구현부*/
}
// 예시
func printMyName(name: String) -> Void {
  print(name)
}
// 반환 값이 없는 경우, 반환 타입(Void)을 생략해줄 수 있다.
func printYourName(name: String) {
  print(name)
}
```

### 매개변수가 없는 함수

```swift
func 함수이름() -> 반환타입 {
  /*함수 구현부*/
}
// 예시
func maximumIntegerValue() -> Int {
  return Int.max
}
```

### 매개변수와 반환값이 없는 함수

```swift
func 함수이름() -> Void {
  /*함수 구현부*/
  return
}

/* 함수 구현이 짧은 경우
가독성을 해치지 않는 범위에서
줄바꿈을 하지 않고 한 줄에 표현해도 무관하다.*/
func hello() -> Void {print("hello")}

// 반환 값이 없는 경우, 반환 타입(Void)을 생략해줄 수 있다.
func 함수이름() {
  /*함수 구현부*/
  return
}

func bye() {print("bye")}
```

### 함수의 호출

```swift
sum(a: 3, b:5) //8

printMyName(name: "yagom") //yagom

printYourName(name: "haha") //haha

maximumIntegerValue() //Int의 최댓값

hello() //hello

bye() //bye
```

## 8. 조건문

### 생각해보기

- if-else 구문과 switch 구문의 적절한 활용 예에 대해 생각해보기
- if-else 구문과 switch 구문의 사용에 있어 각각의 장단점은 무엇이 있을지 생각해보기

### if-else 구문

#### if-else 구문의 기본 형태

- if만 단독으로 사용해도 되고, else, else if 와 조합해서도 사용 가능
- if 뒤의 조건 값에는 **Bool 타입의 값만** 위치해야 한다. (0, 1 불가능)
- 조건을 감싸는 소괄호는 선택사항이다.

```swift
if 조건 {
  /*실행구문*/
} else if 조건 {
  /*실행구문*/
}
else {
  /*실행구문*/
}
```

#### if-else의 사용

```swift
let someInteger = 100
if someInteger < 100 {
  print("100 미만")
} else if someInteger > 100 {
  print("100 초과")
} else {
  print("100")
}

/* 스위프트의 조건에는 항상 Bool 타입이 들어와야 한다.
someIneger는 Bool 타입이 아닌 Int 타입이기 때문에
컴파일 오류가 발생한다.*/
if someInteger {}
```

### switch 구문

- 스위프트의 switch 구문은 다른 언어에 비해 굉장히 강력한 힘을 발휘한다.
- 기본적으로 사용하던 정수타입의 값만 비교하는 것이 아니라 대부분의 스위프트 기본 타입을 지원하며, 다양한 패턴과 응용이 가능하다.
- 스위프트의 다양한 패턴은 Swift Programming Language Reference의 패턴에서 확인할 수 있다.

[Patterns - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/ReferenceManual/Patterns.html#//apple_ref/doc/uid/TP40014097-CH36-ID419)

- 각각의 case 내부에는 실행가능한 코드가 반드시 위치해야 한다.
- 매우 한정적인 값(ex. enum의 case 등)이 비교값이 아닌 한 default 구문은 반드시 작성해야 한다.
- 명시적 break를 하지 않아도 자동으로 case마다 break 된다.
- falltrhough 키워드를 사용하여 break를 무시할 수 있다.
- 쉽표(,)를 사용하여 하나의 case에 여러 패턴을 명시할 수 있다.

#### switch 구문의 기본 형태

```swift
switch 비교값 {
case 패턴:
  /*실행구문*/
default:
  /*실행구문*/
}
```

#### switch 구문의 사용

```swift
// 범위 연산자를 활용하면 더욱 쉽고 유용하다.
switch someInteger {
case 0:
  print("zero")
case 1..<100:
  print("1~99")
case 100:
  print("100")
case 101...Int.max:
  print("over 100")
default:
  print("unknown")
} //100

// 정수 외의 대부분의 기본 타입을 사용할 수 있다.
switch "yagom"{
case "jake":
  print("jake")
case "mina":
  print("mina")
case "yagom":
  print("yagom!!")
default:
  print("unknown")
} // yagom!!
```

## 9. 반복문

### or-in 구문

- 기존 언어의 for-each 구문과 유사하다.
- Dictionary의 경우 이터레이션 아이템으로 튜플이 들어온다. (애플 문서 참조)

[The Basics - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/TheBasics.html)

#### for-in 구문 기본 형태

```swift
for item in items {
  /*실행구문*/
}
```

#### for-in 구문의 사용

```swift
var integers = [1, 2, 3]
let people = ["yagom": 10, "eric": 15, "mike": 12]

for integer in integers {
  print(integer)
}

// Dictionary의 item은 key와 value로 구성된 튜플 타입이다.
for (name, age) in people {
  print("\(name): \(age)")
}
```

### while 구문

#### while 구문의 기본 형태

```swift
while 조건 {
  /*실행구문*/
}
```

#### while 구문의 사용

```swift
while integers.count > 1 {
  integers.removeLast()
}
```

### repeat-while 구문

- 기존 언어의 do-while 구문과 형태/동작이 유사하다.

#### repeat-while 구문의 기본 형태

```swift
repeat {
  /*실행구문*/
} while 조건
```

#### repeat-while 구문의 사용

```swift
repeat {
  integers.removeLast()
} while integers.count > 0
```

### while 구문과 repeat-while 구문의 차이점 (스스로 찾아보고 추가한 부분)

- **while** 구문은 condition이 충족되는지를 <U>**먼저 체크**</U>한 뒤, 충족될 경우에만 구문을 실행하는 반면,  
  **repeat-while** 구문은 <U>**우선 구문을 한 번 실행**</U>한 뒤 condition이 충족되는지를 체크하고 반복한다.

```swift
var integers = [1, 2, 3]

while integers.count > 3 {
  integers.removeLast()
}
print(integers) // [1, 2, 3]

var integers = [1, 2, 3]
repeat {
  integers.removeLast()
} while integers.count > 3
print(integers) // [1, 2]
```

## 10. 옵셔널

### 옵셔널이란??

- 값이 있을 수도, 없을 수도 있음을 표현
- nil이 할당될 수 있는지 없는지를 표현

```swift
//someOptionalParam에 nil이 할당될 수 있다.
func someFunction (someOptionalParam: Int?) {
  // ...
}

//someOptionalParam에 nil이 할당될 수 없다.
func someFunction (someOptionalParam: Int) {
  // ...
}

someFunction(someOptionalParam: nil)
// someFunction(someParam: nil)
```

### 옵셔널을 쓰는 이유

- **명시적 표현**
  1. nil의 가능성을 **코드만으로** 표현가능
  2. 문서/주석 작성 시간 절약
- **안전한 사용**
  1. 전달받은 값이 옵셔널이 아니라면 nil 체크를 하지 않고 사용가능
  2. 예외 상황을 최소화 하는 안전한 코딩
  3. 효율적 코딩

### 옵셔널 문법과 선언

- 옵셔널 문법 = enum + generics

#### 옵셔널 선언

```swift
enum Optional<Wrapped>: ExpressibleByNiliteral {
  case none
  case some(Wrapped)
}

let optionalValue: Optional<Int> = nil
let optionalValue: Int? = nil
```

#### 옵셔널 표현

##### 느낌표(!)를 이용한 암시적 추출(Implicitly Unwrapped Optional)

```swift
//Implicitly Unwrapped Optional
var implicitlyUnwrappedOptionalValue: Int! = 100

switch implicitlyUnwrappedOptionalValue {
case .none:
  print("This Optional variable is nil")
case .some(let value):
  print("Value is \(value)")
}

// 기존 변수처럼 사용 가능
implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1

// nil 할당 가능
implicitlyUnwrappedOptionalValue = nil

// 잘못된 접근으로 인한 런타임 오류 발생
//implicitlyUnwrappedOptionalValue = implicitlyUnwrappedOptionalValue + 1
```

##### 물음표(?)를 이용한 옵셔널

```swift
//Optional
var optionalValue: Int? = 100

switch optionalValue {
case .none:
  print("This Optional variable is nil")
case .some(let value):
  print("Value is \(value)")
}

// 기존 변수처럼 사용불가 - 옵셔널과 일반 값은 다른 타입이므로 연산불가
//optionalValue = optionalValue = 1

// nil 할당 가능
optionalValue = nil
```

## 11. 옵셔널 추출

### 옵셔널 추출이란?

- 옵셔널에 들어있는 값을 사용하기 위해 꺼내오는 것

### 옵셔널 방식

- **옵셔널 바인딩**

  1. nil 체크 + 안전한 추출
  2. 옵셔널 안에 값이 들어있는지 확인하고, 값이 있으면 값을 꺼내온다.
  3. if-let 방식 사용

  ```swift
  func printName(_ name: String) {
    print(name)
  }

  var myName: String? = nil

  //printName(myName)
  //전달되는 값의 타입이 다르기 때문에 컴파일 오류발생

  if let name: String = myName {
    printName(name)
  } else {
    print("myName == nil")
  }

  var yourName: String! = nil

  if let name: String = yourName {
    printName(name)
  } else {
    print("yourName == nil")
  }

  //name 상수는 if-let 구문 내에서만 사용 가능하다.
  //상수 사용범위를 벗어났기 때문에 컴파일 오류 발생
  //printName(name)

  // ,를 사용해 한 번에 여러 옵셔널을 바인딩할 수 있다.
  // 모든 옵셔널에 값이 있을 때만 작동한다.
  myName = "yagom"
  yourName = nil

  if let name = myName, friend = yourName {
    print("\(name) and \(friend)")
  }
  //yourName이 nil이기 때문에 실행되지 않는다.
  yourName = "haha"

  if let name = myName, friend = yourName {
    print("\(name) and \(friend)")
  }
  // yagom and haha
  ```

#### 강제추출 방식: 옵셔널에 값이 들어있는지 아닌지 확인하지 않고 강제로 값을 꺼내는 방식

- 만약 값이 없을 경우(nil) 런타임 오류가 발생하기 때문에 추천되지 않는다.

  ```swift
  var myName: String? = "yagom"
  var yourName: String! = nil

  printName(myName!) //yagom
  myName = nil

  //print(myName!)
  //강제추출시 값이 없으므로 런타임 오류 발생

  yourName = nil

  //printName(yourName)
  // nil이 전달되기 때문에 런타임 오류발생
  ```

## 12. 구조체 (struct)

### 생각해보기

- 내가 알고 있는 프로그래밍 언어의 구조체와 스위프트의 구조체가 어떤 점에서 다른지 비교해보기

### 구조체란?

- 스위프트의 대부분 타입은 구조체로 이루어져 있다.
- 구조체는 **값(value) 타입**이다.
- 타입이름은 대문자 카멜케이스를 사용해서 정의한다.

### 구조체 문법

#### 구조체 정의: "struct" 키워드 사용

```swift
struct Name {
  /*구현부*/
}
```

#### 구조체 프로퍼티 및 메서드 구현

- 프로퍼티란?: 클래스나 구조체 혹은 열거체의 객체 (인스턴스)가 그 내부에 가지고 있는, 객체의 상태에 관한 정보를 말한다.
- 메서드란?: 객체 (인스턴스) 내부에 정의된 함수라고 볼 수 있다.

[Properties - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/Properties.html)

[Methods - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/Methods.html)

```swift
struct Sample {
  //가변 프로퍼티(값 변경 가능)
  var mutableProperty: Int = 100

  //불변 프로퍼티(값 변경 불가능)
  let immutableProperty: Int = 100

  //타입 프로퍼티(static 키워드 사용: 타입 자체가 사용하는 프로퍼티)
  static var typeProperty: Int = 100

  //인스턴스 메서드(인스턴스가 사용하는 메서드)
  func instanceMethod() {
    print("instance method")
  }

  //타입 메서드(static 키워드 사용: 타입 자체가 사용하는 메서드)
  static func typeMethod() {
    print("type method")
  }
}
```

#### 구조체 사용

```swift
//가변 인스턴스 생성
var mutable: Sample = Sample()

mutable.mutableProperty = 200

/*
불변 프로퍼티는 인스턴스 생성 후 수정할 수 없다.
컴파일오류 발생
*/
//mutable.immutableProperty = 200

//불면 인스턴스
let immutable: Sample = Sample()

/*
불변 인스턴스는 아무리 가변 프로퍼티라도
인스턴스 생성 후에 수정할 수 없다.
컴파일 오류 발생
*/
//immutable.mutableProperty = 200
//immutable.immutableProperty = 200

//타입 프로퍼티 및 메서드
Sample.typeProperty = 300
Sample.typeMethod() // type method

/* 인스턴스는 타입 프로퍼티나 타입 메서드를 사용할 수 없다.
컴파일 오류 발생*/
//mutable.typeProperty = 400
//mutable .typeMethod()
```

#### 학생 구조체 만들어보기

```swift
//구조체 만들기
struct Student {
  //가변 프로퍼티
  var name: String = "unknown"

  //class와 같은 키워드로 `(백틱)로 묶어주면 이름으로 사용할 수 있다.
  var 'class':String = "Swift"

  //타입 메서드
  static func.selfIntroduce() {
    print("학생타입입니다")
  }

  //인스턴스 메서드
  //self는 인스턴스 자신을 지칭하며, 몇몇 경우를 제외하고 사용은 선택사항이다.
  func selfIntroduce() {
    print("저는 \(self.class)반 \(name)입니다."
  }
}

//타입 메서드 사용
Student.selfIntroduce() //학생타입입니다.

//가변 인스턴스 생성 & 가변 프로퍼티 값 바꿔주기
var sjpark: Student = Student()
sjpark.name = "sjpark"
sjpark.class = "스위프트"
sjpark.selfIntroduce() //저는 스위프트반 sjpark입니다

//불변 인스턴스 생성
var mina: Student = Student()

/*
불변 인스턴스이므로 프로퍼티 값 변경 불가
컴파일 오류 발생
*/
//mina.name = "mina"
mina.selfIntroduce() //저는 Swift반 unknown입니다
```

## 13. 클래스

### 클래스란?

- 클래스는 참조(reference) 타입이다.
- 타입이름은 대문자 카멜케이스를 사용해서 정의한다.
- Swift의 클래스는 다중 상속이 되지 않는다. (파이썬은 다중 상속이 된다.)

### 클래스 문법

#### 정의: "class" 키워드 사용

```swift
class Name {
  /*구현부*/
}
```

#### 프로퍼티 및 메서드 구현

```swift
class Sample {
  //가변 프로퍼티
  var mutableProperty: Int = 100

  //불변 프로퍼티
  let immutableProperty: Int = 10

  //타입 프로퍼티
  var typeProperty: Int = 100

  //인스턴스 메서드
  func instanceMethod() {
    print("instance method")
  }

  //타입 메서드
  //상속 시 재정의 불가 타입 메서드 - static
  static func typeMethod() {
    print("type method - static")
  }

  //상속 시 재정의 가능 타입 메서드 - class
  class func classMethod() {
    print("type method - class")
  }
}
```

#### 클래스 사용

```swift
//인스턴스 생성 - 참조정보 수정 가능
var mutableReference: Sample = Sample()

mutableReference.mutableProperty = 200

//불변 프로퍼티는 인스턴스 생성 후 수정할 수 없다. 컴파일 오류 발생
//mutableReference.immutableProperty = 200

//인스턴스 생성 - 참조정보 수정 불가
let immutableReference: Sample = Sample()

//클래스의 인스턴스는 참조 타입이므로 let으로 선언되었더라도 인스턴스 프로퍼티의 값 변경이 가능하다.
immutableReference.mutableProperty = 200

//다만 참조정보를 변경할 수는 없다.
//immutableReference = mutableReference

/*
참조 타입이라도 불변 인스턴스는 인스턴스 생성 후에 수정할 수 없다.
컴파일 오류 발생
*/
//immutableReference.immutableProperty = 200

//타입 프로퍼티 및 메서드
Sample.typeProperty = 300
Sample.typeMethod() // type method - static
Sample.classMethod() // type method - class

/*
인스턴스에서는 타입 프로퍼티나 타입 메서드를 사용할 수 없다.
컴파일 오류 발생
*/
//mutableReference.typeProperty = 400
//mutableReference.typeMethod()
//mutableReference.classMethod()
```

### 학생 클래스 만들어 보기

```swift
class Student {
  //가변 프로퍼티
  var name: String = "unknown"

  //키워드도 `(백틱)로 묶어주면 이름으로 사용할 수 있다.
  var `class`: String = "Swift"

  //타입 메서드
  class func selfIntroduce() {
    print("학생타입입니다")
  }

  //인스턴스 메서드
  //self는 인스턴스 자신을 지칭하며, 몇몇 경우를 제외하고 사용은 선택사항이다.
  func selfIntroduce() {
    print("저는 \(self.calss)반 \(self.name)입니다")
  }
}

//타입 메서드 사용
Student.selfIntroduce() // 학생타입입니다.

//인스턴스 생성
var sjpark: Student = Student()
sjpark.name = "sjpark"
sjpark.class = "스위프트"
sjpark.selfIntroduce() // 저는 스위프트반 sjpark입니다

//인스턴스 생성
let jiho: Student = Student()
jiho.name = "jiho"
jiho.selfIntroduce() // 저는 Swift반 jiho입니다
```

### 생각해보기

- '사람'을 나타내는 클래스를 만들어 보자
  - Hint1: 사람이 가질 수 있는 속성을 프로퍼티로, 사람이 할 수 있는 행동을 메서드로 구현할 수 있다.
  - Hint2: 이름짓기 규칙을 다시 한 번 살펴보자.

```swift
class Human {
  var name: String = "unknown"
  var age: Int = 0

  let species: String = "Human Being"

  class func selfIntroduce() {
    print("사람타입입니다.")
  }

  func selfIntroduce() {
    print("안녕하세요 저는 \(self.name)입니다. 제 나이는 \(self.age)세입니다.")
  }

  func sayHi() {
    print("안녕하세요!")
  }

  func sayBye() {
    print("안녕히 가세요!")
  }
}

var sjpark: Human = Human()

sjpark.name = "sjpark"
sjpark.age = 27

Human.selfIntroduce() // 사람타입입니다.

sjpark.selfIntroduce() // 안녕하세요 저는 sjpark입니다. 제 나이는 27세입니다.
sjpark.sayHi() // 안녕하세요!
sjpark.sayBye() // 안녕히 가세요!
```

## 14. 열거형

### 열거형

Swift 열거형은 다른 언어의 열거형과 많이 다르다.

- **유사한 종류의 여러 값을 한 곳에 모아서 정의한** 것이다. 예) 요일, 월, 계절 등
- enum 자체가 하나의 **데이터 타입**으로, 대문자 카멜케이스를 사용하여 이름을 정의한다.
- 각 case는 소문자 카멜케이스로 정의한다.
- 각 case는 그 자체가 고유의 값이다. (각 case에 자동으로 정수값이 할당되지 않음)
- 각 case는 한 줄씩 개별적으로도, 한 줄 안에 여러개로도 정의할 수 있다.

```swift
enum Name {
  case name1
  case name2
  case name3, name4, name5
  //...
}

//예제
enum BoostCamp {
  case iosCamp
  case androidCamp
  case webCamp
}
```

### 열거형 사용

- 타입이 명확할 경우, 열거형의 이름을 생략할 수 있다.
- switch 구문에서 사용하면 좋다.

```swift
enum Weekday {
  case mon
  case tue
  case wed
  case thu, fri, sat, sun
}

//열거형 타입과 케이스를 모두 사용해도 된다.
var day: Weekday = Weekday.mon

//타입이 명확하다면 .케이스 처럼 표현해도 무방하다.
day = .tue

print(day) //tue

/*
 switch의 비교값에 열거형 타입이 위치할 때
 모든 열거형 케이스를 포함한다면 default를 작성할 필요가 없다
 */
switch day {
case .mon, .tue, .wed, .thu:
  print("평일입니다")
case .fri:
  print("불금 파티!!")
case .sat, .sun:
  print("시나는 주말!!")
} // 평일입니다
```

### rawValue (원시값)

- C 언어의 enum 처럼 정수값을 가질 수 있다.
- rawValue는 case별로 각각 다른 값을 가져야 한다.
- 자동으로 1이 증가된 값이 할당된다.
- rawValue를 반드시 지닐 필요가 없다면 굳이 만들지 않아도 된다.

```swift
enum Fruit: Int {
  case apple = 0
  case grape = 1
  case peach

  // mango와 apple의 원시값이 같으므로 mango 케이스의 원시값을 0으로 정의할 수 없다.
  //case mango = 0
}

print("Fruit.peach.rawValue == \(Fruit.peach.rawValue)")
//Fruit.peach.rawValue == 2
```

- 정수 타입 뿐만 아니라, Hashable 프로토콜을 따르는 모든 타입을 원시값의 타입으로 지정할 수 있다.

```swift
enum School: String {
  case elementary = "초등"
  case middle = "중등"
  case high = "고등"
  case university
}

print("School.middle.rawValue == \(School.middle.rawValue)")
//Scholl.middle.rawValue == 중등

//열거형의 원시값 타입이 String일 때, 원시값이 지정되지 않았다면
//case의 이름을 원시값으로 사용한다.
print("School.university.rawValue == \(School.university.rawValue)")
//School.university.rawValue == university
```

### 원시값을 통한 초기화

- rawValue를 통해 초기화할 수 있다.
- rawValue가 **case에 해당하지 않을 수 있으므로**, rawValue를 통해 초기화한 인스턴스는 **옵셔널 타입**이다.

```swift
enum Fruit: Int {
  case apple = 0
  case grape = 1
  case peach

  //mango와 apple의 원시값이 같으므로
  //mango 케이스의 원시값을 0으로 정의할 수 없다
  //case mango = 0
}

//rawValue를 통해 초기화한 열거형 값은 옵셔널 타입이므로 Fruit 타입이 아니다
//let apple: Fruit = Fruit(rawValue: 0)
let apple: Fruit? = Fruit(rawValue: 0)

//if let 구문을 사용하면 rawValue에 해당하는 케이스를 곧바로 사용할 수 있다.
if let orange: Fruit = Fruit(rawValue: 5) {
  print("rawValue 5에 해당하는 케이스는 \(orange)입니다")
} else {
  print("rawValue 5에 해당하는 케이스가 없습니다")
}//rawValue에 해당하는 케이스가 없습니다
```

### 메서드

Swift의 열거형에는 메서드도 추가할 수 있다.

```swift
enum Month {
  case dec, jan, feb
  case mar, apr, may
  case jun, jul, aug
  case sep, oct, nov

  func printMessage() {
    switch self {
    case .mar, .apr, .may:
      print("따스한 봄")
    case .jun, .jul, .aug:
      print("여름 더워요~")
    case .sep, .oct, .nov:
      print("가을은 독서의 계절!")
    case .dec, .jan, .feb:
      print("추운 겨울입니다")
    }
  }
}

Month.mar.printMessage() //따스한 봄
```

### 생각해보기

- 본문 예시의 BoostCamp, Weekday, School, Fruit, Month 는 각각 열거형이 예로 적합한가?
- 그렇게 생각한 이유는?

## 15. 클래스 vs 구조체 / 열거형

[Structures and Classes - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/ClassesAndStructures.html#//apple_ref/doc/uid/TP40014097-CH13-ID82)

- 클래스는 **참조 타입**, 열거형과 구조체는 **값 타입**이라는 것이 가장 큰 차이!
- 클래스는 상속이 가능하지만, 열거형과 **구조체**는 상속이 불가능하다.

### 값 타입과 참조 타입 비교

- 값 타입 (Value Type): 데이터를 전달할 때 **값을 복사하여 전달**한다.
- 참조 타입 (Reference Type): 데이터를 전달할 때 값의 **메모리 위치를 전달**한다.

```swift
struct ValueType {
  var property = 1
}

class ReferenceType {
  var property = 1
}

//첫 번째 구조체 인스턴스
let firstStructInstance = ValueType()

//두 번째 구조체 인스턴스에 첫 번째 인스턴스 값 복사
var secondStructInstance = firstStructInstance

//두 번째 구조체 인스턴스 프로퍼티 값 수정
secondStructInstance.property = 2

/*
 두 번째 구조체 인스턴스는 첫 번째 구조체를 똑같이 복사한 별도의 인스턴스이기 때문에,
 두 번째 구조체 인스턴스의 프로퍼티 값을 변경해도 첫 번째 구조체 인스턴스의 프로퍼티 값에는 영향이 없다.
 */
print("first struct instance property: \(firstStructInstance.property)") // 1
print("second struct instance property: \(secondStructInstance.property)") // 2

//클리스 인스턴스 생성 후 첫 번째 참조 생성
let firstClassReference = ReferenceType()
//두 번째 참조 변수에 첫 번째 참조 할당
var secondClassReference = firstClassReference
// 클래스의 경우 아래와 같이 불변인스턴스로 생성해도 그 안의 가변프로퍼티 값을 변경할 수 있다.
//let secondClassReference = firstClassReference

secondClassReference.property = 2

/*
 두 번째 클래스 참조는 첫 번째 클래스 인스턴스를 참조하기 때문에
 두 번째 참조를 통해 인스턴스의 프로퍼티 값을 변경하면
 첫 번째 클래스 인스턴스의 프로퍼티 값을 변경하게 된다.
 */
print("first class reference property: \(firstClassReference.property)") // 2
print("second class reference property: \(secondClassReference.property)") // 2
```

### 값 타입을 사용하는 경우

- 연관된 몇몇의 값들을 모아서 하나의 데이터 타입으로 표현하고 싶은 경우
- 다른 객체 또는 함수 등으로 전달될 때 참조가 아니라 복사(값 복사)할 경우
- 자신을 상속할 필요가 없거나, 다른 타입을 상속 받을 필요가 없는 경우

### 스위프트에서의 사용

- 스위프트의 기본 데이터 타입은 모두 구조체로 구현되어있다.
- 스위프트는 구조체와 열거형 사용을 선호한다.
- Apple 프레임워크는 대부분 클래스를 사용한다.
- 구조체 / 클래스 선택과 사용은 개발자의 몫이다.

## 16. 클로저 기본

### 클로저

- 클로저는 실행가능한 코드 블럭이다
- 함수와 다르게 이름정의는 필요하지 않지만, 매개변수 전달과 반환 값이 존재할 수 있다는 점이 동일하다.
- 함수는 이름이 있는 클로저다.
- 일급객체로 전달인자, 변수, 상수 등에 저장 및 전달이 가능하다.

### 기본 클로저 문법

- 클로저는 중괄호 {}로 감싸져 있다.
- 괄호를 이용해 파라미터를 정의한다.
- → 를 이용해 반환 타입을 명시한다.
- "in" 키워드를 이용해 실행 코드와 분리한다.

```swift
{ (매개변수 목록) -> 반환타입 in
  실행 코드
}
```

### 클로저 사용

```swift
//sum이라는 상수에 클로저를 할당
let sum: (Int, Int) -> Int = { (a: Int, b: Int) -> Int in
  return a + b
}

let sumResult: Int = sum(1, 2)
print(sumResult) // 3
```

### 함수의 전달인자로서의 클로저

- 클로저는 주로 함수의 전달인자로 많이 사용된다.
- 함수 내부에서 원하는 코드블럭을 실행할 수 있다.

```swift
let add: (Int, Int) -> Int
add = { (a: Int, b: Int) in
  return a + b
}

let substract: (Int, Int) -> Int
substract = { (a: Int, b: Int) in
  return a - b
}

let divide: (Int, Int) -> Int
divide = { (a: Int, b: Int) in
  return a / b
}

func calculate(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
  return method(a, b)
}

var calculated: Int

calculated = calculate(a: 50, b:10, method: add)

print(calculated) // 60

calculated = calculate(a: 50, b: 10, method: substract)

print(calculated) // 40

calculated = calculate(a: 50, b: 10, method: divide)

print(calculated) // 5

//따로 클로저를 상수/변수에 넣어 전달하지 않고,
//함수를 호출할 때 클로저를 작성하여 전달할 수도 있다.

calculated = calculate(a: 50, b: 10, method: { (left: Int, right: Int) -> Int in
  return left * right
})

print(calculated) // 500
```

### 생각해보기

- 클로저가 일급 객체라는 것은 클로저를 활용하는데 있어서 어떤 의미를 가질까?

  클로저는 일급객체이기 때문에 함수의 매개변수로도 사용될 수 있고, 반환값이 될 수도 있으며, 변수나 상수에 할당될 수도 있다. 따라서 클로저는 여러가지 상황에서 활용성이 높을 것이라고 생각된다!

[Closures - The Swift Programming Language (Swift 5.3)](https://docs.swift.org/swift-book/LanguageGuide/Closures.html)

### 찾아본 내용

[일급 객체](https://ko.wikipedia.org/wiki/일급_객체)

#### 일급객체

- 컴퓨터 프로그래밍 언어 디자인에서, 일급 객체란 다른 객체들에 일반적으로 적용 가능한 연산을 모두 지원하는 객체를 가리킨다.
- 보통 함수에 **매개변수로 넘기기**, **수정하기**, **변수에 대입하기**와 같은 연산을 지원할 때 일급 객체라고 한다.
- 로빈 포플스톤은 일급 객체를 구성하는 요소는 기본적인 권리가 있다는, 다음의 정의를 내렸다.
  1. 모든 요소는 함수의 실제 매개변수가 될 수 있다.
  2. 모든 요소는 함수의 반환값이 될 수 있다.
  3. 모든 요소는 할당 명령문의 대상이 될 수 있다.
  4. 모든 요소는 동일 비교의 대상이 될 수 있다.

## 17. 클로저 고급

#### 클로저는 아래 규칙을 통해 다양한 모습으로 표현될 수 있다.

1. **후행 클로저**: 함수의 매개변수 마지막으로 전달되는 클로저는 후행클로저(trailing closure)로 함수 밖에 구현될 수 있다.
2. **반환타입 생략**: 컴파일러가 클로저의 타입을 유추할 수 있는 경우 매개변수, 반환 타입을 생략할 수 있다.
3. **단축 인자 이름**: 전달인자의 이름이 굳이 필요없고, 컴파일러가 타입을 유추할 수 있는 경우 축약된 전달인자 이름($0, $1, \$2 ...)을 사용할 수 있다.
4. **암시적 반환 표현**: 반환 값이 있는 경우, 암시적으로 맨 마지막 줄은 return 키워드를 생략하더라도 반환 값으로 취급한다.

### 기본 클로저 표현

```swift
//클로저를 매개변수로 갖는 함수 calcualte(a:b:method:)와 결과값을 저장할 변수 result 선언
func calcualte(a: Int, b: Int, method: (Int, Int) -> Int) -> Int {
  return method(a, b)
}

var result: Int
```

### 후행 클로저

클로저가 함수의 마지막 전달인자일 때, 마지막 매개변수 이름을 생략한 후 함수 소괄호 외부에 클로저를 구현할 수 있다.

```swift
result = calcualte(a: 10, b: 10) { (left: Int, right: Int) -> Int in
  return left + right
}
print(result) // 20
```

### 반환타입 생략

`calculate(a:b:method:)` 함수의 method 매개변수는 Int 타입을 반환할 것이라는 사실을 컴파일러도 알기 때문에 굳이 클로저에서 반환타입을 명시해 주지 않아도 된다. 대신 in 키워드는 생략할 수 없다.

```swift
result = calcualte(a: 10, b: 10, method: { (left: Int, right: Int) in
  return left + right
})
print(result) // 20

//후행클로저와 함께 사용할 수도 있다.
result = calcualte(a: 10, b: 10) { (left: Int, right: Int) in
  return left + right
}
print(result) // 20
```

### 단축 인자이름

클로저의 매개변수 이름이 굳이 불필요하다면 단축 인자이름을 활용할 수 있다. 단축 인자이름은 클로저의 매개변수의 순서대로 $0, $1, \$2 ...처럼 표현한다.

```swift
result = calcualte(a: 10, b: 10, method: {
  return $0 + $1
})
print(result) // 20

//당연히 후행클로저와 함께 사용할 수 있다.
result = calcualte(a: 10, b: 10) {
  return $0 + $1
}
print(result) // 20
```

### 암시적 반환 표현

클로저가 반환하는 값이 있다면 클로저의 마지막 줄의 결과값은 암시적으로 반환값으로 취급한다.

```swift
result = calcualte(a: 10, b: 10) {
  $0 + $1
}
print(result) // 20

//간결하게 한 줄로 표현해줄 수 도 있다.
result = calcualte(a: 10, b: 10) { $0 + $1 }

print(result) // 20
```

### 축약 전과 후 비교

**너무 축약된 코드는 타인이 보거나, 시간이 지난 뒤에 볼 때 명시성이 떨어질 수 있으므로 적정선에서 축약하도록 하자!**

```swift
//축약 전
result = calcualte(a: 10, b: 10, method: { (left: Int, right: Int) -> Int in
  return left + right
})

//축약 후
result = calcualte(a: 10, b: 10) { $0 + $1 }
```

### 생각해보기

- 라이브러리 혹은 다른 사람의 스위프트 코드를 보면서 클로저의 축약표현 때문에 당황했던 적은 없나?

  아직 다른 사람의 스위프트 코드를 볼 일이 없었지만, 낯선 라이브러리나 코드에서 반환타입 생략, 단축 인자이름 생략 등이 적용된 코드를 본다면 그 의미를 빠르게 파악하기 힘들 것 같다는 생각이 들었다.

## 18. 프로퍼티

### 프로퍼티의 종류

- **인스턴스 저장 프로퍼티**
- **타입 저장 프로퍼티**
- **인스턴스 연산 프로퍼티**
- **타입 연산 프로퍼티**
- 지연 저장 프로퍼티

### 정의와 사용

```swift
struct Student {
  //인스턴스 저장 프로퍼티
  var name: String = ""
  var `class`: String = "Swift"
  var koreanAge: Int = 0

  //인스턴스 연산 프로퍼티
  var westernAge: Int {
    get {
      return koreanAge - 1
      }

    set(inputValue) {
      koreanAge = inputValue + 1
    }
  }

  //타입 저장 프로퍼티
  static var typeDescription: String = "학생"

  /*
   //인스턴스 메서드
   func selfIntroduce() {
    print("저는 \(self.class)반 \(name)입니다")
   }
   */

  //읽기전용 인스턴스 연산 프로퍼티
  //간단히 위의 selfIntroduce() 메서드를 대체할 수 있다.
  var selfIntroduction: String {
    get {
      return "저는 \(self.class)반 \(name)입니다"
    }
  }

  /*
   //타입 메서드
   static func selfIntroduce() {
    print("학생다입입니다")
   }
   */

  //읽기전용 타입 연산 프로퍼티
  //읽기전용에서는 get을 생략할 수 있다.
  static var selfIntroduction: String {
    return "학생타입입니다"
  }
}

//타입 연산 프로퍼티 사용
print(Student.selfIntroduction) // 학생타입입니다

//인스턴스 생성
var sjpark: Student = Student()
sjpark.koreanAge = 27

//인스턴스 저장 프로퍼티 사용
sjpark.name = "sjpark"
print(sjpark.name) //sjpark

//인스턴스 연산 프로퍼티 사용
print(sjpark.selfIntroduction) //저는 Swift반 sjpark입니다

print("제 한국나이는 \(sjpark.koreanAge)살이고, 미쿡나이는 \(sjpark.westernAge)살입니다.")
//제 한국나이는 27살이고, 미쿡나이는 26살입니다.
```

### 응용

```swift
struct Money {
  var currencyRate: Double = 1100
  var dollar: Double = 0
  var won: Double {
    get {
      return dollar * currencyRate
    }

    set {
      dollar = newValue / currencyRate
      // set에 매개변수를 넘겨주지 않으면 그 값이 자동으로 newValue에 입력됨
    }
  }
}

var moneyInMyPocket = Money()

moneyInMyPocket.won = 11000

print(moneyInMyPocket.won) // 11000.0

moneyInMyPocket.dollar = 10

print(moneyInMyPocket.won) // 11000.0
```

### 지역변수 및 전역변수

저장 프로퍼티와 연산 프로퍼티의 기능은 함수, 메서드, 클로저, 타입 등의 외부에 위치한 지역/전역 변수에도 모두 사용 가능하다.

```swift
var a: Int = 100
var b: Int = 200
var sum: Int {
  return a + b
}

print(sum) // 300
```

## 19. 프로퍼티 감시자

### 프로퍼티 감시자

- 프로퍼티 감시자를 사용하면 **프로퍼티의 값이 변경**될 때 원하는 동작을 수행할 수 있다.
- 값이 변경되기 직전에 willSet 블럭이, 값이 변경된 직후에 didSet블럭이 호출된다.
- 둘 중 필요한 하나만 구현해 주어도 무관하다.
- 변경되려는 값이 **기존 값과 똑같더라도** 프로퍼티 감시자는 항상 동작한다.
- **willSet** 블럭에서는 암시적 매개변수 **newValue**를, **didSet** 블럭에서는 **oldValue**를 사용할 수 있다.
- 프로퍼티 감시자는 여산 프로퍼티에는 사용할 수 없다. (저장된 값이 바뀔 때 작동하는 것이기 때문)
- 프로퍼티 감시자는 함수, 메서드, 클로저, 타입 등의 지역/전역 변수에 모두 사용 가능하다.

### 정의 및 사용

```swift
struct Money {
  //프로퍼티 감시자 사용
  var currencyRate: Double = 1100 {
    willSet(newRate) {
      print("환율이 \(currencyRate)에서 \(newRate)으로 변경될 예정입니다")
    }
    didSet(oldRate) {
      print("환율이 \(oldRate) 에서 \(currencyRate)으로 변경되었습니다")
    }
  }

  //프로퍼티 감시자 사용
  var dollar: Double = 0 {
    //wilSet의 암시적 매개변수 이름 newValue
    willSet {
      print("\(dollar)달러에서 \(newValue)달러로 변경될 예정입니다")
    }
    //didSet의 암시적 매개변수 이름 oldValue
    didSet {
      print("\(oldValue)달러에서 \(dollar)달러로 변경되었습니다")
    }
  }

  //연산 프로퍼티
  var won: Double {
    get {
      return dollar * currencyRate
    }
    set {
      dollar = newValue / currencyRate
    }

    /*
     프로퍼티 감시자와 연산 프로퍼티 기능은 동시에 사용할 수 없다.
     willSet {

     }
     */
  }
}

var moneyInMyPocket: Money = Money()

//환율이 1100.0에서 1150.0으로 변경될 예정입니다
moneyInMyPocket.currencyRate = 1150
//환율이 1100.0에서 1150.0으로 변경되었습니다

//0.0달어에서 10.0달러로 변경될 예정입니다
moneyInMyPocket.dollar = 10
//0.0달러에서 10.0달러로 변경되었습니다

print(moneyInMyPocket.won)
//11500.0
```
