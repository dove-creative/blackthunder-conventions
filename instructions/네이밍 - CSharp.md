# 네이밍 - C#

## 목적

이 문서는 C#과 .NET 프로젝트에만 존재하는 이름 표면의 표기 방식을 정리한다.

이름 표면을 구분하는 기본 원칙은 [네이밍](네이밍.md)을 따르고, 코드 식별자의 대소문자와 접두사는 [C# 컨벤션](../conventions/02.%20dove%20CSharp%20convention.md)을 따른다.

## 기본 원칙

- 패키지 식별자, 네임스페이스, 어셈블리 이름은 소유자명과 제품명을 `.`으로 구분하고, 각 세그먼트는 PascalCase로 작성한다. 네임스페이스와 어셈블리 이름은 코드에서 읽히는 표면이므로 C# 컨벤션의 대소문자 규칙을 따른다.

## 패키지 식별자

.NET 패키지의 `PackageId`는 소유자명과 제품명을 `.`으로 구분하고, 각 세그먼트는 PascalCase로 작성한다.

예:

```xml
<PropertyGroup>
  <PackageId>BlackThunder.UniEngine</PackageId>
</PropertyGroup>
```

## 네임스페이스

C# 네임스페이스는 회사명 또는 소유자명에서 시작하고, 각 세그먼트는 PascalCase로 작성한다.

예:

```csharp
namespace BlackThunder.UniEngine
{
}
```

## 어셈블리 이름과 RootNamespace

어셈블리 이름의 대소문자와 계층 표기는 C# 컨벤션의 `CS-NAME-05`, `CS-NAME-06`을 따른다.

예:

```xml
<PropertyGroup>
  <AssemblyName>BlackThunder.UniEngine</AssemblyName>
</PropertyGroup>
```

테스트, 샘플, 도구처럼 하위 어셈블리가 필요하면 대표 어셈블리 이름 뒤에 PascalCase 세그먼트를 붙인다.

예:

```text
BlackThunder.UniEngine.Tests
BlackThunder.UniEngine.Samples
BlackThunder.UniEngine.Tools
```

프로젝트 파일명도 어셈블리 이름과 맞추는 것을 기본으로 한다.

예:

```text
BlackThunder.UniEngine.csproj
BlackThunder.UniEngine.Tests.csproj
```

`RootNamespace`는 C# 소스에 선언된 네임스페이스를 변경하지 않는다. 포함 리소스의 이름을 구성할 때 별도의 기준이 필요한 경우에만 명시한다.

## 혼동 방지

- C# 네임스페이스에 `blackthunder.uniengine`처럼 전부 소문자인 식별자를 그대로 쓰지 않는다.

요약하면, 저장소 이름은 `blackthunder-uniengine`, 배포 식별자와 코드 식별자는 `BlackThunder.UniEngine`, 사용자 표시 이름은 `UniEngine`처럼 쓴다.
