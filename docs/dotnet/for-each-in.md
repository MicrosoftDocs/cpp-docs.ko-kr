---
title: "각 항목에 대해에서 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- cliext::foreach
- for
- each
- in
dev_langs:
- C++
helpviewer_keywords:
- for each keyword [C++]
ms.assetid: 0c3a364b-2747-43f3-bb8d-b7d3b7023f79
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5dab51168b656422ddcf2c317a7f7fee1faf162e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="for-each-in"></a>for each, in
배열 또는 컬렉션을 반복합니다. 이 비표준 키워드는 C++/CLI 및 네이티브 C++ 프로젝트에서 사용할 수 있습니다. 그러나 사용하지 않는 것이 좋습니다. 표준을 사용 하는 것이 좋습니다 [범위 기반에 대 한 문 (c + +)](../cpp/range-based-for-statement-cpp.md) 대신 합니다.  
  
## <a name="all-runtimes"></a>모든 런타임  
 **구문**  
  
```  
  
      for each (typeidentifierinexpression) {  
   statements  
}  
  
```  
  
 **매개 변수**  
  
 `type`  
 `identifier`의 형식입니다.  
  
 `identifier`  
 반복 변수는 컬렉션 요소를 나타냅니다.  때 `identifier` 는 [추적 참조 연산자](../windows/tracking-reference-operator-cpp-component-extensions.md), 요소를 수정할 수 있습니다.  
  
 `expression`  
 배열 식 또는 컬렉션입니다. 컬렉션 요소는 컴파일러가 `identifier` 형식으로 변환할 수 있어야 합니다.  
  
 `statements`  
 실행할 하나 이상의 문입니다.  
  
 **주의**  
  
 `for each` 문은 컬렉션을 반복하는 데 사용됩니다. 컬렉션의 요소를 수정할 수 있지만 요소를 추가하거나 삭제할 수 없습니다.  
  
 *문을* 배열 또는 컬렉션의 각 요소에 대해 실행 됩니다. 컬렉션의 모든 요소에 대해 반복이 완료된 후 제어가 `for each` 블록 다음 문으로 전달됩니다.  
  
 `for each`및 `in` 는 [상황에 맞는 키워드](../windows/context-sensitive-keywords-cpp-component-extensions.md)합니다.  
  
 추가 정보  
  
-   [for each를 사용하여 C++ 표준 라이브러리 컬렉션 반복](../dotnet/iterating-over-stl-collection-by-using-for-each.md)  
  
-   [방법: for each로 배열 반복](../dotnet/how-to-iterate-over-arrays-with-for-each.md)  
  
-   [방법: for each로 제네릭 컬렉션 반복](../dotnet/how-to-iterate-over-a-generic-collection-with-for-each.md)  
  
-   [방법: for each로 사용자 정의 컬렉션 반복](../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)  
  
## <a name="windows-runtime"></a>Windows 런타임  
  
### <a name="requirements"></a>요구 사항  
 컴파일러 옵션: **/ZW**  
  
### <a name="example"></a>예  
 이 예제는 `for each`를 사용해서 문자열을 반복하는 방법을 보여줍니다.  
  
```  
// for_each_string1.cpp  
// compile with: /ZW  
#include <stdio.h>  
using namespace Platform;  
  
ref struct MyClass {  
   property String^ MyStringProperty;  
};  
  
int main() {  
   String^ MyString = ref new String("abcd");  
  
   for each ( char c in MyString )  
      wprintf("%c", c);  
  
   wprintf("/n");  
  
   MyClass^ x = ref new MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( char c in x->MyStringProperty )  
      wprintf("%c", c);  
}  
```  
  
 **출력**  
  
```Output  
abcd  
  
Testing  
```  
  
## <a name="common-language-runtime"></a>공용 언어 런타임 
 **주의**  
  
 CLR 구문은 동일는 **모든 런타임** 구문을 다음과 같이 제외 하 고 있습니다.  
  
 *식*  
 관리되는 배열 식 또는 컬렉션입니다. 컬렉션 요소는 컴파일러에서 변환할 수 있도록 있어야 <xref:System.Object> 에 *식별자* 유형입니다.  
  
 *식* 구현 하는 형식으로 계산 <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, 또는 형식이 정의 하는 `GetEnumerator` 형식을 반환 하거나 메서드를 구현 하는 <xref:System.Collections.IEnumerator> 하거나 모든 에정의된메서드를선언`IEnumerator`.  
  
### <a name="requirements"></a>요구 사항  
 컴파일러 옵션: **/clr**  
  
### <a name="example"></a>예  
 이 예제는 `for each`를 사용해서 문자열을 반복하는 방법을 보여줍니다.  
  
```  
// for_each_string2.cpp  
// compile with: /clr  
using namespace System;  
  
ref struct MyClass {  
   property String ^ MyStringProperty;  
};  
  
int main() {  
   String ^ MyString = gcnew String("abcd");  
  
   for each ( Char c in MyString )  
      Console::Write(c);  
  
   Console::WriteLine();  
  
   MyClass ^ x = gcnew MyClass();  
   x->MyStringProperty = "Testing";  
  
   for each( Char c in x->MyStringProperty )  
      Console::Write(c);  
}  
```  
  
 **출력**  
  
```Output  
abcd  
  
Testing   
```  
  
## <a name="see-also"></a>참고 항목  
 [런타임 플랫폼용 구성 요소 확장](../windows/component-extensions-for-runtime-platforms.md)