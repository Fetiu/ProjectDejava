# Dejava

> - 함수형 언어.
>
> - 트랜스파일러.
>
> - C와의 바인딩, 글루코드 만들기. 다른 언어로 래핑이 가능한 언어. 컴파일 이전 작업이 되는느낌.
>
> - 입력과 출력을 확실히. 입력은 ()로 묶인 값이며, 출력은 바로 그이후에 오는 =임 
>
> - 입력과 동등히 하다는 다소 유사성이 정리되지 않은 점들이있음. 
>
> - if while for등 를 제외한 모든 선언자는 =를 조건판단이 아닌 대입(또는 동등하게 하는)으로 생각함.
>
> - 암시적으로 일어나는 작업이 없도록. 있어봤자 조건 판단 정도?
>
> - all that matters is name. every thing should be named.
>
> - 구상만 하지말고, 실제로코딩을 해봐. 얼마나 오래걸리고 얼마나 편한지. 파이썬 정도는 되나? 
>
> - 특수문자는 최대한 적게. 이걸 쓰면 명확하고 깔끔한 표현이 가능해지는게 아니면 삼가하기. 특수문자를 남발해서 난잡하게 만들지는 말지. 한구문에 연속으로 특수문자 두개를 사용하지 않도록 간결하게.
>
>    

< 와 >를 최초에는 입력과 출력으로 생각하려 했으나, 기존언어와의 유사성을 해치고 난잡한 문법을 만들어낼 수 있기때문에, 해당 문자는 입력과 출력으로 사용하지 않고(?), 입력을 위해 = 작업의 앞에 선언자를 붙이는 방식으로 입출력이라는걸 명확히 하도록함.

입력은 ()로 묶인 곳. 혹은 =만 있을때? (선언자를 정리해야될듯. gen에 한해서만 출력을 입력으로 생각? 아니면 숫자나 데이터가 ()같은 입력없이 출력을 돌려주는 함수?로 정의?)

출력은 보통 데이터이다. 

그리고 데이터는 단순히 네임심볼로만 표현되거나, {}로 묶어서 표현된다.

함수의 기능적인 구현또한 {}로 묶여서 표현된다.



>  **컴퓨터의 모든것은 입력과 출력으로 이루어진다.**

함수형 언어는 반드시 등장했어야하는 언어다. 다소 암시적이지만 묵인되고 그저 사용해왔던 우리의 모든 언어들은 이제 함수형 패러다임으로 전환되고있다.



이 언어의 목적은 함수형프로그래밍을 염두에 두고, 각각의 명령어와 키워드들의 기능을 명확히하면서

기존 언어들과의 유사성을 해치지 않도록 하는것이 목적이다.



그리고 확실한 개념을 위해

 데이터/변수명에 **네임 심볼** / **라벨** 이라 불리는 개념을 도입하고, :라는 특수문자로 해당 네임 심볼의 타입을 지정하는 식으로 했다.

```python
import stdio

fn main(){
    do stdio.printf('Hello World');
}

--
do main()
```

void형을 리턴하는 메인함수.

함수호출과

대입같은 작업을 명확하게 보여주기 위한부분.



Dejava에서는 암시적으로 일어나는 작업은 없다.

모든 작업들은 각각의 키워드들로 제어된다.

크게, 키워드를 선언해주는 def와,(키워드도 곧 함수다, 하지만 ()와 =로써 입력이 만들어지지 않을뿐이다.입력은 공백 이후에 오는 모든것이고, 그것을 받아 컴퓨터 시스템에 전달한다. Q. def가 전달하는 자료형은 뭘까.)

## 예약된 특수문자

`:` 타입 형식을 지정한다. 보통 선행되는 라벨의 데이터 타입을 정의한다. ex) do a:string

형식을 지정하는 위치는 **라벨 바로 옆**/ **표현식의 제일 마지막** 으로 제한된다.

```python	
do a:string = "hello world"
do a = "hello wolrd" : string
def main:func(argc:int, )
```

`@` 위치 지정, 접근 지정자. 변수가 할당될 위치를 지정한다.(가독성만?) 보통은 네임스페이스를 적어준다. has

