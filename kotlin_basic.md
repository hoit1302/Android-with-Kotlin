# 코틀린 사용을 위한 기본 문법
`이것이 안드로이드다 with 코틀린, 고돈호 지음` 책의 03장 기반으로 하여 정리하였습니다.

03장 정리

## 01 코딩 준비하기

```kotlin
// 안드로이드 스튜디오에서 제공하는 로그를 통해 출력하기
Log.d("BasicSyntax", "로그를 출력합니다. method = Log.d")
// 태그(로그 검색용), 로그 내용
```   

로그(Log): 코드의 흐름을 파악하기 위해 앱 외부에 출력하는 정보

로그캣(Logcat): 출력되는 로그를 모아 보는 도구.

### 로그 함수의 종류

|   함수    |의미| 내용               |
|:---:|:---:|:-----------------|
| Log.v() |verbose| 상세한 로그 내용        |
| Log.d() |debug| 개발에 필요한 내용       |
| Log.i() |information| 정보성의 일반적 메세지     |
| Log.w() |warning| 에러는 아니지만 경고서 메세지 |
| Log.e() |error| 에러 메세지           |

## 02 변수와 상수

### 변수 var

값이 입력되는 순간 해당 값의 형태(문자 숫자, 불린 등)으로 변수의 타입이 결정된다.
```kotlin
var myName = "박주은"

var myAge: Int
myAge = 20
```

### 데이터 타입

Double, Float, Long, Int, Short, Byte, Char, String, Boolean

### 상수 val

```kotlin
val PI = 3.141592F
val = myRoomArea = 10 * 10 * PI
```

### 네이밍 컨벤션

- 클래스명: Camel case, 첫 글자 대문자로
  - `MainActivity`
- 함수명과 변수명: Camel case, 첫 글자 소문자로
  - `fun onCreateActivity()`
  - `var intValue: Int`
- 상수명: 모두 대문자
  - `val HOW_ARE_YOU: String = "어떻게 지내?"`
- 들여쓰기 (Indent)
  - 주로 공백 4칸으로 하는데, 책의 저서는 `탭` 사용을 권장 

## 03 조건문
          
### 조건문 if

상식적으로 아는 if문과 같음.
```kotlin
// 변수에 직접 if문 사용 가능
// ex 1
var bigger = if (a > b) a else b

// ex 2
var eraOfRyu = 2.32
var eraOfDegrom = 2.43
val era = if (eraOfRyu < eraOfDegrom) {
    Log.d("MLB_Result", "2019 류현진이 디그롬을 이겼습니다.")
    eraOfRyu
} else {
    Log.d("MLB_Result", "2019 디그롬이 류현진을 이겼습니다.")
    eraOfDegrom
}
Log.d("MLB_Result", "2019 MLB에서 가장 높은 ERA는 ${era}입니다")
```
### 조건문 when
```kotlin
// 일반적인 when의 사용법
var now = 9
when (now) {
    8 -> {
        Log.d("when", "현재 시간은 8시 입니다")
    }
    9, 10 -> {
        Log.d("when", "현재 시간은 9시 또는 10시 입니다")
    }
    else -> { // 위의 모든 조건에 맞지 않으면 else 다음 코드가 실행된다.
        Log.d("when", "지금은 8시 ~ 10시가 아닙니다")
    }
}

// in 을 사용해서 범위를 비교할 수도 있다. 처리코드가 한줄이면 중괄호 생략가능
var ageOfMichael = 19
when (ageOfMichael) {
    in 10..19 -> Log.d("when", "마이클은 10대입니다")
    !in 10..19 -> Log.d("when", "마이클은 10대가 아닙니다")
    else -> Log.d("when", "마이클의 나이를 알 수 없습니다")
}

// 인자가 없이 if처럼 사용할 수도 있다.
var currentTile = 6
when  {
    currentTile == 5 -> {
        Log.d("when", "현재 시간은 5시 입니다")
    }
    currentTile > 5 -> {
        Log.d("when", "현재 시간은 5시가 넘었습니다")
    }
    else -> {
        Log.d("when", "현재 시간은 5시 이전입니다")
    }
}
```
### if문과 when문은 언제 사용할까?

