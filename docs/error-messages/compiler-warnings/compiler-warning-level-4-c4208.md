---
title: 컴파일러 경고 (수준 4) C4208 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b61f8b0a6a0ac61982bee79abb81f083d40a48f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292365"
---
# <a name="compiler-warning-level-4-c4208"></a>컴파일러 경고(수준 4) C4208
비표준 확장이 사용 됨: delete [exp]-exp가 계산 되지만 무시  
  
 대괄호 내의 값을 사용 하 여 배열을 Microsoft 확장 (/Ze)을 삭제할 수 있습니다는 [delete 연산자](../../cpp/delete-operator-cpp.md)합니다. 값이 무시 됩니다.  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 이러한 값은 ANSI 규격 사용할 수 없습니다 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).