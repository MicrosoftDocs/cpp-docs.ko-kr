---
description: Messages_base 클래스에 대해 자세히 알아보세요.
title: messages_base 클래스
ms.date: 11/04/2016
f1_keywords:
- xlocmes/std::messages_base
helpviewer_keywords:
- messages_base class
ms.assetid: 9aad38c6-4c13-445d-b096-364bd0836efb
ms.openlocfilehash: 45ea81b02bd15011c9f98b9364ea9918e248692a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97230590"
---
# <a name="messages_base-class"></a>messages_base 클래스

기본 클래스는 **`int`** 메시지 카탈로그에 대 한 형식을 설명 합니다.

## <a name="syntax"></a>구문

```cpp
struct messages_base : locale::facet {
    typedef int catalog;
    explicit messages_base(size_t _Refs = 0)
};
```

## <a name="remarks"></a>설명

형식 카탈로그는 **`int`** messages:: [do_open](../standard-library/messages-class.md#do_open)에서 가능한 반환 값을 설명 하는 형식의 동의어입니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<locale>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
