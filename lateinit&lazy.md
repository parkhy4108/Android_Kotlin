### lateinit 
- 전역변수로 선언부터 하고 초기화는 나중에 하는 것
- 코드를 보면 이해가 쉽다!

```kotlin
class MainActivity : AppCompatActivity() , Contract. View {

    private lateinit var binding : ActivityMainBinding
    private lateinit var presenter: Presenter
    private lateinit var repository: UserDataRepository

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        binding = ActivityMainBinding.inflate(layoutInflater)
        setContentView(binding.root)
```

    MainActivity 클래스 안에 보면 
    =>  private lateinit var binding : ActivityMainBinding
        private lateinit var presenter: Presenter
        private lateinit var repository: UserDataRepository
        
전역변수로 선언을하면 타입을 정해주지만 초기화는 안되어있다.
특징으로는 기본형 primitive type을 사용할 수 없고,
var 선언만 가능하다. 또한 getter와 setter를 정의할 수 없다.
 
 ### lazy 
 lazy는 선언과 동시에 초기화를 해줘야 한다.
 ```kotlin
 lateinit var input : String
 val x : Int by lazy { input.length }
 input = "initialized"
 println(x)
 ```
laze는 val만 가능하다.
위의 코드를 보면 굳이 왜 쓰지? 라고 생각할 수 있는데
만약에 어떤 변수 y 가 변수 x를 가지고 있다고 가정해보자.
그럼 x를 먼저 어딘가에서 가지고 와야 쓸 수가 있으므로
x에 대한 작업을 먼저 마치고 받은 x로 y를 나중에, 늦게 쓰게된다.
이럴때는 lazy로 선언하여 뒤로 미뤄둘수있다.
(약간 callback 과 비슷한건가...??)

### 둘의 차이
       lateinit은 var만 사용하고 lazy는 val만 사용한다.
       var는 변경 가능한 변수이고 val는 불가능하니까
       상황에 맞게 쓰면 되지 않을까??
       
> **lateinit과 lazy는 좀 더 공부해서 알아보자.
