# 리뷰 내용
> 2022.05.11

### Delegate 

- 어떨때 Delegate를 써야하나?
	- 머써야 할지 모를때 ? 
	- Singleton, Notification Center를 사용하는 경우 틀린 상황인 경우가 많음
	- Singleton / Notification Center 피해야 하는 이유

- Stepper : 잘 사용 하지 않는 컴포넌트다
	- customizing이 잘 안되서 힘듬

# 고민한 점 답변

1. iOS 10 이하 지원은 버그가 많음 
- iOS 11이상 부터 생산성이 좋은 함수가 많음

> 카카오톡 참조 해서 본다.

2. present에서 같이 속성 값 보내는 것 (너무 당연한것)
- OrderViewController
	from A to B : 부모가 자식 관계로 봐야는데 
	 
- StoreViewController 

3. Delegate : 자식이 부모에게 알리고 싶을때 / 역전이 필요할때 (의존성 역전) 
	- 의존성을 끊어 주기 위해서 쓰는 패턴이다.
	- Delegate 패턴에 대한 공부를 꼭 해야함. 
	 
4. Singleton 패턴 : 안티 패턴 이다.
	- 전역 변수를 선언하니까 어디서든 접근이 가능하다
	- 어디서든 접근할 수 있어야 하는 시나리오??
	- 내가 객체를 단순하게 바로 얻을 수 없는 경우 사용하고 싶어짐
	- 정상적인 로직 시나리오를 방해한다
	- 트리형태가 정상적인 좋은 흐름이다. 

5. Notification Center : 안티 패턴이다. 
	- 나 이거 이벤트 발생했다? 소리치는 방식이다.
	- 그 이벤트를 받고 싶은 함수들이 실행 되야함
	- 부모와 자식의 거리가 먼 경우? 
	- 쉬운길은 보통 틀림.

- 디버깅하려면 이전에 어떤 이벤트가 실행됬는지 파악해야는데 역추적 하기가 너무 어렵다. 

- 하지만! 필요한 순간이 있다
	- Apple : UIApplication.shared
	- URLSession.shared
	- keyboardNotification - system의 이벤트 
	- gps 다루는 모듈 ? 

### Delegate를 패턴 
> 부모의 클래스를 숨기는 역할을 한다.
> DataSource 패턴  -> Return 타입이 많다. 
>> 내가 어떤 타이밍을 알고 싶을떄 써야함. 

> UICollectionViewDelgate 패턴 -> Return 타입 대부분 없고
> > 눌렸다, 곧 보일거야 같은 타이밍

class XXX {} , XXXDelegate
class XXXView{} XXXViewDelegate

func xxx(_xxx: XXX, didChangeValue value: Int)
func didCancelledStoreViewController(_ vc: OrderViewController)


### final
> 성능과 별개로 '상속이 필요없다' 를 동료에게 알려줄 수 있어야함,


### traitCollection
> 별도의 Auto layout으로 대응
> Collection View를 쓰면 화면이 작으면 자동으로 Scoll 할 수 있게 해줌


### IBOutlet Collection 
> 한번의 고민이 들어가는 건 안좋은 코드다. 
> 명시적인게 좋다 
> 계산기 라도 개별 선언 했을 것이다.


### setup <-> getter
get -> fetch 
makeStock 

present 시점에 주입. 

# StoreViewController
뷰로 바라봐야한다 
-> 능동적으로 움직일수 없는 친구?  
-> 수동적인 뷰는 재사용성이 좋다. 
-> 능동적인 친구는 Delegate를 쓰지 않는다
-> 능동적이면 Class를 떤진다 .

func stepperValueDidChanged(_ type: FruitType, with : number Int) 
func storeViewControllerWillDismiss()









