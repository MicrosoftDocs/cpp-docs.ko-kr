---
title: "컴파일러 오류 C2039 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2039
dev_langs:
- C++
helpviewer_keywords:
- C2039
ms.assetid: f9dfd521-9b36-4454-a69c-d63f45b606bb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 753ba66cfbc20e19bab5351ff67d9e6f8cc3a392
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2039"></a>컴파일러 오류 C2039
'identifier1': 'identifier2'의 구성원이 아닙니다  
  
 코드 잘못 호출 하거나 구조체, 클래스 또는 공용 구조체의 멤버를 참조 합니다.  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2039 오류가 발생 합니다.  
  
```  
// C2039.cpp  
struct S {  
   int mem0;  
} s, *pS = &s;  
  
int main() {  
   pS->mem1 = 0;   // C2039 mem1 is not a member  
   pS->mem0 = 0;   // OK  
}  
```  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2039 오류가 발생 합니다.  
  
```  
// C2039_b.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   Console::WriteLine( "{0}", DateTime::get_Now());   // C2039  
   Console::WriteLine( "{0}", DateTime::Now);   // OK  
   Console::WriteLine( "{0}", DateTime::Now::get());   // OK  
}  
```  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2039 오류가 발생 합니다.  
  
```  
// C2039_c.cpp  
// compile with: /clr /c  
ref struct S {  
   property int Count {  
     int get();  
     void set(int i){}  
   };  
};  
  
int S::get_Count() { return 0; }   // C2039  
int S::Count::get() { return 0; }   // OK  
```  
  
## <a name="example"></a>예  
 C2039 기본 인덱서를 올바르게 액세스 하려고 할 경우에 발생할 수 있습니다. 다음 샘플 C#에서 작성 된 구성 요소를 정의 합니다.  
  
```  
// C2039_d.cs  
// compile with: /target:library  
// a C# program  
[System.Reflection.DefaultMember("Item")]  
public class B {  
   public int Item {  
      get { return 13; }  
      set {}  
   }  
};  
```  
  
## <a name="example"></a>예  
 다음 샘플에서는 C2039 오류가 발생 합니다.  
  
```  
// C2039_e.cpp  
// compile with: /clr  
using namespace System;  
#using "c2039_d.dll"  
  
int main() {  
   B ^ b = gcnew B;  
   int n = b->default;   // C2039  
   // try the following line instead  
   // int n = b->Item;  
   Console::WriteLine(n);  
}  
```  
  
## <a name="example"></a>예  
 C2039는 제네릭을 사용 하는 경우에 발생할 수 있습니다. 다음 샘플에서는 C2039 오류가 발생 합니다.  
  
```  
// C2039_f.cpp  
// compile with: /clr  
interface class I {};  
  
ref struct R : public I {  
   virtual void f3() {}  
};  
  
generic <typename T>  
where T : I  
void f(T t) {  
   t->f3();   // C2039  
   safe_cast<R^>(t)->f3();   // OK  
}  
  
int main() {  
   f(gcnew R());  
}  
```  
  
## <a name="example"></a>예  
 C2039 관리 되거나 관리 되지 않는 리소스를 해제 하려고 할 때 발생할 수 있습니다. 자세한 내용은 참조 [소멸자 및 종료자](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)합니다.  
  
 다음 샘플에서는 C2039 오류가 발생 합니다.  
  
```  
// C2039_g.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Threading;  
  
void CheckStatus( Object^ stateInfo ) {}  
  
int main() {  
   ManualResetEvent^ event = gcnew ManualResetEvent( false );     
   TimerCallback^ timerDelegate = gcnew TimerCallback( &CheckStatus );  
   Timer^ stateTimer = gcnew Timer( timerDelegate, event, 1000, 250 );  
  
   ((IDisposable ^)stateTimer)->Dispose();   // C2039  
  
   stateTimer->~Timer();   // OK  
}  
```