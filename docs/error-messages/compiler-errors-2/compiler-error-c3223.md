---
description: '자세한 정보: 컴파일러 오류 C3223'
title: 컴파일러 오류 C3223
ms.date: 11/04/2016
f1_keywords:
- C3223
helpviewer_keywords:
- C3223
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
ms.openlocfilehash: d768bba53634e3614ba4dc583cb57d2d16e744fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267692"
---
# <a name="compiler-error-c3223"></a>컴파일러 오류 C3223

'property': 속성에 'typeid'를 적용할 수 없습니다.

속성에 [typeid](../../extensions/typeid-cpp-component-extensions.md) 를 적용할 수 없습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3223을 생성합니다.

```cpp
// C3223.cpp
// compile with: /clr
ref class R {
public:
   property int myprop;
};

int main() {
   System::Type^ type2 = R::myprop::typeid;   // C3223
}
```
