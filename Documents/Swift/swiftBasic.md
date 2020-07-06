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
