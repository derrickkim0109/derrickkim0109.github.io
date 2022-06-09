# Structures and Classes
> Structure와 class는 프로그램 코드의 구성요소가 되는 광범위하고 유연한 구조이다.

- 메서드와 프로퍼티 정의가 가능하다.
- 다른 언어와 다르게, 커스텀 structure와 class에 분리된 인터페이스나 구현파일을 요구하지 않는다.
- 클래스의 인스턴스는 전통적으로 object로 알려져 있다. 그러나 스위프트 structure와 class의 instance 들은 다른언어와는 다르게 기능적이다 그러므로 object가 아닌 instance라 칭한다

# Comparing Structures and Classes

- 공통점:

	- 저장 값으로 프로퍼티 정의

	- 기능성 제공을 위해 메서드 정의

- 그들의 value 에 접근하기 위해 subscript sytax사용을 제공하는 subscripts 정의

```swift
var numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
numberOfLegs["bird"] = 2  // [,] 는 subsctipt brackets 라고 부른다
```

- 초기 상태 설정을 위해 이니셜라이저 정의

- 기본 구현을 넘어선 기능확장을 위해 extended

- 특정 종류의 표준기능을 제공하기 위해 protocol 준수

#### Class만 가진 추가 기능(struct엔 없음) :

- 상속은 한 class 가 다른 class의 특성들을 상속받을 수 있게 해준다
- 타입캐스팅은 런타임시 클래스 인스턴스의 타입을 확인하고 해석할 수 있게 해준다
- class의 인스턴스의 Deinitializer는 할당된 어느 자원이든 해제?하게 해준다
- ReferenceCounting 은 클래스 인스턴스에 대한 하나 이상 참조를 허락한다
- 일반적 가이드라인으로, 추론하기 더 쉬운 Struct사용을 권장한다
	- class는 그것이 적합하고 필요할 때 사용하라

- structure 또는 class 는 사용자 정의 타입이다.

- dot syntax 를 이용해서 인스턴스의 프로퍼티값에 접근 가능하다. 파고파고 들어가기도 가능하고, 거기에 값 할당도 가능하다

- struct타입을 위한 memberwise 이니셜라이저

- struct의 새 인스턴스에 프로퍼티를 초기화할 때 사용하는 memberwise 이니셜라이저가 자동으로 생성된다. 

```swift
struct Resolution {
	var width = 0
	var height = 0
}
let vga = Resolution( // 까지만 치면 자동으로 (width:,height:) 가 뜬다
																			// memberwise initializer
```

- class는 기본 memberwise initializer를 받지 않는다.

# Structures and Enumerations Are Value Types
> 값타입은 변수나 상수에 할당 될때나, 함수에 전달될 때 그 값이 복사되는 타입이다

> 기본타입( Int, Float, Bool, String, Array, Dictionary )은 값타입이고, 뒤에서 structure로 구현된다

- Collection은 복사의 수행비용을 줄이기 위해 최적화를 사용한다.
-  즉시 복사를 만드는 것 대신에, 원본값과 복사값 사이에 요소가 저장된 메모리를 공유한다. 
- 복사본중 하나가 수정되면, 요소들은 수정 바로 전에 복사된다

```swift
let hd = Resolution(width: 1920, height: 1080)
var cinema = hd

// hd 와 cinema는 완전히 다른 (따로 떨어진) 인스턴스가 된다. 복사되었기 때문, 

cinema.width = 2048 // hd.width 에 영향을 미치지 않는다  
```

```swift
enum CompassPoint {
	case north, south, east, west
	mutating func turnNorth() {
		self = .north
	}
}
var currentDirection = CompassPoint.west
let rememberedDirection = currentDirection
currentDirection.turnNorth()
print(\(currentDirection))  // north
print(\(rememberedDirection)) // west
```

# Classes Are Reference Types
> 값타입과 다르게, 참조타입은 변수나 상수에 할당될 때나, 함수에 전달될 때 복사되지 않는다

> 값타입의 인스턴스1을 만들고, 그 안의 프로퍼티를 수정하면 원본값이 수정이 된다.

> 인스턴스 1 을 받는 인스턴스 2 를 만들고 , 인스턴스2 안의 프로퍼티를 수정하면 원본값이 수정되어 인스턴스1과 인스턴스2 안의 프로퍼티가 모두 바뀐다

> 만약 인스턴스1과 인스턴스2 가 멀리 떨어져 있다면 원본값이 바뀐 이유를 찾기 힘들 것이다… 그래서 class보다 struct를 추천하는 것

- class는 참조타입 이므로, 많은 상수들과 변수들이 하나의 클래스의 인스턴스를 참조하는 것이 가능하다

- Identity operator는 두 상수나 변수가 같은 클래스 인스턴스를 참조하는지 찾아내는 유용한 방법이다

```swift
Identical to (===)
Not identical to (!==)
if tenEighty === alsoTenEighty {
	print("tenEighty and alsoTenEighty refer to the same VideoMode instance.")
}
```
