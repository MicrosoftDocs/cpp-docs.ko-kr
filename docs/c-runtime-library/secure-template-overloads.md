---
title: 안전한 템플릿 오버로드
description: 보안이 강화 된 기능을 제공 하는 Microsoft C 런타임 템플릿 오버 로드에 대 한 설명입니다.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
helpviewer_keywords:
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES
- _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES
- _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT
- secure template overloads
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
ms.openlocfilehash: 69ddeed831bde26de23e0a29ece9f5550de8cf9f
ms.sourcegitcommit: 90c300b74f6556cb5d989802d2e80d79542f55e7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2021
ms.locfileid: "102514527"
---
# <a name="secure-template-overloads"></a>안전한 템플릿 오버로드

Microsoft는 여러 CRT(C 런타임) 라이브러리 함수를 보안이 강화된 버전으로 대체했습니다. 예를 들어 `strcpy_s`가 `strcpy`보다 더 안전합니다. 사용 되지 않는 함수는 메모리를 덮어쓸 수 있는 작업을 차단 하지 않기 때문에 보안 버그의 일반적인 소스입니다. 기본적으로 컴파일러는 이러한 함수 중 하나를 사용할 때 사용 중단 경고를 생성합니다. CRT는 더 안전한 변형으로 쉽게 전환할 수 있도록 이러한 함수에 대한 C++ 템플릿 오버로드를 제공합니다.

예를 들어 이 코드 조각은 `strcpy`가 더 이상 사용되지 않기 때문에 경고를 생성합니다.

```cpp
char szBuf[10];
strcpy(szBuf, "test"); // warning: deprecated
```

코드가 안전하지 않을 수 있다는 것을 알리는 사용 중단 경고가 있습니다. 코드에서 메모리를 덮어쓸 수 없는 것으로 확인 된 경우 여러 가지 옵션을 선택할 수 있습니다. 경고를 무시하거나, 경고를 표시하지 않도록 CRT에 대한 include 문 앞에 기호 `_CRT_SECURE_NO_WARNINGS`를 정의하거나, `strcpy_s`를 사용하도록 코드를 업데이트할 수 있습니다.

```cpp
char szBuf[10];
strcpy_s(szBuf, 10, "test"); // security-enhanced _s function
```

템플릿 오버로드는 추가 옵션을 제공합니다. `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES`를 1로 정의하면 더 안전한 변형을 자동으로 호출하는 표준 CRT 함수의 템플릿 오버로드가 사용하도록 설정됩니다. `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES`가 1이면 코드를 변경할 필요가 없습니다. 내부적으로 `strcpy`에 대한 호출은 자동으로 제공된 크기 인수를 사용하는 `strcpy_s`에 대한 호출로 변경됩니다.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char szBuf[10];
strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

매크로는 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 와 같이 개수를 사용 하는 함수에 영향을 주지 않습니다 `strncpy` . 개수 함수에 대한 템플릿 오버로드를 사용하도록 설정하려면 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT`를 1로 정의합니다. 그러나 이러한 작업을 수행하기 전에 코드가 버퍼의 크기가 아닌(일반적인 실수) 문자 개수를 전달하는지 확인해야 합니다. 또한 안전한 변형이 호출되는 경우 함수 호출 이후 명시적으로 버퍼의 끝에 null 종결자를 쓰는 코드는 필요하지 않습니다. 잘라내기 동작이 필요한 경우 [_TRUNCATE](../c-runtime-library/truncate.md)를 참조하세요.

> [!NOTE]
> `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 매크로의 경우 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES`도 1로 정의되어야 합니다. `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT`가 1로 정의되고 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES`가 0으로 정의되는 경우 애플리케이션은 템플릿 오버로드를 수행하지 않습니다.

`_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES`를 1로 정의하면 안전한 변형(“_s”로 끝나는 이름)의 템플릿 오버로드가 사용하도록 설정됩니다. 이 경우 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES`가 1이면 원본 코드에서 작은 변경 작업이 하나 수행되어야 합니다.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char szBuf[10];
strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")
```

“_s”를 추가하여 함수 이름만 변경해야 합니다. 템플릿 오버로드는 크기 인수를 제공합니다.

기본적으로 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 및 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT`가 0(해제)으로 정의되고 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES`가 1(설정)로 정의됩니다.

이러한 템플릿 오버 로드는 정적 배열에 대해서만 작동 합니다. 동적으로 할당된 버퍼의 경우 추가 소스 코드 변경이 필요합니다. 위 예제를 다시 봅니다.

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy(szBuf, "test"); // still deprecated; change it to
                       // strcpy_s(szBuf, 10, "test");
```

또 다른 예제:

```cpp
#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1

// ...

char *szBuf = (char*)malloc(10);
strcpy_s(szBuf, "test"); // doesn't compile; change it to
                         // strcpy_s(szBuf, 10, "test");
```

## <a name="see-also"></a>추가 정보

[CRT의 보안 기능](../c-runtime-library/security-features-in-the-crt.md)<br/>
[CRT (c 런타임) 및 STL (c + + 표준 라이브러리) `.lib` 파일](../c-runtime-library/crt-library-features.md)
