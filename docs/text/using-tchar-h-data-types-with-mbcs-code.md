---
description: '자세히 알아보기: TCHAR.H 사용 _MBCS 코드를 포함 하는 H 데이터 형식'
title: _MBCS 코드와 TCHAR.H 데이터 형식 사용
ms.date: 11/04/2016
helpviewer_keywords:
- mapping generic-text
- generic-text data types [C++]
- generic-text mappings [C++]
- MBCS [C++], generic-text mappings
- TCHAR.H data types, mapping
- mappings [C++], TCHAR.H
ms.assetid: 298583c5-22c3-40f6-920e-9ec96d42abd8
ms.openlocfilehash: 4672ba210e0df0af1a4f4ee106d31cc978bdf2fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97306588"
---
# <a name="using-tcharh-data-types-with-_mbcs-code"></a>_MBCS 코드와 TCHAR.H 데이터 형식 사용

매니페스트 상수가 `_MBCS` 정의 되 면 지정 된 일반 텍스트 루틴이 다음 종류의 루틴 중 하나에 매핑됩니다.

- 멀티바이트 바이트, 문자 및 문자열을 적절하게 처리하는 SBCS 루틴. 이 경우 문자열 인수는 형식 이어야 **`char*`** 합니다. 예를 들어는 `_tprintf` 에 매핑됩니다. `printf` 에 대 한 문자열 인수는 `printf` 형식입니다 **`char*`** . `_TCHAR`문자열 형식에 대해 일반 텍스트 데이터 형식을 사용 하는 경우와 일치 하는 형식 및 실제 매개 변수 형식은에 `printf` `_TCHAR*` 매핑됩니다 **`char*`** .

- MBCS 관련 루틴. 이 경우 문자열 인수는 `unsigned char*` 형식이어야 합니다. 예를 들어 `_tcsrev`는 `unsigned char*` 형식의 문자열을 사용하고 반환하는 `_mbsrev`에 매핑됩니다. `_TCHAR`문자열 형식에 대해 일반 텍스트 데이터 형식을 사용 하는 경우가 형식에 매핑되므로 형식 충돌이 발생할 수 있습니다 `_TCHAR` **`char`** .

이러한 형식 충돌(및 이로 인한 C 컴파일러 경고 또는 C++ 컴파일러 오류)을 방지하기 위한 방법으로는 다음 세 가지가 있습니다.

- 기본 동작을 사용합니다. tchar.h는 다음 예제와 같이 런타임 라이브러리의 루틴에 대 한 일반 텍스트 루틴 프로토타입을 제공 합니다.

    ```cpp
    char * _tcsrev(char *);
    ```

   기본 경우의 프로토타입은 `_tcsrev` `_mbsrev` Libc의 썽크를 통해에 매핑됩니다. 이렇게 하면 `_mbsrev` 들어오는 매개 변수 및 나가는 반환 값의 형식이에서 `_TCHAR*` 로 변경 됩니다 `char *` `unsigned char *` . 이 메서드는를 사용할 때 형식 일치를 보장 `_TCHAR` 하지만 함수 호출 오버 헤드로 인해 상대적으로 느립니다.

- 코드에서 다음 전처리기 문을 통합하여 함수 인라인을 사용합니다.

    ```cpp
    #define _USE_INLINING
    ```

   이 메서드는 tchar.h에 제공 되는 인라인 함수 썽크를 발생 하 여 제네릭 텍스트 루틴을 적절 한 MBCS 루틴에 직접 매핑합니다. Tchar.h의 다음 코드에서는이 작업을 수행 하는 방법의 예를 제공 합니다.

    ```cpp
    __inline char *_tcsrev(char *_s1)
    {return (char *)_mbsrev((unsigned char *)_s1);}
    ```

   인라인을 사용할 수 있는 경우 형식 일치가 보장되고 추가적으로 시간이 소요되지 않으므로 최선의 방법입니다.

- 코드에서 다음 전처리기 문을 통합 하 여 직접 매핑을 사용 합니다.

    ```cpp
    #define _MB_MAP_DIRECT
    ```

   기본 동작을 사용하지 않으려고 하거나 인라인을 사용할 수 없는 경우 이 방법이 가장 빠른 대안입니다. Tchar.h의 다음 예제와 같이 제네릭 텍스트 루틴이 매크로를 통해 MBCS 버전의 루틴에 직접 매핑됩니다.

    ```cpp
    #define _tcschr _mbschr
    ```

   이 방법을 사용 하는 경우 문자열 인수 및 문자열 반환 값에 적절 한 데이터 형식을 사용 하도록 주의 해야 합니다. 형식 캐스팅을 사용하여 적절한 형식 일치를 보장하거나 `_TXCHAR` 일반 텍스트 데이터 형식을 사용할 수 있습니다. `_TXCHAR`**`char`** SBCS 코드의 형식에 매핑되고 **`unsigned char`** MBCS 코드의 형식에 매핑됩니다. 일반 텍스트 매크로에 대 한 자세한 내용은 *런타임 라이브러리 참조* 에서 [일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)
