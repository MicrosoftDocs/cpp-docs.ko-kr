---
description: '자세한 정보: 컴파일러 오류 C3189'
title: 컴파일러 오류 C3189
ms.date: 11/04/2016
f1_keywords:
- C3189
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
ms.openlocfilehash: 9253a1d4333a7454bfbff5442cfaa5a24ebc68ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97242004"
---
# <a name="compiler-error-c3189"></a>컴파일러 오류 C3189

' typeid \<type abstract declarator> ':이 구문은 더 이상 지원 되지 않습니다. 대신:: typeid를 사용 하십시오.

사용 되지 않는 [typeid](../../extensions/typeid-cpp-component-extensions.md) 형식이 사용 되었습니다. 새 양식을 사용 합니다.

다음 샘플에서는 C3189를 생성 합니다.

```cpp
// C3189.cpp
// compile with: /clr
int main() {
   System::Type^ t  = typeid<System::Object>;   // C3189
   System::Type^ t2  = System::Object::typeid;   // OK
}
```
