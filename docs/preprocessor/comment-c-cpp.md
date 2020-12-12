---
description: '자세히 알아보기: 주석 pragma'
title: 주석 pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragmas, comment
- comment pragma
ms.assetid: 20f099ff-6303-49b3-9c03-a94b6aa69b85
ms.openlocfilehash: 71172632ee1589c3f6d66136e9567929bff5d08c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97300816"
---
# <a name="comment-pragma"></a>주석 pragma

주석 기록을 개체 파일 또는 실행 파일에 배치합니다.

## <a name="syntax"></a>Syntax

> **#pragma 주석 (** *주석 유형* [ **,** "*주석-문자열*"] **)**

## <a name="remarks"></a>설명

*주석-형식은* 아래에 설명 된 미리 정의 된 식별자 중 하나로, 주석 레코드의 형식을 지정 합니다. 선택적 *주석 문자열* 은 일부 주석 형식에 대 한 추가 정보를 제공 하는 문자열 리터럴입니다. *주석 문자열* 은 문자열 리터럴 이므로 이스케이프 문자, 포함 된 따옴표 () 및 연결에 대 한 문자열 리터럴에 대 한 모든 규칙을 따르는 `"` 합니다.

### <a name="compiler"></a>compiler

컴파일러의 이름 및 버전 이름을 개체 파일에 배치합니다. 이 주석 기록은 링커에 의해 무시됩니다. 이 레코드 형식에 대 한 *주석 문자열* 매개 변수를 제공 하는 경우 컴파일러에서 경고를 생성 합니다.

### <a name="lib"></a>lib

라이브러리 검색 기록을 개체 파일에 배치합니다. 이 주석 형식은 링커에서 검색할 라이브러리의 이름 (및 가능한 경우 경로)을 포함 하는 *주석 문자열* 매개 변수와 함께 제공 되어야 합니다. 라이브러리 이름은 개체 파일의 기본 라이브러리 검색 레코드를 따릅니다. 링커가 [/nodefaultlib](../build/reference/nodefaultlib-ignore-libraries.md)로 지정 되지 않은 경우 링커는이 라이브러리를 명령줄에서 이름을 지정 하는 것 처럼 검색 합니다. 여러 라이브러리 검색 기록을 같은 소스 파일에 배치할 수 있으며 각 기록은 소스 파일과 동일한 순서로 개체 파일에 표시됩니다.

기본 라이브러리의 순서와 추가 된 라이브러리가 중요 한 경우 [/zl](../build/reference/zl-omit-default-library-name.md) 스위치로 컴파일하면 기본 라이브러리 이름이 개체 모듈에 배치 되지 않습니다. 그런 다음 두 번째 주석 pragma를 사용하여 추가된 라이브러리 다음에 기본 라이브러리의 이름을 삽입할 수 있습니다. pragma를 사용하여 나열된 라이브러리는 소스 코드와 동일한 순서로 개체 모듈에 표시됩니다.

### <a name="linker"></a>링커

개체 파일에 [링커 옵션](../build/reference/linker-options.md) 을 배치 합니다. 이 주석 형식을 이용하여 명령줄에 주석을 전달하거나 개발 환경에 지정하는 대신 링커 옵션을 지정할 수 있습니다. 예를 들어, /include 옵션을 지정하면 기호를 포함하도록 할 수 있습니다.

```C
#pragma comment(linker, "/include:__mySymbol")
```

다음 (*주석 형식*) 링커 옵션만 링커 식별자에 전달할 수 있습니다.

- [/DEFAULTLIB](../build/reference/defaultlib-specify-default-library.md)

- [/EXPORT](../build/reference/export-exports-a-function.md)

- [/INCLUDE](../build/reference/include-force-symbol-references.md)

- [/MANIFESTDEPENDENCY](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [/MERGE](../build/reference/merge-combine-sections.md)

- [/SECTION](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>사용자

일반 주석을 개체 파일에 배치합니다. *주석 문자열* 매개 변수에는 주석의 텍스트가 포함 됩니다. 이 주석 기록은 링커에 의해 무시됩니다.

## <a name="examples"></a>예제

다음 pragma를 사용하면 링커가 연결하는 동안 EMAPI.LIB 라이브러리를 검색할 수 있습니다. 링커는 먼저 현재 작업 경로에서 검색한 다음 LIB 환경 변수에 지정된 경로에서 검색합니다.

```C
#pragma comment( lib, "emapi" )
```

다음 pragma는 컴파일러가 컴파일러의 이름과 버전 번호를 개체 파일에 배치하도록 합니다.

```C
#pragma comment( compiler )
```

*주석 문자열* 매개 변수를 사용 하는 주석의 경우 매크로가 문자열 리터럴로 확장 되는 경우 문자열 리터럴을 사용 하는 모든 위치에서 매크로를 사용할 수 있습니다. 문자열 리터럴에 확장되는 문자열 리터럴 및 매크로의 조합을 연결할 수도 있습니다. 예를 들어, 다음 문을 사용할 수 있습니다.

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