연도 데이터와 같이 범위가 넓고 값을 특정할 수 없는 경우 -> if문

요일 데이터와 같이 7개로 범위가 제한되고 값도 특정할 수 있는 경우 -> when -> 코드가 쉽게 읽힘.

## 04 배열과 컬렉션

### 배열

```kotlin
// 1. 기본타입 배열 선언하기 - 각 기본타입별로 10개의 빈 공간이 할당된다
var students = IntArray(10)
var longArray = LongArray(10)
var CharArray = CharArray(10)
var FloatArray = FloatArray(10)
var DoubleArray = DoubleArray(10)
// arrayOf를 사용하면 선언과 동시에 값을 입력할 수 있다
var intArray = intArrayOf(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)
// intArray 변수에는 1 부터 10까지의 값이 각각의 배열공간에 저장되어 있다

// 2. 문자열타입 배열 선언하기
var stringArray = Array(10, {item->""})
// arrayOf 함수로 값을 직접 입력해서 배열을 생성할 수 있다
var dayArray = arrayOf("MON","TUE","WED","THU","FRI","SAT","SUN")

// 3. 앞에서 선언한한 studens 변수에 값 넣기
// 가. 대괄호를 사용하는 방법
students[0] = 90
students[1] = 91
students[2] = 92
students[3] = 93
students[4] = 94
// 나. set 함수를 사용하는 방법
students.set(5, 95)
students.set(6, 96)
students.set(7, 97)
students.set(8, 98)
students.set(9, 99)

// 4. 값 변경해 보기
intArray[6] = 137    // 6번 인덱스인 7번째 값 7이 137로 변경된다
intArray.set(9, 200) // 9번 인덱스인 10번째 값 8이 200으로 변경된다

// 5. 배열 값 사용하기
var seventhValue = intArray[6]
Log.d("Array","8번째 intArray의 값은 ${seventhValue}입니다")
var tenthValue = intArray.get(9)
Log.d("Array","10번째 intArray의 값은 ${tenthValue}입니다")

Log.d("Array","1번째 dayArray 값은 ${dayArray[0]}입니다")
Log.d("Array","6번째 dayArray 값은 ${dayArray.get(5)}입니다")
```
### 컬렉션

**List**
``` kotlin
// 1. 값으로 컬렉션 생성하기
var mutableList = mutableListOf("MON","TUE","WED")
// 값 추가하기
mutableList.add("THU")
// 값 꺼내기
Log.d("Collection","mutableList의 첫 번째 값은 ${mutableList.get(0)}입니다")
Log.d("Collection","mutableList의 두 번째 값은 ${mutableList.get(1)}입니다")
// 값 개수 가져오기
Log.d("Collection","mutableList의 크기는 ${mutableList.size}입니다")

// 2. 빈 컬렉션 생성하기
var stringList = mutableListOf<String>() // 문자열로 된 빈 컬렉션 생성
// 값 추가하기
stringList.add("월")
stringList.add("화")
stringList.add("수")
// 값 변경하기
stringList.set(1, "날짜 변경")
// 사용
Log.d("Collection","stringList에 입력된 두 번째 값은 ${stringList.get(1)}입니다")
// 삭제
stringList.removeAt(1) // 두 번째 값이 삭제된다.
Log.d("Collection","stringList에 입력된 두 번째 값은 ${stringList.get(1)}입니다")
```
**set**
```kotlin
// 1. 셋 생성하고 값 추가하기
var set = mutableSetOf<String>()
set.add("JAN")
set.add("FEB")
set.add("MAR")
set.add("JAN") // 동일한 값은 입력되지 않는다.

// 2. 전체 데이터 출력해보기
Log.d("Collection", "Set 전체출력 = ${set}")

// 3. 특정 값 삭제하기
set.remove("FEB")
Log.d("Collection", "Set 전체출력 = ${set}")
```

