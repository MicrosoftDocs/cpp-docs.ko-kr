---
title: "Clr이-C 스타일 캐스팅 (C + + /cli CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- C-style casts and /clr
ms.assetid: d2a4401a-156a-4da9-8d12-923743e26913
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e529a40f8eb876791f49559d3970696fdece489d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="c-style-casts-with-clr-ccli"></a>/clr을 사용한 C 스타일 캐스트(C++/CLI)
다음 항목 공용 언어 런타임에만 적용 됩니다.  
  
 와 CLR 형식을 함께 사용 하면 컴파일러에서는 C 스타일 캐스트는 다음 순서 대로 아래에 나열 된 캐스트 중 하나에 매핑할 수 있습니다:  
  
1.  const_cast  
  
2.  safe_cast  
  
3.  safe_cast 및 const_cast  
  
4.  static_cast  
  
5.  static_cast 플러스 const_cast  
  
 위에 나열 된 캐스트 중 올바른지 및 식의 형식과 대상 형식을 CLR 참조 형식인 경우 C 스타일 캐스트는 런타임 검사 (castclass MSIL 명령)에 매핑됩니다. 그렇지 않은 경우, C 스타일 캐스트는 잘못 된 것으로 간주 됩니다 하 고 컴파일러에서 오류가 발생 합니다.  
  
## <a name="remarks"></a>설명  
 C 스타일 캐스트 권장 되지 않습니다. 로 컴파일할 때 [/clr (공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md)를 사용 하 여 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)합니다.  
  
 다음 샘플은 C 스타일 캐스팅에 매핑되는 `const_cast`합니다.  
  
```  
// cstyle_casts_1.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
int main() {  
   const R^ constrefR = gcnew R();  
   R^ nonconstR = (R^)(constrefR);   
}  
```  
  
 다음 샘플은 C 스타일 캐스팅에 매핑되는 `safe_cast`합니다.  
  
```  
// cstyle_casts_2.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Object ^ o = "hello";  
   String ^ s = (String^)o;  
}  
```  
  
 다음 샘플은 C 스타일 캐스팅에 매핑되는 `safe_cast` 플러스 `const_cast`합니다.  
  
```  
// cstyle_casts_3.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct R {};  
ref struct R2 : public R {};  
  
int main() {  
   const R^ constR2 = gcnew R2();  
   try {  
   R2^ b2DR = (R2^)(constR2);  
   }  
   catch(InvalidCastException^ e) {  
      System::Console::WriteLine("Invalid Exception");  
   }  
}  
```  
  
 다음 샘플은 C 스타일 캐스팅에 매핑되는 `static_cast`합니다.  
  
```  
// cstyle_casts_4.cpp  
// compile with: /clr  
using namespace System;  
  
struct N1 {};  
struct N2 {  
   operator N1() {  
      return N1();  
   }  
};  
  
int main() {  
   N2 n2;  
   N1 n1 ;  
   n1 = (N1)n2;  
}  
```  
  
 다음 샘플은 C 스타일 캐스팅에 매핑되는 `static_cast` 플러스 `const_cast`합니다.  
  
```  
// cstyle_casts_5.cpp  
// compile with: /clr  
using namespace System;  
struct N1 {};  
  
struct N2 {  
   operator const N1*() {  
      static const N1 n1;  
      return &n1;  
   }  
};  
  
int main() {  
   N2 n2;  
   N1* n1 = (N1*)(const N1*)n2;   // const_cast + static_cast  
}  
```  
  
 다음 샘플에서는 C 스타일 캐스트는 런타임 검사에 매핑되는 보여 줍니다.  
  
```  
// cstyle_casts_6.cpp  
// compile with: /clr  
using namespace System;  
  
ref class R1 {};  
ref class R2 {};  
  
int main() {  
   R1^ r  = gcnew R1();  
   try {  
      R2^ rr = ( R2^)(r);  
   }  
   catch(System::InvalidCastException^ e) {  
      Console::WriteLine("Caught expected exception");  
   }  
}  
```  
  
 다음 샘플에는 잘못 된 C 스타일 캐스팅을 사용 하면 컴파일러는 오류를 보여 줍니다.  
  
```  
// cstyle_casts_7.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   String^s = S"hello";  
   int i = (int)s;   // C2440  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 컴파일러 옵션: **/clr**  
  
## <a name="see-also"></a>참고 항목  
 [런타임 플랫폼용 구성 요소 확장](../windows/component-extensions-for-runtime-platforms.md)