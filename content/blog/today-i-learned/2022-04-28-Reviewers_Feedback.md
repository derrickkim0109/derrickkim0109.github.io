피드백 받은 내용


- 팩토리 메서드 
	- make는 전치사 붙지 않는다. 
	- _ 로 변경 
	- with 도 나쁘지 않다.(apple도 좀 많음)

- Type들을 명시 할때 Enum이 좋다.

# class
- 변경이 필요한 경우

- Final은 상속을 안할때 붙인다가 아니라 
상속이 필요하지 않을때 붙인다. 

# struct 
- 변경을 허용하지 않는다.
- 메모리까지 같은 객체로 두지 않음.
- 새로 만드는 게 싸게 먹히는 것이다. 


swift 문은 더이상 줄일 부분이 없다. 

상속은 객체지향의 근본이다. 
부모 자식 관계는 조심해서 써야 한다.

final 상속을 못하게 했겠구나 상상을 하게되어 
하면 안되는 상황에서만 붙여야 한다.

정말 상속을 하면 안되는 부분에서만 붙여줘야한다. 

os 부모 것을 호출해야는지 자식것을 호출해야는지 고민한다 -> 성능저하 

성능을 위해서 final을 붙인다? 안좋은 생각.

상속을 시킬 것인지 아닌지에 따라 구현 방식이 달라진다. 

재정의를 할 수 도 있는지 ?

상속은 꼭 해야하는지? 

- Fruit -> FruitType
	 - Fruit를 아껴 뒀을 것이다. 

# Array 네이밍 
> Array: FruitList / Fruits


# 딕셔너리 네이밍
> FruitDictionary -> 의도가 없다. 

> FruitStock / FruitStorage (의미를 부여하라)


# Protocol
> 네이밍이 어렵다

- FruitStoring
- FruitStoreDescribing 
- FruitStoreProtocol

# 주석 
> 메소드명에서 적을수 없는 내용을 적는 것이다. 

# for in vs forEach 
> forEach 가 함수형이다
> 함수형 스타일은 예외를 두지 않는다. 
> 예외를 두는것은 가독성을 해치는 것이다.

- consume(target)
- max 처리? 

figure out -> return 타입이 Error or Error Optional

결과를 보여주기 위해 Throws를 쓰는 것은 이상하다. 

Throws만을 위한 함수로 쓰면 
consume에 써야 더 자연스러운 것이다. 

Bool로 표현 하면 
true of false 로 리턴 하면 

넉넉한지?

- out of bounds 

struct Ingredient {
	let fruitType: Fruit
	let amount: Int
	
}

-> [Intgrdient]


# 추상화 상상

쥬스메이커가 여러개? 

DrinkMakerable

메모리의 프로토콜다. 
디비 일수도 있고 서버일 수도 있도록 하는 상상