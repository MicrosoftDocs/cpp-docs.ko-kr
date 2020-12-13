---
description: '자세한 정보: 메시지 pragma'
title: message pragma
ms.date: 08/29/2019
f1_keywords:
- message_CPP
- vc-pragma.message
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
ms.openlocfilehash: 82b8efa7e232c24402b7fb1cce0fd1e38ff8be29
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333384"
---
# <a name="message-pragma"></a>message pragma

컴파일이 종료되지 않은 상태에서 문자열 리터럴을 표준 출력에 보냅니다.

## <a name="syntax"></a>Syntax

> **#pragma 메시지 (** *메시지 문자열* **)**

## <a name="remarks"></a>설명

**메시지** pragma의 일반적인 용도는 컴파일 시간에 정보 메시지를 표시 하는 것입니다.

*메시지 문자열* 매개 변수는 문자열 리터럴로 확장 되는 매크로 일 수 있으며, 이러한 매크로를 조합 하 여 문자열 리터럴과 연결할 수 있습니다.

**Message** pragma에 미리 정의 된 매크로를 사용 하는 경우 매크로는 문자열을 반환 해야 합니다. 그렇지 않으면 매크로의 출력을 문자열로 변환 해야 합니다.

다음 코드 조각에서는 **메시지** pragma를 사용 하 여 컴파일하는 동안 메시지를 표시 합니다.

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

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