`=` 단독으로 수식으로 쓰일 경우엔 같은지를 판단 그리고 bool을 반환하는 명령으로 동작. 

하지만, 명령어와 조합되는 경우, 동등하게 만들어줌. 상수에 대해서는 동작안함.

`(` 함수에 넣을 입력을 지정한다. '')''가 (다른 특수문자가?)오기전까지의 모든것을 입력으로 판단한다

`)` 함수에서 반환될 타입(형)을 지정한다.

`{}` 네임스페이스 생성, 자료형 포매팅, 함수내용 구현 등, 메모리 할당 구조를 모사 하는데 이용되는 특수문자

`<` `()` 입력을 의미하는 부분. 함수나 클래스에 주는 입력이 전달된다.

`>` 단독 사용시 대소비교.

선언자와 함께 사용시 출력. 하지만, 이 지정자가 없더라도, 모든 데이터들은 기본적으로 출력을 하고있기때문에 잘안쓸 것이다.

그리고 무엇보다 `)`를 출력으로 생각하는것이 오히려 편할수도 있다.

확실한건, >를 쓸경우, 그것의 오른쪽에 입력을 받을 변수나 자료형이 와야한다.

`[]` 배열을 위해 예약되어있다.

`&` 주소연산에 사용된다.

- [ ] 주소 접근연산은 아직 정의되지않았다. *는 아닐지도...`->`는 어떨지

## 자료형 Data Type

자료형은 Data의 형태이다. 자료형 키워드 그 자체로는 명령이 될 수 없고, 자료를 만들어내고 제어하기 위해서는 반드시 **명령어**와 함께 쓰여야한다. `do` `let` `def` 등이 주로 쓰인다.

변수의 선언에서 

```scala
do int //메모리상에 int를 할당한다. 하지만, 호출이 불가능한 이름이다.(함수호출을 위한 메커니즘)

do a:int//메모리상에 int를 할당하고, a라고 이름 붙인다.
do int as a//위와 동일

let a:string //let을 통한 형식 재지정은 불가능.
let b = string{a} //let을 통해 할수있는건, a를 string형태로 포매팅하는것.

do c="hello world":string
do d:string="hello world"
//위 두 표현식의 기능은 동일.
```

특성을 나타내게 해주는 `:`와 함께 주로 사용. 이때 `:자료형`은 반드시 데이터명의 **오른쪽**에 위치해야한다.

여러 자료형을 명기할경우(int array같이), 호환가능한



Dejava의 모든 자료형은 아래로부터 기원된다. 그리고 후술할 def에 의해서 상속된다.

`type` 

data를 나타내는 다양한 키워드들이 있다.

`int` `string` `byte` ...추가바람

그리고 모든 자료형을 대표하는 키워드 `any`가 있다.

``` python	
for a:any in array[1,2,"three",4] {
    
}
//for이 만들어내는건 아무래도 인스턴스다. 자료형은 아니다. 그러니
```

위와같이 다양한 내용이 들어있는 집합체의 내용을 참조할 때의 자료형은 any가 된다.

하지만, any는 



Dejava에는 크게 네개의 특수 자료형이 있다. 일반적으로 쓰이는 자료형이다

 `array` `struct` `func`  `class`

array는 `[]` 라는 표현으로 대체가능하다. def array: []

- [ ] array의 크기의 동적 생성에 대해서는 아직 정리되지않았다. 추가바람.

- [ ] 리스트를 만들수있게해야할텐데. 자동으로 힙영역에 만들도록할까







### Type Formatting 자료형 포매팅

그리고 모든 자료 타입은 {}를 통해 묶어서 표현할 수 있다. ->이를 포맷팅이라고 한다.

자료형자체에서 제공되는 내부 메소드?로써 {} 사이에 입력되는 내용이 왼쪽에 명기한 데이터 타입으로 변환된다.

```go
do struct {
    a: int = 4,
    b: byte = 0xFF,
    c: string ="hello"
}as data //임시 구조체 생성.


do data: struct {}

do a = string{ data.a, data.b, data.c}

do func{}


```

