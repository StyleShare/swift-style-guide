Swift Style Guide
=================

본 문서는 Swift 코드를 명확하게 작성하기 위한 스타일 가이드입니다.


## 공백 (Spacing)

* 들여쓰기에는 탭(tab) 대신 4개의 space를 사용합니다.
* 모든 파일은 빈 줄(new-line)로 끝나도록 합니다.
* 띄어쓰기로만 이루어진 라인은 띄어쓰기를 모두 제거합니다.
* 연산자 오버로딩 함수 정의에서는 연산자와 괄호 사이에 한 칸 띄어씁니다.

    ```swift
    func ** (lhs: Int, rhs: Int)
    ```


## 줄바꿈 (Line Break)

#### 코드 최대 길이는 119자로 제한합니다.

GitHub에서 가로 스크롤 없이 코드를 볼 수 있는 최적의 길이입니다.


#### 클래스 정의가 긴 경우에는 적당한 위치에서 줄바꿈하고, 한 단계 들여쓰기합니다.

```swift
class AwesomeViewController: UIViewController, UITableViewDataSource, UITableViewDelegate, UIActionSheetDelegate,
    UIViewControllerTransitioningDelegate, UIViewControllerAnimatedTransitioning {
    ...
}
```


#### 함수 정의가 길 때에는 괄호를 기준으로 줄바꿈합니다.

```swift
func collectionView(collectionView: UICollectionView,
                    cellForItemAtIndexPath indexPath: NSIndexPath) -> UICollectionViewCell {
    ...
}

func animationControllerForPresentedController(presented: UIViewController,
                                               presentingController presenting: UIViewController,
                                               sourceController source: UIViewController)
                                               -> UIViewControllerAnimatedTransitioning? {
    ...
}
```


#### 함수 호출 코드가 길 때에는 파라미터 이름을 기준으로 줄바꿈합니다.

```swift
let actionSheet = UIActionSheet(
    title: "정말 계정을 삭제하실 건가요?",
    delegate: self,
    cancelButtonTitle: "취소",
    destructiveButtonTitle: "삭제해주세요"
)
```

파라미터 이름이 없는 첫 번째 파라미터는 첫 줄에 씁니다. 만약 이름이 없는 첫 번째 파라미터가 너무 길다면 줄바꿈해도 무방합니다.

```swift
UIView.animateWithDuration(0.25,
    animations: {
        ...
    },
    completion: { finished in
        ...
    }
)
```


#### 변수 정의가 길 때에는 적당한 위치에서 줄바꿈하고, 한 단계 들여쓰기합니다.

```swift
let cell = tableView.dequeueReusableCellWithIdentifier(CellIdentifier.VeryVeryLongUser)
    as! UserCell
```


#### `class` 내부 코드의 가장 윗줄과 아랫줄에는 공백을 둡니다.

```swift
class ProfileViewController: UIViewController {

    var user: User?

}
```


#### `// MARK:` 앞에는 두 줄의 공백을, 뒤에는 한 줄의 공백을 둡니다.

```swift
// MARK: - Layout

override func layoutSubviews() {
    ...
}


// MARK: - Actions

override func menuButtonDidTap() {
    ...
}
```


#### `if let` 구문이 길 경우에는 `let`과 `where`를 기준으로 줄바꿈합니다.

*(각 라인이 엄청나게 길다고 가정해봅시다.)*

```swift
if let user = self.user,
       name = user.name
 where user.gender == .Female {
   ...
}
```


## 네이밍 (Naming)

#### Class Prefix

Swift에서는 네임스페이스 구분을 위한 Class Prefix를 사용하지 않습니다.


#### 상수(constant)에는 소문자로 시작하는 Camel Case를 사용합니다.

**좋은 예:**

```swift
let maximumNumberOfLines = 3
```

**나쁜 예:**

```swift
let kMaximumNumberOfLines = 3
let MAX_LINES = 3
```


#### 약어(abbreviation)는 대문자로 표시합니다.

**좋은 예:**

```swift
let userID: Int?
let HTML: String?
let websiteURL: NSURL?
let URLString: String?
```

**나쁜 예:**

```swift
let userId: Int?
let html: String?
let websiteUrl: NSURL?
let urlString: String?
```


#### 함수 이름 앞에 사용되는 `get`을 지양합니다.

**좋은 예:**

```swift
func nameForUser(user: User) -> String?
```

**나쁜 예:**

```swift
func getNameForUser(user: User) -> String?
```


#### Action 함수의 네이밍은 '주어 + 동사 + 목적어' 형태를 사용합니다.

* *Tap(눌렀다 뗌)*은 `UIControlEvents`의 `.TouchUpInside`에 대응하고, *Press(누름)*는 `.TouchDown`에 대응합니다.
* *will~*은 특정 행위가 일어나기 직전이고, *did~*는 특정 행위가 일어나기 직전입니다.
* *should~*는 일반적으로 `Bool`을 반환하는 함수에 사용됩니다.

