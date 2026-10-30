# AGENTS 템플릿

## 1. 목적

이 문서는 프로젝트 루트 `AGENTS.md`의 기본 형식을 제공한다.

템플릿은 프로젝트 문서와 BlackThunder Conventions를 작업 전에 확인하게 하고, 대화·파일·검증에 관한 공통 작업 규칙을 에이전트에게 전달하는 것을 목적으로 한다.

## 2. 사용 방법

템플릿을 프로젝트 루트의 `AGENTS.md`로 복사한다.

코드 작업은 해당 언어의 컨벤션을 기본 문서로 읽는다. 언어별 문서에는 적용되는 공통 규칙도 함께 수록되어 있다. 템플릿의 개발 언어별 추가 확인 절은 현재 제공하는 [C# 컨벤션](../conventions/02.%20dove%20CSharp%20convention.md)과 [TypeScript 컨벤션](../conventions/02.%20dove%20TypeScript%20convention.md)을 기준으로 작성되어 있다.

## 3. AGENTS 템플릿

```markdown
# AGENTS

## 참조 문서

- 프로젝트 문서는 `docs` 폴더에 존재한다. 작업 시작 전, 관련 문서가 존재하는지 확인하고, 존재할 경우 해당 내용을 숙지한 후 작업을 시작한다.
- 공통 컨벤션과 작업 지침은 `guidelines/blackthunder-conventions`에 존재한다. 해당 경로가 없거나 비어 있다면 서브모듈이 초기화되지 않았을 수 있으므로 사용자에게 알린다.
- 코드 작업 시, 공통 규칙도 함께 수록된 해당 언어의 컨벤션을 기본 문서로 읽는다. 언어별 문서는 아래 개발 언어별 추가 확인을 따른다.
- 해당 언어의 문서가 없거나 언어 간 공통 기준을 확인할 때는 `guidelines/blackthunder-conventions/conventions/02. dove common convention.md`를 참고한다.
- 코드 컨벤션의 적용 우선순위는 프로젝트 지침·설정 → 언어별 컨벤션 → 공통 컨벤션이다.
- 문서 작업 시, 별도 지침이 없다면 `guidelines/blackthunder-conventions/conventions/01. dove documentation convention.md`를 따른다.
- 작업 유형에 해당하는 구체적인 지침이 `guidelines/blackthunder-conventions/instructions`에 존재한다면 해당 지침을 따른다.

## 언어

- 한국어로 대화할 때는 존댓말을 사용한다.
- 코드 내 주석은 영어를 사용한다.
- Git 커밋 제목은 영어를 사용한다.

## 파일 형식

- 이 작업공간에서 코드 파일을 새로 작성하거나 수정할 때는 줄 끝을 Unix 형식인 `LF`로 유지한다.
- 일부 코드 파일은 UTF-8이 아닐 수 있다. `apply_patch`가 `invalid utf-8 sequence`로 실패하면 파일 손상으로 판단하지 말고, PowerShell/.NET에서 기존 인코딩으로 읽은 뒤 필요한 범위만 UTF-8로 저장한다(.md 등 단순 문서 파일의 경우 인코딩 검사를 하지 않아도 된다).

## 작업

- 사용자가 명시적으로 테스트 실행을 요청하지 않은 경우 테스트를 실행하지 않는다. 필요한 확인은 빌드, 정적 검색, 문서 검사처럼 테스트가 아닌 검증으로 한정하고, 테스트가 필요하면 먼저 사용자에게 확인한다.

## 개발 언어별 추가 확인

### C#

- C# 코드 작업 시 `guidelines/blackthunder-conventions/conventions/02. dove CSharp convention.md`를 기본 문서로 읽는다.
- 대상 프레임워크, 언어 버전, nullable 사용, 다른 프로젝트와의 연동 방식은 `guidelines/blackthunder-conventions/instructions/플랫폼 기준 - CSharp.md`를 따른다.
- `.csproj`, `.props`, `.targets`, `.sln`, `.slnx` 같은 프로젝트 파일도 `LF` 적용 대상에 포함한다.

### TypeScript

- TypeScript 코드 작업 시 `guidelines/blackthunder-conventions/conventions/02. dove TypeScript convention.md`를 기본 문서로 읽는다.
```

## 4. 검증 기준

- 파일명이 프로젝트 루트의 `AGENTS.md`인지 확인한다.
- 프로젝트 문서와 컨벤션 경로가 실제 구조와 일치하는지 확인한다.
- 공통 규칙도 포함된 언어별 문서를 기본 문서로 안내하고, 프로젝트 지침·설정을 우선하도록 안내하는지 확인한다.
- C# 프로젝트는 Unity 등과의 호환이 필요한지 확인하고, 플랫폼 기준 문서를 그대로 따를지 프로젝트 지침에서 조정할지 결정한다.
- LF 정책을 사용한다면 해당 파일 형식을 `.gitattributes`나 편집기 설정에도 반영한다.
