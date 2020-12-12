---
description: '예외: MFC 매크로 및 c + + 예외 사용에 대 한 자세한 정보'
title: '예외: MFC 매크로 및 C++ 예외 사용'
ms.date: 11/04/2016
helpviewer_keywords:
- exception objects [MFC]
- memory leaks [MFC], exception object not deleted
- exception handling [MFC], MFC
- try-catch exception handling [MFC], mixing MFC macros and C++ keywords
- exception objects [MFC], deleting
- exceptions [MFC], MFC macros vs. C++ keywords
- catch blocks [MFC], mixed
- exception handling [MFC], mixed-language
- nested try blocks [MFC]
- catch blocks [MFC], explicitly deleting code in
- try-catch exception handling [MFC], nested try blocks
- heap corruption [MFC]
- nested catch blocks [MFC]
ms.assetid: d664a83d-879b-44d4-bdf0-029f0aca69e9
ms.openlocfilehash: 4f46cdff236f37ccdccde8215c7937300014aca6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290451"
---
# <a name="exceptions-using-mfc-macros-and-c-exceptions"></a>예외: MFC 매크로 및 C++ 예외 사용

이 문서에서는 MFC 예외 처리 매크로 및 c + + 예외 처리 키워드를 모두 사용 하는 코드를 작성할 때 고려해 야 하는 사항을 설명 합니다.

이 문서는 다음 항목을 설명합니다.

- [예외 키워드 및 매크로 혼합](#_core_mixing_exception_keywords_and_macros)

- [Catch 블록 내의 Try 블록](#_core_try_blocks_inside_catch_blocks)

## <a name="mixing-exception-keywords-and-macros"></a><a name="_core_mixing_exception_keywords_and_macros"></a> 예외 키워드 및 매크로 혼합

동일한 프로그램에서 MFC 예외 매크로 및 c + + 예외 키워드를 혼합할 수 있습니다. 그러나 매크로는 범위를 벗어날 때 예외 개체를 자동으로 삭제 하는 반면 예외 처리 키워드를 사용 하는 코드는 예외를 제외 하 고 동일한 블록에서 c + + 예외 키워드와 함께 MFC 매크로를 혼합할 수 없습니다. 자세한 내용은 예외 [: 예외 catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)문서를 참조 하세요.

매크로와 키워드의 주요 차이점은 예외가 범위를 벗어날 때 매크로가 "자동"으로 catch 된 예외를 삭제 하는 것입니다. 키워드를 사용 하는 코드는 그렇지 않습니다. catch 블록에서 catch 된 예외는 명시적으로 삭제 해야 합니다. 매크로와 c + + 예외 키워드를 혼합 하면 예외 개체가 삭제 되지 않을 때 메모리 누수가 발생 하거나 예외가 두 번 삭제 될 때 힙 손상이 발생할 수 있습니다.

예를 들어 다음 코드는 예외 포인터를 무효화 합니다.

[!code-cpp[NVC_MFCExceptions#10](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_1.cpp)]

이 문제는 `e` 실행이 "내부" **CATCH** 블록 밖으로 전달 될 때가 삭제 되기 때문에 발생 합니다. **THROW** 문 대신 **THROW_LAST** 매크로를 사용 하면 "outer" **CATCH** 블록이 올바른 포인터를 수신 합니다.

[!code-cpp[NVC_MFCExceptions#11](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_2.cpp)]

## <a name="try-blocks-inside-catch-blocks"></a><a name="_core_try_blocks_inside_catch_blocks"></a> Catch 블록 내의 Try 블록

**`try`** **CATCH** 블록 내에 있는 블록 내에서 현재 예외를 다시 throw 할 수 없습니다. 다음 예제는 올바르지 않습니다.

[!code-cpp[NVC_MFCExceptions#12](codesnippet/cpp/exceptions-using-mfc-macros-and-cpp-exceptions_3.cpp)]

자세한 내용은 예외 [: 예외 내용 검사](exceptions-examining-exception-contents.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
