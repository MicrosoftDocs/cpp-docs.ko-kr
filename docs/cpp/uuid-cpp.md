---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511659"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 전용**

컴파일러는 클래스 또는 구조체 선언 또는 정의 된 (전체 COM 개체 정의 해당)에 GUID를 연결 합니다 **uuid** 특성입니다.

## <a name="syntax"></a>구문

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>설명

합니다 **uuid** 특성 인수로 문자열을 사용 합니다. 이 문자열 하거나 사용 하지 않고 일반 레지스트리 형식으로 GUID 이름을 지정 합니다 **{}** 구분 기호입니다. 예를 들어:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

재선언에서 이 특성을 적용할 수 있습니다. 와 같은 인터페이스의 정의 제공 하는 시스템 헤더를 사용 하면이 `IUnknown`, 및 일부 다른 헤더의 재선언 (같은 \<comdef.h >) GUID를 제공 합니다.

키워드 [__uuidof](../cpp/uuidof-operator.md) 사용자 정의 형식에 연결 된 GUID 상수를 검색에 적용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고자료

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)