---
description: '자세한 정보: 링커 도구 오류 LNK2005'
title: 링커 도구 오류 LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: c6de300bc731104f51056911515d0cc7a95e05f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338495"
---
# <a name="linker-tools-error-lnk2005"></a>링커 도구 오류 LNK2005

> 개체에 *기호가* 이미 정의 되어 있습니다.

기호 *기호가* 두 번 이상 정의 되었습니다.

이 오류 다음에는 심각한 오류 [LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)이 발생 합니다.

### <a name="possible-causes-and-solutions"></a>가능한 원인 및 해결 방법

일반적으로이 오류는 특정 개체 파일에서 사용 되는 템플릿, 함수, 형식 또는 개체에 대해 하나의 정의만 허용 하 고 외부에서 볼 수 있는 개체 또는 함수의 전체 실행 파일에 대해 하나의 정의만 허용 하는 *정의 규칙 하나* 를 중단 했음을 의미 합니다.

이 오류의 몇 가지 일반적인 원인은 다음과 같습니다.

- 헤더 파일에서 변수를 정의 하는 경우이 오류가 발생할 수 있습니다. 예를 들어 프로젝트의 둘 이상의 소스 파일에이 헤더 파일을 포함 하는 경우 오류가 발생 합니다.

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   가능한 솔루션은 다음과 같습니다.

  - 헤더 파일에서 변수를 선언 하 고 **`extern`** `extern int global_int;` , 정의 하 고, 필요에 따라 소스 파일 하나에만 초기화 `int global_int = 17;` 합니다. 이 변수는 이제 헤더 파일을 포함 하 여 모든 소스 파일에서 선언 하 여 사용할 수 있는 전역입니다 **`extern`** . 전역적 이어야 하는 변수에는이 솔루션을 권장 하지만 좋은 소프트웨어 엔지니어링 방법은 글로벌 변수를 최소화 하는 것입니다.

  - [정적](../../cpp/storage-classes-cpp.md#static)변수를 선언 `static int static_int = 17;` 합니다. 이는 정의의 범위를 현재 개체 파일로 제한 하 고 여러 개체 파일에서 고유한 변수 복사본을 가질 수 있도록 합니다. 전역 변수와 혼동 될 수 있으므로 헤더 파일에 정적 변수를 정의 하지 않는 것이 좋습니다. 정적 변수 정의를이를 사용 하는 소스 파일로 이동 하는 것이 좋습니다.

  - [Selectany](../../cpp/selectany.md)변수를 `__declspec(selectany) int global_int = 17;` 선언 합니다. 이렇게 하면 링커에서 모든 외부 참조에서 사용할 정의를 하나 선택 하 고 나머지를 삭제할 수 있습니다. 이 솔루션은 가져오기 라이브러리를 결합할 때 유용할 수 있습니다. 그렇지 않으면 링커 오류를 방지 하는 방법으로 사용 하지 않는 것이 좋습니다.

- 헤더 파일이이 아닌 함수를 정의 하는 경우이 오류가 발생할 수 있습니다 **`inline`** . 이 헤더 파일을 둘 이상의 소스 파일에 포함 하는 경우 실행 파일에서 함수에 대 한 여러 정의를 가져옵니다.

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   가능한 솔루션은 다음과 같습니다.

  - **`inline`** 함수에 키워드를 추가 합니다.

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - 헤더 파일에서 함수 본문을 제거 하 고 선언만 유지 한 다음 하나의 소스 파일에만 함수를 구현 합니다.

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- 헤더 파일의 클래스 선언 외부에 멤버 함수를 정의 하는 경우에도이 오류가 발생할 수 있습니다.

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   이 문제를 해결 하려면 멤버 함수 정의를 클래스 내에서 이동 합니다. 클래스 선언 내에 정의 된 멤버 함수는 암시적으로 인라인 됩니다.

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 이 오류는 표준 라이브러리 또는 CRT의 둘 이상의 버전을 연결 하는 경우에 발생할 수 있습니다. 예를 들어 정품 및 디버그 CRT 라이브러리나 라이브러리의 정적 및 동적 버전을 모두 또는 두 개의 다른 버전의 표준 라이브러리를 실행 하는 경우이 오류가 여러 번 보고 될 수 있습니다. 이 문제를 해결 하려면 링크 명령에서 각 라이브러리의 복사본을 하나만 제외 하 고 모두 제거 합니다. 일반 정품 및 디버그 라이브러리나 라이브러리의 다른 버전을 동일한 실행 파일에 혼합 하지 않는 것이 좋습니다.

   링커에서 기본값 이외의 라이브러리를 사용 하도록 지시 하려면 명령줄에서 사용할 라이브러리를 지정 하 고 [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) 옵션을 사용 하 여 기본 라이브러리를 사용 하지 않도록 설정 합니다. IDE에서 프로젝트에 대 한 참조를 추가 하 여 사용할 라이브러리를 지정 하 고 프로젝트에 대 한 **속성 페이지** 대화 상자를 연 다음 **링커** 의 **입력** 속성 페이지에서 **모든 기본 라이브러리 무시** 또는 **특정 기본 라이브러리 무시** 속성을 기본 라이브러리를 사용 하지 않도록 설정으로 설정 합니다.

- [/Clr](../../build/reference/clr-common-language-runtime-compilation.md) 옵션을 사용 하는 경우 정적 라이브러리와 동적 라이브러리를 함께 사용 하는 경우이 오류가 발생할 수 있습니다. 예를 들어 정적 CRT에 연결 되는 실행 파일에서 사용할 DLL을 빌드하는 경우이 오류가 발생할 수 있습니다. 이 문제를 해결 하려면 정적 라이브러리 또는 전체 실행 파일에 대해 동적 라이브러리만 사용 하 고 실행 파일에서 사용 하기 위해 빌드하는 라이브러리에만 사용 합니다.

- 이 오류는 기호가 [/gy](../../build/reference/gy-enable-function-level-linking.md)로 컴파일하여 생성 된 패키지 함수이 고 둘 이상의 파일에 포함 되었지만 컴파일 간에 변경 된 경우에 발생할 수 있습니다. 이 문제를 해결 하려면 패키지 함수를 포함 하는 모든 파일을 다시 컴파일하십시오.

- 이 오류는 다른 라이브러리의 두 멤버 개체에서 기호가 다르게 정의 되 고 두 멤버 개체가 모두 사용 되는 경우에 발생할 수 있습니다. 라이브러리가 정적으로 연결 된 경우이 문제를 해결 하는 한 가지 방법은 한 라이브러리의 멤버 개체를 사용 하 고 링커 명령줄에 해당 라이브러리를 먼저 포함 하는 것입니다. 두 기호를 모두 사용 하려면 구분 하는 방법을 만들어야 합니다. 예를 들어 원본에서 라이브러리를 빌드할 수 있는 경우 각 라이브러리를 고유한 네임 스페이스로 래핑할 수 있습니다. 또는 고유 이름을 사용 하 여 참조를 원래 라이브러리 중 하나로 래핑하고 새 라이브러리를 원본 라이브러리에 연결한 다음 원래 라이브러리 대신 새 라이브러리에 실행 파일을 연결 하는 새 래퍼 라이브러리를 만들 수 있습니다.

- `extern const`변수를 두 번 정의 하 고 각 정의에 다른 값이 있는 경우이 오류가 발생할 수 있습니다. 이 문제를 해결 하려면 상수를 한 번만 정의 하거나 네임 스페이스 또는 **`enum class`** 정의를 사용 하 여 상수를 구분 합니다.

- Guid (예: oledb 및 adsiid .lib)를 정의 하는 다른 .lib 파일과 함께 uuid를 사용 하는 경우이 오류가 발생할 수 있습니다. 예를 들어:

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   이 문제를 해결 하려면 링커 명령줄 옵션에 [/force: MULTIPLE](../../build/reference/force-force-file-output.md) 을 추가 하 고, uuid가 첫 번째로 참조 된 라이브러리 인지 확인 합니다.
