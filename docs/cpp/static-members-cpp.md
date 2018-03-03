---
title: "정적 멤버 (c + +) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0d19985271648e66aa86946c685608f805b1dfe1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="static-members-c"></a>정적 멤버(C++)
클래스는 정적 멤버 데이터와 멤버 함수를 포함할 수 있습니다. 로 데이터 멤버가 선언 되는 경우 **정적**, 클래스의 모든 개체에 대 한 데이터의 복사본을 하나만 유지 됩니다.
  
 정적 데이터 멤버는 지정된 클래스 형식의 개체에 속하지 않습니다. 결과적으로, 정적 데이터 멤버 선언은 정의로 간주되지 않습니다. 데이터 멤버는 클래스 범위에서 선언되지만 정의는 파일 범위에서 수행됩니다. 이러한 정적 멤버에는 외부 링크가 있습니다. 다음 예제는 이러한 과정을 보여 줍니다.  
  
```  
// static_data_members.cpp  
class BufferedOutput  
{  
public:  
   // Return number of bytes written by any object of this class.  
   short BytesWritten()  
   {  
      return bytecount;  
   }  
  
   // Reset the counter.  
   static void ResetCount()  
   {  
      bytecount = 0;  
   }  
  
   // Static member declaration.  
   static long bytecount;  
};  
  
// Define bytecount in file scope.  
long BufferedOutput::bytecount;  
  
int main()  
{  
}  
```  
  
 앞의 코드에서 `bytecount` 멤버는 `BufferedOutput` 클래스에서 선언되었지만 클래스 선언 밖에서 정의되어야 합니다.  
  
 클래스 형식의 개체를 참조하지 않고 정적 데이터 멤버를 참조할 수 있습니다. `BufferedOutput` 개체를 사용하여 쓴 바이트 수는 다음과 같이 확인할 수 있습니다.  
  
```  
long nBytes = BufferedOutput::bytecount;  
```  
  
 정적 멤버가 존재하기 위해 클래스 형식의 개체가 있어야 하는 것은 아닙니다. 멤버 선택을 사용 하 여 정적 멤버 액세스할 수도 있습니다 (**합니다.** 및  **->** ) 연산자. 예:  
  
```  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 앞의 경우에서 개체(`Console`)에 대한 참조는 평가되지 않습니다. 반환된 값은 정적 개체 `bytecount`의 값입니다.  
  
 정적 데이터 멤버에는 클래스 멤버 액세스 규칙이 적용되므로 정적 데이터 멤버에 대한 전용 액세스는 클래스 멤버 함수 및 friend에만 허용됩니다. 이러한 규칙에 설명 된 [멤버 액세스 제어](../cpp/member-access-control-cpp.md)합니다. 예외는 정적 데이터 멤버가 해당 액세스 제한에 관계없이 파일 범위에서 정의되어야 한다는 것입니다. 데이터 멤버를 명시적으로 초기화하는 경우 이니셜라이저에 정의를 제공해야 합니다.  
  
 정적 멤버의 형식은 클래스 이름으로 한정되지 않습니다. 따라서 `BufferedOutput::bytecount`의 형식은 `long`입니다.  
  
## <a name="see-also"></a>참고 항목  
 [클래스 및 구조체](../cpp/classes-and-structs-cpp.md)