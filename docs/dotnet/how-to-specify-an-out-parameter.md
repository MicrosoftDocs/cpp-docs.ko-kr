---
description: '자세한 정보: 방법: out 매개 변수 지정'
title: '방법: out 매개 변수 지정'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: b43930557b4bdfd22bf902a6d9adf95eb8ba4d01
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286340"
---
# <a name="how-to-specify-an-out-parameter"></a>방법: out 매개 변수 지정

이 샘플에서는 함수 매개 변수를 매개 변수로 지정 하는 방법 `out` 및 c # 프로그램에서 해당 함수를 호출 하는 방법을 보여 줍니다.

`out`매개 변수는를 사용 하 여 c + +로 지정 됩니다 <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="example"></a>예제

이 샘플의 첫 번째 부분에서는 c + + DLL을 만듭니다. 매개 변수를 사용 하 여 함수를 포함 하는 형식을 정의 `out` 합니다.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

이 소스 파일은 이전 예제에서 만든 c + + 구성 요소를 사용 하는 c # 클라이언트입니다.

```csharp
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>참고 항목

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