포맷팅에 있어서 생략이 가능하다. 포맷팅이 될때에 {}왼쪽에 자료형이 명기되어있지 않아도, 표현식의 형태를 통해서 어떤 데이터인지 알수 있는 경우에는 타입 추론을 통해 컴파일 단계에서 적절한 키워드가 추가된다. 

일단 any라는 자료형으로 포맷팅된다고 생각하면좋다.

- [ ] 자료형과 동일한 이름으로 메소드를 만들수 있을까?..파이썬도 안그랬는데..



자료형뒤에 {}가 오는 경우 포매팅이라고 생각하면 좋고,

자료형 뒤에 =가 오면 이미 포맷된 데이터를 넣는것이라고 생각하면된다.



배열만 예외적으로 포맷팅에 {}대신 []를 사용한다.



#### 

## 명령어

종종 자료형으로 예약된 키워드와 철자와 기능이 비슷한 키워드들이 있을것이다.

하지만 자료형은 최대한 철자를 유지하고, 명령어는 좀더 단축시킨다. 

선언된 키워드들 정리

#### first level commands

`import` 라이브러리를 불러온다

`def`  define 새로운 키워드(타입?)를 정의한다.

 `do` data operation. 생략 가능하다. 명령어 없는 모든 표현은 앞에 이것이 붙는다고 생각하면된다.

 `let` 허락하다. 다음에 오는 작업을 허용한다.

 `if`

 `else`

 `while` 

`return` 반환할 값을 지정한다. 반환타입의 지정은:

`in` 집합체의 내용을 불러온다.

```python
do 
```



#### second level commands

`fn` 함수를 만들어낸다. def func as와  와 동의어.

즉, def

`as` 타입지정을 앞에서 할수 있게 한다. 라벨을 타입 지정 뒤에 쓸 수 있게 만들어준다. 

'' : ''를 사용한 형식 지정에서 라벨을 제일 처음에 적지만, as를 사용할 경우 라벨이 뒤에오게 할 수 있다.

```rust
a:int
int as a
```

위와 아래의 표현은 동치이다. 타언어를 쓰다온 사람들에게도 Dejava의 어순이 익숙하도록 만들어 줄 수 있다.

혹은 여러 속성 지정이 섞여 알아보기 힘들 경우에도 가독성을 높여주는 도구가 될 수 있다.

순서에 유의하자

`:`사용시에는`이름 : 타입`순이고, `as`사용시에는`타입 as 이름`순이다.



> branch column-> 단순히 보면 이 언어를 더 어렵게 만드는 요소같겠지만, 
>
> 다른 언어에서는 표현이 길어지고 장황해질수록 자료형과 명령어, 변수명 등이 혼동되기 시작할때가 많다
>
> ```
> typedef public const uint8_t bool;
> ```
>
> 암시적으로 그 형식 지정이 쓰여진 위치로만 그 속성을 유추할 수 있기에 더 어려워 지는 것이다.
>
> dejava는 그 암시적인 표현을 좀더 명시적으로 만들기 위한 방법을 만들어보았다.
>
> 형식 지정의 위치를 자유롭게 하는 대신, 앞에 특수문자를 붙여 보도록했다.
>
> 마치 우리가 변수에 대입을 하기 전에는 =라는 특수문자를 적어준다는 느낌으로
>
> `a:int` a의 속성은 int다. 위치는 @으로. 동적할당도 new말고, @heap으로 하기. 암시적이지 않도록.
>
> 어떤 라이브러리로부터 함수를 가져왔는지도, 라이브러리를 네임스페이스로 생각한다면,
>
> do gethostnamebyaddr(addr) @inet
>
> 같은 표현도 가능해질 것이다. inet에서 이걸 수행하겠다.혹은
>
> do system('ls -al') @unistd
>
> 유닉스 라이브러리에서 do system을 하겠다.
>
> inet has gethostnamebyaddr(addr) //이건 좀 이상하다.
>
> 그냥 여기에선 네임스페이스.이 나을듯도한데. has같은
>
> 음. from inet같은건 어때. import
>
> "물론 inet.gethostnamebyaddr(addr)같은 표현도 가능하다."라고 하기엔, 문제가 많다.
>
> 객체인지, 라이브러린지 함수인지 모호함을 줄 수 있기 때문에, 객체가 아닌 네임 스페이스(ex.모듈)에 한해서
>
> .이 아니라 @만을 사용하도록 강제 하도록 하겠다. 그러므로 앞으로 이런표현은 허용되지 않는다.
>
> ```python
> import turtle
> turtle.Turtle().backward(100)
> ```
>
> 대신 이렇게 사용해야한다
>
> ```python
> import turtle
> 
> Turtle().backward(100) @turtle
> Turtle@turtle ().backward(100) 
> #속성지정은 적절한 문자가 붙어있다면 어디서든 가능-하지만 끝을 권장.
> #다른 지정자를 만나면 속성에 None을 넣고 종료 - 혹은 타입 유추.
> turtle has Turtle().backward(100)
> 
> @turtle
> Turtle().backward(100)
> 
> turtle::Turtle().backward(100) //허용?
> 
> #혹은 접근 지정을 생략하고
> Turtle().backward(100) #가장 가독성이 좋은 방법.
> 
> ```
>
>
>
>



