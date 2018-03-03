---
title: "컴파일러 경고 (수준 4) C4463 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4463
dev_langs:
- C++
helpviewer_keywords:
- C4463
ms.assetid: a07ae70c-db4e-472b-8b58-9137d9997323
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 71b438de515a4fd01e7714de685ee0a89adb609e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4463"></a>컴파일러 경고 (수준 4) C4463  
  
> 오버플로. 할당 *값* 값만 포함할 수 있는 비트 필드에 *low_value* 를 *high_value*  
  
할당 된 *값* 비트 필드에서 보유할 수 있는 값의 범위를 벗어났습니다. 부호 있는 비트 필드 형식을 사용 하 여 상위 비트가 부호에 대 한 비트가 하면  *n*  는 부호 있는 비트 필드는-2 비트 필드 크기 범위<sup>n-1</sup> 2로<sup>n-1</sup>-1을 반환 하는 동안 부호 없는 비트 필드는 0에서 2 사이의<sup>n</sup>-1입니다.  
  
## <a name="example"></a>예  
  
형식의 비트 필드에 값 3 할당 하려고 했기 때문에이 예제에서는 C4463 `int` 1-2에서 범위 크기가 2가 있습니다.  
  
이 문제를 해결 하려면 허용 되는 범위 내의 요소에 할당 된 값을 변경할 수 있습니다. 비트 필드는 0에서 3 사이에 부호 없는 값을 보유할 경우 선언 형식을 변경할 수 있습니다 `unsigned`합니다. 필드는 범위-4-3에 값을 보유할 경우 3 비트 필드 크기를 변경할 수 있습니다.  
  
```cpp  
// C4463_overflow.cpp
// compile with: cl /W4 /EHsc C4463_overflow.cpp
struct S { 
    int x : 2; // int type treats high-order bit as sign
}; 

int main() { 
    S s; 
    s.x = 3; // warning C4463: overflow; assigning 3 
    // to bit-field that can only hold values from -2 to 1 
    // To fix, change assigned value to fit in range,
    // increase size of bitfield, and/or change base type 
    // to unsigned.
} 
```  
