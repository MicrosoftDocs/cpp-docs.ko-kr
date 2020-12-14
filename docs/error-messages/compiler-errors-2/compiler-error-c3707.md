---
description: '자세한 정보: 컴파일러 오류 C3707'
title: 컴파일러 오류 C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 77a1193eae9b9d0158065978438b5af1d2176d12
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241848"
---
# <a name="compiler-error-c3707"></a>컴파일러 오류 C3707

' function ': 서 수 메서드에는 dispid가 있어야 합니다.

메서드를 사용 하는 경우 `dispinterface` 에는 해당 메서드를 할당 해야 합니다 `dispid` . 이 오류를 해결 하려면를 `dispid` 메서드에 할당 합니다 `dispinterface` . 예를 들어 `id` 아래 샘플의 메서드에 대 한 특성을 주석 처리 합니다. 자세한 [내용은 특성 특성](../../windows/attributes/dispinterface.md) 및 [id](../../windows/attributes/id.md)를 참조 하십시오.

다음 샘플에서는 C3707를 생성 합니다.

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
