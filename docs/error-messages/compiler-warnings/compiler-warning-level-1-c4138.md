---
title: "컴파일러 경고 (수준 1) C4138 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4138
dev_langs:
- C++
helpviewer_keywords:
- C4138
ms.assetid: 65ebf929-bba0-4237-923b-c1b66adfe17d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 568c12beecfcfc7f5fd8cece4b19f10fa38e54e7
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
---
# <a name="compiler-warning-level-1-c4138"></a>컴파일러 경고(수준 1) C4138
'*/'가 주석 외부에 있습니다.  
  
 닫는 주석 구분 기호 앞에 여는 주석 구분 기호가 없습니다. 컴파일러는 별표(**\***)와 슬래시(/) 사이에 공백이 있다고 가정합니다.  
  
## <a name="example"></a>예제  
  
```  
// C4138a.cpp  
// compile with: /W1  
int */*comment*/ptr;   // C4138 Ambiguous first delimiter causes warning  
int main()  
{  
}  
```  
  
 이 경고는 주석을 중첩하려는 경우에 발생할 수 있습니다.  
  
 주석을 포함하는 코드 섹션을 주석으로 처리하고 **#if/#endif** 블록에 코드를 포함한 다음 제어하는 식을 0으로 설정하면 이 경고를 해결할 수 있습니다.  
  
```  
// C4138b.cpp  
// compile with: /W1  
#if 0  
int my_variable;   /* Declaration currently not needed */  
#endif  
int main()  
{  
}  
```