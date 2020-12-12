---
description: '자세한 정보: 컴파일러 경고 (수준 3 및 4) C4244'
title: 컴파일러 경고(수준 3 및 4) C4244
ms.date: 11/04/2016
ms.assetid: f116bb09-c479-4b4e-a647-fe629a1383f6
ms.openlocfilehash: 60c23dde99a74dd47d2a01d60ac97d1214dc13d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97285151"
---
# <a name="compiler-warning-levels-3-and-4-c4244"></a>컴파일러 경고(수준 3 및 4) C4244

'conversion': 'type1'에서 'type2'(으)로 변환하면서 데이터가 손실될 수 있습니다.

정수 형식은 더 작은 정수 형식으로 변환됩니다. *Type1* 이이 **`int`** 고 *type2* 가 보다 작은 경우이는 수준 4 경고입니다 **`int`** . 그렇지 않으면 수준 3 (형식의 변수에 [__int64](../../cpp/int8-int16-int32-int64.md) 형식 값이 할당 됨 **`unsigned int`** )입니다. 데이터 손실이 발생했을 수 있습니다.

C4244 오류가 발생하는 경우 호환되는 형식을 사용하도록 프로그램을 변경하거나 코드에 일부 논리를 추가하여 가능한 값의 범위가 사용 중인 형식과 항상 호환되는지 확인해야 합니다.

C4244는 수준 2에서 발생 시킬 수도 있습니다. 자세한 내용은 [컴파일러 경고 (수준 2) C4244](../../error-messages/compiler-warnings/compiler-warning-level-2-c4244.md) 를 참조 하세요.

암시적 변환으로 인해 변환에 문제가 있을 수 있습니다.

다음 샘플에서는 C4244 오류가 발생하는 경우를 보여 줍니다.

```cpp
// C4244_level4.cpp
// compile with: /W4
int aa;
unsigned short bb;
int main() {
   int b = 0, c = 0;
   short a = b + c;   // C4244

   bb += c;   // C4244
   bb = bb + c;   // C4244
   bb += (unsigned short)aa;   // C4244
   bb = bb + (unsigned short)aa;   // OK
}
```

자세한 내용은 [일반적인 산술 변환](../../c-language/usual-arithmetic-conversions.md)을 참조 하세요.

```cpp
// C4244_level3.cpp
// compile with: /W3
int main() {
   __int64 i = 8;
   unsigned int ii = i;   // C4244
}
```

32비트 대상에 대해 빌드할 때 경고를 생성하지 않는 코드를 64비트 대상에 대해 빌드하는 경우 C4244 경고가 발생할 수 있습니다. 예를 들어 포인터 간 차이가 32비트 플랫폼에서는 32비트 수량이지만 64비트 플랫폼에서는 64비트 수량입니다.

다음 샘플에서는 64비트 대상에 대해 컴파일하는 경우 C4244 오류가 발생합니다.

```cpp
// C4244_level3_b.cpp
// compile with: /W3
int main() {
   char* p1 = 0;
   char* p2 = 0;
   int x = p2 - p1;   // C4244
}
```