`has`  접근 지정을 앞에서 할 수 있게 해준다. 좋은점은, 다른 접근 지정자가 나오기 전까지(? 혹은 인덴트로 구분된 블록) 모든 변수를 같은 네임 스페이스로 묶어둘 수 있다. has없이 {}로도 네임 스페이스 지정이 가능하다.

```
int as num @public
public has int as num
private has
	int as pnum;
	string as name;
public{
    int as pnum;
    name: string;
}
```



* 네임스페이스 지정방법 세가지 @, has, {}.

def as = reversed :

이건 let as = : 아냐 이건 데





#### 이외의 명령어

`const` `static`



### do

자료형으로부터 실제 데이터를 생성하는 키워드. 이걸 사용하는 시점에 메모리에 데이터가 할당되고, 그곳에 변수명이 라벨링된다. (call은 어때.. 너무긴가. or label / lab  var. do.그래도 익숙한 명령어. val var흠..)

```c
do a = 4; //a=4를 수행.
do b; //b라는 라벨 생성. 변수값은 Null. 널포인터 변수의 사용시점에 자료형이 결정됨.
do a = 8; //불가능. a는 8이 아님. 변수의 사용시 let을 사용해야함.
```

함수 호출 또한 같은 명령을 사용한다. (함수 선언은 자료형과 동등한 레벨로 취급한다. 상기했듯, 자료형 키워드는 스탠드얼론으로 동작하는 명령어가 아니다. )

```c
do myfuction(args);
//do myfunction(args):func가 아니다. 함수는 자체가 자료형으로,

//변수에 함수를 담을수 있는가

do c = myfunction(args); //this is honking great. 변수 선언과 대입을 동시에 함!

do print(c); //we can now see result!

println(c); //현재로써는 불가능하다. 충돌되지 않는다는 보장이 생긴다면 제거하도록하자.
```

do는 오로지 변수 선언만을 위한건가? 그러면 굳이 이게 명령어로 있어야할 이유가 있는건가?

if에만 =가 초건판단으로 동작하게 하면되는거 아닌가?

ex) 만약 불리언 값을 대입하고 싶다면?  do a = (name = true)

혼동이 오지 않을까? 괄호로 묶는 =에 대해서만 조건판단인걸로?



### let

데이터를 변경하는것을 허용하는 명령. "~라고 하자" 같은 느낌.

사칙 연산 및 부등호 연산자들과 함께 사용한다.  

+-/ * %같은 연산들은 데이터를 변형하여 저장하게 해주고, 

< > =는  

보통 데이터의 내용을 바꾸거나, 형의 변환을 가능하게 한다. 

let 



일반적으로 =와 사용되면, 오른쪽에 있는 데이터와 동등하게 만들어줌

