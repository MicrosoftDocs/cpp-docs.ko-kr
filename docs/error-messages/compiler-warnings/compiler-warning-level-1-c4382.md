---
title: 컴파일러 경고 (수준 1) C4382 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4382
dev_langs:
- C++
helpviewer_keywords:
- C4382
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c02f0cb2d22aebb9af31844aec3bf68b97c3442e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4382"></a>컴파일러 경고(수준 1) C4382
'type'를 throw: __clrcall 소멸자 또는 복사 생성자 인 형식이 /clr에서 낼 수 있습니다: 순수 모듈  
  
 **/clr: pure** 컴파일러 옵션은 Visual Studio 2015에서 사용 되지 않습니다.  
  
 로 컴파일하는 경우 **/clr** (하지 **/clr: pure**), 예외 처리를 네이티브 형식에 멤버 함수에 필요한 [__cdecl](../../cpp/cdecl.md) 아닌 [__clrcall](../../cpp/clrcall.md). 멤버 함수를 사용 하 여 네이티브 형식은 `__clrcall` 호출 규칙으로 컴파일된 모듈에서 발생 함 없습니다 **/clr**합니다.  
  
 로 컴파일된 모듈에서 예외를 발견 됩니다 경우 **/clr: pure**,이 경고를 무시할 수 있습니다.  
  
 자세한 내용은 [/clr(공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md)을 참조하세요.  
  
## <a name="example"></a>예제  
 다음 샘플에서는 C4382 경고가 발생 합니다.  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```