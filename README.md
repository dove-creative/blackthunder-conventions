# BlackThunder Conventions

BlackThunder Conventions는 여러 프로젝트에서 공유하는 코드·문서 컨벤션과 작업 지침을 모은 저장소이다.

프로젝트마다 반복해서 작성하던 기준을 한곳에서 관리하고, 각 프로젝트에서는 서브모듈을 통해 동일한 규칙을 참조하는 것을 목적으로 한다.

## 목차

1. 구성
2. 사용 방법
3. 적용 기준
4. 문서
5. 라이선스

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

프로젝트 루트의 `AGENTS.md`는 [AGENTS 템플릿](instructions/AGENTS%20템플릿.md)을 복사해 사용한다.

## 3. 적용 기준

- 코드 컨벤션의 적용 우선순위는 프로젝트 지침·설정 → 언어별 컨벤션 → 공통 컨벤션이다. 프로젝트의 `AGENTS.md`, 관련 문서와 도구 설정을 우선 확인한다.
- 코드 작업 시 사용하는 언어의 컨벤션을 기본 문서로 읽는다. 언어별 문서에는 적용되는 공통 규칙과 언어별 규칙이 함께 수록되어 있다.
- 해당 언어의 문서가 없거나 언어 간 공통 기준을 확인할 때는 [공통 코드 컨벤션](conventions/02.%20dove%20common%20convention.md)을 참고한다.
- 문서 작업과 그 밖의 작업은 해당 유형에 맞는 컨벤션과 지침을 선택한다.
- 컨벤션은 판단 기준을 제공하고, 지침은 구체적인 작업 절차와 결과물 형식을 제공한다.
- 필요한 문서만 읽고 프로젝트와 관계없는 규칙을 임의로 적용하지 않는다.

## 4. 문서

### 4-1. 컨벤션

- [BlackThunder Conventions Overview](conventions/00.%20Overview.md): 컨벤션의 목적과 선택 기준
- [01. dove documentation convention](conventions/01.%20dove%20documentation%20convention.md): 문서 작성 기준
- [02. dove common convention](conventions/02.%20dove%20common%20convention.md): 여러 언어에 공통으로 적용하는 코드 작성 기준
- [02. dove CSharp convention](conventions/02.%20dove%20CSharp%20convention.md): C#에 적용되는 공통 규칙, 전용 규칙과 예시
- [02. dove TypeScript convention](conventions/02.%20dove%20TypeScript%20convention.md): TypeScript에 적용되는 공통 규칙

### 4-2. 작업 지침

- [AGENTS 템플릿](instructions/AGENTS%20템플릿.md): 프로젝트 `AGENTS.md`의 기본 형식과 개발 언어별 추가 확인 사항
- [README 템플릿](instructions/README%20템플릿.md): 저장소와 패키지의 README 작성 기준
- [README 템플릿 - C#](instructions/README%20템플릿%20-%20CSharp.md): C#과 .NET README의 설치, 빠른 시작, 테스트 명령 예시
- [네이밍](instructions/네이밍.md): 저장소, 패키지, 네임스페이스, 산출물, 표시 이름의 공통 표기 기준
- [네이밍 - C#](instructions/네이밍%20-%20CSharp.md): C#과 .NET 프로젝트의 패키지 식별자, 네임스페이스, 어셈블리 이름 기준
- [문서 양식](instructions/문서%20양식.md): 마크다운 문서의 구조와 표기 기준
- [번역](instructions/번역.md): 문서 번역 기준
- [예시 프로젝트](instructions/예시%20프로젝트.md): 예시 프로젝트의 실행 방식, 출력, README 구성 기준
- [예시 프로젝트 - C#](instructions/예시%20프로젝트%20-%20CSharp.md): C#과 .NET 예시 프로젝트의 파일 구성, 설정, 실행 명령
- [플랫폼 기준 - C#](instructions/플랫폼%20기준%20-%20CSharp.md): C# 프로젝트의 대상 프레임워크, 언어 버전, nullable 사용, DLL 연동 기준

## 5. 라이선스

이 프로젝트는 MIT 라이선스로 배포된다. 자세한 내용은 [LICENSE.md](LICENSE.md)를 참고한다.
