---
description: '다음에 대 한 자세한 정보: `__uuidof` 연산자'
title: __uuidof 연산자
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: e6c14ac6f00b5e6314e1e4d844aea479fa714984
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97116719"
---
# <a name="__uuidof-operator"></a>`__uuidof` 연산자

**Microsoft 전용**

식에 연결된 GUID를 검색합니다.

## <a name="syntax"></a>Syntax

> **`__uuidof (`***식***`)`**

## <a name="remarks"></a>설명

*식은* 형식 이름, 포인터, 참조 또는 해당 형식의 배열, 이러한 형식에 대해 특수화 된 템플릿 또는 이러한 형식의 변수 일 수 있습니다. 컴파일러에서 인수를 사용하여 연결된 GUID를 찾을 수 있으면 해당 인수는 유효합니다.

이 내장 함수의 특수 한 경우는 **0** 또는 NULL이 인수로 제공 되는 경우입니다. 이 경우 **`__uuidof`** 는 0으로 구성 된 GUID를 반환 합니다.

이 키워드를 사용하여 연결된 GUID를 다음으로 추출합니다.

- 확장 특성에의 한 개체 [`uuid`](../cpp/uuid-cpp.md) 입니다.

- 특성을 사용 하 여 만든 라이브러리 블록 [`module`](../windows/attributes/module-cpp.md) 입니다.

> [!NOTE]
> 디버그 빌드에서는 **`__uuidof`** 항상 개체를 동적으로 초기화 합니다 (런타임에). 릴리스 빌드에서는 **`__uuidof`** 컴파일 타임에 정적으로 개체를 초기화할 수 있습니다.

이전 버전과의 호환성을 위해 **`_uuidof`** 는 **`__uuidof`** 컴파일러 옵션 [ `/Za` \( 언어 확장 사용 안 함](../build/reference/za-ze-disable-language-extensions.md) 을 지정 하지 않는 경우의 동의어입니다.

## <a name="example"></a>예제

ole32.lib를 사용하여 컴파일된 다음 코드는 module 특성을 사용하여 만든 라이브러리 블록의 uuid를 표시합니다.

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>의견

라이브러리 이름이 더 이상 범위에 없는 경우 대신을 사용할 수 있습니다 `__LIBID_` **`__uuidof`** . 예를 들어:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)
