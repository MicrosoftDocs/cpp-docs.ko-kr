---
description: '자세한 정보: 컴파일러 오류 C3808'
title: 컴파일러 오류 C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: e5d31e884de0b04caba7c52e8d6abc01b3d21a35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315155"
---
# <a name="compiler-error-c3808"></a>컴파일러 오류 C3808

> '*type*': ComImport 특성이 있는 클래스는 '*member*' 멤버를 정의할 수 없습니다. abstract 또는 dllimport 함수만 사용할 수 있습니다.

## <a name="remarks"></a>설명

에서 파생 된 형식은 <xref:System.Runtime.InteropServices.ComImportAttribute> *멤버* 를 정의할 수 없습니다.

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3808를 생성 합니다.

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```
