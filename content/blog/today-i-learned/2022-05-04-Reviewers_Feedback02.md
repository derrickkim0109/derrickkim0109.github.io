# 리뷰 내용

- ViewController에서 Configuration이라는 것을 Nesting 했을때 
중첩을 해도 좋다. 

여기 저기에서 써야하는 경우 불필요한 상황.
적용 범위에 따라 다를 것이다.

- Result 반환 타입을 사용할 때[
extension을 만들어서 

extention Result { 
	func handleValue(_ closure: (Success) -> Void) -> Result {
		switch self {
		case .success(let value):
			clousre(value) 
		default: 
			break
	}
	
	func handleError(_ closure: (Failure) -> Void) -> Result {
		switch self {
		case .failure(let value):
			clousre(value) 
		default: 
			break
	}
}


- Modality : 어떤 환경을 많이 깰 때!

- Navigation : 흘려가는 순차적인 

- tag 많이 안쓴다. -> 중복이 가능해서 유니크를 보장 안한다.
	- 태그에 대해 명시 해줘야함.


// 두개를 꼭 분리해야 한다.
@IBAction func orderJuice(_ sender: UIButton) {

-> 
@IBAction func JuiceButtonDidtapped(_ sender: UIButton) {
	// Bussiness Login
	orderJuice() 
}
	
func orderJuice() {
	
}

func updateUI()
func updateText()


func check ->> Bool?일거 같다. 

func handleSuccess(_ value: T)
func handleError(_ error: Error) 

show/display/hidden는 isHidden 속성을 다루는 것처럼 읽힙니다. (visibility다루는 느낌)

present / push -> Routing 화면의 이동 
1. route 
2. present

---
Extension에서 비지니스 로직이 들어가면 공통 로직이 아니게 되므로 쓰면 안된다. 
Util에 비지니스로직을 넣지말고 설정할수 있도록 바꿔야함.
---

func present(with storyboardIdentifier: String) 

func a(with param: String)

fruitStore는 지운다. 


tag 안쓰고

extension OrderViewController {
	func juiceType(for button: UIButton) -> JuiceType {
	 switch button {
	 
	 }
	}
}
JuiceType.localeKorean 
koreanTypec
-> string file 

extension swift


instantiate(from: stroyboard: String = "Main", bundle: Bundle?  = nil

Self.self
Factory Method 
---> make()
신경 쓰는걸 줄일수 있다. 
