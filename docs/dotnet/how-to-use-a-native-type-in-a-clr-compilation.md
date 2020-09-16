---
title: 방법:-clr 컴파일에서 네이티브 형식 사용
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- compilation, native types in /clr
- /clr compiler option [C++], using native types
ms.assetid: 3a505c90-4adb-4942-9cf9-7d1fdcbc01e7
ms.openlocfilehash: 88a678a19043d3229218dd69afbf8548348817df
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90683964"
---
# <a name="how-to-use-a-native-type-in-a-clr-compilation"></a>방법: /clr 컴파일에 네이티브 형식 사용

**/Clr** 컴파일에서 네이티브 형식을 정의할 수 있으며, 어셈블리 내에서 해당 네이티브 형식을 사용 하는 것은 유효 합니다. 그러나 참조 된 메타 데이터에서는 네이티브 형식을 사용할 수 없습니다.

각 어셈블리에는 사용할 모든 네이티브 형식의 정의가 포함 되어야 합니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)를 참조 하세요.

## <a name="examples"></a>예제

이 샘플에서는 네이티브 형식을 정의 하 고 사용 하는 구성 요소를 만듭니다.

```cpp
// use_native_type_in_clr.cpp
// compile with: /clr /LD
public struct NativeClass {
   static int Test() { return 98; }
};

public ref struct ManagedClass {
   static int i = NativeClass::Test();
   void Test() {
      System::Console::WriteLine(i);
   }
};
```

이 샘플에서는 구성 요소를 사용 하는 클라이언트를 정의 합니다. Compiland에 정의 되지 않은 경우 네이티브 형식에 액세스 하는 것은 오류입니다.

```cpp
// use_native_type_in_clr_2.cpp
// compile with: /clr
#using "use_native_type_in_clr.dll"
// Uncomment the following 3 lines to resolve.
// public struct NativeClass {
//    static int Test() { return 98; }
// };

int main() {
   ManagedClass x;
   x.Test();

   System::Console::WriteLine(NativeClass::Test());   // C2653
}
```

## <a name="see-also"></a>추가 정보

[C + + Interop 사용 (암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
