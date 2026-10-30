# README 템플릿 - C#

## 목적

이 문서는 C#과 .NET 저장소나 패키지의 README에 들어가는 명령과 코드 예시를 정리한다.

README의 구성과 각 절의 작성 기준은 [README 템플릿](README%20템플릿.md)을 따른다.

## 설치

NuGet 패키지로 배포한다면 패키지 추가 명령을 먼저 제시한다.

```powershell
dotnet add package Company.Product
```

필요한 경우 프로젝트 파일에 직접 추가하는 형식도 함께 제시한다.

```xml
<ItemGroup>
  <PackageReference Include="Company.Product" Version="1.0.0" />
</ItemGroup>
```

저장소 자체를 빌드하거나 실행해야 한다면 필요한 SDK 버전과 명령을 별도로 적는다.

```powershell
dotnet build src/Company.Product/Company.Product.csproj
```

## 빠른 시작

빠른 시작 절은 아래처럼 작성한다.

````markdown
## 빠른 시작

```csharp
var service = new ProductService();
var result = service.Run();
```

이 코드는 아래 작업을 수행한다.

- 대표 서비스를 생성한다.
- 기본 동작을 실행한다.
- 처리 결과를 반환한다.
````

실행 가능한 예시 프로젝트를 제공한다면 대화형 실행과 대표 명령의 일회 실행 명령을 함께 적는다.

```powershell
dotnet run --project samples/Company.Product.Samples.csproj
dotnet run --project samples/Company.Product.Samples.csproj -- basic
```

## 테스트

테스트 절에는 테스트 실행 명령을 적는다.

```powershell
dotnet test
```
