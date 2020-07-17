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
  </details>
    <details>
    <summary>1-3. 인터페이스 빌더의 객체를 코드와 연결(IBOutlet)</summary>
  </details>
    <details>
    <summary>1-4. 인터페이스 빌더의 객체를 코드와 연결(IBAction)</summary>
  </details>
    <details>
    <summary>1-5. UIButton, UISlider, UILable</summary>
  </details>
  </details>
  <details>
    <summary>2. Foundation과 UIKit 그리고 Cocoa Touch</summary>
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
