---
description: pragmaMicrosoft C/c + +의 메시지 지시문에 대해 자세히 알아보세요.
title: 메시지 pragma
ms.date: 01/22/2021
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragma, message
no-loc:
- pragma
ms.openlocfilehash: 6f5e39896e0ba644f9d40665e80cbf7de9026223
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713495"
---
# <a name="message-no-locpragma"></a>`message` pragma

컴파일이 종료되지 않은 상태에서 문자열 리터럴을 표준 출력에 보냅니다.

## <a name="syntax"></a>구문

> **`#pragma message(`***메시지 문자열***`)`**

## <a name="remarks"></a>설명

는 일반적으로 **`message`** pragma 컴파일 시간에 정보 메시지를 표시 하는 데 사용 됩니다.

*메시지 문자열* 매개 변수는 문자열 리터럴로 확장 되는 매크로 일 수 있으며, 이러한 매크로를 조합 하 여 문자열 리터럴과 연결할 수 있습니다.

에서 미리 정의 된 매크로를 사용 하는 경우 **`message`** pragma 매크로는 문자열을 반환 해야 합니다. 그렇지 않으면 매크로의 출력을 문자열로 변환 해야 합니다.

다음 코드 조각에서는를 사용 하 여 **`message`** pragma 컴파일하는 동안 메시지를 표시 합니다.

```cpp
// pragma_directives_message1.cpp
// compile with: /LD
#if _M_IX86 >= 500
#pragma message("_M_IX86 >= 500")
#endif

#pragma message("")

#pragma message( "Compiling " __FILE__ )
#pragma message( "Last modified on " __TIMESTAMP__ )

#pragma message("")

// with line number
#define STRING2(x) #x
#define STRING(x) STRING2(x)

#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")

#pragma message("")
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