**좋은 예:**

```swift
func backButtonDidTap() {
    ...
}
```


**나쁜 예:**

```swift
func back() {
    ...
}

func pressBack() {
    ...
}
```


#### Delegate 메서드는 프로토콜명으로 네임스페이스를 구분합니다.

**좋은 예:**

```swift
protocol UserCellDelegate: NSObjectProtocol {

    func userCellDidSetProfileImage(button: FollowButton)
    func userCell(button: FollowButton, didTapFollowButtonWithUser user: User)
    
}
```

**나쁜 예:**

```swift
protocol UserCellDelegate: NSObjectProtocol {

    func didSetProfileImage()
    func followPressed(user: User)
    
    // `UserCell`이라는 클래스가 존재할 경우 에러 발생
    func UserCell(button: FollowButton, didTapFollowButtonWithUser user: User)

}
```


## 클래스 (Class)

#### UI 개발에 사용되는 상수들은 클래스 내부의 `struct`에서 관리합니다.

재사용성과 유지보수 측면에서 큰 향상을 가져옵니다.

```swift
class ProfileView: UIView {

    struct Metric {
        static let ProfileImageViewLeft: CGFloat = 10
        static let ProfileImageViewRight: CGFloat = 10
        static let NameLabelTopBottom: CGFloat = 8
        static let BioLabelTop: CGFloat = 6
    }
    
    struct Font {
        static let NameLabel = UIFont.boldSystemFontOfSize(14)
        static let BioLabel = UIFont.boldSystemFontOfSize(12)
    }
    
    // SwiftyColor에서 제공하는 Color Operator를 사용합니다.
    struct Color {
        static let NameLabelText = 0x000000~
        static let BioLabelText = 0x333333~70%
    }

}
```

이렇게 선언된 상수들은 다음과 같이 사용될 수 있습니다:

```swift
self.profileImageView.frame.origin.x = Metric. ProfileImageViewLeft
self.nameLabel.font = Font.NameLabel
self.nameLabel.textColor = Color.NameLabelText
```


#### 클래스 내부에서는 `self`를 명시적으로 사용합니다.


## 구조체 (Struct)

#### 구조체를 생성할 때에는 Swift 구조체 생성자를 사용합니다.

**좋은 예:**

```swift
let frame = CGRect(x: 0, y: 0, width: 100, height: 100)
```

**나쁜 예:**

```swift
let frame = CGRectMake(0, 0, 100, 100)
```


## 타입 선언

#### 타입 선언은 필요한 경우에만 사용합니다.

**좋은 예:**

```swift
let name = "Suyeol Jeon"
```

**나쁜 예:**

```swift
let name: String = "Suyeol Jeon"
```


#### `Array<T>`와 `Dictionary<T: U>` 보다는 `[T]`, `[T: U]`를 사용합니다.

**좋은 예:**

```swift
var messages: [String]?
var names: [Int: String]?
```

**나쁜 예:**

```swift
var messages: Array<String>?
var names: Dictionary<Int, String>?
```


## Control Flow

#### 중첩된 `if let` 구문은 하나로 합쳐서 사용합니다.

**좋은 예:**

```swift
if let user = self.user, name = user.name {
   ...
}
```

**나쁜 예:**

```swift
if let user = self.user {
    if let name = user.name {
        ...
    }
}
```


#### 중첩된 `if let`과 `if` 구문은 `if let...where` 구문으로 줄여서 사용합니다.

**좋은 예:**

```swift
if let user = self.user where user.gender == .Female {
    ...
}
```

**나쁜 예:**

```swift
if let user = self.user {
    if user.gender == .Female {
        ...
    }
}
```


## 주석 (Comment)

#### 문서화를 위한 주석에는  `///` 을 사용합니다.

```swift
/// 사용자 프로필을 그려주는 뷰
class ProfileView: UIView {

    /// 사용자 닉네임을 그려주는 라벨
    var nameLabel: UILabel!

}
```


#### `// MARK:`를 사용해서 연관된 코드를 구분짓습니다.

Objective-C에서 제공하는 `#pragma mark`와 같은 기능으로, 연관된 코드와 그렇지 않은 코드를 구분할 때 사용합니다.

```swift
// MARK: - Init

override init(frame: CGRect) {
    ...
}

deinit {
    ...
}


// MARK: - Layout

override func layoutSubviews() {
    ...
}


// MARK: - Actions

override func menuButtonDidTap() {
    ...
}
```


## 기타

#### `import`는 위부터 ABC순으로 작성합니다.

```swift
import Alamofire
import SuperModel
import UIKit
```
