---
title: 컴파일러 오류 C2813 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 253f0d54b603c2b859f806053a906378025a39ca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2813"></a>컴파일러 오류 C2813
\#/MP와 가져오기가 지원 되지 않습니다.  
  
 C2813은 컴파일러 명령에서 **/MP** 컴파일러 옵션과 컴파일할 파일을 둘 이상 지정하고 파일 중 하나 이상에[#import](../../preprocessor/hash-import-directive-cpp.md) 전처리기 지시문이 포함된 경우에 내보내집니다. [#import](../../preprocessor/hash-import-directive-cpp.md) 지시문은 지정된 형식 라이브러리의 형식에서 C++ 클래스를 생성한 다음 두 개의 헤더 파일에 이러한 클래스를 씁니다. 여러 컴파일 단위가 동일한 형식 라이브러리를 가져오는 경우 동시에 동일한 헤더 파일에 쓰려고 할 때 해당 단위가 충돌하기 때문에 [#import](../../preprocessor/hash-import-directive-cpp.md) 지시문은 지원되지 않습니다.  
  
 컴파일러 오류가 고 **/MP** 컴파일러 옵션은 Visual Studio 2008의 새로운 기능입니다.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C2813을 생성합니다. "compile with:" 주석의 명령줄은 **/MP** 및 **/c** 컴파일러 옵션을 사용하여 여러 파일을 컴파일하도록 컴파일러에 알립니다. 파일 중 하나 이상에 [#import](../../preprocessor/hash-import-directive-cpp.md) 지시문이 포함되어 있습니다. 이 예제를 테스트하기 위해 동일한 파일을 두 번 사용합니다.  
  
```  
// C2813.cpp  
// compile with: /MP /c C2813.cpp C2813.cpp  
#import "C:\windows\system32\stdole2.tlb"   // C2813  
int main()   
{  
}  
```