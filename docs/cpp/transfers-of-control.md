---
title: 컨트롤 전송 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1ee906061c7b51ade818b164c1d371a88ef3d462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="transfers-of-control"></a>컨트롤 전송
사용할 수 있습니다는 `goto` 문 또는 **대/소문자** 이라는 레이블이 `switch` 이니셜라이저 지난 분기 하는 프로그램을 지정 하는 문입니다. 이 같은 코드는 이니셜라이저를 포함한 선언이 점프 명령문이 있는 블록이 둘러싼 블록에 없는 경우 올바르지 않습니다.  
  
 다음 예제에서는 `total`, `ch` 및 `i` 개체를 선언하고 초기화하는 루프를 보여 줍니다. 또한 이니셜라이저를 지나 컨트롤을 전송하는 잘못된 `goto` 문이 있습니다.  
  
```  
// transfers_of_control.cpp  
// compile with: /W1  
// Read input until a nonnumeric character is entered.  
int main()  
{  
   char MyArray[5] = {'2','2','a','c'};  
   int i = 0;  
   while( 1 )  
   {  
      int total = 0;  
  
      char ch = MyArray[i++];  
  
      if ( ch >= '0' && ch <= '9' )  
      {  
         goto Label1;  
  
         int i = ch - '0';  
      Label1:  
         total += i;   // C4700: transfers past initialization of i.  
      } // i would be destroyed here if  goto error were not present  
   else  
      // Break statement transfers control out of loop,  
      //  destroying total and ch.  
      break;  
   }  
}  
```  
  
 위의 예제에서 `goto` 문은 `i`의 초기화를 지나 컨트롤을 전송합니다. 단, `i`가 선언되었지만 초기화되지 않은 경우 전송은 유효합니다.  
  
 개체 `total` 및 `ch`역할을 하는 블록에 선언 된는 *문을* 의 `while` 문을 사용 하 여 해당 블록을 종료할 때 삭제 됩니다는 `break` 문.  
  
