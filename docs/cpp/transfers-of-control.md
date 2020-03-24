---
title: 컨트롤 전송
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: c9a46ccb1cf519080c5105855e41ecd3ebc23f77
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188053"
---
# <a name="transfers-of-control"></a>컨트롤 전송

**Switch** 문에 **goto** 문이나 **case** 레이블을 사용 하 여 이니셜라이저를 지나서 분기 하는 프로그램을 지정할 수 있습니다. 이 같은 코드는 이니셜라이저를 포함한 선언이 점프 명령문이 있는 블록이 둘러싼 블록에 없는 경우 올바르지 않습니다.

다음 예제에서는 `total`, `ch` 및 `i` 개체를 선언하고 초기화하는 루프를 보여 줍니다. 또한 이니셜라이저를 지나서 제어를 전달 하는 잘못 된 **goto** 문이 있습니다.

```cpp
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

앞의 예제에서 **goto** 문은 `i`초기화를 지나서 제어를 전송 하려고 시도 합니다. 단, `i`가 선언되었지만 초기화되지 않은 경우 전송은 유효합니다.

**While** 문의 *문으로* 사용 되는 블록에 선언 된 `total` 및 `ch`개체는 **break** 문을 사용 하 여 해당 블록이 종료 될 때 소멸 됩니다.