```scala	
//데이터의 할당
a = 4
a:= 4

let a = 4

do a = 4; //a=4를 수행.
do a = 8; //불가능. a는 8이 아님. 변수 재선언.
let a = 8; //가능. a가 8로 변경.

let a + 8; //가능하게 할수있을까?
let a+ = 8; //a에 모드를지정. +,append되는 모드.
let a = a + 8;
let a - 8;
let a = a - 8;

```

let a = 8. let명령은 left value를 입력 모드로, right value를 출력 모드로 열어놓은 것과 같다.





함수형 언어인 점에 관해서 아직 언급하지 않았지만, 

숫자와 계산 식으로로 표현되는  모든 것은 그 자체가 입력이면서 출력인 함수이다. 

모든 데이터는 그자신이 입력이면서출력이다. //confirm필요.

### 

(네임심볼로 표현되는) 



속성 변경도 let으로 허용할것인가? 

fn n(a,b){

​	let a: int

}

이건 형변환의 관점인듯한데...메모리 영역을 넓혀야됨. 새롭게 만드는게 맞음. 동적할당이면 모를까..암시적이 되진 말자.

new string as a = stringfy(a:int) //이런식으로 인자로 넘겨줄때도 이 변수가 원래 뭐였는지 알수 있음.



### def

자료형을 선언한다. (또는 키워드를 선언? 아직 정리되지 않음.)

ex) 

```c 
def pointer: &; //&로 포매팅된 자료형 선언. 
def array: [];
def func: type(any)any{}
```



def에서는 대입 연산을 사용하지 않는다. 정의는 =등호나 assign되는 것이 아니다.

Dejava에서는 새롭게 선언하는 함수 또한 자료형이다. 함수의 선언은 `fn`을 사용하는것이 보통이지만,

이또한 def 통해 가능하다. 아래와 같다. (하지만, 장황하기에 권장하는 방식은 아니다.)

```scala
def main:func (inputs:any) bool {
} //:func지정자는
def func as main (inputs: any) bool {
    
}


```

def

func타입의 선언..

def type as func 타입을 func이라고 정의해라. 라고 해버리는것. 이건 불가능해. func가 앞으로 최상위type이 되버릴테니까.

그것보다는 

def type(any)={any} as func 같은느낌이 좋을듯.()와 =이 필요한 type은 funtion이다.



def main 

## fn

함수를 선언한다.

선언된 함수는 마치 자료형과 같으며, do를 통해 호출된다.

fn은 def func as와 완벽하게 동의어다.

```rust
fn main(int, string) bool{
    
}
```

함수의 선언부는 이렇게 해석된다: 

괄호 이전의 `함수명`에 `( `이후의 매개변수를 대입하고 , `)` 이후에는 반환형을 기입해준다.



즉, 함수의 반환형은 () 이후에 나오는 자료형이다.

반환형은 생략이 가능하다. 함수의 정의 과정에서 명확하게 return을 해주기만 한다면 {}안의 일련의 과정 그 자체를 반환형으로 생각할수 있을 것이니까.

fn name() bool {} 이게 익숙지 않다면 이렇게 생각해라

( 는 input / )output

fn name gets a,b,c returns bool



함수는 **자료형**과 동등한 레벨로 취급하기에 스탠드얼론으로 동작할 수 있는 **명령어**가 아니다. 

`do`를 사용하여, 메모리에 할당되어 실행될 수 있게 된다.

```c
do myfuction(args);
//do myfunction(args):func가 아니다. 함수는 자체가 자료형으로, 특정 자료형을 메모리에

//변수에 함수를 담을수 있는가

do c = myfunction(args); //this is honking great. 변수 선언과 대입을 동시에 함!

do print(c); //we can now see result!

println(c); //현재로써는 불가능하다. 충돌되지 않는다는 보장이 생긴다면 제거하도록하자.
```

함수가 끝나고 난뒤의 반환값은 그 자리에 남지만, 그저 호출만하면 이름이 없는 데이터이기 때문에



퍼블릭함수는 어떻게?

프라이빗함수는 어떻게?

그냥 구역 지정을 할까. 외부 접근가능한 메모리 구역과 불가능한 구역. 네임스페이스 느낌으로.

public{

​	fn main;

​	fn add;

}

private