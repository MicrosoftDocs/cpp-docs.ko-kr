---
title: "컴파일러 오류 C3540 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3540
dev_langs:
- C++
helpviewer_keywords:
- C3540
ms.assetid: 3c0c959c-e3b7-40eb-b922-ccac44bd9d85
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b3befc331c4f43f4efd4e5039258e0faddae97db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3540"></a>컴파일러 오류 C3540
'type': 'auto' 포함 하는 형식에 sizeof를 적용할 수 없습니다  
  
 [sizeof](../../cpp/sizeof-operator.md) 연산자 포함 하기 때문에 지정된 된 형식에 적용할 수 없습니다는 `auto` 지정자입니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 C3540를 생성합니다.  
  
```  
// C3540.cpp  
// Compile with /Zc:auto  
int main() {  
    auto x = 123;  
    sizeof(x);    // OK  
    sizeof(auto); // C3540  
    return 0;  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [auto 키워드](../../cpp/auto-keyword.md)   
 [/Zc: auto (변수 형식 추론)](../../build/reference/zc-auto-deduce-variable-type.md)   
 [sizeof 연산자](../../cpp/sizeof-operator.md)