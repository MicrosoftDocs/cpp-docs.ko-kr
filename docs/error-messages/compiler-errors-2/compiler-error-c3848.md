---
description: '자세한 정보: 컴파일러 오류 C3848'
title: 컴파일러 오류 C3848
ms.date: 11/04/2016
f1_keywords:
- C3848
helpviewer_keywords:
- C3848
ms.assetid: 32d3ccef-01ec-4f8b-bbff-fb9b1a76b4c4
ms.openlocfilehash: 8bd81f59927dd1b34c23148dd1e9bd69ec715609
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255381"
---
# <a name="compiler-error-c3848"></a>컴파일러 오류 C3848

' t r u e ' 형식의 식에서 ' function '을 호출 하기 위해 일부 const volatile 한정자가 손실 됩니다.

지정 된 const volatile 형식의 변수는 동일 하거나 더 큰 const volatile 자격으로 정의 된 멤버 함수만 호출할 수 있습니다.

다음 샘플에서는 C3848를 생성 합니다.

```cpp
// C3848.cpp
void glbFunc1()
{
}

typedef void (* pFunc1)();

struct S3
{
   operator pFunc1() // const
   {
      return &glbFunc1;
   }
};

int main()
{
   const S3 s3;
   s3();   // C3848, uncomment const qualifier
}
```