**map**
```kotlin
// 1. 맵 생성하기
var map = mutableMapOf<String, String>()

// 2. 값 넣기
map.put("키1","값2")
map.put("키2","값2")
map.put("키3","값3")

// 3. 값 사용하기
var variable = map.get("키2")
Log.d("Collection", "키2의 값은 ${variable}입니다")

// 4. 값 수정하기
map.put("키2","두 번째 값 수정")
Log.d("Collection", "키2의 값은 ${map.get("키2")}입니다")

// 5. 값 삭제하기
map.remove("키2")
// 5.1 없는 값을 불러오면 null값이 출력된다
Log.d("Collection", "키2의 값은 ${map.get("키2")}입니다")
```

### Immutagble Collection
크기와 값을 변경할 수 없는 컬렉션
- 최초에 입력된 값만을 사용
- 기존 컬렉션에서 mutable 이라는 접두어를 제거하여 사용
- 상수로 선언하고 상수명을 대문자로 표기하는 것을 추천
```kotlin
// 생성
val DAY_LIST = listOf("월", "화", "수", "목", "금", "토", "일")
// 사용
Log.d("Collection","리스트의 2번째 값은 ${DAY_LIST.get(1)} 입니다")
```
    

## 05 반복문

### for 반복문
```kotlin
 // 1. 일반적인 반복문 사용으로 10번 반복하기, 특이점: 10까지 모두!
for(index in 1..10){
    Log.d("For", "현재 숫자는 ${index}")
}

// 2. until: 마지막 숫자 제외하기
var array = arrayOf("JAN","FEB","MAR","APR","MAY","JUN")
for ( index in 0 until array.size ) {
    Log.d("For", "현재 월은 ${array.get(index)} 입니다")
}

// 3. step: 건너뛰기
for(index in 0..10 step 3){
    Log.d("For", "건너뛰기 : ${index}") // 0, 3, 6, 9
}

// 4. downTo: 감소시키기
for(index in 10 downTo 0) {
    Log.d("For", "감소시키기 : ${index}")
}

// 4.1 건너뛰면서 감소시키기
for(index in 10 downTo 0 step 3) {
    Log.d("For", "건너뀌면서 감소시키기 : ${index}") // 10, 7, 4, 1
}

// 5.1 배열, 컬렉션 사용하기
for(month in array) {
    Log.d("for", "현재 월은 ${month} 입니다")
}
```

### while 반복문

```kotlin
// 1. 일반적인 while 사용하기
var current = 1
val until = 12
while( current < until ) {
    Log.d("while", "현재값은 ${current} 입니다")
    // current를 1씩 증가시켜서 11번 반복한 후 while문을 빠져 나간다.
    current = current + 1
}

// 2. do~while 사용하기
var game = 1
val match = 6
do {
    Log.d("while", "${game}게임 이겼습니다 우승까지 ${match-game}게임 남았습니다")
    game += 1
} while( game < match )

// 3. while vs do~while
// while 테스트
game = 6
while( game < match ) {
    Log.d("while", "while 테스트 입니다")
    game += 1
}
// do ~ while 테스트
game = 6
do {
    Log.d("while", "do ~ while 테스트 입니다.")
    game += 1
} while( game < match )

// 4. break 반복문 탈출하기
for(index in 1..10){
    Log.d("while", "break > 현재 index 는 $index 입니다")
    if(index > 5) { // index 가 5보다 크면 break 명령어로 현재 반복문을 벗어난다.
        break       // 따라서 Log 는 6까지만 출력된다.
    }
}

// 5. continue 다음 반복문으로
for(except in 1..10){
    // except가 3보다 크고 8보다 작으면 continue 명령으로 로그를  찍지 않고 for문의 처음으로 jump 한다.
    if(except > 3 && except < 8){
        continue
    }
    // 따라서 4,5,6,7은 출력되지 않는다.
    Log.d("while", "continue > 현재 index 는 $except 입니다")
}

// 0. 무한루프 테스트
// 무한루프에 빠지는 while 문 - 실행 후 멈추기 위해서는 우측 상단에 있는 빨간색 사각형 아이콘(Stop)을 클릭하면 된다.
var a = 1
while ( a == 1 ) {
    Log.d("While", "조건을 만족하면 여기를 출력하세요!")
}
```

