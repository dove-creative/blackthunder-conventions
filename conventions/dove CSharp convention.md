# dove’s C# Convention

## 목차

1. 들어가며
   - 1-1. 규칙 강도

2. 코드 컨벤션
   - 2-1. 명명 컨벤션
   - 2-2. 구조 컨벤션

3. 설계 컨벤션
   - 3-1. 상속 및 계층 컨벤션

## 1. 들어가며

- 이 문서는 작성자 dove의 C# 컨벤션을 정리한 것이다.
- 공개 API와 라이브러리 설계는 Microsoft의 [Framework Design Guidelines](https://learn.microsoft.com/ko-kr/dotnet/standard/design-guidelines/)를, 일반적인 코드 스타일은 [Common C# code conventions](https://learn.microsoft.com/ko-kr/dotnet/csharp/fundamentals/coding-style/coding-conventions)를 기본 토대로 삼는다.
- 여기서 다루지 않은 서식 사항은 [Microsoft C# 서식 가이드라인](https://learn.microsoft.com/ko-kr/dotnet/fundamentals/code-analysis/style-rules/csharp-formatting-options)을 따르는 것을 기본 원칙으로 한다.

### 1-1. 규칙 강도

- **[Must]**: 반드시 준수한다.
- **[Should]**: 특별한 이유가 없다면 준수한다.
- **[May]**: 상황과 의도에 따라 선택할 수 있다.
- **[Must Not]**: 사용하지 않는다.
- **[Should Not]**: 특별한 이유가 없다면 사용하지 않는다.

## 2. 코드 컨벤션

### 2-1. 명명 컨벤션

#### 2-1-1. 기준

식별자 이름은 해당 요소의 핵심 역할이 바로 드러나도록 짓는다.

#### 2-1-2. 기본 명명 규칙

##### 2-1-2.1. 구체적인 이름 사용

- **[Should]** 숫자나 모호한 이름보다, 의미가 드러나는 구체적인 이름을 우선한다.

##### 2-1-2.2. 언더스코어 사용

- **[Should]** 기본적인 PascalCase / camelCase만으로 의미 전달이 어려울 때만 제한적으로 `_`를 사용한다.
- 예: `TestDisposedDisconnectSegmentNotContaining` 대신 `Test_Disposed_DisconnectSegment_NotContaining`
- **[Must Not]** 공개 API에서는 `_`를 사용하지 않는다.
- 공개 API에서는 더 짧고 명확한 이름, 혹은 네임스페이스 계층으로 의미를 분리한다.

#### 2-1-3. 한정자 사용 규칙

- **[Should]** private 필드나 메서드에 `private` 한정자를 사용한다.
- **[Should]** `sealed` 한정자를 남용하지 않는다. 상속을 강하게 제한할 필요가 있을 때만 `sealed` 한정자를 사용한다.
- **[Should]** 변경되지 않는 구조체의 경우 `readonly` 한정자를 사용한다.

#### 2-1-4. 식별자별 명명 규칙

##### 2-1-4.1. private 필드

- **[Must]** `const`를 제외한 모든 private 필드는 `_` 접두사를 사용한다.
- **[Should Not]** `s_`, `t_` 같은 별도 접두사는 사용하지 않는다.

##### 2-1-4.2. 소스 코드 파일 / 폴더 / 어셈블리

- **[Must]** PascalCase를 사용한다.
- **[Must]** 폴더 경로의 물리적 계층은 `/`로, 어셈블리 등 논리적 이름의 계층은 `.`으로 표현한다.
- 예: `UniEngine/Plugins/GeoSystem.Tests`
- **[Must Not]** 공백은 사용하지 않는다.

##### 2-1-4.3. 상수

- **[Must]** `const`는 PascalCase를 사용한다.
- **[Must Not]** `const`나 `readonly`에 `SCREAMING_SNAKE_CASE`를 쓰지 않는다.

##### 2-1-4.4. 열거형

- **[Must]** 일반 enum 형식명은 단수형, `[Flags]` enum 형식명은 복수형으로 작성한다.
- **[Must]** enum 형식이나 식별자에 `Enum`, `Flags` 같은 접미사는 붙이지 않는다.
- **[Should]** enum임을 드러내야 할 때는 의미 중심 이름을 쓰고, 정말 필요할 때만 `Type`, `Kind`, `Mode`, `State` 등을 붙인다.

### 2-2. 구조 컨벤션

#### 2-2-1. 코드 블록 규칙

##### 2-2-1.1. 한 줄 코드 블록

- **[Should]** 한 줄짜리 블록은 식 본문 멤버를 우선 사용한다.

```csharp
private void Start() => DoSomething();
```

- **[May]** 필요하면 한 줄 중괄호 블록도 허용한다.

```csharp
private void Start() { DoSomething(); }
```

- **[Should Not]** 세 문장 이상을 한 줄에 몰아넣지 않는다.

##### 2-2-1.2. 두 줄 이상 코드 블록

- **[Should]** 두 줄 이상 블록은 Allman(BSD) 스타일을 사용한다.
- **[Must Not]** 두 줄 이상 블록에서 다른 스타일은 사용하지 않는다.

```csharp
private void Start()
{
    DoSomething();
}
```

##### 2-2-1.3. 한 줄 빈 코드 블록

- **[Should]** 한 줄 빈 블록은 `{ }` 형태로 작성하고, 중괄호 사이에 공백 한 칸을 둔다.

```csharp
private void Start() { }
private Action _start = () => { };
private class MyClass { }
```

- **[May]** 여러 줄 선언문에 딸린 블록은 가독성상 다음 줄에 `{ }`를 둘 수 있다.
- 단, 짧고 단순한 선언은 그 방식으로 쓰지 않는다.

##### 2-2-1.4. 두 줄 빈 블록

- **[Should]** 두 줄 빈 블록은 빈 줄 없는 Allman(BSD) 스타일로 작성한다.
- **[Should Not]** 중간에 빈 줄을 넣지 않는다.
- **[Must Not]** Allman(BSD) 외의 스타일은 사용하지 않는다.

```csharp
private void Start()
{
}
```

#### 2-2-2. 줄바꿈 규칙

##### 2-2-2.1. 기준

- 콤마는 항상 **이전 요소의 끝**에 둔다.
- 같은 수준의 인자는 같은 레벨로 보이게 정렬한다.
- 호출 구조는 공간을 아끼는 방향으로, 자료구조 표현은 구조가 드러나는 방향으로 줄바꿈한다.

##### 2-2-2.2. 연산자 줄바꿈

- **[Should]** 연산자는 다음 줄 첫 항목 앞에 둔다.

```csharp
if (value >= predicate
    && !isRunning)
```

```csharp
private readonly Exception _animationFailure
    = new InvalidOperationException("애니메이션 재생 중 오류가 발생했습니다.");
```

- **[May]** 문자열 결합처럼 가독성이 더 중요한 경우에는 가장 읽기 좋은 위치로 조정할 수 있다.

##### 2-2-2.3. 인자 목록 줄바꿈

- **[Should]** 긴 인자 목록이나 제네릭 목록은 여러 줄로 나눌 수 있다.
- 방법은 두 가지다.
  - 첫 줄 일부를 유지하고 다음 줄부터 한 번 들여쓰기
  - 첫 줄부터 바로 개행하고 각 인자를 한 줄씩 배치
- **[Should Not]** 닫는 괄호 `)` 또는 `>`를 별도 줄에 두지 않는다.
- **[May]** 깊은 메서드 체이닝이나 중첩 자료구조에서는 가독성을 위해 닫는 괄호를 다음 줄로 내릴 수 있다.
- **[Must Not]** 콤마를 새 줄 첫머리에 두지 않는다.

##### 2-2-2.4. record 생성자 줄바꿈

- **[Should]** 본문이 있는 `record`의 생성자는 호출 구조처럼 취급한다.
- **[Should]** 본문이 없는 `record`는 자료구조처럼 개행할 수 있다.

예:

```csharp
public record PlayInfo(
    string AnimationName,
    string TriggerName = null,
    float StartTime = default,
    float EndTime = default)
{
}
```

```csharp
public record PlayInfo
(
    string AnimationName,
    string TriggerName = null,
    float StartTime = default,
    float EndTime = default
);
```

##### 2-2-2.5. 람다 표현식과 식 본문 멤버

- **[Should]** 람다와 식 본문 멤버는 선언부의 일부로 보고 같은 흐름 안에서 배치한다.
- 중괄호가 없다면, 마치 중괄호가 있었을 때의 들여쓰기 감각을 유지한다.

```csharp
private void Start() =>
    DoSomething();

private Action _start = () =>
    DoSomething();
```

###### 2-2-2.5.1. 람다/식 본문 멤버의 switch 식

- **[Should]** switch 식은 보통 줄바꿈 후 본문처럼 배치한다.
- **[May]** 짧고 단순한 경우에는 메서드와 같은 줄에 `=> value switch` 형태로 둘 수 있다.

```csharp
private string ToString(SettingInfo info) =>
    info.Type switch
    {
        MyEnum.None => "None",
        MyEnum.Normal => "Normal",
        MyEnum.Special => "Special",
        _ => throw new ArgumentOutOfRangeException(nameof(info.Type), info.Type, null)
    };
```

##### 2-2-2.6. 상속 및 구현 줄바꿈

- **[Should]** 상속/구현 목록이 길면 줄바꿈을 사용할 수 있다.
- 콤마는 이전 줄 끝에 둔다.
- 두 번째 줄부터는 한 번 들여쓴다.
- `:` 위치는 가독성과 의도가 가장 잘 드러나는 방식으로 배치한다.
- **[Must Not]** 콤마를 다음 요소 앞에 두지 않는다.
- **[Must Not]** `:` 앞뒤를 붙여 쓰지 않는다.
- **[Must]** 생성자 이니셜라이저의 `: base(...)`는 다음 줄 시작에 둔다.
- **[Should]** 제네릭 제약은 `where` 절 단위로 줄바꿈할 수 있다.

예:

```csharp
private class ChildClass
    : ParentClass,
    IInterface
{
}
```

```csharp
public ChildClass(int value)
    : base(value)
{
}
```

## 3. 설계 컨벤션

### 3-1. 상속 및 계층 컨벤션

#### 3-1-1. 객체 컨벤션

##### 3-1-1.1. 메서드 순서

- **[Should]** 객체의 메서드는 생애주기 순으로 읽을 수 있도록 적는다.

#### 3-1-2. 상속 컨벤션

##### 3-1-2.1. 기본 구현 메서드

- **[Should]** 인터페이스의 기본 구현 메서드는 구현체에 중복해서 구현하지 않는다.
