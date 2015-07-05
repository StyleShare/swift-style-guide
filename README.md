Swift Style Guide
=================

본 문서는 StyleShare 구성원들이 Swift 코드를 이해하기 쉽고 명확하게 작성하기 위한 스타일 가이드입니다. 구성원들의 의사결정에 따라 수시로 변경될 수 있습니다.


Table of Contents
-----------------

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [공백](#%EA%B3%B5%EB%B0%B1)
- [줄바꿈](#%EC%A4%84%EB%B0%94%EA%BF%88)
    - [코드 최대 길이는 119자로 제한합니다.](#%EC%BD%94%EB%93%9C-%EC%B5%9C%EB%8C%80-%EA%B8%B8%EC%9D%B4%EB%8A%94-119%EC%9E%90%EB%A1%9C-%EC%A0%9C%ED%95%9C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [클래스 정의가 긴 경우에는 적당한 위치에서 줄바꿈하고, 한 단계 들여쓰기합니다.](#%ED%81%B4%EB%9E%98%EC%8A%A4-%EC%A0%95%EC%9D%98%EA%B0%80-%EA%B8%B4-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%8A%94-%EC%A0%81%EB%8B%B9%ED%95%9C-%EC%9C%84%EC%B9%98%EC%97%90%EC%84%9C-%EC%A4%84%EB%B0%94%EA%BF%88%ED%95%98%EA%B3%A0-%ED%95%9C-%EB%8B%A8%EA%B3%84-%EB%93%A4%EC%97%AC%EC%93%B0%EA%B8%B0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [함수 정의가 길 때에는 괄호를 기준으로 줄바꿈합니다.](#%ED%95%A8%EC%88%98-%EC%A0%95%EC%9D%98%EA%B0%80-%EA%B8%B8-%EB%95%8C%EC%97%90%EB%8A%94-%EA%B4%84%ED%98%B8%EB%A5%BC-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-%EC%A4%84%EB%B0%94%EA%BF%88%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [함수 호출 코드가 길 때에는 파라미터 이름을 기준으로 줄바꿈합니다.](#%ED%95%A8%EC%88%98-%ED%98%B8%EC%B6%9C-%EC%BD%94%EB%93%9C%EA%B0%80-%EA%B8%B8-%EB%95%8C%EC%97%90%EB%8A%94-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%9D%B4%EB%A6%84%EC%9D%84-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-%EC%A4%84%EB%B0%94%EA%BF%88%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [변수 정의가 길 때에는 적당한 위치에서 줄바꿈하고, 한 단계 들여쓰기합니다.](#%EB%B3%80%EC%88%98-%EC%A0%95%EC%9D%98%EA%B0%80-%EA%B8%B8-%EB%95%8C%EC%97%90%EB%8A%94-%EC%A0%81%EB%8B%B9%ED%95%9C-%EC%9C%84%EC%B9%98%EC%97%90%EC%84%9C-%EC%A4%84%EB%B0%94%EA%BF%88%ED%95%98%EA%B3%A0-%ED%95%9C-%EB%8B%A8%EA%B3%84-%EB%93%A4%EC%97%AC%EC%93%B0%EA%B8%B0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [`class` 내부 코드의 가장 윗줄과 아랫줄에는 공백을 둡니다.](#class-%EB%82%B4%EB%B6%80-%EC%BD%94%EB%93%9C%EC%9D%98-%EA%B0%80%EC%9E%A5-%EC%9C%97%EC%A4%84%EA%B3%BC-%EC%95%84%EB%9E%AB%EC%A4%84%EC%97%90%EB%8A%94-%EA%B3%B5%EB%B0%B1%EC%9D%84-%EB%91%A1%EB%8B%88%EB%8B%A4)
    - [`// MARK:` 앞에는 두 줄의 공백을, 뒤에는 한 줄의 공백을 둡니다.](#-mark-%EC%95%9E%EC%97%90%EB%8A%94-%EB%91%90-%EC%A4%84%EC%9D%98-%EA%B3%B5%EB%B0%B1%EC%9D%84-%EB%92%A4%EC%97%90%EB%8A%94-%ED%95%9C-%EC%A4%84%EC%9D%98-%EA%B3%B5%EB%B0%B1%EC%9D%84-%EB%91%A1%EB%8B%88%EB%8B%A4)
    - [`if let` 구문이 길 경우에는 `let`과 `where`를 기준으로 줄바꿈합니다.](#if-let-%EA%B5%AC%EB%AC%B8%EC%9D%B4-%EA%B8%B8-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%8A%94-let%EA%B3%BC-where%EB%A5%BC-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-%EC%A4%84%EB%B0%94%EA%BF%88%ED%95%A9%EB%8B%88%EB%8B%A4)
- [네이밍](#%EB%84%A4%EC%9D%B4%EB%B0%8D)
    - [Class Prefix](#class-prefix)
    - [상수(constant)에는 소문자로 시작하는 Camel Case를 사용합니다.](#%EC%83%81%EC%88%98constant%EC%97%90%EB%8A%94-%EC%86%8C%EB%AC%B8%EC%9E%90%EB%A1%9C-%EC%8B%9C%EC%9E%91%ED%95%98%EB%8A%94-camel-case%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [약어(abbreviation)는 대문자로 표시합니다.](#%EC%95%BD%EC%96%B4abbreviation%EB%8A%94-%EB%8C%80%EB%AC%B8%EC%9E%90%EB%A1%9C-%ED%91%9C%EC%8B%9C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [함수 이름 앞에 사용되는 `get`을 지양합니다.](#%ED%95%A8%EC%88%98-%EC%9D%B4%EB%A6%84-%EC%95%9E%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%98%EB%8A%94-get%EC%9D%84-%EC%A7%80%EC%96%91%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [Action 함수의 네이밍은 '주어 + 동사 + 목적어' 형태를 사용합니다.](#action-%ED%95%A8%EC%88%98%EC%9D%98-%EB%84%A4%EC%9D%B4%EB%B0%8D%EC%9D%80-%EC%A3%BC%EC%96%B4--%EB%8F%99%EC%82%AC--%EB%AA%A9%EC%A0%81%EC%96%B4-%ED%98%95%ED%83%9C%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [Delegate 메서드는 프로토콜명으로 네임스페이스를 구분합니다.](#delegate-%EB%A9%94%EC%84%9C%EB%93%9C%EB%8A%94-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C%EB%AA%85%EC%9C%BC%EB%A1%9C-%EB%84%A4%EC%9E%84%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EA%B5%AC%EB%B6%84%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Closure](#closure)
    - [파라미터와 리턴 타입이 없는 Closure 정의시에는 `() -> Void`를 사용합니다.](#%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0%EC%99%80-%EB%A6%AC%ED%84%B4-%ED%83%80%EC%9E%85%EC%9D%B4-%EC%97%86%EB%8A%94-closure-%EC%A0%95%EC%9D%98%EC%8B%9C%EC%97%90%EB%8A%94----void%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [Closure 정의시 파라미터에는 괄호를 사용하지 않습니다.](#closure-%EC%A0%95%EC%9D%98%EC%8B%9C-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0%EC%97%90%EB%8A%94-%EA%B4%84%ED%98%B8%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [Closure 정의시 가능한 경우 타입 정의를 생략합니다.](#closure-%EC%A0%95%EC%9D%98%EC%8B%9C-%EA%B0%80%EB%8A%A5%ED%95%9C-%EA%B2%BD%EC%9A%B0-%ED%83%80%EC%9E%85-%EC%A0%95%EC%9D%98%EB%A5%BC-%EC%83%9D%EB%9E%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [Closure 호출시 또다른 유일한 Closure를 마지막 파라미터로 받는 경우, 파라미터 이름을 생략합니다.](#closure-%ED%98%B8%EC%B6%9C%EC%8B%9C-%EB%98%90%EB%8B%A4%EB%A5%B8-%EC%9C%A0%EC%9D%BC%ED%95%9C-closure%EB%A5%BC-%EB%A7%88%EC%A7%80%EB%A7%89-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0%EB%A1%9C-%EB%B0%9B%EB%8A%94-%EA%B2%BD%EC%9A%B0-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%9D%B4%EB%A6%84%EC%9D%84-%EC%83%9D%EB%9E%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [Closure 호출시 Closure를 유일한 파라미터로 받는 경우, 괄호를 생략해도 됩니다.](#closure-%ED%98%B8%EC%B6%9C%EC%8B%9C-closure%EB%A5%BC-%EC%9C%A0%EC%9D%BC%ED%95%9C-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0%EB%A1%9C-%EB%B0%9B%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EA%B4%84%ED%98%B8%EB%A5%BC-%EC%83%9D%EB%9E%B5%ED%95%B4%EB%8F%84-%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [간결한 Closure 호출시 파라미터와 `return` 구문을 생략합니다.](#%EA%B0%84%EA%B2%B0%ED%95%9C-closure-%ED%98%B8%EC%B6%9C%EC%8B%9C-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0%EC%99%80-return-%EA%B5%AC%EB%AC%B8%EC%9D%84-%EC%83%9D%EB%9E%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
- [클래스](#%ED%81%B4%EB%9E%98%EC%8A%A4)
    - [UI 개발에 사용되는 상수들은 클래스 내부의 `struct`에서 관리합니다.](#ui-%EA%B0%9C%EB%B0%9C%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%98%EB%8A%94-%EC%83%81%EC%88%98%EB%93%A4%EC%9D%80-%ED%81%B4%EB%9E%98%EC%8A%A4-%EB%82%B4%EB%B6%80%EC%9D%98-struct%EC%97%90%EC%84%9C-%EA%B4%80%EB%A6%AC%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [클래스 내부에서는 `self`를 명시적으로 사용합니다.](#%ED%81%B4%EB%9E%98%EC%8A%A4-%EB%82%B4%EB%B6%80%EC%97%90%EC%84%9C%EB%8A%94-self%EB%A5%BC-%EB%AA%85%EC%8B%9C%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
- [구조체](#%EA%B5%AC%EC%A1%B0%EC%B2%B4)
    - [구조체를 생성할 때에는 Swift 구조체 생성자를 사용합니다.](#%EA%B5%AC%EC%A1%B0%EC%B2%B4%EB%A5%BC-%EC%83%9D%EC%84%B1%ED%95%A0-%EB%95%8C%EC%97%90%EB%8A%94-swift-%EA%B5%AC%EC%A1%B0%EC%B2%B4-%EC%83%9D%EC%84%B1%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
- [타입 선언](#%ED%83%80%EC%9E%85-%EC%84%A0%EC%96%B8)
    - [타입 선언은 필요한 경우에만 사용합니다.](#%ED%83%80%EC%9E%85-%EC%84%A0%EC%96%B8%EC%9D%80-%ED%95%84%EC%9A%94%ED%95%9C-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%A7%8C-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [`Array<T>`와 `Dictionary<T: U>` 보다는 `[T]`, `[T: U]`를 사용합니다.](#arrayt%EC%99%80-dictionaryt-u-%EB%B3%B4%EB%8B%A4%EB%8A%94-t-t-u%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Control Flow](#control-flow)
    - [중첩된 `if let` 구문은 하나로 합쳐서 사용합니다.](#%EC%A4%91%EC%B2%A9%EB%90%9C-if-let-%EA%B5%AC%EB%AC%B8%EC%9D%80-%ED%95%98%EB%82%98%EB%A1%9C-%ED%95%A9%EC%B3%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [중첩된 `if let`과 `if` 구문은 `if let...where` 구문으로 줄여서 사용합니다.](#%EC%A4%91%EC%B2%A9%EB%90%9C-if-let%EA%B3%BC-if-%EA%B5%AC%EB%AC%B8%EC%9D%80-if-letwhere-%EA%B5%AC%EB%AC%B8%EC%9C%BC%EB%A1%9C-%EC%A4%84%EC%97%AC%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
- [주석](#%EC%A3%BC%EC%84%9D)
    - [문서화를 위한 주석에는  `///` 을 사용합니다.](#%EB%AC%B8%EC%84%9C%ED%99%94%EB%A5%BC-%EC%9C%84%ED%95%9C-%EC%A3%BC%EC%84%9D%EC%97%90%EB%8A%94---%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [`// MARK:`를 사용해서 연관된 코드를 구분짓습니다.](#-mark%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%B4%EC%84%9C-%EC%97%B0%EA%B4%80%EB%90%9C-%EC%BD%94%EB%93%9C%EB%A5%BC-%EA%B5%AC%EB%B6%84%EC%A7%93%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [기타](#%EA%B8%B0%ED%83%80)
    - [`import`는 위부터 ABC순으로 작성합니다.](#import%EB%8A%94-%EC%9C%84%EB%B6%80%ED%84%B0-abc%EC%88%9C%EC%9C%BC%EB%A1%9C-%EC%9E%91%EC%84%B1%ED%95%A9%EB%8B%88%EB%8B%A4)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

--

공백
----

* 들여쓰기에는 탭(tab) 대신 4개의 space를 사용합니다.
* 모든 파일은 빈 줄(new-line)로 끝나도록 합니다.
* 띄어쓰기로만 이루어진 라인은 띄어쓰기를 모두 제거합니다.
* 콜론(`:`)을 쓸 때에는 콜론의 오른쪽에만 공백을 둡니다.

    ```swift
    let names: [String: String]
    ```

* 연산자 오버로딩 함수 정의에서는 연산자와 괄호 사이에 한 칸 띄어씁니다.

    ```swift
    func ** (lhs: Int, rhs: Int)
    ```


줄바꿈
----

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


## 네이밍

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
* *will~*은 특정 행위가 일어나기 직전이고, *did~*는 특정 행위가 일어난 직후입니다.
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


Closure
-------

#### 파라미터와 리턴 타입이 없는 Closure 정의시에는 `() -> Void`를 사용합니다.

**좋은 예:**

```swift
let completionBlock: (() -> Void)?
```

**나쁜 예:**

```swift
let completionBlock: (() -> ())?
let completionBlock: ((Void) -> (Void))?
```


#### Closure 정의시 파라미터에는 괄호를 사용하지 않습니다.

**좋은 예:**

```swift
{ operaion, responseObject in
    ...
}
```

**나쁜 예:**

```swift
{ (operaion, responseObject) in
    ...
}
```


#### Closure 정의시 가능한 경우 타입 정의를 생략합니다.

**좋은 예:**

```swift
...,
completion: { finished in
   ...
}
```

**나쁜 예:**

```swift
...,
completion: { (finished: Bool) -> Void in
    ...
}
```


#### Closure 호출시 또다른 유일한 Closure를 마지막 파라미터로 받는 경우, 파라미터 이름을 생략합니다.

**좋은 예:**

```swift
UIView.animateWithDuration(0.5) {
    ...
}
```

**나쁜 예:**

```swift
UIView.animateWithDuration(0.5, animations: { () -> Void in
    ...
})
```


#### Closure 호출시 Closure를 유일한 파라미터로 받는 경우, 괄호를 생략해도 됩니다.

```swift
let sortedArray = array.sort { ... }
let sortedArray = array.sort() { ... }
```


#### 간결한 Closure 호출시 파라미터와 `return` 구문을 생략합니다.

**좋은 예:**

```swift
let sortedArray = array.sort { $0 > $1 }
```

**나쁜 예:**

```swift
let sortedArray = array.sort { obj1, objc2 in
    return obj1 > obj2
}
```



클래스
----

#### UI 개발에 사용되는 상수들은 클래스 내부의 `struct`에서 관리합니다.

재사용성과 유지보수 측면에서 큰 향상을 가져옵니다. [CGFloatLiteral][cgfloatliteral]과 [SwiftyColor][swiftycolor]를 사용해서 코드를 단순화시킵니다.

```swift
class ProfileView: UIView {

    struct Metric {
        static let profileImageViewLeft = 10.f
        static let profileImageViewRight = 10.f
        static let nameLabelTopBottom = 8.f
        static let bioLabelTop = 6.f
    }
    
    struct Font {
        static let nameLabel = UIFont.boldSystemFontOfSize(14)
        static let bioLabel = UIFont.boldSystemFontOfSize(12)
    }
    
    // SwiftyColor에서 제공하는 Color Operator를 사용합니다.
    struct Color {
        static let nameLabelText = 0x000000~
        static let bioLabelText = 0x333333~70%
    }
    
    ...

}
```

이렇게 선언된 상수들은 다음과 같이 사용될 수 있습니다:

```swift
self.profileImageView.frame.origin.x = Metric.profileImageViewLeft
self.nameLabel.font = Font.nameLabel
self.nameLabel.textColor = Color.nameLabelText
```


#### 클래스 내부에서는 `self`를 명시적으로 사용합니다.


구조체
----

#### 구조체를 생성할 때에는 Swift 구조체 생성자를 사용합니다.

**좋은 예:**

```swift
let frame = CGRect(x: 0, y: 0, width: 100, height: 100)
```

**나쁜 예:**

```swift
let frame = CGRectMake(0, 0, 100, 100)
```


타입 선언
-------

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


Control Flow
------------

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


주석
----

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


기타
----

#### `import`는 위부터 ABC순으로 작성합니다.

```swift
import Alamofire
import SwiftyColor
import SwiftyModel
import JLToast
import UIKit
import UINavigationItem_Margin
import UITextView_Placeholder
```


라이센스
------

본 스타일 가이드 문서는 CC-By 3.0 라이센스를 따릅니다. 자세한 내용은 [http://creativecommons.org/licenses/by/3.0/][cc] 링크를 참조해주세요.


[cgfloatliteral]: https://gist.github.com/devxoul/5186803939957b2c3f8a
[swiftycolor]: https://github.com/devxoul/SwiftyColor
[cc]: http://creativecommons.org/licenses/by/3.0/

