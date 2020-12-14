---
description: '자세한 정보: 컴파일러 오류 C3278'
title: 컴파일러 오류 C3278
ms.date: 11/04/2016
f1_keywords:
- C3278
helpviewer_keywords:
- C3278
ms.assetid: 56f818f5-85a6-4792-843b-54fe16327658
ms.openlocfilehash: cdbb53b4f11357ae9058d9a5ebc3882c8701fc88
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228965"
---
# <a name="compiler-error-c3278"></a>컴파일러 오류 C3278

> 인터페이스 또는 순수 메서드 '*method*'의 직접 호출이 런타임에 실패 합니다.

## <a name="remarks"></a>설명

인터페이스 메서드 또는 순수 메서드를 호출했지만 허용되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3278을 생성합니다.

```cpp
// C3278_2.cpp
// compile with: /clr
using namespace System;
interface class I
{
   void vmf();
};

public ref class C: public I
{
public:
   void vmf()
   {
      Console::WriteLine( "In C::vmf()" );
      I::vmf(); // C3278
   }

};

int main()
{
   C^ pC = gcnew C;
   pC->vmf();
}
```
