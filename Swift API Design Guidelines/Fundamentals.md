# Fundamentals

## Clarity at the point of use
* 사용 시점을 명확하게 잡는게 가장 중요한 목표다!
* 메소드나 프로퍼티는 한번 선언되어, 끊임없이 재사용 되어야 한다.
<br> (Design APIs는 이러한 사용을 명확하고 간결하게 도와줄 것이다.)
* 선언문을 읽어 보는 것에만 그치지 말고, 문법이 명확하게 돌아가는지 항상 문맥을 다 살펴야 한다.

## Clarity is more important than brevity
* 간결한 코딩 보다는, 확실히 알 수 있는 코드가 더 중요하다!
* 스위프트는 되게 콤팩트한 언어지만, 코드를 최대한 짧게 짜려는게 이 언어의 목표는 아니다.
* 짧게 짠 코드는 코드의 위험성을 높일 수 있기 때문에, 오히려 시스템에 강력한 부작용을 낳을 수 있다.

## Write a documentation comment
* 모든 선언에 확실한 주석처리를 진행해야 한다!
* 주석을 통한 확실한 코드이해는 코드설계에 큰 영향력을 가지므로 미루지 말자!


<br>

> 만약, 자신의 API를 짧은주석으로 담아내기가 어렵다면, API의 설계가 잘못 된 걸지도 모른다..!!
<br>

## Begin with a summary
* 보통, 선언문 자체로나 그 주석으로부터 API를 파악할 수 있게되므로,
<br>선언할 엔터티를 설명하는 요약부터 시작하자!
  ```swift
  // Returns a "view" of `self` containing the same elements in
  // reverse order.
  func reversed() -> ReverseCollection
  ```

* **Focus on the summary**
<br>요약에 집중 하는것은 매우 중요하다!! 멋진 문서는 멋진 요약으로부터 시작된다!

* **Use a single sentence fragment**
<br>완전한 문장으로는 만들지말자. 되도록 작성 날짜를 함께적자!

* **Describe what a function or method does and what it returns**
<br>함수 또는 메소드의 기능을 표현하자. ex> 리턴하면 뭘 리턴하는지(nil, void 등)
<br>드물게, 아래 코드중 popFirst()의 주석처럼 세미콜론으로 문장을 나눠 여러개 쓸 수도 있다.
  ```swift
  /// Inserts `newHead` at the beginning of `self`.
  mutating func prepend(_ newHead: Int)

  /// Returns a `List` containing `head` followed by the elements
  /// of `self`.
  func prepending(_ head: Element) -> List

  /// Removes and returns the first element of `self` if non-empty;
  /// returns `nil` otherwise.
  mutating func popFirst() -> Element?
  ```

* **Describe what a subscript accesses**
<br>접근하는 방향에 대해 설명할 수 있다.
  ```swift
  /// Accesses the `index`th element.
  subscript(index: Int) -> Element { get set }
  ```

* **Describe what an initializer creates**
<br>생성자를 만들 때, 설명을 적어줄 수 있다.
  ```swift
  /// Creates an instance containing `n` repetitions of `x`.
  init(count n: Int, repeatedElement x: Element)
  ```

* **Describe what the declared entity is**
<br>선언한 모든 선언의 속성에 대한 설명을 적어줄 수 있다.
  ```swift
  /// A collection that supports equally efficient insertion/removal
  /// at any position.
  struct List {

      /// The element at the beginning of `self`, or `nil` if self is
      /// empty.
      var first: Element?
      ...
  }
  ```

## Optionally, continue
* 선택적으로, 계속해서 Bullet list등을 이용하여 문장 단락을 이어나갈 수 있다.
<br>단락과 단락은 빈 줄로 구분하여, 완전한 문장을 사용한다.
  ```swift
  /// Writes the textual representation of each    ← Summary
  /// element of `items` to the standard output.
  ///                                              ← Blank line
  /// The textual representation for each item `x` ← Additional discussion
  /// is generated by the expression `String(x)`.
  ///
  /// - Parameter separator: text to be printed    ⎫
  ///   between items.                             ⎟
  /// - Parameter terminator: text to be printed   ⎬ Parameters section
  ///   at the end.                                ⎭
  ///                                              
  /// - Note: To print without a trailing          ⎫
  ///   newline, pass `terminator: ""`             ⎟
  ///                                              ⎬ Symbol commands
  /// - SeeAlso: `CustomDebugStringConvertible`,   ⎟
  ///   `CustomStringConvertible`, `debugPrint`.   ⎭
  public func print(
    _ items: Any..., separator: String = " ", terminator: String = "\n")
  ```

* **Use recognized symbol documentation markup elements**
<br>필요할 때 마다, 잘 알려져있는 [다큐먼트 마크업 기호](https://developer.apple.com/library/archive/documentation/Xcode/Reference/xcode_markup_formatting_ref/MarkupSyntax.html#//apple_ref/doc/uid/TP40016497-CH105-SW1)를 이용하여 summury이외의 정보를 추가한다.

* **Know and use recognized bullet items with symbol command syntax**
<br>[명령어 문법](https://developer.apple.com/library/content/documentation/Xcode/Reference/xcode_markup_formatting_ref/SingleLineComment.html#//apple_ref/doc/uid/TP40016497-CH102-SW1)에 나와있는, 잘 알려져있는 기호항목을 익히고 사용하자.
<br>Xcode와 같은 인기있는☹️ 개발도구는 다음과같은 키워드로 시작하는 bullet item을 특별하게 다룬다.

  |||||
  |:--:|:--:|:--:|:--:|
  |[Attention](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Attention.html)|[Author](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Author.html)|[Authors](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Authors.html)|[Bug](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Bug.html)|
  |[Complexity](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Complexity.html)|[Copyright](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Copyright.html)|[Date](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Date.html)|[Experiment](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Experiment.html)|
  |[Important](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Important.html)|[Invariant](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Invariant.html)|[Note](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Note.html)|[Parameter](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Parameter.html)|
  |[Parameters](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Parameters.html)|[Postcondition](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Postcondition.html)|[Precondition](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Precondition.html)|[Remark](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Remark.html)|
  |[Requires](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Requires.html)|[Returns](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Returns.html)|[SeeAlso](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/SeeAlso.html)|[Since](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Since.html)|
  |[Throws](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Throws.html)|[ToDo](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Todo.html)|[Version](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Version.html)|[Warning](https://developer.apple.com/library/prerelease/mac/documentation/Xcode/Reference/xcode_markup_formatting_ref/Warning.html)|
  |||