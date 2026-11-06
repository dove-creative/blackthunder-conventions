# 변경 이력

이 문서는 BlackThunder Conventions의 규칙 변경을 날짜별로 기록한다. 서브모듈을 갱신할 때는 이전 갱신 이후의 항목을 확인한다.

규칙 ID 초기화 이전의 기록은 [이전 변경 이력](old/CHANGELOG.md)에 보관한다.

## 기록 기준

- 최신 날짜를 위에 둔다.
- 날짜 아래는 `추가`, `변경`, `삭제`로 나누고, 해당하는 항목만 둔다.
- 규칙 ID가 있으면 항목 앞에 적고, 대상 문서를 괄호로 밝힌다.
- 기존 코드나 문서를 맞춰야 한다면 그 방법을 항목에 함께 적는다.
- 오탈자 수정처럼 규칙의 의미가 바뀌지 않는 변경은 기록하지 않는다.

## 2026-11-07

### 추가

- `CF-WRAP-01`(공통, C#): 코드, 주석, 문서 주석의 한 줄 길이는 120자를 넘지 않도록 한다. C#의 120자 기준을 C 계열 규칙으로 올리고 주석과 문서 주석까지 적용 범위를 넓힌다. 기존 코드는 해당 코드를 수정할 때 함께 맞춘다.
- 언어별 문서가 없는 언어(공통): 공통 컨벤션의 해당 절을 기본 문서로 읽고, 다루지 않는 사항은 프로젝트 지침과 해당 언어의 관례를 따른다.

### 변경

- 규칙 계층(공통, C#, Python): 공통 컨벤션을 모든 언어에 적용하는 2절과 C 계열 언어에 적용하는 3절로 나눈다. C 계열은 C#, TypeScript처럼 중괄호 블록과 클래스를 사용하는 언어이며 규칙 범위는 `CF`이다. Python은 공통 규칙과 `PY` 규칙만 적용하므로 문서의 제외 목록을 없앤다.
- 규칙 ID(공통, C#, Python): 구조 변경에 맞춰 ID를 한 번 초기화한다. 바로 앞 규칙의 예외인 May 규칙은 세부 규칙으로 옮긴다. 이 날짜의 항목은 초기화 이후 번호를 사용하며, 프로젝트의 문서나 주석에 이전 ID를 적었다면 아래 대응표에 따라 갱신한다.
- 영역 정의(공통, C#): `Front`·`Property`·`Internal`을 접근 제한자가 아니라 멤버의 논리적 역할로 정의한다.
- `CS-BLOCK-03.1`(C#): 스타일을 통일하는 규칙임을 구분하기 위해 Allman을 권장하는 `CS-BLOCK-03`의 세부 규칙으로 옮긴다. 문구와 강도는 유지한다.
- `CS-BLOCK-05`(C#): 두 줄 빈 블록의 규칙을 '중간에는 빈 줄을 넣지 않는다'로 줄인다. 스타일은 `CS-BLOCK-03`과 `CS-BLOCK-03.1`을 따른다.
- `CS-WRAP-01`(C#): 줄바꿈 기준 절로 옮겨 모든 줄바꿈에 적용하고, 기준 절의 '콤마는 항상 이전 요소의 끝에 둔다'를 합친다.
- `CS-WRAP-06`(C#): 강도를 Should에서 May로 바꾼다.
- `CS-WRAP-10`(C#): 줄바꿈 시점이 아니라 형식을 정하는 문장으로 바꾸고, 콤마 내용은 `CS-WRAP-01`로 옮긴다.
- `CS-WRAP-12`(C#): 강도를 Should에서 May로 바꾸고, 줄 길이와 관계없이 `where` 절 단위로 줄바꿈할 수 있음을 밝힌다.

#### 규칙 ID 대응표

표에 없는 ID는 번호가 바뀌지 않았다.

| 이전 ID | 현재 ID |
|---|---|
| COM-BLANK-05 | COM-BLANK-02 |
| COM-REGION-01 | CF-REGION-01 |
| COM-REGION-03 | CF-REGION-01.1 |
| COM-REGION-02 | CF-REGION-02 |
| COM-REGION-04 | CF-REGION-03 |
| COM-REGION-05 | CF-REGION-04 |
| COM-BLANK-02 | CF-BLANK-01 |
| COM-BLANK-03 | CF-BLANK-01.1 |
| COM-BLANK-04 | CF-BLANK-02 |
| COM-BLANK-06 | CF-BLANK-03 |
| CS-BLOCK-02 | CS-BLOCK-01.1 |
| CS-BLOCK-03 | CS-BLOCK-02 |
| CS-BLOCK-04 | CS-BLOCK-03 |
| CS-BLOCK-05 | CS-BLOCK-03.1 |
| CS-BLOCK-06 | CS-BLOCK-04 |
| CS-BLOCK-07 | CS-BLOCK-04.1 |
| CS-BLOCK-08 | CS-BLOCK-05 |
| CS-WRAP-06 | CS-WRAP-01 |
| CS-WRAP-01 | CS-WRAP-02 |
| CS-WRAP-02 | CS-WRAP-02.1 |
| CS-WRAP-17 | CS-WRAP-03.1 |
| CS-WRAP-05 | CS-WRAP-04.1 |
| CS-WRAP-07 | CS-WRAP-05 |
| CS-WRAP-08 | CS-WRAP-06 |
| CS-WRAP-09 | CS-WRAP-07 |
| CS-WRAP-18 | CS-WRAP-08 |
| CS-WRAP-10 | CS-WRAP-09 |
| CS-WRAP-11 | CS-WRAP-09.1 |
| CS-WRAP-12 | CS-WRAP-10 |
| CS-WRAP-14 | CS-WRAP-11 |
| CS-WRAP-16 | CS-WRAP-12 |
| CS-DECL-02 | CS-DECL-01.1 |
| CS-DECL-03 | CS-DECL-02 |

### 삭제

- TypeScript 컨벤션: 고유 규칙이 없고 적용 규칙이 공통 컨벤션과 같아 문서와 `TS` 범위를 삭제한다. TypeScript 작업은 공통 컨벤션의 공통 규칙과 C 계열 규칙을 따른다. 프로젝트의 `AGENTS.md`에 복사한 경로도 갱신한다.
- `PY-WRAP-01`(Python): PEP 8의 79자·72자 제한 대신 120자를 쓰던 규칙을 삭제하고 PEP 8을 따른다. 기존 코드는 해당 코드를 수정할 때 함께 맞춘다.
- 이전 `CS-BLOCK-09`, `CS-BLOCK-10`(C#): `CS-BLOCK-05`와 `CS-BLOCK-03`, `CS-BLOCK-03.1`에 통합한다.
- 이전 `CS-WRAP-13`(C#): `CS-WRAP-01`에 통합한다.
