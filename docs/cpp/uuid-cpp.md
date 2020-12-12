---
description: '자세한 정보: uuid (c + +)'
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c841bb1813769ab70e756fe4edb7fd351c1dbc49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116732"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft 전용**

컴파일러는 특성을 사용 하 여 선언 되거나 정의 된 클래스 또는 구조체 (전체 COM 개체 정의에만 해당)에 GUID를 연결 합니다 **`uuid`** .

## <a name="syntax"></a>구문

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>설명

**`uuid`** 특성은 문자열을 인수로 사용 합니다. 이 문자열은 **{}** 구분 기호를 사용 하거나 사용 하지 않고 일반 레지스트리 형식으로 GUID의 이름을 지정 합니다. 예를 들어:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

재선언에서 이 특성을 적용할 수 있습니다. 이를 통해 시스템 헤더는와 같은 인터페이스 정의를 제공 하 `IUnknown` 고, 다른 헤더 (예:)의 재선언을 제공 하 여 GUID를 제공할 수 있습니다 \<comdef.h> .

[__Uuidof](../cpp/uuidof-operator.md) 키워드를 적용 하 여 사용자 정의 형식에 연결 된 상수 GUID를 검색할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__declspec](../cpp/declspec.md)<br/>
[키워드](../cpp/keywords-cpp.md)
