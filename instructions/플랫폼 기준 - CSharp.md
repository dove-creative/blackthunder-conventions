# 플랫폼 기준 - C#

## 목적

이 문서는 C# 프로젝트의 대상 프레임워크, 언어 버전, nullable 사용, 다른 프로젝트와의 연동 방식을 정리한다.

이 기준의 목표는 Unity 등 .NET Standard 환경과의 호환성이다. Unity는 .NET 5 이상(`net10.0` 등)을 대상으로 빌드한 DLL을 불러오지 못하고, Unity가 소스를 직접 컴파일할 때는 C# 9까지만 지원한다.

## 기본 원칙

- 라이브러리는 `netstandard2.1`을 대상으로 한다.
- 언어 버전은 저장소 전체에서 C# 9로 맞춘다.
- 다른 프로젝트와는 컴파일된 DLL로 연동한다.
- 예시, 테스트, 도구처럼 Unity에 들어가지 않는 실행 프로젝트는 현재 .NET LTS 버전을 대상으로 한다.

이 기준은 Unity 2021.2 이상을 전제로 한다. 그보다 낮은 Unity 버전을 지원해야 하는 프로젝트는 프로젝트 지침에서 `netstandard2.0`과 C# 8로 낮춘다.

## 라이브러리

라이브러리는 `netstandard2.1`을 대상으로 한다.

.NET Standard는 실행 환경이 아니라 여러 .NET 구현이 공통으로 제공하는 API 규격이다. `netstandard2.1` 라이브러리는 이 규격을 구현한 .NET 5 이상, Mono, Unity에서 모두 동작한다. 반면 `net10.0`처럼 특정 .NET 버전을 대상으로 한 라이브러리는 해당 .NET 런타임에서만 동작하므로 Unity가 불러오지 못한다.

예:

```xml
<PropertyGroup>
  <TargetFramework>netstandard2.1</TargetFramework>
</PropertyGroup>
```

## 언어 버전

언어 버전은 저장소 공통 설정에서 C# 9로 지정한다. SDK의 기본 언어 버전은 대상 프레임워크마다 다르므로 명시적으로 지정한다.

예:

```xml
<Project>
  <PropertyGroup>
    <LangVersion>9.0</LangVersion>
  </PropertyGroup>
</Project>
```

C# 9를 기준으로 하면 DLL 배포, 소스 배포, 예시 코드 복사 중 어느 경우에도 Unity에서 그대로 컴파일된다.

`record`나 `init` 접근자를 사용하려면 `netstandard2.1`에 없는 `IsExternalInit` 형식을 프로젝트 안에 정의한다.

```csharp
namespace System.Runtime.CompilerServices
{
    internal static class IsExternalInit { }
}
```

## nullable

nullable 참조 형식은 사용할 수 있다. 프로젝트 단위로 사용할 때는 `.csproj`에 `<Nullable>enable</Nullable>`을 지정하고, Unity가 직접 컴파일하는 소스에서는 파일마다 `#nullable enable`을 지정한다.

`netstandard2.1`에는 `NotNullWhen`, `MaybeNull`, `AllowNull` 같은 기본 nullable 특성이 있다. 다만 .NET 5 이후에 추가된 `MemberNotNull`, `MemberNotNullWhen` 같은 특성과 `ArgumentNullException.ThrowIfNull` 같은 API는 없으므로 사용하지 않는다.

예:

```csharp
_name = name ?? throw new ArgumentNullException(nameof(name));
```

## API 사용 범위

`netstandard2.1` 라이브러리는 컴파일러가 사용할 수 있는 API를 .NET Standard 2.1 범위로 제한한다.

실행 프로젝트는 최신 .NET API를 모두 사용할 수 있으므로, Unity 사용자가 옮겨 쓸 수 있는 예시 코드는 .NET Standard 2.1에 있는 API만 사용한다.

## 실행 프로젝트

예시, 테스트, 도구처럼 Unity에 들어가지 않는 실행 프로젝트는 현재 .NET LTS 버전인 `net10.0`을 대상으로 한다. .NET Standard는 규격이므로 단독으로 실행되는 앱을 만들 수 없다.

`net10.0` 실행 프로젝트는 `netstandard2.1` 라이브러리를 그대로 참조할 수 있다. 언어 버전은 저장소 공통 설정의 C# 9를 따른다.

.NET LTS 버전이 바뀌면 이 기준도 함께 갱신한다.

## 다른 프로젝트와의 연동

다른 프로젝트와 연동할 때는 소스를 복사하거나 소스 패키지로 넘기지 않고, 컴파일된 DLL로 전달한다. NuGet 패키지는 DLL을 전달하는 방식 중 하나이다.

Unity에는 NuGet이 기본으로 포함되어 있지 않으므로, Unity 프로젝트에서는 DLL을 `Plugins` 폴더에 넣거나 DLL을 포함한 UPM 패키지 또는 NuGet 연동 도구를 사용한다.

같은 저장소 안의 프로젝트끼리는 `ProjectReference`로 참조한다.

## 향후 변경

Unity는 CoreCLR 전환과 함께 .NET 10과 C# 14 지원을 계획하고 있다. Unity가 이를 정식 버전에서 지원하면 이 기준을 다시 검토한다.

## 검증 기준

- 라이브러리의 대상 프레임워크가 `netstandard2.1`인가
- 저장소 공통 설정에서 언어 버전이 C# 9로 지정되어 있는가
- 실행 프로젝트가 현재 .NET LTS 버전을 대상으로 하는가
- `netstandard2.1`에 없는 nullable 특성과 API를 사용하지 않았는가
- Unity 사용자가 옮겨 쓸 수 있는 예시 코드가 .NET Standard 2.1 API만 사용하는가
- 다른 프로젝트에 소스가 아니라 DLL로 전달하는가