## 06 함수

### 함수의 정의

- 반환값과 입력값이 있는 함수의 정의
- 반환값이 없는 함수의 정의
- 입력값 없이 반환값만 있는 함수의 정의

### 함수의 사용
- 반환값과 입력값이 있는 함수의 호출
- 반환값이 없는 함수의 호출
- 입력값이 없는 함수의 호출

### 함수 파라미터의 정의

참고: 코틀린에서의 함수 파라미터는 모두 상수 키워드 val이 생략된 형태
- 파라미터의 기본값 정의와 호출

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // 4. 반환값이 있는 함수 square 사용하기
        var squareResult = square(30)
        Log.d("fun", "30의 제곱은은 ${squareResult}입니다")

        // 5. 반환값이 없는 함수는 그냥 실행한다
        printSum(3,5)

        // 6. 입력값이 없는 함수 사용
        val PI = getPi()
        Log.d("fun", "지름이 10인 원의 둘레는 ${10 * PI}입니다")

        // 7. 기본값이 있는 함수 사용
        newFunction("Hello")

        // 8. 파라미터 이름을 직접 지정하기
        newFunction("Michael", weight=67.5)

        // 문제풀이 호출
        Log.d("fun", "5와7을 더한 결과값은 ${plus(5, 7)}입니다")
        Log.d("fun", "0부터 100을 모두 더한 결과값은 ${sum(100)}입니다")
        printString("문자열")
    }
    // 1. 반환값이 있는 함수
    fun square(x: Int): Int {
        return x * x  // <- square 함수는 입력받은 값에 2를 곱해서 반환한다.
    }
    // 2. 반환값이 없는 함수
    fun printSum(x: Int, y: Int) {
        Log.d("fun", "x + y = ${x+y}")
    }
    // 3. 입력값 없이 반환값만 있는 함수
    fun getPi(): Double {
        return 3.14
    }
    // 7. 기본값을 갖는 함수
    fun newFunction(name:String, age:Int = 29, weight:Double = 65.5) {
        Log.d("fun","name의 값은 ${name}입니다")
        Log.d("fun","age의 값은 ${age}입니다")
        Log.d("fun","weight의 값은 ${weight}입니다")
    }
}
```

## 07 클래스와 설계

### 클래스의 기본 구조
### 클래스의 생성
- 프라이머리 생성자
- 세컨더리 생성자: `constructor` 키워드를 사용해 함수처럼 작성
### 클래스의 사용
- companion object 코드 블럭을 사용하여 클래스를 인스턴스화 하지 않고 사용할 수 있음.
### 데이터 클래스
- 간단한 값 저장 용도의 데이터 클래스 제공
- 생성자와 다르게 파라미터 앞에 var 또는 val을 명시해주어 변수인지 상수인지 구분해야함

```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        ...

        // 1. 생성자가 없는 클래스 호출
        Kotlin()

        // 2. 클래스의 생성자 사용
        KotlinOne("안녕")
        KotlinTwo("안녕")

        // 3. 클래스의 프로퍼티와 메서드 사용하기
        var kotlin = KotlinThree()
        // 메서드 먼저 출력하기
        kotlin.printOne()
        // 프로퍼티에 값 넣고 출력하기
        kotlin.one = "Hello"
        kotlin.printOne()

        // 4. companion object 사용하기 - 자세히보면 첫 글자가 대문자다
        // 클래스를 인스턴스화 하지 않고 사용하기
        KotlinFour.printOne( )
        KotlinFour.one = "Hello"
        KotlinFour.printOne( )

        // 5. 데이터 클래스 사용하기
        var dataUser = DataUser("Michael",21)
        var newUser = dataUser.copy() // 복사 지원
        newUser.name = "Jane"
        Log.d("class","원본 dataUser는 ${dataUser.toString()}")
        Log.d("class","복사된 newUser는 ${newUser.toString()}")

    }
}
// 파라미터가 없는 클래스
class Kotlin() {
    init {
        Log.d("class","Kotlin 클래스 생성됨")
    }
}
// 파라미터가 있는 프라이머리 생성자
class KotlinOne(value: String) {
    Log.d("class","KotlinTwo : 파라미터 값은 ${value}입니다")
}
// 파라미터가 있는 세컨더리 생성자
class KotlinTwo {
    constructor (value: String) {
        Log.d("class","KotlinTwo : 파라미터 값은 ${value}입니다")
    }
}
// 프로퍼티와 메서드가 있는 클래스
class KotlinThree {
    var one:String = "None"
    fun printOne( ) {
        Log.d("class","KotlinThree : one에 입력된 값은 ${one}입니다")
    }
}
// 스테틱 멤버를 갖는 클래스
class KotlinFour {
    companion object {
        var one: String = "None"
        fun printOne() {
            Log.d("class", "KotlinFour : one에 입력된 값은 ${one}입니다")
        }
    }
}
// 데이터 클래스
data class DataUser(var name: String, var age: Int)
```

### 클래스의 상속
부모 클래스 앞에 open 키워드를 붙여주어야만 상속이 가능
### 프로퍼티와 메서드의 재정의: override
override를 위해선 부모 클래스의 함수와 프로퍼티 앞에 open 키워드를 붙여주어야 함.
### extensions
이미 만들어져 있는 클래스를 메서드를 추가하여 사용할 수 있음.
```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        ...

        // 1. 부모 클래스 직접 호출하기
        var parent = Parent()
        parent.sayHello()
        // 1. 자식 클래스 호출해서 사용하기
        var child = Child()
        child.myHello()

        testStringExtension()
    }
    
    // String 익스텐션 테스트 하기
    fun testStringExtension() {
        var original = "Hello"
        var added = " Guys~"
        // plus 함수를 사용해서 문자열을 더할 수 있다.
        Log.d("Extension"," added를 더한값은 ${original.plus(added)}입니다")
    }
}

