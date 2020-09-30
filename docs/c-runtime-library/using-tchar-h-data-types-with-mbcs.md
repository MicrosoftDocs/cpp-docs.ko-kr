---
title: _MBCS와 TCHAR.H 데이터 형식 사용
description: TCHAR.H를 사용할 때 Microsoft C 런타임 텍스트 루틴이 매핑되는 방법에 대 한 개요입니다. 멀티 바이트 상수를 사용 하는 H 데이터 형식 _MBCS.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- TCHAR.H data types
- MBCS data type
- _MBCS data type
ms.assetid: 48f471e7-9d2b-4a39-b841-16a0e15c0a18
ms.openlocfilehash: 001f745c03e4e0c0090e40c00c5394397028659f
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589954"
---
# <a name="using-tcharh-data-types-with-_mbcs"></a>_MBCS와 TCHAR.H 데이터 형식 사용

**Microsoft 전용**

일반 텍스트 루틴 매핑 표([일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md) 참조)에 나와 있듯이 **_MBCS** 매니페스트 상수가 정의되면 지정된 일반 텍스트 루틴은 다음 종류의 루틴 중 하나에 매핑됩니다.

- 멀티바이트 바이트, 문자 및 문자열을 적절하게 처리하는 SBCS 루틴. 이 경우 문자열 인수는 **char&#42;** 형식이어야 합니다. 예를 들어 **_tprintf**는 **printf**에 매핑되며, **printf**에 대한 문자열 인수는 **char&#42;** 형식입니다. 문자열 형식으로 **_TCHAR** 일반 텍스트 데이터 형식을 사용하는 경우, **_TCHAR&#42;** 이 **char&#42;** 에 매핑되므로 **printf**에 대한 공식 및 실제 매개 변수 형식은 일치합니다.

- MBCS 관련 루틴. 이 경우 문자열 인수는 __unsigned char&#42;__ 형식이어야 합니다. 예를 들어 **_tcsrev**는 **_mbsrev**에 매핑되며, __unsigned char&#42;__ 형식의 문자열을 반환합니다. 또한 문자열 형식에 대 한 **_TCHAR** 일반 텍스트 데이터 형식을 사용 하는 경우 **_TCHAR** 가 형식에 매핑되기 때문에 형식 충돌이 발생할 수 있습니다 **`char`** .

이러한 형식 충돌(및 이로 인한 C 컴파일러 경고 또는 C++ 컴파일러 오류)을 방지하기 위한 방법으로는 다음 세 가지가 있습니다.

- 기본 동작을 사용합니다. TCHAR.H는 다음 예제와 같이 런타임 라이브러리의 루틴에 일반 텍스트 루틴 프로토타입을 제공합니다.

   ```C
   char *_tcsrev(char *);
   ```

   기본적으로 **_tcsrev**에 대한 프로토타입은 LIBC.LIB의 썽크를 통해 **_mbsrev**에 매핑됩니다. 이렇게 하면 들어오는 **_mbsrev** 매개 변수 및 나가는 반환 값의 형식이 **_TCHAR &#42;**(예: **char &#42;**)에서 **unsigned char &#42;** 로 변경됩니다. 이 메서드는 **_TCHAR**을 사용 하는 경우 형식 일치를 보장 하지만 함수 호출 오버 헤드로 인해 상대적으로 느립니다.

- 코드에서 다음 전처리기 문을 통합하여 함수 인라인을 사용합니다.

   ```C
   #define _USE_INLINING
   ```

   이 방법을 사용하면 TCHAR.H에 제공된 인라인 함수 썽크가 일반 텍스트 루틴을 해당 MBCS 루틴에 직접 매핑합니다. TCHAR.H에서 발췌한 다음 코드는 이 방법의 에제를 제공합니다.

   ```C
   __inline char *_tcsrev(char *_s1)
   {return (char *)_mbsrev((unsigned char *)_s1);}
   ```

   인라인을 사용할 수 있는 경우 형식 일치가 보장되고 추가적으로 시간이 소요되지 않으므로 최선의 방법입니다.

- 코드에서 다음 전처리기 문을 통합하여 “직접 매핑"을 사용합니다.

   ```C
   #define _MB_MAP_DIRECT
   ```

   기본 동작을 사용 하지 않거나 인라인을 사용할 수 없는 경우이 방법을 사용 하면 빠른 대안이 제공 됩니다. 매크로는 TCHAR.H의 다음 예제와 같이 제네릭 텍스트 루틴을 MBCS 버전의 루틴에 매핑합니다.

   ```C
   #define _tcschr _mbschr
   ```

이 방법을 사용 하는 경우 문자열 인수 및 문자열 반환 값에 적절 한 데이터 형식이 사용 되도록 주의 해야 합니다. 형식 캐스팅을 사용하여 적절한 형식 일치를 보장하거나 **_TXCHAR** 일반 텍스트 데이터 형식을 사용할 수 있습니다. **_TXCHAR** 는 **`char`** SBCS 코드의 형식에 매핑되고 **`unsigned char`** MBCS 코드의 형식에 매핑됩니다. 일반 텍스트 매크로에 대한 자세한 내용은 [일반 텍스트 매핑](../c-runtime-library/generic-text-mappings.md)을 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[국제화](../c-runtime-library/internationalization.md)\
[범주별 유버니설 C 런타임 루틴](../c-runtime-library/run-time-routines-by-category.md)
