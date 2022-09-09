<!-- vscode-markdown-toc -->
	* 1. [컴퓨터의 동작원리](#)
	* 2. [메모리 저장방식에 대한 이해](#-1)
	* 3. [메모리에서 음수 표현 방법](#-1)
	* 4. [변수와 상수 / 데이터 타입](#-1)
	* 5. [기본 연산자](#-1)
	* 6. [조건문](#-1)
	* 7. [튜플 (Tuple)](#Tuple)
	* 8. [삼항연산자와 범위연산자](#-1)
	* 9. [반복문](#-1)
	* 10. [함수](#-1)
	* 11. [Guard 문](#Guard)
	* 12. [Optional](#Optional)
	* 13. [Collection](#Collection)
		* 13.1. [1. Array](#Array)
		* 13.2. [2. Dictionary](#Dictionary)
		* 13.3. [3. Set (집합)](#Set)
	* 14. [열거형 (Enumeration)](#Enumeration)
	* 15. [클래스와 구조체의 이해](#-1)
		* 15.1. [1. 클래스](#-1)
		* 15.2. [2. 구조체](#-1)
		* 15.3. [3. 클래스와 구조체 비교](#-1)
		* 15.4. [4. 클래스와 구조체를 사용하는 이유](#-1)
	* 16. [속성](#-1)
		* 16.1. [1. 저장속성](#-1)
		* 16.2. [2. 계산속성](#-1)
		* 16.3. [3. 타입속성](#-1)
		* 16.4. [4. 속성 감시자(관찰자)](#-1)
	* 17. [메서드](#-1)
		* 17.1. [1. 인스턴스 메서드](#-1)
		* 17.2. [2. 타입 메서드](#-1)
		* 17.3. [3. 서브스크립트](#-1)
		* 17.4. [4. 참고](#-1)
	* 18. [클래스의 상속과 초기화](#-1)
	* 19. [타입캐스팅](#-1)
		* 19.1. [1. is 연산자](#is)
		* 19.2. [2. as 연산자](#as)
		* 19.3. [3. 타입과 다형성](#-1)
		* 19.4. [4. Any와 AnyObject를 위한 타입캐스팅](#AnyAnyObject)
	* 20. [타입의 확장 (Extension)](#Extension)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc --># Swift Study Note

###  1. <a name=''></a>컴퓨터의 동작원리
* 폰노이만 컴퓨터 구조 : cpu <-> ram(주기억 장치) <-> hdd(보조기억 장치)
* 프로세스 : 실행중인 프로그램
* 프로그래밍 -> 컴파일 -> 기계어
* 메모리 = **코**드(프로그램) + (**데**이터 + **힙** + **스**택)

###  2. <a name='-1'></a>메모리 저장방식에 대한 이해
- 비트 : 2진수(0b)에서 한개의 자릿수
- 바이트 : 비트 8개 (컴퓨터에서 데이터를 다루기 위해 사용되는 기본단위)
- 2$^8$ 즉 256가지를 표현 할 수 있다.
- 1바이트 = 글자 1개
- 16진법(0x) : 2진수를 4비트 2개로 나눠서 16진법을 사용하면 쉽게 표현된다.
- 2$^{32}$ = 32비트 = 4G 메모리 주소 기억
- 2$^{64}$ = 64비트 = 16 EByte 메모리 주소 기억(16억)

###  3. <a name='-1'></a>메모리에서 음수 표현 방법
- 가장 앞에 자릿수로 부호를 표기
- 기존 숫자에 2의 보수로 변환하고 1을 더함으로  음수를 표현
- 2의 보수의 방식은 컴퓨터의 덧샘을 보다 빨리 계산할 수 있게 한다.

###  4. <a name='-1'></a>변수와 상수 / 데이터 타입
- String Interpolation : 문자열 보간법
    ```swift
    print("저의 이름은 \(name)입니다")
    ```
- Type Annotation : 변수를 선언하면서 타입도 명확하게 지정하는 방식
- Type Inference : 타입을 지정하지 않아도 컴파일러가 타입을 유추해서 알아내는 방식
- Type Safety : 다른 데이터 타입끼리 계산 할 수 없다. (메모리 공간의 크기가 다름)
- Type Conversion : 기존의 값을 다른 형식으로 바꿔서 새로운 값을 생성후 다른 메모리 공간에 저장
- Type Alias : 기존에 선언되어 있는 타입에 새로운 별칭을 붙여서 코드의 가독성을 높이는 방법
    ```swift
    typealias: Something = (Int) -> String

    func someFunction(completionHandler: (int) -> String) {   
    }

    func someFunction(completionHandler: Something) {			 
    }
    ```
- Literals : 코드에서 고정된 값으로 표현되는 데이터 그 자체
- Identifier (식별자) : 변수, 상수, 함수, 사용자 정의 타입의 이름들 모두

###  5. <a name='-1'></a>기본 연산자
- Operator (연산자), Operand (피연산자)
- 모듈로 연산자 : 시간, 분, 배열에서 선택 할 때 유용
- Compound Assignment Operator (복합 할당 연산자) : ++는 지원하지 않음
- 접근연산자 : 점 (하위개념으로 접근)

###  6. <a name='-1'></a>조건문
- 프로그래밍의 세가지 논리 : 순차, 조건, 반복
- 스위치문에서 콤마는 또는의 의미이다.
- 스위치문은 비교하는 모든 경우의 수를 반드시 다뤄야 함 (exhaustive)
- 패턴 매칭 연산자 (~=) : 참과 거짓의 결과가 나옴
- 스위치문에서 범위연산자(...)를 사용해야함
- fallthrough : 매칭된 값에 대한 고려없이 무저건 다음문장도 실행하고 싶을때 사용
- 바인딩 : 새로운 변수나 상수에 새로운 식별자로 할당한다
    ```swift
    var num = 10

    switch num {
    case let x where x % 2 == 0:
        print("짝수숫자 : \(x)")
    case let x where x % 2 != 0:
        print("홀수숫자 : \(x)")
    default:
        break
    }
    ```
###  7. <a name='Tuple'></a>튜플 (Tuple)
- 괄호와 쉼표로 복수 데이터 할당
- 접근방법 : 변수명.0
- Named Tuple :  코드의 가독성이 높아짐
    ```swift
    let iOS = (language: "swift", version: "5.0")

    iOS.language
    iOS.version
    ```
- Decomposition (튜플의 분해)
    ```swift
    let (name, age, address) = ("홍길동", 20, "남산")
    ```
- 튜플의 바인딩
    ```swift
    var coordinate = (0, 5)

    switch coordinate {
    case (let distance, 0), (0, let distance):
        print("X 또는 Y축 위에 위치하며, \(distance)만큼의 거리가 떨어져있다.")
    default:
        print("축 위에 있지 않음")
    }

    coordinate = (1, -1)

    switch coordinate {
    case let (x, y) where x == y:
        print("(\(x), \(y))의 좌표는 y = x 1차 함수의 그래프 위에 있다.")
    case let (x, y) where x == -y:
        print("(\(x), \(y))의 좌표는 y = -x 1차 함수의 그래프 위에 있다.")
    case let (x, y):
        print("(\(x), \(y))의 좌표는 임의의 지점에 있다.")
    }
    ```

###  8. <a name='-1'></a>삼항연산자와 범위연산자
- 조건 ? 참 : 거짓  (조건에 따라 선택이 두가지 일 경우)
- 조건에 따라서 리터럴 값을 변수에 할당 할 때 *주로* 사용
    ```swift
    var name = a > 0 ? "스티브" : "팀쿡"
    let result = score >= 70 ? "Pass" : "Fail"
    ```
- 패턴매칭 연산자 : 오른쪽의 표현식이 왼쪽의 범위에 포함되는 지에 따라 참과 거짓을 리턴
    ```swift
    a...b ~= age
    ```

###  9. <a name='-1'></a>반복문
- for 문 : 반복횟수를 미리 알고 있거나 컬렉션, 범위 등을 이용 할 때 사용 (범위, 컬렉션, 문자열, stride등)
- while 문 : 반복횟수가 미리 정해저 있지 않고 조건에 따라 바꿜 때 사용 (조건)
- 제어전송문
  1. **continue** : 반복문에서 다음 주기로 넘어가서 계속함
    ```swift 
    for num in 1...20 {
        if num % 2 == 0 {
            continue
        }
        print(num)    // 1, 3, 5, 7, 9 ....
    }
    ```
  2. **break** : 반복문을 아예 중지
    ```swift
    for num iun 1...20 {
        if num % 2 == 0 {
            break
        }
        print(num)    // 1
    }
    ```
 3) fallthrough
 4) throw: 에러가 발생 가능하도록 정의된 함수에서 throw 다음의 에러의 타입을 리턴후 함수를 벗어남
 5) return : 아래줄 참조


###  10. <a name='-1'></a>함수

- 리턴 타입이 없는 함수는 결과값이 Void 타입
- 리턴 타입이 있는 함수는 결과값이 있는것 (일반적으로 사용)
- Parameter (매개변수=인자)
- Argument (인수)
- Nested Function : 함수를 제한적으로 사용하고 싶을 때 사용 (stepForward, stepBackward)
- 함수의 타입 표기 방법
    ```swift
    var function1: (Int) -> () = numberPrint(n:)
    var function2: (Int, Int) -> Void = addPrintFunction(_:_:)
    ```
- Overloading : 같은 함수에 매개변수를 다르게 선언하여, 하나의 함수이름에 여러개의 함수를 대응 시킴
- Scope : 상식적으로 생각해
- inout 키워드 : 함수내에서 변수의 값을 바꾸고 싶을 때 사용 (선언은 inout 키워드, 실행시 & 사용)
    ```swift
    num1 = 123
    num2 = 456

    func swapNumber(a: inout Int, b: inout Int) {
        temp = a
        a = b
        b = temp
    }

    swapNumber(a: &num1, b: &num2)
    ```

###  11. <a name='Guard'></a>Guard 문
- 여러개의 조건이 있을때 코드의 가독성 문제를 해결하기 위해 사용
- if-else에서 else문이 먼저 배치해서 조건을 판별하여 조기 종료 (early exit)
- if 문 조건을 만족해야만 내부 실행, guard 문 조건을 만족하지 않으면 다음을 실행
    ```swift
    func checkNumber(words: String) -> Bool {
        guard words.count >= 5 else { 
            print("5글자 이하입니다.")
            return false }

        print("\(words.count) 글자 입니다.")
        return true
    }
    ```
- guard 문에는 반드시 return, throw, break, countinue로 조기 종료해야 함
- 어트리뷰트 키워드 : 선언과 타입에 추가적인 정보를 제공하는 키워드 
- @discardableResult : 함수의 결과값이 나오더라도 사용하지 않을수도 있다고 알려줌
- 재귀함수 : 자기 자신을 반복해서 호출하는 함수 (조건을 반드시 넣어줘야 함  =!stackoverflow)
    ```swift
    func factorial(num: Int) -> Int {
        var sum = 1
        for i in 1...num {
            sum = sum * i
        }
        return sum
    }
    // 아래 재귀 함수로 표현
    func factorialF(num: Int) -> Int {
        if num <= 1 {
        return 1
        }
        return num * factorialF(num: num - 1)
    }

    factorial(num: 10)
    ```
- guard문에서 선언된 상수는 래에서 사용 가능

###  12. <a name='Optional'></a>Optional
- 옵셔널 타입은 반드시 변수(var)로 선언해야 한다.
- 옵셔널 타입 추출 방법
    1) 강제추출 : num! (값이 항상 있는것이 확실 할 때 사용)
    2) nil 아닌지 확인후 강제추출 : if문을 통해 nil이 아님을 먼저 확인 후, 강제추출
 
    ```swift
    if num != nil {print(num!)}
    ```

    3) ==**옵셔널 바인딩** : 바인딩(상수나 변수에 대입)이 되는 경우만 특정작업을 하겠다==
    
    ```swift
    if let name = optionalName {
        print(name)
    }

    func doSomething(name: String) {
        guard let n = name else {return}
        print(n)
    }
    ```
    4) Nil-Coalescing : 옵셔널 표현식 뒤에 기본값을 제시하여 옵셔널의 기능을 없앰
    ```swift
    var serverName: String?
    var userName = serverName ?? "미인증 사용자" 

    var hello = "인사하겠습니다." + (str ?? "Say, Hi")

    ```
  5) 옵셔널 체이닝 : 표현식 자체가 옵셔널의 가능성이 있다는 것을 표현, 결과는 항상 옵셔널
    ```swift
    human?.choco?.name
    ```

  6) 함수에서 옵셔널 타입의 사용 : nil을 초기값으로 선언해 넣어 두면 편하다
    ```swift
    func doSomething(with label: String, name: String? = nil) {
        print("\(label): \(name)")
    }
    ```

###  13. <a name='Collection'></a>Collection
> 데이터를 담는 바구니 (Array, Dictionary, Set)
####  13.1. <a name='Array'></a>1. Array
- 빈 배열을 생성하는 방법
    ```swift
    let emptyArray: [Int] = []
    let emptyArray = Array<Int>()
    let emptyArray = [Int]()
    ```
- 배열의 기본기능
    ```swift
    var numsArray = ["goog", "ssdf"]

    numsArray.count
    numsArray.isEmpty
    numsArray.contains(1)
    numsArray.randomElement()
    numsArray.swapAt(0, 1)

    numsArray.first
    numsArray.last
    numsArray.startIndex
    numsArray.endIndex
    numsArray[numsArray.endIndex - 1]  // 사용주의!

    numsArray.firstIndex(of: "iOS")
    numsArray.lastIndex(of: "iOS")

    if let index = numsArray.firstIndex(of: "iOS") {
        print(index)
        print(numsArray[index])
    }
    ```
- 메소드 : insert, replace, append, remove
- 메소드 함수명 
    - 동사원형 : 컬렉션 자체를 ==직접적으로 변환함==
    - 과거형 : 컬렉션 자체를 직접 ==변환하지 않고 변경된 값만 리턴함==

####  13.2. <a name='Dictionary'></a>2. Dictionary
- 키, 밸류값
- 동일한 타입 쌍의 데이터만 담을수 있음
- 중첩사용 가능
- Key 값은 hashable 해야 함 (유일성 보증)
- 빈 딕셔너리를 생성하는 방법
    ```swift
    let emptyDic1: Dictionary<Int, String> = [:]
    let emptyDic2: Dictionary<Int, String>()
    let emptyDic3: [Int: String]()
    ```
- 딕셔너리는 기본적으로 서브스크립트[]를 이용한 문법을 주로 사용
- 딕셔너리의 키로 호출시 옵셔널 타입으로 값을 반환함
- 딕셔너리의 기본기능
    ```swift
    print(dic.keys)
    print(dic.values)

    dic.keys.sorted()    // 키를 배열로 변환함
    dic.values.sorted()  // 밸류를 배열로 변환함

    for key in dic.keys.sorted() {
        print(key)
    }
    ```
- 메소드 : update (삽입, 교체, 추가), remove
- 반복문과의 결합
    ```swift
    for (key, value) in dict {
        print("\(key): \(value)")
    }
    ```


####  13.3. <a name='Set'></a>3. Set (집합)
- 배열이랑 구분이 안되기 때문에 타입을 반드시 선언해야 함!
- 요소는 중복 저장이 되지 않음 (hashable)
- 서브스크립트 관련 문법이 없음


###  14. <a name='Enumeration'></a>열거형 (Enumeration)
- 타입 자체를 한정된 사례(CASE) 안에서 정의 할 수 있는 타입 (열거형은 타입이다!)
- 일반적으로 switch 문으로 분기처리
- 타입의 값(리터럴)
- 열거형의 원시값 (Raw Value) : 원시값을 정의하여(타입) 열거형을 좀 더 쉽게 사용
    ```swift
    enum RpsGame: Int {
        case rock
        case paper
        case scissors
    }

    // 실제 사용
    var game = RpsGame(rawValue: 0)
    RpsGame(rawValue: 0)
    RpsGame(rawValue: 1)
    RpsGame(rawValue: 2)
    ```
- 열거형의 연관값 (Associated Value) : 열거형에 구체적인 추가정보를 저장하기 위해 사용
    ```swift
    enum Computer {
        case cpu(core: Int, ghz: Double)
        case ram(Int, String)
        case hardDisk(gb: Int)
    }

    var chip = Computer.cpu(core: 8, ghz: 3.1)
    chip = Computer.ram(8, "DRAM")

    switch chip {
    case .cpu(core: 8, ghz: 3.1):
        print("CPU 8코어 3.1GHz 입니다.")
    case .cup(core: 8, ghz: 2.8):
        print("CPU 8코어 2.8GHz 입니다.")
    case .ram(32, _):
        print("32기가 램 입니다.")
    default:
        print("그 이외의 칩에는 관심이 없습니다.")
    }

    // 바인딩 사용
    switch chip {
    case let .cpu(a, b):
        print("CPU는 \(a)코어 \(b)GHz 입니다.")
    case let .ram(a, _):
        print("\(a)기가 램입니다.")
    case hardDisk(let a):
        print("하드디스크 \(a)기가 용량입니다.")
    }
    ```
 - 옵셔널 열거형인 경우 swift에서 switch문에서 편의적인 기능을 제공한다
 - 열거형에 연관값이 있는 경우 switch문외에 조건문과 반복문에도 사용가능하다. (열거형 케이스 패턴)
 - 옵셔널 패턴 : 
 - @unknown 키워드 : switch 문에서 열거형의 모든 케이스를 다루지 않은 경우 경고창을 출력



###  15. <a name='-1'></a>클래스와 구조체의 이해
####  15.1. <a name='-1'></a>1. 클래스
- 프로그래밍 패러다임 : 객체 지향 프로그래밍으로 변화됨
- 객체 지향 프로그래밍 : 틀(클래스, 구조체)로 실제데이터(객체)를 찍어내는 것
    ```swift
    class Dog {
        var name = "강아지"
        var weight = 0
        func sit() {
            print("앉았습니다.")
        }
        func layDown {
            print("누웠습니다.")	
        }	
    }

    var bori = Dog()
    var choco = Dog()
    ```
- 클래스는 변수와 함수를 묶음으로 만들어 내는 것
- 클래스 내의 변수는 속성(property), 함수는 메서드(method)라고 하고 반드시 2가지로 이루어짐

####  15.2. <a name='-1'></a>2. 구조체
- 기본적으로 클래스와 동일한 구조를 가지고 있으나, 상속이 안됨


####  15.3. <a name='-1'></a>3. 클래스와 구조체 비교
- 둘다 메모리에 찍어낸 것을 인스턴스라고 함
- 인스턴스 : 실제로 메모리에 할당되어 구체적 실체를 갖춘 것이라는 의미
- 클래스의 인스턴스를 특별히 객체(object)라고 부름

| 구조체 | 클래스 | 
| ---- | ---- | 
| 값형식(Value Type)| 참조형식(Reference)| 
| 인스턴스 데이터를 모두 **스택**에 저장 | 인스턴스 데이터를 **힙**에 저장| 
| 복사시 값을 전달할때 마다 **복사본 생성** <br> (서로 다른 데이터 존재) | 복시시 값을 전달하지 않고 저장된 **주소를 전달** <br>(동일한 데이터를 가르킨다)|
| 스택 프레임 종료시 메모리에서 자동 제거 | ARC 시스템을 통해 메모리 관리| 





- 관습 : 속성과 메서드의 순서로 작성함
- 주의 : 클래스 내부에는 메서드 실행문이 올 수 없다. 그러나, 선언문 안에서는 함수 실행 가능
- 초기화의 생성자(initializer)의 의미
	-  모든 저장 속성(변수)을 초기화 해야함
	- 생성자의 목적은 결국 "저장속성 초기화"
        ```swift
        class Dog {
            var name: String
            var weight: Double

            init(name: String, weight: Double) {
                self.name = name
                self.weight = weight
            }
        }

        var bori = Dog(name: "보리", weight: 12)
        ```
- 식별 연산자(Identity) : 두개의 참조가 같은 인스턴스를 가르키고 있는지 비교하는 방법
    ```swift
    print(dog1 === dog2)
    print(dog1 !== dog2)
    ```

####  15.4. <a name='-1'></a>4. 클래스와 구조체를 사용하는 이유
- 의미있는 데이터를 묶음으로 만들려고 함 (모델링)
	1. 사용하려는 모델의 설계
	2. 애플이 미리 설계해 놓은 클래스/구조체를 잘 사용하기 위함

- 객체지향(OOP)의 4대 특징 (==캡상추다==)
	1. 추상화(모델링) : 공통적인 특성을 뽑아내서 하나의 분류(class)로 만든 것
	2. 캡슐화 : 속성(상태)와 매서드(기능)을 하나의 클래스로 묶어서 활용 (은닉화 가능)
	3. 상속성 : 재사용과 확장
	4. 다형성 : 오버라이딩, 오버로딩


###  16. <a name='-1'></a>속성
####  16.1. <a name='-1'></a>1. 저장속성
- 그 자체가 메모리 공간을 갖는것 (변수)
- 지연 저장속성 (Lazy Stored Property) : 처음엔 메모리 공간을 가지지 않는 것, 초기화 값 반드시 필요
- 지연 저장속성을 사용하는 이유 
	1. 메모리 공간을 많이 차지 하는 속성을 사용 할 때
	2. 다른 속성을 이용해야 할 때 (순서상)

####  16.2. <a name='-1'></a>2. 계산속성
- 다른 저장 속성의 의한 결과로 계산해 나오는 방식의 메서드인 경우 아예 속성으로 만들어버림
- get(값을 얻음, getter), set(값을 저장, setter)
- set은 생략가능 (read-only)
    ```swift
    class Person {
        var height: Double = 0
        var weight: Double = 0
        func calculateBMI() -> Double {
            let bmi = weight / (height * height) * 10000
            return bmi
        }
    }

    let p = Person()
    p.height = 178
    p.weight = 81
    p.calculateBMI()

    class Person1 {
        var height: Double = 0
        var weight: Double = 0
        var bmi: Double {
            get {        // get ===> 값을 얻는다는 의미
                let bmi = weight / (height * height) * 10000
                return bmi
            }
        }
    }

    let p1 = Person1()
    p1.height = 183
    p1.weight = 86
    p1.bmi
    ```

####  16.3. <a name='-1'></a>3. 타입속성
- 타입 자체에 속한 속성이므로 내/외부에서 Type.property로 접근, static keyword
- 저장 타입 속성 : 모든 인스턴스가 동일하게 가져야 하는 보편적인 속성이나 공유해야 하는 성격의 것들 
						(초기값 반드시  필요)
- 계산 타입 속성 : 상속시 재정의 가능 (class 키워드를 사용시), 메서드라서 메모리 공간 미할당


####  16.4. <a name='-1'></a>4. 속성 감시자(관찰자)
- (일반적으로) 저장 속성을 관찰함
- willset : 값이 변하기 직전에 호출
- didset : 값이 변한후 직후에 호출 (실제 프로젝트에서 일반적으로 주로 사용)
    ```swift
    class Profile {
        var name: String = "이름"

        var statusMessage: String {
    //        willSet(message) {      // 바뀔 값이 파라미터로 전달
    //            print("상태가 \(statusMessage)에서 \(message)로 변경될 예정입니다.")
    //            print("상태메세지 업데이트 준비")
    //        }
            willSet {      // newValue 사용
                print("상태가 \(statusMessage)에서 \(newValue)로 변경될 예정입니다.")
                print("상태메세지 업데이트 준비")
            }
    //        didSet(message) {       // 바뀌기 전의 과거값이 파라미터로 전달
    //            print("상태가 \(message)에서 \(statusMessage)로 이미 변경되었습니다.")
    //            print("상테메시지 업데이트 완료")
    //        }
            didSet {       // oldValue 사용
                print("상태가 \(oldValue)에서 \(statusMessage)로 이미 변경되었습니다.")
                print("상테메시지 업데이트 완료")
            }
        }

        init(message: String) {
            self.statusMessage = message
        }
    }

    let profile = Profile(message: "기본 상태 메시지")
    profile.statusMessage = "기분 좋아졌으"

    >> 상태가 기분 상태 메시지에서 기분 좋아졌으로 변경될 예정입니다.
    >> 상태메시지 업데이트 준비
    >> 상태가 기본 상태 메시지에서 기분 좋아졌으로 이미 변경되었습니다.
    >> 상태메시지 업데이트 완료
    ```


###  17. <a name='-1'></a>메서드
클래스나 구조체이 있는 함수

####  17.1. <a name='-1'></a>1. 인스턴스 메서드
- 구조체는 인스턴스 메서드 내에서 속성을 수정 할 수 없음 (mutating 키워드 사용해야 함)
- 오버로딩 적용 가능

####  17.2. <a name='-1'></a>2. 타입 메서드
- 인스턴스에 속한 속성이 아니라 타입 자체에 속한 속성이므로 Type.method() 로 접근
- static 키워드 사용 : 타입 저장속성에 접근가능 (붕어빵 틀 안에 속해 있는 메서드)
    ```swift
    // 예시
    Int.random(in: 1...100)
    Double.random(in: 1.2...3.7)
    ```
- class 키워드 사용 :  상속시 재정의 가능 (static 으로 선언하면 상속시 재정의 불가)

####  17.3. <a name='-1'></a>3. 서브스크립트
- 대괄호는 사실 특별한 형태의 메서드 호출 역할임 -> 따라서, 직접 구현도 가능하다.
- 인스턴스.method()의 형태가 아닌 인스턴스[파라미터]의 형태
    ```swift
    class Somedata {
        var datas = ["Apple", "Swift", "iOS", "hello"]
        subscript(index: Int) -> String {
            get {
                return datas[index]
            }
            set(parameterName) {      // newValue로 교체 가능, setter와 동일
                datas[index] = parameterName
            }
        }
    }

    var data = Somedata()
    data[0]
    data[0] = "AAA"
    ```
- 계산 속성과 형태는 유사함 (getter / setter)
- 인스턴스 서브스크립트와 타입 서브스크립트 모두 가능 (static/class 키워드 사용)

####  17.4. <a name='-1'></a>4. 참고
- 접근제어 : private 키워드를 사용하면 외부에서 접근이 불가능하게 객체의 은닉화
- 싱글톤 패턴 : 메모리상에 유일하게 1개만 존재하는 객체 설계 (==static let== 키워드)
    ```swift
    class Singleton {
        static let shared = Singleton()
        var userInfoId = 12345
        private init(){}    // 새로운 객체를 찍어 내는것을 막는다!
    }

    let object = Singleton.shared    // 싱글톤에 접근
    let object = Singleton()         // 에러!!
    ```
    
###  18. <a name='-1'></a>클래스의 상속과 초기화
    
- 상속 (Inherance = Subclassing) : 새로운 타입을 만들어서 저장속성을 추가하는 것 (수직확장)
- 재정의 (Overriding) : 상위클래스의 속성/메서드를 재정의(기능을 변형하여 사용) 하는 것 (==저장속성 불가==)
- 속성과 메서드는 재정의 방식이 다름 : 메서드는 재정의시 배열을 새롭게 만들기 때문에 변형 가능
    ```swift
    class SomeSuperclass {
        var aValue = 0
        func doSomething() {
            print("Do something")
        }
    }

    class SomeSubclass: SomeSuperclass {
        // override var aValue = 3
        // 저장속성의 재정의는 불가

    override var aValue: Int {
            get {
                return 1
            }
            set {        // self가 아님!!
                super.aValue = newValue
            }
        }
        // 저장속성 ===> (재정의) 계산속성 가능

    override func doSomething() {
            super.doSomething()
            print("Do something 22222")
        }
    }
    ```
- 초기화(Initialization) : 클래스, 구조체, 열거형의 인스턴스를 생성하는 과정
  -  각 "저장 속성"에 대한 초기값을 설정하여 인스턴스를 사용 가능한 상태로 만드는것 <br>(열거형은 저장속성이 존재하지 않으므로, case 중 한가지를 선택 및 생성)
	- 생성자는 overloading을 지원하여 생성자를 여러개 구현 가능
	- 반드시 생성자를 정의해야만 하는것은 아님 (저장 속성 선언시 값 저장, 저장 속성을 옵셔널로 선언)
	- 구조체는 멤버와이즈 이니셜라이저 자동 제공해서 초기화 안해도 됨
- 구조체의 지정(Designated) 생성자(일반적인 생성자)의 구현
    ```swift
    struct Color {
        let red, green, blue: Double

        init(red: Double, green: Double, blue: Double) {
            self.red = red
            self.green = green
            self.blue = blue
        }

        init() {
            self.init(red: 0.0, green: 0.0, blue: 0.0)
        }

        init(white: Double) {
            self.init(red: white, green: white, blue: white)
        }
    }
    ```
- 클래스의 편의(Convenience) 생성자의 구현 : convenience 키워드 사용, 상속시 재정의 불가
- 편의 생성자는 다른 편의 생성자를 호출하거나, 지정 생성자를 호출해야 함 (궁긍적으로 지정 생성자 호출)
    ```swift
    class Aclass {
        var x: Int
        var y: Int
        init(x: Int, y: Int) {
            self.x = x
            self.y = y
        }
        convenience init() {
            self.init(x: 0, y: 0)
        }
    }  

    class Bclass: Aclass {
        var z: Int
        init(x: Int, y: Int, z: Int) {
            self.z = z                // 필수
            super.init(x: x, y: y)    // 필수
        }
        convenience init(z: Int) {
            self.init(x: 0, y: 0, z: z)
        }
        convenience init() {
            self.init(z: 0)
        }
    }
    ```
- 필수 생성자 : required 키워드를 사용하며 하위 생성자는 반드시 해당 필수 생성자를 구현해야 함
- 필수 생성자 자동상속 조건 : 다른 지정 생성자를 구현 안하면, 자동으로 필수 생성자가 상속됨
- 실패가능 생성자 : 인스턴스 생성에 실패 할 수도 있는 가능성을 가진 생성자(클래스, 구조체, 열거형)
- 소멸자 : deinit 키워드 사용, 인스턴트가 메모리에서 해제 되기 직전에 필요한 내용을 구현




###  19. <a name='-1'></a>타입캐스팅
- 정의???
####  19.1. <a name='is'></a>1. is 연산자
- 인스턴트의 타입에 대한 검사를 수행하는 연산자
    ```swift
    class Person {
        var id = 0
        var name = "이름"
        var email = "abc@gmail.com"
    }

    class Student: Person {
        var studentId = 1
    }

    class Undergraduate: Student {
        var major = "전공"
    }

    let person1 = Person()
    let student1 = Student()
    let undergraduated1 = Undergraduate()
    let person2 = Person()
    let student2 = Student()
    let undergraduated2 = Undergraduate()

    let people = [person1, person2, student1, student2, undergraduated1, undergraduated2]

    var studentNumber = 0

    for someOne in people {
        if someOne is Student {
            studentNumber += 1
        }
    }

    print(studentNumber)
    ```
####  19.2. <a name='as'></a>2. as 연산자
- 인스턴트의 타입의 힌트를 변경하는 연산자 
- 다운캐스팅 (Downcasting)
	- 인스턴스 as? 타입 : 성공시 옵셔널 타입으로 리턴, 실패시 nil 리턴, 언래핑 필요
	- 인스턴스 as! 타입 : 성공시 강제 언래핑, 실패시 런타임 오류
- 업캐스팅 (Upcasting) - as 항상 성공 (당연)
- as 연산자 활용 - 브릿징

####  19.3. <a name='-1'></a>3. 타입과 다형성
- 다형성 (Polymorphism) : 여러가지 모양 (추상화)
	1 ) 하나의 객체(인스턴스)가 여러가지 타입의 형태로 표현 될 수 있다 
	2) 상속했을 때 ==재정의한 메서드가 실행==된다
	3) 다형성이 구현되는 것은 "클래스의 상속"과 깊은 연관이 있다 (프로토콜과 깊은 연관)

####  19.4. <a name='AnyAnyObject'></a>4. Any와 AnyObject를 위한 타입캐스팅
- Any Type : 어떤 타입의 인스턴스도 표현 할 수 있는 타입 (옵셔널 포함)
- AnyObject Type : 어떤 ***클래스*** 타입의 인스턴스도 표현 할 수 있는 타입
- switch문에 is/as 패턴을 사용하여 case에서 배열등 열거후 분기처리 가능
    ```swift
    let array: [Any] = [5, "안녕", 3.5]

    for (index, item) in array.enumerated() {
        switch item {
        case is Int:
            print("Index - \(index): 정수입니다.")
        case let num as Double:
            print("Index - \(num): 소수입니다.")
        case is String:
            print("Index - \(index): 문자열입니다.")
        default:
            print("Index - \(index): 그 외의 타입니다.")
        }
    }
    ```
###  20. <a name='Extension'></a>타입의 확장 (Extension)
- 현재 존재하는 타입에 기능(메서드)을 추가하여 사용 (클래스, 구조체, 열거형 모두 가능)
- 확장의 장점 : 소급-모델링(retroactive modeling)을 사용 할 수 있다 (애플이 미리 만들어 놓은 타입)
    ```swift
    extension Int {
        var squared: Int {
            return self * self
        }
    }

    func squard(num: Int) {      // 함수로도 만들수는 있으나;;;;
        return num * num
    }

    5.squared
    squared(num: 5)              // 사용 할 때 매우 불편하다..
    ```
- 확장 가능 멤버
    1) 타입 및 인스턴스의 계산 속성
        ```swift
        extension Double {
            static var zero: Double { return 0.0 }
        }

        Double.zero

        extension Double {
            var km: Double { return self * 1_000.0 }
            var m: Double { return self }
            var cm: Double { return self / 100.0 }
            var mm: Double { return self / 1_000.0 }
            var ft: Double { return self / 3.28084 }
        }

        let oneInch = 25.4.mm
        print("1인치는 \(oneInch)미터 입니다.")

        let threeFeet = 3.ft
        print("3피트는 \(threeFeet)미터 입니다.")
        ```
    2) 타입 및 인스턴스의 메서드
        ```swift
        extension Int {                             // 타입 메서드 확장
            static func printNumbersFrom1to5() {
                for i in 1...5 {
                print(i)
                }
            }
        }

        Int.printNumbersFrom1to5()

        extension String {
            func printHelloRepetitions(of times: Int) {
                for _ in 0..<times {
                    print("Hello \(self)!")
                }
            }
        }

        "Steve".printHelloRepetitions(of: 10)

        extension Int {
            mutating func squared() {    // 구조체(열거형)에서 자신의 속성을 변경하는
                self = self * self       // 메서드는 mutating 키워드 필요
            }
        }

        var someInt = 3
        someInt.squared()
        ```
    3) 새로운 생성자 (클래스의 경우 편의 생성자만 가능, 구조체는 제한이 없으나 예외사항 존재)
        ```swift
        // 클래스
        extension UIColor {
            convenience init(color: CGFloat) {
                self.init(red: color/255, green: color/255, blue: color/255, alpha: 1)
            }
        }

        UIColor(color: 1)

        // 구조체
        struct Point {
            var x = 0.0, y = 0.0
        }

        extension Point {
            init(num: Double) {
                self.init(x: num, y: num)
            }
        }
        ```
    4) 서브스크립트
        ```swift
        extension Int {
            subscript(num: Int) -> Int {
                var decimalBase = 1
                for _ in 0..<num {
                    decimalBase *= 10
                }
                return (self / decimalBase) % 10
            }
        }

        123456789[0]    // 9
        123456789[1]    // 8
        123456789[2]    // 7
        123456789[3]    // 6   
        ```
    5) 새로운 중첩 타입 정의 및 사용
        ```swift
        extension Int {
            enum Kind {
                case negative, zero, positive
            }
            var kind: Kind {
                switch self {
                case 0:
                    return .zero            // Kind.zero
                case let x where x > 0:
                    return .positive        // Kind.positive
                default:
                    return .negative        // Kind.negative
                }
            }
        }

        func printIntegerKinds(_ numbers: [Int]) {
            for number in numbers {
                switch number.kind {
                case .negative:
                    print("- ", terminator: "")
                case .positive:
                    print("+ ", terminator: "")
                case .zero:
                    print("0 ", terminator: "")
                }
            }
        }

        printIntegerKinds([1, 3, -1, 0, 1, -2])
        ```
    6) 프로토콜 채택 및 프로토콜 관련 메서드