// 상속 연습
open class Parent {
    var hello:String = "안녕하세요"
    fun sayHello() {
        Log.d("inheritance", "${hello}")
    }
}
class Child : Parent() {
    fun myHello() {
        hello = "Hello"
        sayHello( )
    }
}

// 메서드 오버라이드 연습
open class BaseClass {
    open fun opened() {

    }
    fun notOpened() {

    }
}
class ChildClass: BaseClass() {
    override fun opened() {

    }

//    override fun notOpened() { // 오버라이드 되지 않고 에러가 발생한다.
//    }
}

// 프로퍼티 오버라이드 연습
open class BaseClass2 {
    open var opened: String = "I am"
}
class ChildClass2: BaseClass2() {
    override var opened: String = "You are"
}
fun String.plus(word:String): String {
    return this + word
}
```

### 패키지
### 추상화
### 인터페이스
### 접근 제한자
### 제네릭
```kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        // 접근제한자 테스트
        var child = Child()
        child.callVariables()
        // 부모클래스 직접 호출해보기
        var parent = Parent()
        Log.d("Visibility", "Parent : protected 변수의 값은 ${parent.defaultVal}")
        Log.d("Visibility", "Parent : protected 변수의 값은 ${parent.internalVal}")
    }
}
// 추상 클래스 설계
abstract class Animal {
    fun walk() {
        Log.d("abstract", "걷습니다")
    }
    abstract fun move()
}
// 구현
class Bird : Animal() {
    override fun move() {
        Log.d("abstract", "날아서 이동합니다")
    }
}
// 인터페이스 설계
interface InterfaceKotlin {
    var variable : String
    fun get()
    fun set()
}
// 구현
class KotlinImpl : InterfaceKotlin {
    override var variable: String = "init value"
    override fun get() {
        // 코드 구현
    }
    override  fun set() {
        // 코드 구현
    }
}
// 접근제한자 테스트를 위한 부모 클래스
open class Parent {
    private val privateVal = 1
    protected open val protectedVal = 2
    internal val internalVal = 3
    val defaultVal = 4
}
// 자식 클래스
class Child : Parent() {
    fun callVariables() {
        // privateVal은 호출이 안된다
        Log.d("Visibility", "Child : protected 변수의 값은 ${protectedVal}")
        Log.d("Visibility", "Child : internal 변수의 값은 ${internalVal}")
        Log.d("Visibility", "Child : 기본제한자 변수 defaultVal의 값은 ${defaultVal}")
    }
}
```

## 08 null 값에 대한 안정적인 처리 : Null Safety

코틀린은 null 값 처리에 많은 공을 들인 언어.

### Nullable(null 값 허용하기) `?`

- 코틀린에서 지정하는 기본 변수는 모두 null이 입력되지 않음
- null을 입력하기 위해서는 변수를 선언할 때 타입 뒤에 `?`를 입력
- 변수, 함수 파라미터, 함수의 리턴 타입에 사용할 수 있음.
- 함수 파라미터가 null을 허용할 경우는 코드 내부에서 해당 파라미터에 대해 null 체크를 먼저 해야만 사용할 수 있음!

### Safe call(안전한 호출) `?.`

- null 체크를 좀 더 간결하게 할 수 있음.
- Nullable인 변수 다음에 ?.를 사용하면 해당 변수가 null일 경우 ?. 다음 메서드나 프로퍼티를 호출하지 않고 바로 null을 반환함.
- `var result = 변수?.length`
- `var result = 변수?.프로퍼티?.something`

### Elvis operator(Null 값 대체하기) `?:`

- 원본 변수가 null일 때 넘겨줄 기본값 설정
- `var result = 변수?:0`
- `var result = 변수?.프로퍼티?:0`
``` kotlin
class MainActivity : AppCompatActivity() {

