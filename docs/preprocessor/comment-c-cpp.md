---
description: pragmaMicrosoft C/c + +의 주석 지시문에 대해 자세히 알아보세요.
title: 주석의 pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.comment
- comment_CPP
helpviewer_keywords:
- annotations [C++]
- comments [C++], compiled files
- pragma, comment
- comment pragma
no-loc:
- pragma
ms.openlocfilehash: 8a4df005b672cb108a2b55004a1149693acd4f95
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713066"
---
# <a name="comment-no-locpragma"></a>`comment` pragma

주석 기록을 개체 파일 또는 실행 파일에 배치합니다.

## <a name="syntax"></a>구문

> **`#pragma comment(`***주석-유형* [ **`,`** "*주석-문자열*"]**`)`**

## <a name="remarks"></a>설명

*주석-형식은* 아래에 설명 된 미리 정의 된 식별자 중 하나로, 주석 레코드의 형식을 지정 합니다. 선택적 *주석 문자열* 은 일부 주석 형식에 대 한 추가 정보를 제공 하는 문자열 리터럴입니다. *주석 문자열* 은 문자열 리터럴 이므로 이스케이프 문자, 포함 된 따옴표 () 및 연결을 사용 하 여 문자열 리터럴에 대 한 모든 규칙을 따르는 `"` 합니다.

### <a name="compiler"></a>compiler

컴파일러의 이름 및 버전 이름을 개체 파일에 배치합니다. 이 주석 기록은 링커에 의해 무시됩니다. 이 레코드 형식에 대 한 *주석 문자열* 매개 변수를 제공 하는 경우 컴파일러에서 경고를 생성 합니다.

### <a name="lib"></a>lib

라이브러리 검색 기록을 개체 파일에 배치합니다. 이 주석 형식은 링커에서 검색할 라이브러리의 이름 (및 경로)이 포함 된 *주석 문자열* 매개 변수와 함께 제공 되어야 합니다. 라이브러리 이름은 개체 파일의 기본 라이브러리 검색 레코드를 따릅니다. 링커는를 사용 하 여 라이브러리를 지정 하지 않은 경우 명령줄에서 지정한 것과 동일한 방식으로이 라이브러리를 검색 [`/nodefaultlib`](../build/reference/nodefaultlib-ignore-libraries.md) 합니다. 동일한 소스 파일에 여러 라이브러리 검색 레코드를 둘 수 있습니다. 각 레코드는 소스 파일에 있는 것과 동일한 순서로 개체 파일에 표시 됩니다.

기본 라이브러리와 추가 된 라이브러리의 순서가 중요 한 경우 스위치를 사용 하 여 컴파일하면 [`/Zl`](../build/reference/zl-omit-default-library-name.md) 기본 라이브러리 이름이 개체 모듈에 배치 되지 않습니다. 그런 다음 두 번째 주석을 pragma 사용 하 여 추가 된 라이브러리 다음에 기본 라이브러리의 이름을 삽입할 수 있습니다. 이러한 지시문을 사용 하 여 나열 된 라이브러리는 pragma 소스 코드에서 찾을 수 있는 것과 동일한 순서로 개체 모듈에 표시 됩니다.

### <a name="linker"></a>링커

개체 파일에 [링커 옵션](../build/reference/linker-options.md) 을 배치 합니다. 이 주석 형식을 이용하여 명령줄에 주석을 전달하거나 개발 환경에 지정하는 대신 링커 옵션을 지정할 수 있습니다. 예를 들어, /include 옵션을 지정하면 기호를 포함하도록 할 수 있습니다.

```C
#pragma comment(linker, "/include:__mySymbol")
```

다음 (*주석 형식*) 링커 옵션만 링커 식별자에 전달할 수 있습니다.

- [`/DEFAULTLIB`](../build/reference/defaultlib-specify-default-library.md)

- [`/EXPORT`](../build/reference/export-exports-a-function.md)

- [`/INCLUDE`](../build/reference/include-force-symbol-references.md)

- [`/MANIFESTDEPENDENCY`](../build/reference/manifestdependency-specify-manifest-dependencies.md)

- [`/MERGE`](../build/reference/merge-combine-sections.md)

- [`/SECTION`](../build/reference/section-specify-section-attributes.md)

### <a name="user"></a>사용자

일반 주석을 개체 파일에 배치합니다. *주석 문자열* 매개 변수에는 주석의 텍스트가 포함 됩니다. 이 주석 기록은 링커에 의해 무시됩니다.

## <a name="examples"></a>예

다음으로 pragma 인해 링커가 EMAPI를 검색 합니다. 연결 하는 동안 LIB 라이브러리. 링커는 현재 작업 디렉터리를 먼저 검색 한 다음 LIB 환경 변수에 지정 된 경로에서 검색 합니다.

```C
#pragma comment( lib, "emapi" )
```

컴파일러는 다음을 수행 pragma 하 여 컴파일러의 이름과 버전 번호를 개체 파일에 저장 합니다.

```C
#pragma comment( compiler )
```

*주석 문자열* 매개 변수를 사용 하는 주석의 경우 매크로를 문자열 리터럴로 확장 하기만 하면 문자열 리터럴을 사용 하는 모든 위치에서 매크로를 사용할 수 있습니다. 문자열 리터럴에 확장되는 문자열 리터럴 및 매크로의 조합을 연결할 수도 있습니다. 예를 들어, 다음 문을 사용할 수 있습니다.

```C
#pragma comment( user, "Compiled on " __DATE__ " at " __TIME__ )
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
