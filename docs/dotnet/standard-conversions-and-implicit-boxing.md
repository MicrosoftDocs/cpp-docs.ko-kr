---
description: '자세한 정보: 표준 변환 및 암시적 Boxing'
title: 표준 변환 및 암시적 boxing
ms.date: 11/04/2016
helpviewer_keywords:
- boxing, implicit
ms.assetid: 33f7fc7d-5674-44a2-a859-0e6a04fae519
ms.openlocfilehash: 9775effdae92ac9689bc7c08f2ba7887e6b54dbc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335354"
---
# <a name="standard-conversions-and-implicit-boxing"></a>표준 변환 및 암시적 boxing

Boxing이 필요한 변환에 대해 컴파일러에서 표준 변환을 선택 합니다.

## <a name="example"></a>예제

```cpp
// clr_implicit_boxing_Std_conversion.cpp
// compile with: /clr
int f3(int ^ i) {   // requires boxing
   return 1;
}

int f3(char c) {   // no boxing required, standard conversion
   return 2;
}

int main() {
   int i = 5;
   System::Console::WriteLine(f3(i));
}
```

```Output
2
```

## <a name="see-also"></a>참고 항목

[boxing](../extensions/boxing-cpp-component-extensions.md)
