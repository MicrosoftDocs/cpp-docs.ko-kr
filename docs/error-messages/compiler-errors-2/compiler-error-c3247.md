---
description: '자세한 정보: 컴파일러 오류 C3247'
title: 컴파일러 오류 C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: 02e8f20f9804067e0179f3b5583d589d16dae302
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307191"
---
# <a name="compiler-error-c3247"></a>컴파일러 오류 C3247

'class1': coclass는 다른 coclass 'class2'에서 상속할 수 없습니다.

[coclass](../../windows/attributes/coclass.md) 특성으로 표시된 클래스는 `coclass` 특성으로 표시된 다른 클래스에서 상속할 수 없습니다.

다음 샘플에서는 C3247을 생성합니다.

```cpp
// C3247.cpp
[module(name="MyLib")];
[coclass]
class a {
};

[coclass]
class b : public a {   // C3247
};
int main() {
}
```