    override fun onCreate(savedInstanceState: Bundle?) {

        ...

        var nullable:String? = null
        var size = nullable?.length?:33
        Log.d("Nullable","문자열의 길이 = $size")

        nullParameter("새로운 문자열")

        val nValue = nullReturn()
        Log.d("Nullable", "${nValue}")

        Log.d("Null Safety", "length of null = ${testSafeCall(null)}")
        Log.d("Null Safety", "length of abc = ${testSafeCall("abc")}")

        Log.d("Null Safety", "length of null by elvis = ${testElvis("")}")
    }

    fun nullParameter(str:String?) {
        if (str != null) {
            var length2 = str.length
            Log.d("Null Safey","문자열 길이=$length2")
        }
        Log.d("Null Safey","문자열이 입력되지 않았습니다.")
    }

    fun nullReturn() : String? {
        return null
    }

    fun testSafeCall(str:String?) : Int? {
        // str이 null이면 length를 체크하지 않고 null을 반환합니다.
        var resultNull:Int? = str?.length
        return resultNull
    }

    fun testElvis(str:String?) : Int {
        // length 오른쪽에 ?: (콜론)을 사용하면 null일 경우 ?: 오른쪽의 값이 반환됩니다.
        var resultNonNull:Int = str?.length?:0
        return resultNonNull
    }
}
```