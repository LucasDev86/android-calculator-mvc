## UI 테스트

### 🚀 3단계 - 문자열 계산기

#### 문자열 사칙 연산 계산기 구현

#### 기능 요구 사항

- 사용자가 입력한 문자열 값에 따라 사칙 연산을 수행할 수 있는 계산기를 구현해야 한다.
- 문자열 계산기는 사칙 연산의 계산 우선순위가 아닌 입력 값에 따라 계산 순서가 결정된다.
  즉, 수학에서는 곱셈, 나눗셈이 덧셈, 뺄셈 보다 먼저 계산해야 하지만 이를 무시한다.
- 예를 들어 "2 + 3 * 4 / 2"와 같은 문자열을 입력할 경우 2 + 3 * 4 / 2 실행 결과인 10을 출력해야 한다.

#### 프로그래밍 요구 사항

- 메서드가 너무 많은 일을 하지 않도록 분리하기 위해 노력해 본다.

#### 힌트

##### 테스트할 수 있는 단위로 나누어 구현 목록을 만든다.

- 덧셈
- 뺄셈
- 곱셈
- 나눗셈
- 입력값이 null이거나 빈 공백 문자일 경우 IllegalArgumentException throw
- 사칙연산 기호가 아닌 경우 IllegalArgumentException throw
- 사칙 연산을 모두 포함하는 기능 구현

##### 공백 문자열을 빈 공백 문자로 분리하려면 String 클래스의 split(" ") 메소드를 활용한다. 반복적인 패턴을 찾아 반복문으로 구현한다.

#### JUnit4

##### JUnit4는 테스트 코드를 실행하기 위해 필요한 기본적인 틀을 제공하는 테스트 프레임워크입니다.

```
import static org.junit.Assert.assertEquals
import org.junit.Test

class CalculatorTest {
    @Test
    fun evaluatesExpression() {
        val calculator = Calculator()
        val actual: Int = calculator.evaluate("1+2+3")
        assertEquals(6, actual)
    }
}
```

#### JUnit4 + Truth

##### Truth는 테스트 코드에서 assertion을 위한 라이브러리입니다.
##### JUnit에서 기본적으로 제공하는 assertion 기능보다 훨씬 가독성이 좋은 기능을 제공합니다.

```
import com.google.common.truth.Truth.assertThat
import org.junit.Test;

class CalculatorTest {
    @Test
    fun evaluatesExpression() {
        val calculator = Calculator()
        val actual: Int = calculator.evaluate("1+2+3")
        assertThat(actual).isEqualTo(6)
    }
}
```
