# BlackThunder Conventions

BlackThunder Conventions는 여러 프로젝트에서 공유하는 코드·문서 컨벤션과 작업 지침을 모은 저장소이다.

프로젝트마다 반복해서 작성하던 기준을 한곳에서 관리하고, 각 프로젝트에서는 서브모듈을 통해 동일한 규칙을 참조하는 것을 목적으로 한다.

## 목차

1. 구성
2. 사용 방법
3. 적용 기준
4. 문서
5. 이용 범위

## 1. 구성

- `conventions`: 코드와 문서를 작성할 때 적용하는 공통 컨벤션과 판단 기준
- `instructions`: 특정 작업을 수행할 때 따르는 구체적인 절차와 템플릿

## 2. 사용 방법

프로젝트의 `guidelines/blackthunder-conventions` 경로에 서브모듈로 추가한다.

```powershell
git submodule add https://github.com/dove-creative/blackthunder-conventions.git guidelines/blackthunder-conventions
```

서브모듈이 포함된 프로젝트를 받은 뒤에는 아래 명령으로 초기화한다.

```powershell
git submodule update --init --recursive
```

프로젝트의 `AGENTS.md`에서는 필요한 컨벤션과 작업 지침의 실제 경로를 명시한다. 기본 형식은 [AGENTS 템플릿](instructions/AGENTS%20템플릿.md)을 참고한다.

## 3. 적용 기준

- 프로젝트에 별도 규칙이 있다면 프로젝트의 `AGENTS.md`와 관련 문서를 우선한다.
- 별도 규칙이 없다면 이 저장소에서 작업 유형에 맞는 컨벤션과 지침을 선택한다.
- 컨벤션은 판단 기준을 제공하고, 지침은 구체적인 작업 절차와 결과물 형식을 제공한다.
- 필요한 문서만 읽고 프로젝트와 관계없는 규칙을 임의로 적용하지 않는다.

## 4. 문서

### 4-1. 컨벤션

- [Convention Center Overview](conventions/01.%20Overview.md): 컨벤션의 목적과 선택 기준
- [dove CSharp convention](conventions/dove%20CSharp%20convention.md): C# 코드 작성 기준
- [dove documentation convention](conventions/dove%20documentation%20convention.md): 문서 작성 기준

### 4-2. 작업 지침

- [AGENTS 템플릿](instructions/AGENTS%20템플릿.md): 일반용 및 C#용 `AGENTS.md` 기본 형식
- [README 템플릿](instructions/README%20템플릿.md): 저장소와 패키지의 README 작성 기준
- [네이밍](instructions/네이밍.md): 프로젝트와 코드 요소의 이름 작성 기준
- [문서 양식](instructions/문서%20양식.md): 마크다운 문서의 구조와 표기 기준
- [번역](instructions/번역.md): 문서 번역 기준
- [예시 프로젝트](instructions/예시%20프로젝트.md): .NET 예시 프로젝트 구성 기준

## 5. 이용 범위

이 저장소는 BlackThunder 프로젝트와 관련 작업에서 사용하는 비공개 내부 규칙 저장소이다. 별도의 배포 라이선스는 제공하지 않는다.
