---
title: __uuidof 연산자 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
dev_langs:
- C++
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 440d985a522edbb6e30136ec841f934584823204
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39463056"
---
# <a name="uuidof-operator"></a>__uuidof 연산자
**Microsoft 전용**  
  
 식에 연결된 GUID를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
__uuidof (expression)  
```  
  
## <a name="remarks"></a>설명  
 합니다 *식* 이러한 형식 또는 이러한 형식의 변수에서 특수화 된 템플릿, 형식 이름, 포인터, 참조 또는 해당 형식의 배열과 될 수 있습니다. 컴파일러에서 인수를 사용하여 연결된 GUID를 찾을 수 있으면 해당 인수는 유효합니다.  
  
 이 내장 함수의 특별 한 경우 때 어느 **0** 또는 NULL 인수로 제공 됩니다. 이 예에서 **__uuidof** 0으로 구성 된 GUID가 반환 됩니다.  
  
 이 키워드를 사용하여 연결된 GUID를 다음으로 추출합니다.  
  
-   개체를 [uuid](../cpp/uuid-cpp.md) 확장 된 특성입니다.  
  
-   사용 하 여 만든 라이브러리 블록의 [모듈](../windows/module-cpp.md) 특성입니다.  
  
> [!NOTE]
>  디버그 빌드에서 **__uuidof** 항상 동적으로 (런타임으로) 개체를 초기화 합니다. 릴리스 빌드에서 **__uuidof** 정적으로 (컴파일 시) 개체를 초기화할 수 있습니다.  
  
## <a name="example"></a>예  
 ole32.lib를 사용하여 컴파일된 다음 코드는 module 특성을 사용하여 만든 라이브러리 블록의 uuid를 표시합니다.  
  
```cpp 
// expre_uuidof.cpp  
// compile with: ole32.lib  
#include "stdio.h"  
#include "windows.h"  
  
[emitidl];  
[module(name="MyLib")];  
[export]  
struct stuff {  
   int i;  
};  
  
int main() {  
   LPOLESTR lpolestr;  
   StringFromCLSID(__uuidof(MyLib), &lpolestr);  
   wprintf_s(L"%s", lpolestr);  
   CoTaskMemFree(lpolestr);  
}  
```  
  
## <a name="comments"></a>설명  
 라이브러리를 더 이상 범위의 경우에 사용할 수 없습니다 `__LIBID_` of **__uuidof**합니다. 예를 들어:  
  
```cpp 
StringFromCLSID(__LIBID_, &lpolestr);  
```  
  
 **Microsoft 전용 종료**  
  
## <a name="see-also"></a>참고자료  
 [단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)   
 [키워드](../cpp/keywords-cpp.md)