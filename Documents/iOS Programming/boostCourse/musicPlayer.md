# 네이버 부스트코스 iOS Programming #1 Music Player

[Naver BoostCourse](https://www.edwith.org/boost-course/intro)

<details>
  <summary>1. 애플리케이션 만들기</summary>

  <details>
    <summary>1-1. 프로젝트에 이미지 추가하기</summary>
  
  ### 에셋 카탈로그란?

[Apple Documentation](https://help.apple.com/xcode/mac/current/#/dev10510b1f7)

에셋 카탈로그는 에셋과 다양한 디바이스의 속성에 대한 파일의 연결을(mapping) 통해 애플리케이션 리소스에 쉽게 접근할 수 있도록 도와준다.

### 에셋 카탈로그 구성

- Groups: 그룹은 한 개 이상의 또 다른 그룹이나 에셋을 가질 수 있다.
- Assets: 에셋은 한 가지 타입의 관련된 속성과 파일들의 집합을 나타낸다.
- 에셋 이름(Asset name)은 에셋에 접근하기 위해 개발자가 정의한 문자열이다.
- 에셋 파일(Asset files)은 선택한 에셋의 데이터 파일 또는 리소스이다.
- Attributes: 속성은 선택한 그룹, 에셋, 에셋파일의 속성을 나타낸다.
- Asset variations: 에셋 파일들의 집합을 나타낸다. 같은 속성 값(value)이 적용되는 하나의 단위이다.

#### 에셋 카탈로그의 3가지 콘텐츠

- Folders: 에셋 카탈로그 폴더는 다른 그룹 폴더나 에셋 폴더를 포함할 수 있다. 파일시스템의 폴더 이름은 대체적으로 확장자를 갖지 않는다. 하지만 에셋 카탈로그 폴더는 해당 에셋 타입의 확장자가 자동으로 붙는다.
- JSON files: .json 확장자 파일로서 속성에 대한 정보를 포함하도 있다.
- Content files: 콘텐츠 파일은 리소스 파일을 나타낸다.

#### 에셋 카탈로그 폴더의 구조

- Asset catalog folder: 에셋 카탈로그 폴더는 모든 폴더와 파일들을 갖고 있다.
- Group folder: 그룹 폴더는 다른 그룹 폴더나 에셋 폴더를 갖고 있다.
- Asset folder: 에셋 폴더는 리소스 파일들을 갖고 있다.
  - **프로젝트 내의 같은 타겟에는 에셋(폴더)의 이름이 반드시 고유해야 한다. 리소스 타입에 상관없이 이름은 고유해야 한다.**

### 에셋 카탈로그 대표 타입

[Types Overview](https://developer.apple.com/library/archive/documentation/Xcode/Reference/xcode_ref-Asset_Catalog_Format/AssetTypes.html)

- App Icon Type: 애플리케이션의 아이콘
  - 확장자: .appiconset
  - 다양한 크기와 해상도의 애플리케이션 아이콘 원본 이미지
- Catalog Type: 에셋 카탈로그의 최상위 폴더
  - 확장자: xcassets
  - 에셋 카탈로그 폴더구조의 최상위 폴더. 한 개의 에셋 카탈로그에 하나만 존재할 수 있다.
- Image Set type: 객체들이 사용하는 이미지
  - 확장자: .imageset
  - 이미지 에셋에서 UIImage와 NSImage의 인스턴스에 사용되는 이미지 파일
- Data Set Type: 애플리케이션에서 사용되는 데이터 파일
  - 확장자: .dataset
  - 장치 실행 가능 코드(device-executable code)를 제외한 Xcode에 의해 생성된 모든 종류의 데이터를 포함하는 파일들의 집합
- Launch Image Type: 애플리케이션의 실행화면 이미지
  - 확장자: .launchiamge
  - 애플리케이션 실행화면 이미지 (iOS 7.0 이하 버전에만 필요함. iOS 8.0 버전 이상은 기본적으로 실행화면 스토리보드(launch screen storyboard)를 사용한다.)

### 앱 시닝과 앱 슬라이싱이란?

#### 앱 시닝(app thining)

- 애플리케이션이 디바이스에 설치될 때 앱 스토어와 운영체제가 그 디바이스 특성에 맞게 설치하도록 하는 설치 최적화 기술
- 애플리케이션의 설치용량을 최소화하고 다운롣의 속도를 향상시킬 수 있다.
- 앱 시닝의 기술 구성요소는 슬라이싱(slicing), 비트코드(bitcode), 주문형 리소스(on-demand resource)가 있다.

#### 앱 슬라이싱(slicing)

- 애플리케이션이 지원하는 다양한 디바이스에 대한 여러 조각의 애플리케이션 번들(app bundle)을 생성하고 디바이스에 알맞은 조각을 전달하는 기술
- 개발자가 애플리케이션의 전체 버전을 iTunes Connect에 업로드하면, 앱 스토어에는 각 디바이스 특성에 따른 다양한 버전의 조각들이 생성된다.
- 사용자가 애플리케이션을 설치할 때 전체 버전이 아닌 슬라이싱된 조각들 중 사용자의 디바이스에 가장 적합한 조각이 다운로드 되어 설치된다.
- 에셋 카탈로그에서 관리하는 이미지들은 자동으로 적용이 된다. (슬라이싱은 iOS 9.0 버전 이상만 지원한다.)
- - iTunes Connect란 개발자가 앱 스토어에 판매할 애플리케이션을 제출하고 관리할 수 있도록 도와주는 웹 기반 도구임
    </details>
    <details>
      <summary>1-2. 인터페이스 빌더로 화면 구성하기</summary>
      
      [Apple Documentation](https://help.apple.com/xcode/mac/current/#/dev9ffcd0c51)
    </details>
    <details>
      <summary>1-3. 인터페이스 빌더의 객체를 코드와 연결(IBOutlet)</summary>
      
      ### 강의 정리

[Apple Documentation](https://help.apple.com/xcode/mac/current/#/devc06f7ee11)

[Swift.org](https://swift.org/documentation/api-design-guidelines/#naming)

[Menu Command Shortcuts (By Menu)](https://developer.apple.com/library/archive/documentation/IDEs/Conceptual/xcode_help-command_shortcuts/MenuCommands/MenuCommands014.html)

- 코드로 먼저 IBOutlet을 생성한 후 인터페이스 빌더의 Outlet Inspector를 통해 연결
- 코드로 먼저 IBOutlet을 생성한 후 일터페이스 빌더에서 View Controller 우클릭(control + 좌클릭) 팝업에서 연결
- 인터페이스 빌더에서 코드로 끌어당겨 연결

**<<변수명 변경 시 주의사항>>**

- 인터페이스 빌더의 객체와 코드를 연결한 후 변수명 수정 시, 기존의 연결을 끊고 새로운 코드와 객체를 다시 연결해주거나,
- 코드의 변수명에 우클릭 후 refactor > rename 을 통해 이름을 변경해주어야 앱 실행 시 오류가 나지 않는다.
    </details>
    <details>
      <summary>1-4. 인터페이스 빌더의 객체를 코드와 연결(IBAction)</summary>

[Apple Developer Documentation](https://developer.apple.com/documentation/uikit/uicontrol/event)

[Target-Action](https://developer.apple.com/library/archive/documentation/General/Conceptual/CocoaEncyclopedia/Target-Action/Target-Action.html)

[Apple Documentation](https://help.apple.com/xcode/mac/current/#/dev9662c7670)

## 학습 목표

1. 인터페이스 빌더에서 생성한 객체가 전달하는 이벤트를 코드의 액션과 연결한다.
2. 객체에서 발생한 액션이 제대로 동작하는지 확인한다.
3. 액션의 타입에 여러 종류가 있음을 이해하고 다양하게 테스트해본다.

## 학습하기

### 컨트롤 이벤트와 액션과의 관계

UIKit 에는 UIButton, UISwitch, UIStepper 등 UIControl을 상속받은 다양한 컨트롤 클래스가 있다. 그런 컨트롤 객체에 발생한 다양한 이벤트 종류를 특정 액션 메서드에 연결할 수 있다. 즉, 컨트롤 객체에서 특정 이벤트가 발생하면, 미리 지정해 둔 타겟의 액션을 호출하게 된다.

### 컨트롤 이벤트의 종류

컨트롤 이벤트는 UIControl에 Event라는 타입으로 정의되어 있다. 아래는 컨트롤 객체에 발생할 수 있는 이벤트의 종류이다. 다양한 이벤트 종류를 실제로 Xcode에서 테스트해보면 이해하는 데에 도움이 될 것이다.

<details><summary>컨트롤 이벤트 종류와 설명</summary>

**touchDown**

    컨트롤을 터치했을 때 발생하는 이벤트

    UIControl.Event.touchDown

**touchDownRepeat**

    컨트롤을 연속 터치할 때 발생하는 이벤트

    UIControl.Event.touchDownRepeat

**touchDragOutside**

    터치 영역이 컨트롤의 바깥쪽에서 드래그할 때 발생하는 이벤트

    UIControl.Event.touchDragOutside

**touchDragInside**

    컨트롤 범위 내에서 터치한 영역을 드래그할 때 발생하는 이벤트

    UIControl.Event.touchDragInside

**touchDragEnter**

    터치 영역이 컨트롤의 일정 영역 바깥쪽으로 나갔다가 다시 들어왔을 때 발생하는 이벤트

    UIControl.Event.touchDragEnter

**touchDragExit**

    터치 영역이 컨트롤의 일정 영역 바깥쪽으로 나갔을 때 발생하는 이벤트

    UIControl.Event.touchDragExit

**touchUpInside**

    컨트롤 영역 안쪽에서 터치 후 뗐을 때

    UIControl.Event.tochUpInside

**touchUpOutside**

    컨트롤 영역 안쪽에서 터치 후 컨트롤 밖에서 뗐을 때 이벤트

    UIControl.Event.touchUpOutside

**touchCancel**

    터치를 취소하는 이벤트 (touchUp 이벤트가 발생하지 않음)

    UIControl.Event.touchCancel

**valueChanged**

    터치를 드래그 및 다른 방법으로 조작하여 값이 변경되었을 때 발생하는 이벤트

    UIControl.Event.valueChanged

**primaryActionTriggered**

    버튼이 눌릴 때 발생하는 이벤트 (iOS보다는 tvOS에서 사용)

    UIControl.Event.primaryActionTriggered

**editingDidBegin**

    UITextField에서 편집이 시작될 때 호출되는 이벤트

    UIControl.Event.eiditingDidBegin

**editingChanged**

    UITextField에서 값이 바뀔 때마다 호출되는 이벤트

    UIControl.Event.editingChanged

**editingDidEnd**

    UITextField에서 외부객체와의 상호작용으로 인해 편집이 종료되었을 때 발생하는 이벤트

    UIControl.Event.editingDidEnd

**editingDidEndOnExist**

    UITextField의 편집상태에서 키보드의 return 키를 터치했을 때 발생하는 이벤트

    UIControl.Event.editingDidEndOnExit

**allTouchEvents**

    모든 터치 이벤트

    UIControl.Event.allTouchEvents

**allEditingEvents**

    UITextField에서 편집작업의 이벤트

    UIControl.Event.allEditingEvents

**applicationReserved**

    각각의 애플리케이션에서 프로그래머가 임의로 지정할 수 있는 이벤트 값의 범위

    UIControl.Event.applicationReserved

**allEvents**

    시스템 이벤트를 포함한 모든 이벤트

    UIControl.Event.allEvents

  </details>

### 강의 정리

인터페이스 빌더의 객체에서 발생한 액션을 코드의 메서드와 연결

- 코드로 먼저 IBAction을 생성한 후 인터페이스 빌더의 Outlet Inspector를 통해 연결
- 코드로 먼저 IBAction을 생성한 후 인터페이스 빌더에서 View Controller 우클릭 후 팝업에서 연결
- 인터페이스 빌더에서 코드로 끌어당겨 연결 / 생성

print 로그를 통해 액션이 제대로 동작하는지 확인

</details>
<details>
<summary>1-5. UIButton, UISlider, UILable</summary>

## UIButton, UISlider, UILabel

## 학습 목표

1. UIButton 생성 방법, 모양 설정 및 사용자 상호작용에 대응하는 방법을 이해한다.
2. UILabel 생성 방법, 레이블에 입력되는 문구를 설정하는 방법을 이해한다.
3. UISlider 생성 방법, 구성요소 및 관련 메서드를 이해한다.

## 학습하기

### UIButton

[Apple Developer Documentation](https://developer.apple.com/documentation/uikit/uibutton)

UIButton 클래스는 사용자의 상호 작용(터치/탭 등의 이벤트)에 반응해 미리 지정된 코드를 실행하는 컨트롤 요소이다.

#### 버튼 생성 3단계

1. 버튼을 생성하고 버튼의 유형을 선택
2. 버튼을 나타내기 위한 문자(타이틀)을 입력하거나, 이미지를 설정한 뒤 크기 조정
3. 버튼에 특정 이벤트가 발생할 때 작동할 하나 이상의 메서드를 연결

#### 버튼과 메서드를 연결하는 방법

1. addTarget(\_:action:for:) 메서드 사용
2. 인터페이스 빌더에서 연결(@IBAction)

#### 버튼과 연결되는 메서드 방식

버튼을 탭했을 때 필요한 정보에 따라 아래 세 가지 중 한 가지를 선택해 사용해보기

```swift
func doSomething()
func doSomething(sender: UIButton)
func doSomething(sender: UIButton, forEvent event: UIEvent)
```

#### 버튼의 상태

- 버튼의 상태는 다섯가지로 표현한다.
  - default, highlighted, focused, selected, disabled
  - 버튼의 상태는 조합된 상태일 수 있다.
  - 예) [default + highlighted], [selected _ disabled] 등
- 버튼 생성 시 기본 상태 값은 default
- 사용자가 버튼과 상호작용을 하면 상태 값이 변하게 된다.
- 프로그래밍 방식 혹은 인터페이스 빌더를 이용해 버튼의 각 상태에 대한 속성을 별도로 지정할 수 있다.
  - 별도로 속성을 지정하지 않으면 UIButton 클래스에서 제공하는 기본 동작을 사용하게 된다.
  - [예] disabled 버튼은 일반적으로 흐리게 표시되며 사용자가 탭 해도 highlighted 되지 않는다.

#### 버튼 주요 프로퍼티

버튼의 프로퍼티 값을 설정하는 방식에는 코드를 이용하는 방법과 스토리보드의 인스펙터를 이용하는 방법이 있다.

- enum UIButtonType: 버튼의 유형
  - 버튼의 유형에 따라 버튼의 기본적인 외형과 동작이 달라진다.
  - 처음 버튼을 생성할 때 init(type:) 메서드를 이용하거나, 인터페이스 빌더의 "Attribute Inspector"에서 버튼 유형을 지정할 수 있다.
  - 한번 생성된 버튼의 유형은 이후 변경할 수 없다.
  - 가장 많이 사용하는 유형은 Custom과 System이지만 필요에 따라 다른 유형(Detail Disclosure, Info Light, Info Dark, Add Contact)를 사용할 수 있다.
- var titleLabel: UILabel?: 버튼 타이틀 레이블
- var imageView: UIImageView?: 버튼의 이미지 뷰
- var tintColor: UIColor!: 버튼 타이틀과 이미지의 틴트 컬러

#### 버튼의 주요 메서드

```swift
//특정 상태의 버튼의 문자열 설정
func setTitle(String?, for: UIControlState)
//특정 상태의 버튼의 문자열 반환
func title(for: UIControlState) -> String?

//특정 상태의 버튼 이미지 설정
func setImage(UIImage?, for:UIControlState)
//특정 상태의 버튼 이미지 반환
func image(for: UIControlState) -> UIImage?

//특정 상태의 백그라운드 이미지 설정
func setBackgroundImage(UIImage?, for: UIControlState)
//특정 상태의 백그라운드 이미지 반환
func backgroundImage(for: UIControlState) -? UIImage?

//특정 상태의 문자열 색상 설정
func setTitleColor(UIColor?, for: UIControlState)
//특정 상태의 attributed 문자열 설정
func setAttributedTitle(NSAttributedString?, for: UIControlState)
```

### UILabel

[Apple Developer Documentation](https://developer.apple.com/documentation/uikit/uilabel)

UILable은 한 줄 또는 여러 줄의 텍스트를 보여주는 뷰로, UIButton 등의 컨트롤의 목적을 설명하기 위해 사용하는 경우가 많다.

#### 레이블 생성 3단계

1. 레이블 생성
2. 레이블이 표시할 문자열 제공
3. 레이블의 모양 및 특성 설정

#### 레이블 주요 프로퍼티

레이블의 프로퍼티에 접근해 나타내려는 문자의 내용, 색상, 폰트, 문자정렬방식, 라인 수 등을 조정할 수 있다.

레이블의 프로퍼티의 값을 설정하는 방식에는 프로그래밍 방식과 스토리보드의 인스펙터를 이용한 방법이 있다.

- var text: String? : 레이블이 표시할 문자열
  - 문자열이 모두 동일한 속성(폰트, 색상, 기울임꼴 등)으로 표시된다.
  - text 프로퍼티에 값을 할당하면 attributedText 프로퍼티에도 똑같은 내용의 문자열이 할당된다.
- var attributedText: NSAttributedString? : 레이블이 표시할 속성 문자열
  - NSAttributed 클래스를 사용한 속성 문자열 중 특정 부분의 속성을 변경할 수 있다. ([예] 일부 글자 색상 변경/일부 글자 폰트 변경)
  - attributedText 프로퍼티에 값을 할당하면 text 프로퍼티에도 똑같은 내용의 문자열이 할당된다.
- var textColor: UIColor! : 문자 색상
- var font: UIFont!: 문자 폰트
- var textAlignment: NSTextAlignment : 문자열의 가로 정렬 방식
  - left, right, center, justified, natural 중 하나 선택 가능
- var numberOfLines: Int : 문자를 나타내는 최대 라인 수
  - 문자열을 모두 표시하는 데 필요한 만큼 행을 사용하려면 0으로 설정. 기본 값은 1임
  - 설정한 문자열이 최대 라인 수를 초과하면 lineBreakMode 프로퍼티의 값에 따라 적절히 잘라서 표현한다.
  - adjustsFontSizeToFitWidth 프로퍼티를 활용하면 폰트 사이즈를 레이블의 넓이에 따라 자동으로 조절해준다.
- var baselineAdjustment: UIBaselineAdjustment : 문자열이 Autoshrink 되었을 때의 수직 정렬 방식
  - Align Baseline: 문자가 작아졌을 때 기존 문자열의 기준선에 맞춤
  - Align Center: 문자가 작아졌을 때 작아진 문자의 중앙선에 맞춤
  - None: 문자가 작아졌을 때 기존 문자열의 위쪽 선에 맞춤
- var lineBreakMode: NSLineBreakMode : 레이블의 경계선을 벗어나는 문자열에 대응하는 방식
  - Character wrap : 여러 줄 레이블에 주로 적용되며, 글자 단위로 줄 바꿈을 결정한다.
  - Word wrap : 여러 줄 레이블에 주로 적용되며, 단어 단위로 줄 바꿈을 결정한다.
  - Truncate head : 한 줄 레이블에 주로 적용되며, 앞쪽 텍스트를 자르고 ...으로 표시한다.
  - Truncate middle : 한 줄 레이블에 주로 적용되며, 중간 텍스트를 자르고 ...으로 표시한다.
  - Truncate tail : 한줄 레이블에 주로 적용되며, 끝쪽 텍스트를 자르고 ...으로 표시한다. **기본 설정 값**이다.

### UISlider

[Apple Developer Documentation](https://developer.apple.com/documentation/uikit/uislider)

UISlider는 연속된 값 중에서 특정 값을 선택하는데 사용되는 컨트롤이다.

#### 슬라이더 생성 3단계

1. 슬라이더를 생성하고, 슬라이더가 나타내는 값의 범위 지정
2. 적절한 색상과 이미지를 이용해 슬라이더의 모양 구성
3. 하나 이상의 메서드를 슬라이더와 연결

#### 사용자 상호작용에 반응하기

사용자가 슬라이더의 값을 변경하면 슬라이더에 연결된 메서드가 호출되어 원하는 작업이 실행된다.

기본적으로는 사용자가 슬라이더의 Thumb를 이동시키면 연속적으로 이벤트를 호출하지만, isContinuous 프로퍼티 값을 false로 설정하면 슬라이더의 Thumb에서 손을 떼는 동시에 이벤트를 호출한다.

#### 슬라이더와 메서드 연결하는 방법

1. addTarget(\_:action:for) 메서드 사용
2. 인터페이스 빌더에서 연결 (@IBAction)

#### 슬라이더와 연결하는 메서드 형식

슬라이더의 값을 변경했을 때 필요한 정보에 따라 아래 세 가지 중 한 가지를 선택해서 사용

```swift
func doSomething()
func doSomething(sender: UISlider)
func doSomething(sender: UISlider, forEvent event: UIEvent)

```

#### 슬라이더 주요 프로퍼티

슬라이더의 프로퍼티 값을 설정하는 방식에는 프로그래밍 방식과, 스토리보드의 인스펙터를 이용하는 방법이 있다.

- var minimumValue: Float, var maximumValue: Float : 슬라이더의 양끝단의 값
- var value: Float : 슬라이더의 현재 값
- var isContinuous: Bool :슬라이더의 연속적인 값 변화에 따라 이벤트 역시 연속적으로 호출할 것인지의 여부
- var minimumValueImage: UIImage?, var maximumValueImage: UIImage? : 슬라이더 양끝단의 이미지
- var thumbTintColor: UIColor? : thumb의 틴트 색상
- var minimumTrackTintCOlor: UIColor?, var maximumTrackTintColor: UIColor? : thumb를 기준으로 앞쪽 트랙과 뒤쪽 트랙의 틴트 색상

#### 슬라이더 주요 메서드

```swift
//슬라이더의 현재 값 설정
func setValue(Float, animated: Bool)

//특정 상태의 minimumTrackImage 반환
func minimumTrackImage(for: UIControlState) -> UIImage?
//특정 상태의 minimumTrackImage 설정
func setMinimumTrackImage(UIImage?, for: UIControlState)

//특정 상태의 maximumTrackImage 반환
func maximumTrackImage(for: UIControlState) -> UIImage?
//특정 상태의 maximumTrackImage 설정
func setMaximumTrackImage(UIImage?, for: UIControlState)

//특정 상태의 thumbImage 반환
func thumbImage(for: UIControlState) -> UIImage?
//특정 상태의 thumbImage 설정
func setThumbImage(UIImage?, for UIControlState)
```

</details>
<details>
<summary>1-6. 구현 코드 작성하기</summary>
  
  # 구현 코드 작성하기

# 학습 목표

1. 음원 재생기 애플리케이션 코드를 작성하고 예상한대로 동작하는지 확인하기
2. 주석과 mark 키워드를 이해하고 프로젝트에 적용해보기
3. AVFoundation과 Timer 클래스를 이해하기

# 학습하기

## AVFoundation

AVFoundation은 다양한 Apple 플랫폼에서 사운드 및 영상 미디어의 처리, 제어, 가져오기 및 내보내기 등 광범위한 기능을 제공하는 프레임워크이다.

[AVFoundation](https://developer.apple.com/documentation/avfoundation)

### 주요 기능

- 미디어 재생 및 편집 (QuickTime 동영상 및 MPEG-4 파일 재생/생성/편집, HLS 스트림 재생: [재생가능 파일 목록 링크](https://developer.apple.com/documentation/avfoundation/avfiletype))
- 디바이스 카메라와 마이크를 이용한 영상 녹화 및 사운드 녹음
- 시스템 사운드 제어
- 문자의 음성화

### AVAudioPlayer Class

파일 또는 메모리에 있는 사운드 데이터를 재생하는 기능을 제공한다.

[AVAudioPlayer](https://developer.apple.com/documentation/avfoundation/avaudioplayer)

#### AVAudioPlayer 주요 기능

- 파일 또는 메모리에 있는 사운드 재생(네트워크에 있는 사운드 파일은 재생 불가)
- 파일 재생 시간 길이의 제한없이 사운드 재생
- 여러 개 사운드 파일 동시 재생
- 사운드의 재생 속도 제어 및 스테레오 포지셔닝
- 앞으로 감기와 뒤로 감기 등의 기능을 지원해 사운드 파일의 특정 지점 찾기
- 현재 재생 정보 데이터 얻기
- 사운드 반복재생 기능

#### AVAudioPlayer 주요 프로퍼티

- var isPlaying: Bool : 사운드가 현재 재생되고 있는지 아닌지 여부
- var volume: Float : 사운드의 볼륩값, 최소 0.0 ~ 최대 1.0
- var rate : Float : 사운드의 재생 속도
- var numberOfLoops: Int : 사운드 재생 반복 횟수
  - 기본값은 0으로 사운드 1회 재생 후 자동 종료
  - 양수값으로 설정 시 설정값+1회 재생(ex. 1로 설정시 2회 재생 후 종료)
  - 음수값으로 설정시 stop 메서드가 호출 될때까지 무한 재생
- var duration: TimeInterval : 사운드의 총 재생 시간(초 단위)
- var currentTime: TimeInterval : 사운드의 현재 재생 시각(초 단위)
- protocol AVAudioPlayerDelegate : 사운드 재생 완료, 재생 중단 및 디코딩 오류에 응답할 수 있는 프로토콜

#### AVAudioPlayer 주요 메서드

- AVAudioPlayer 초기화 메서드

```swift
//특정 위치에 있는 사운드 파일로 초기화
func init(contentOf: URL)
//메모리에 올라와 있는 데이터를 이용해 초기화
func init(data: Data)
```

- AVAudioPlayer 재생관련 메서드

```swift
//사운드 재생
func play()
//특정 시점에서 사운드 재생
func play(atTime: TimeInterval)

//사운드 일시 정지
func puase()
//사운드 재생 정지
func stop()
```

### Timer

일정한 시간 간격이 지나면 지정된 메시지를 특정 객체로 전달하는 기능을 제공한다.

[Timer](https://developer.apple.com/documentation/foundation/timer)

#### Timer 특징

- 타이머는 런 루프(run loops)에서 작동한다.
- 타이머를 생성할 때 반복 여부를 지정한다.
  - 비 반복 타이머: 한 번 실행된 다음 자동으로 무효화 된다.
  - 반복 타이머: 동일한 런 루프에서 특정 TimeInterval 간격으로 실행된다. 반복되는 타이머 기능을 정지하려면 invalidate() 메서드를 호출해 무효화한다.

#### Timer 주요 프로퍼티

- var isValid: Bool : 타이머가 현재 우효한지 아닌지 여부
- var fireDate: Date : 다음에 타이머가 실행될 시각
- var timeInterval: TimeInterval : 타이머의 실행 시간 간격(초 단위)

#### Timer 생성 메서드

1. 타이머 생성과 동시에 런 루프에 default mode로 등록하는 클래스 메서드

   ```swift
   class func scheduledTimer(withTimeInterval: TimeInterval, repeates: Bool, block: (Timer) -> Void)
   class func scheduledTimer(timeInverval: TimeInterval, target: Any, selector: Selector, userInfo: Any?, repeates: Bool)
   class func scheduledTimer(timeInterval: TimeInterval, invocation: NSInvocation, repeats: Bool)
   ```

2. 타이머 생성 후 수동으로 타이머 객체를 add(\_:forMode:) 메서드를 이용해 런 루프에 추가해줘야 하는 메서드

   ```swift
   func init(timeInterval: TimeInterval, invocation: NSInvocation, repeats: Bool)
   func init(timeInterval: TimeInterval, target: Any, selector: Selector, userInfo: Any?, repeats: Bool)
   func init(fireAt: Date, interval: TimeInterval, target: Any, selector: Selector, userInfo: Any?, repeats: Bool)
   ```

## 주석과 마크

```swift
// MARK - 마크 이름
// 위와 같이 표시해 두면 나중에 코드가 길어졌을 때에도 쉽게 찾을 수 있다!
```

[Xcode Help - Write Code](https://help.apple.com/xcode/mac/current/#/dev8716704af)

  </details>
</details>
<details>
  <summary>2. Foundation과 UIKit 그리고 Cocoa Touch</summary>
  
  <details>
    <summary>2-1. Cocoa Touch 프레임워크란?</summary>

# Cocoa Touch 프레임워크란?

## 학습하기

'코코아 터치' 프레임워크는 iOS 애플리케이션 개발 환경으로, 애플리케이션의 다양한 기능 구현에 필요한 여러 프레임워크를 포함하는 최상위 레벨의 프레임워크이다. 참고로 '코코아' 프레임워크는 macOS 애플리케이션 제작에 사용하는 프레임워크이다.

- '코코아'라는 단어는 Objective-C 런타임을 기반으로 하고, NSObject를 상속받는 모든 클래스 또는 객체를 가리킬 때 사용한다.
- '코코아' 또는 '코코아 터치'는 macOS 또는 iOS의 전반적인 기능을 활용해 애플리케이션을 제작할 때 사용하는 프레임워크이다.
- '코코아 터치'는 핵심 프레임워크인 UIKit과 Foundation을 포함한다.

[애플 공식 문서 - Cocoa (Touch)](https://developer.apple.com/library/archive/documentation/General/Conceptual/DevPedia-CocoaCore/Cocoa.html)

[위키피디아 - Cocoa (API)](<https://en.wikipedia.org/wiki/Cocoa_(API)>)

  </details>
  <details>
  <summary>2-2. UIKit이란?</summary>

# UIKit이란?

[Apple Documentation - UIKit](https://developer.apple.com/documentation/uikit)

## 학습하기

### UIKit 소개

UIKit은 iOS 애플리케이션의 사용자 인터페이스를 구현하고 이벤트를 관리하는 프레임워크이다.

- UIKit 프레임워크는 제스처 처리, 애니메이션, 그림 그리기, 이미지 처리, 텍스트 처리 등 사용자 이벤트 처리를 위한 클래스를 포함한다.
- 또한 테이블뷰, 슬라이더, 버튼, 텍스트 필드, 얼럿 창 등 애플리케이션의 화면을 구성하는 요소를 포함한다.
- UIKit 클래스 중 UIResponder에서 파생된 클래스나 사용자 인터페이스에 관련된 클래스는 애플리케이션의 메인 스레드(혹은 메인 디스패치 큐)에서만 사용하자.
- UIKit은 iOS와 tvOS 플랫폼에서 사용한다.

### UIKit 기능별 요소

#### 사용자 인터페이스

- View and Control: 화면에 콘텐츠 표시
- View Controller: 사용자 인터페이스 관리
- Animation and Haptics: 애니메이션과 햅틱을 통한 피드백 제공
- Window and Screen: 뷰 계층을 위한 윈도우 제공

#### 사용자 액션

- Touch, Press, Gesture: 제스처 인식기를 통한 이벤트 처리 로직
- Drag and Drop: 화면 위에서 드래그 앤 드롭 기능
- Peek and Pop: 3D 터치에 대응한 미리 보기 기능
- Keyboard and Menu: 키보드 입력을 처리 및 사용자 정의 메뉴 표시

## 생각해보기

새롭게 ViewController를 생성하면 상단에 'improt UIKit'이 기본적으로 명시되어 있다. 왜 ViewController와 UIKit는 단짝일까?

- ViewControlle는 UIViewController 클래스를 상속받는데, 이 UIViewController 클래스는 UIKit 프레임워크에 정의된 클래스이기 때문에
- UIKit 을 import 해주어야 컴파일러가 UIViewController가 무엇인지 알 수 있다.
  </details>
  <details>
  <summary>2-3. Foundation이란?</summary>
  </details>
</details>
<details>
  <summary>3. 오토 레이아웃</summary>
</details>
<details>
  <summary>4. iOS View의 체계</summary>
</details>
<details>
  <summary>5. MVC (Model-View-Controller)</summary>
</details>
<details>
  <summary>6. Apple Developer Documentation</summary>
</details>
<details>
  <summary>7. Summary</summary>
</details>
