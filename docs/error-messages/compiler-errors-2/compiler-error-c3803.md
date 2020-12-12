---
description: '자세한 정보: 컴파일러 오류 C3803'
title: 컴파일러 오류 C3803
ms.date: 11/04/2016
f1_keywords:
- C3803
helpviewer_keywords:
- C3803
ms.assetid: bad5fb9a-ed9a-4c15-96e7-cf06e200a50d
ms.openlocfilehash: 23b3c9f38470bca471910bb31f7a0acbdf14693e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291560"
---
# <a name="compiler-error-c3803"></a>컴파일러 오류 C3803

' property ': 속성에 해당 접근자 ' accessor ' 중 하 나와 호환 되지 않는 형식이 있습니다.

[속성](../../cpp/property-cpp.md) 으로 정의 된 속성 형식이 해당 접근자 함수 중 하나의 반환 형식과 일치 하지 않습니다.

다음 샘플에서는 C3803를 생성 합니다.

```cpp
// C3803.cpp
struct A
{
   __declspec(property(get=GetIt)) int i;
   char GetIt()
   {
      return 0;
   }

   /*
   // try the following definition instead
   int GetIt()
   {
      return 0;
   }
   */
}; // C3803

int main()
{
}
```
