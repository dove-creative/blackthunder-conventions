# 예시 프로젝트 - C#

## 목차

1. 목적
2. 프로젝트 구조
3. 프로젝트 설정
4. 진입점
5. 출력 경로
6. 사용 방법 문서
7. 검증 기준

## 1. 목적

이 문서는 C#과 .NET 예시 프로젝트에만 해당하는 파일 구성, 설정, 명령을 정리한다.

예시 프로젝트의 기본 원칙, 실행 방식, 출력, README 구성은 [예시 프로젝트](예시%20프로젝트.md)를 따르고, 코드는 [C# 컨벤션](../conventions/02.%20dove%20CSharp%20convention.md)을 따른다.

## 2. 프로젝트 구조

C# 예시 프로젝트는 `dotnet run`으로 실행할 수 있는 콘솔 앱으로 만든다. `samples` 아래의 프로젝트, 폴더, 소스 파일은 PascalCase를 사용한다.

기본 구조는 아래와 같다.

```text
samples/
├─ Program.cs
├─ README.md
├─ Company.Product.Samples.csproj
└─ Scenarios/
   ├─ BasicSample.cs
   └─ AdvancedSample.cs
```

서로 독립적으로 실행되는 예시 프로젝트가 여러 개라면 `samples/FeatureA`, `samples/FeatureB`처럼 프로젝트별 하위 폴더를 추가한다.

공통 문서의 구성 요소는 아래 파일과 폴더에 대응한다.

| 구성 요소 | C# 파일 또는 폴더 |
| --- | --- |
| 진입점 | `Program.cs` |
| 프로젝트 설정 파일 | `Company.Product.Samples.csproj` |
| 시나리오 폴더 | `Scenarios` |

시나리오가 하나뿐이거나 코드가 짧다면 `Scenarios` 폴더 없이 `Program.cs`와 하나의 예시 파일만 둘 수 있다. 시나리오가 여러 개라면 `BasicSample.cs`, `AdvancedSample.cs`처럼 역할이 드러나는 파일로 분리한다.

솔루션 파일은 예시가 여러 프로젝트로 구성되거나 IDE에서 별도로 열어야 할 필요가 있을 때만 추가한다.

## 3. 프로젝트 설정

예시 프로젝트의 `.csproj`는 콘솔 실행에 필요한 최소 설정만 명시한다. 대상 프레임워크, 언어 버전, nullable 설정은 [플랫폼 기준 - C#](플랫폼%20기준%20-%20CSharp.md)을 따른다.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net10.0</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <ProjectReference Include="../src/Company.Product/Company.Product.csproj" />
  </ItemGroup>
</Project>
```

같은 저장소의 현재 소스를 사용하는 예시는 `ProjectReference`를 사용한다.

배포된 패키지를 소비하는 흐름 자체를 검증하는 예시는 `PackageReference`를 사용한다.

```xml
<ItemGroup>
  <PackageReference Include="Company.Product" Version="1.0.0" />
</ItemGroup>
```

패키지 소스 파일을 `Compile Include`로 직접 링크하는 방식은 사용하지 않는다.

## 4. 진입점

`Program.cs`는 예시 프로젝트의 유일한 콘솔 진입점이다.

동기 예시는 `int Main(string[] args)`를 사용할 수 있고, 비동기 API를 보여주는 예시는 `Task<int> Main(string[] args)`를 사용할 수 있다.

## 5. 출력 경로

기본 출력 경로 `SampleOutput`은 `AppContext.BaseDirectory` 아래에 둔다.

예:

```csharp
private static readonly string _outputDirectory
    = Path.Combine(AppContext.BaseDirectory, "SampleOutput");
```

## 6. 사용 방법 문서

README의 실행 절은 아래처럼 작성한다.

````markdown
## 실행

대화형 프롬프트를 실행한다.

```powershell
dotnet run --project Company.Product.Samples.csproj
```

대표 시나리오를 한 번 실행하고 종료한다.

```powershell
dotnet run --project Company.Product.Samples.csproj -- basic
```
````

## 7. 검증 기준

C# 예시 프로젝트를 추가하거나 수정할 때는 공통 문서의 검증 기준을 아래 명령으로 확인한다.

- 필요한 경우 먼저 `dotnet restore samples/Company.Product.Samples.csproj`를 실행한다.
- `dotnet build samples/Company.Product.Samples.csproj --no-restore`가 통과하는지 확인한다.
- `dotnet run --project samples/Company.Product.Samples.csproj -- help`가 명령 목록을 출력하고 종료 코드 0으로 끝나는지 확인한다.
- 대표 명령을 `dotnet run --project samples/Company.Product.Samples.csproj -- basic`으로 실행하여 예상한 결과와 종료 코드를 확인한다.
- 빌드가 만든 `bin`, `obj`를 저장소 소스에 남기지 않는다.
