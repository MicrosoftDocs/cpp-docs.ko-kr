---
title: "단순 할당 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- type conversion [C++], simple assignment
- data type conversion [C++], simple assignment
- operators [C], simple assignment
- assignment operators [C++], simple
- simple assignment operator
- equal sign
ms.assetid: e7140a0a-7104-4b3a-b293-7adcc1fdd52b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1cf9c5675affb6dcaea78e0cabf2a4427ad03938
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="simple-assignment-c"></a>단순 할당 (C)
단순 할당 연산자는 오른쪽 피연산자를 왼쪽 피연산자에 할당합니다. 오른쪽 피연산자의 값은 할당 식의 형식으로 변환되며 왼쪽 피연산자로 지정된 개체에 저장된 값을 대체합니다. 할당에 대한 변환 규칙이 적용됩니다([할당 변환](../c-language/assignment-conversions.md) 참조).  
  
```  
double x;  
int y;  
  
x = y;  
```  
  
 이 예제에서 `y`의 값은 **double** 형식으로 변환되어 `x`에 할당됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [C 할당 연산자](../c-language/c-assignment-operators.md)