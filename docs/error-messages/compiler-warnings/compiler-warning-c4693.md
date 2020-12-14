---
description: '자세한 정보: 컴파일러 경고 C4693'
title: 컴파일러 경고 C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 114809e1f73eb3d4e3481f0baa348d5eb478f4f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315103"
---
# <a name="compiler-warning-c4693"></a>컴파일러 경고 C4693

> 'class': 봉인 추상 클래스는 인스턴스 멤버 'Test'를 포함할 수 없습니다.

형식이 [sealed](../../extensions/sealed-cpp-component-extensions.md) 및 [abstract](../../extensions/abstract-cpp-component-extensions.md)로 표시 되는 경우 정적 멤버만 포함할 수 있습니다.

이 경고는 자동으로 오류로 승격 됩니다. 이 동작을 수정 하려는 경우 [#pragma 경고](../../preprocessor/warning.md)를 사용 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4693을 생성합니다.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```
