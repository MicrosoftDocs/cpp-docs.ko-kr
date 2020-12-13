---
description: 레이블 문에 대해 자세히 알아보세요.
title: 레이블 문
ms.date: 11/04/2016
helpviewer_keywords:
- labeled statement
- statements, labeled
ms.assetid: 456a26d5-0fcc-4d1a-b71f-fa9ff3d73b91
ms.openlocfilehash: dcedce1e67c712102be2d8ebb697c1839f3f53c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333972"
---
# <a name="labeled-statements"></a>레이블 문

레이블은 프로그램 제어를 지정된 문에 직접 전송하는 데 사용됩니다.

```
identifier :  statement
case constant-expression :  statement
default :  statement
```

레이블의 범위는 레이블이 선언된 함수 전체입니다.

## <a name="remarks"></a>설명

세 가지 형식의 레이블 문이 있습니다. 모두 문에서 특정 형식의 레이블을 분리하는 데 콜론을 사용합니다. case 및 기본 레이블은 case 문과 관련이 있습니다.

```cpp
#include <iostream>
using namespace std;

void test_label(int x) {

    if (x == 1){
        goto label1;
    }
    goto label2;

label1:
    cout << "in label1" << endl;
    return;

label2:
    cout << "in label2" << endl;
    return;
}

int main() {
    test_label(1);  // in label1
    test_label(2);  // in label2
}
```

**goto 문**

소스 프로그램에서 *식별자* 레이블의 모양은 레이블을 선언 합니다. [Goto](../cpp/goto-statement-cpp.md) 문만 *식별자* 레이블로 제어를 전달할 수 있습니다. 다음 코드 조각은 **`goto`** 문과 *식별자* 레이블의 사용을 보여 줍니다.

레이블은 단독으로 나타날 수 없고 항상 문에 첨부되어야 합니다. 레이블이 단독으로 필요한 경우 레이블 뒤에 null 문을 배치하세요.

레이블에는 함수 범위가 있으며 함수 내에서 레이블을 다시 선언할 수 없습니다. 그러나 다른 함수에서 동일한 이름을 레이블로 사용할 수 있습니다.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
}

//Output: At Test2 label.
```

**case 문**

키워드 뒤에 오는 레이블은 **`case`** 문 외부에도 나타날 수 없습니다 **`switch`** . 이 제한은 키워드에도 적용 됩니다 **`default`** . 다음 코드 조각에서는 레이블의 올바른 사용을 보여 줍니다 **`case`** .

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );
      EndPaint( hWnd, &ps );
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-case-statement"></a>case 문의 레이블

키워드 뒤에 오는 레이블은 **`case`** 문 외부에도 나타날 수 없습니다 **`switch`** . 이 제한은 키워드에도 적용 됩니다 **`default`** . 다음 코드 조각에서는 레이블의 올바른 사용을 보여 줍니다 **`case`** .

```cpp
// Sample Microsoft Windows message processing loop.
switch( msg )
{
   case WM_TIMER:    // Process timer event.
      SetClassWord( hWnd, GCW_HICON, ahIcon[nIcon++] );
      ShowWindow( hWnd, SW_SHOWNA );
      nIcon %= 14;
      Yield();
      break;

   case WM_PAINT:
      // Obtain a handle to the device context.
      // BeginPaint will send WM_ERASEBKGND if appropriate.

      memset( &ps, 0x00, sizeof(PAINTSTRUCT) );
      hDC = BeginPaint( hWnd, &ps );

      // Inform Windows that painting is complete.

      EndPaint( hWnd, &ps );
      break;

   case WM_CLOSE:
      // Close this window and all child windows.

      KillTimer( hWnd, TIMER1 );
      DestroyWindow( hWnd );
      if ( hWnd == hWndMain )
         PostQuitMessage( 0 );  // Quit the application.
      break;

   default:
      // This choice is taken for all messages not specifically
      //  covered by a case statement.

      return DefWindowProc( hWnd, Message, wParam, lParam );
      break;
}
```

## <a name="labels-in-the-goto-statement"></a>goto 문의 레이블

소스 프로그램에서 *식별자* 레이블의 모양은 레이블을 선언 합니다. [Goto](../cpp/goto-statement-cpp.md) 문만 *식별자* 레이블로 제어를 전달할 수 있습니다. 다음 코드 조각은 **`goto`** 문과 *식별자* 레이블의 사용을 보여 줍니다.

레이블은 단독으로 나타날 수 없고 항상 문에 첨부되어야 합니다. 레이블이 단독으로 필요한 경우 레이블 뒤에 null 문을 배치하세요.

레이블에는 함수 범위가 있으며 함수 내에서 레이블을 다시 선언할 수 없습니다. 그러나 다른 함수에서 동일한 이름을 레이블로 사용할 수 있습니다.

```cpp
// labels_with_goto.cpp
// compile with: /EHsc
#include <iostream>
int main() {
   using namespace std;
   goto Test2;

   cout << "testing" << endl;

   Test2:
      cerr << "At Test2 label." << endl;
// At Test2 label.
}
```

## <a name="see-also"></a>참고 항목

[C + + 문 개요](../cpp/overview-of-cpp-statements.md)<br/>
[switch 문 (c + +)](../cpp/switch-statement-cpp.md)
