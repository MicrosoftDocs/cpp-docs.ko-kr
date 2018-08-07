---
title: (최신 c + +) ABI 경계의 이식성 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: abbd405e-3038-427c-8c24-e00598f0936a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb9ce8012db8617afc7af3183bd7439ddeb8fab7
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402353"
---
# <a name="portability-at-abi-boundaries-modern-c"></a>ABI 경계의 이식성(최신 C++)
이진 인터페이스 경계에서 충분히 이식 가능한 형식과 규칙을 사용 합니다. "휴대용" 형식은 C 기본 제공 형식 또는 C만 기본 제공 형식을 포함 하는 구조체입니다. 클래스 형식 호출자와 호출 수신자에 동의 레이아웃 규칙 등을 호출 하는 경우에 사용할 수 있습니다. 이 둘 다 동일한 컴파일러 및 컴파일러 설정을 사용 하 여 컴파일되는 경우만 가능 합니다.  
  
## <a name="how-to-flatten-a-class-for-c-portability"></a>C 이식성에 대 한 클래스를 평면화 하는 방법  
 호출자의 다른 컴파일러/언어를 사용 하 여 컴파일할 수 있습니다 때 다음 "평면화"에 **extern "C"** 특정 호출 규칙을 사용 하는 API:  
  
```cpp  
// class widget {  
//   widget();  
//   ~widget();  
//   double method( int, gadget& );  
// };  
extern "C" {        // functions using explicit "this"  
   struct widget;   // opaque type (forward declaration only)  
   widget* STDCALL widget_create();      // constructor creates new "this"  
   void STDCALL widget_destroy(widget*); // destructor consumes "this"  
   double STDCALL widget_method(widget*, int, gadget*); // method uses "this"  
}  
```  
  
## <a name="see-also"></a>참고자료  
 [C + +의 진화](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [C++ 언어 참조](../cpp/cpp-language-reference.md)   
 [C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)