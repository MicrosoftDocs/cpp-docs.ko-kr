---
title: '방법: 네이티브 함수에서 참조 클래스 수정 | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- platform invoke, reference class
- reference types, modifying in a C++ native function
ms.assetid: c701145b-62a0-4c4b-b32a-db8d69a59720
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: d08524974c3edee2239e1934685099dfddca6e73
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-reference-class-in-a-native-function"></a>방법: 네이티브 함수에서 참조 클래스 수정
CLR 배열 사용 하 여 참조 클래스에는 네이티브 함수에 전달 하 고 PInvoke 서비스를 사용 하는 클래스를 수정할 수 있습니다.  
  
## <a name="example"></a>예제  
 다음과 같은 네이티브 라이브러리를 컴파일하십시오.  
  
```  
// modify_ref_class_in_native_function.cpp  
// compile with: /LD  
#include <stdio.h>  
#include <windows.h>  
  
struct S {  
   wchar_t* str;  
   int intarr[2];  
};  
  
extern "C"  {  
   __declspec(dllexport) int bar(S* param) {  
      printf_s("str: %S\n", param->str);  
      fflush(stdin);  
      fflush(stdout);  
      printf_s("In native: intarr: %d, %d\n",  
                param->intarr[0], param->intarr[1]);  
      fflush(stdin);  
      fflush(stdout);  
      param->intarr[0]=300;param->intarr[1]=400;  
      return 0;  
    }  
};  
```  
  
## <a name="example"></a>예제  
 다음 어셈블리를 컴파일하십시오.  
  
```  
// modify_ref_class_in_native_function_2.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
[StructLayout(LayoutKind::Sequential, CharSet = CharSet::Unicode)]  
ref class S  {  
public:  
   [MarshalAsAttribute(UnmanagedType::LPWStr)]  
   String ^ str;  
   [MarshalAsAttribute(UnmanagedType::ByValArray,  
        ArraySubType=UnmanagedType::I4, SizeConst=2)]  
   array<Int32> ^ intarr;  
};  
  
[DllImport("modify_ref_class_in_native_function.dll",  
           CharSet=CharSet::Unicode)]  
int bar([In][Out] S ^ param);  
  
int main() {  
   S ^ param = gcnew S;  
   param->str = "Hello";  
   param->intarr = gcnew array<Int32>(2);  
   param->intarr[0] = 100;  
   param->intarr[1] = 200;  
   bar(param);   // Call to native function  
   Console::WriteLine("In managed: intarr: {0}, {1}",  
                       param->intarr[0], param->intarr[1]);  
}  
```  
  
```Output  
str: Hello  
In native: intarr: 100, 200  
In managed: intarr: 300, 400  
```  
  
## <a name="see-also"></a>참고 항목  
 [C++ Interop 사용(암시적 PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)