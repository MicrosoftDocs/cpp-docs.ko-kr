---
description: '자세한 정보: 예외: 버전 3.0의 예외 매크로 변경 내용'
title: '예외: 버전 3.0의 예외 매크로 변경 사항'
ms.date: 11/04/2016
helpviewer_keywords:
- C++ exception handling [MFC], upgrade considerations
- CATCH macro [MFC]
- exceptions [MFC], what's changed
- THROW_LAST macro [MFC]
ms.assetid: 3aa20d8c-229e-449c-995c-ab879eac84bc
ms.openlocfilehash: 3135e78885d0b4f14eb8588419b3b9d1852cf1c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290728"
---
# <a name="exceptions-changes-to-exception-macros-in-version-30"></a>예외: 버전 3.0의 예외 매크로 변경 사항

이는 고급 항목입니다.

MFC 버전 3.0 이상에서 예외 처리 매크로는 c + + 예외를 사용 하도록 변경 되었습니다. 이 문서에서는 이러한 변경 내용이 매크로를 사용 하는 기존 코드의 동작에 미치는 영향에 대해 설명 합니다.

이 문서는 다음 항목을 설명합니다.

- [예외 형식 및 CATCH 매크로](#_core_exception_types_and_the_catch_macro)

- [예외 다시 throw](#_core_re.2d.throwing_exceptions)

## <a name="exception-types-and-the-catch-macro"></a><a name="_core_exception_types_and_the_catch_macro"></a> 예외 형식 및 CATCH 매크로

이전 버전의 MFC에서 **CATCH** 매크로는 mfc 런타임 형식 정보를 사용 하 여 예외의 형식을 결정 합니다. 즉, 예외 형식이 catch 사이트에서 결정 됩니다. 그러나 c + + 예외를 사용 하는 경우 예외 형식은 항상 throw 되는 예외 개체의 형식으로 throw 사이트에서 결정 됩니다. 드물지만 throw 된 개체에 대 한 포인터의 형식이 throw 된 개체의 형식과 다른 경우에는 비 호환성 문제가 발생 합니다.

다음 예제에서는 MFC 버전 3.0와 이전 버전 간의 이러한 차이에 대 한 결과를 보여 줍니다.

[!code-cpp[NVC_MFCExceptions#1](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_1.cpp)]

컨트롤이 항상 **`catch`** 일치 하는 예외 선언을 사용 하 여 첫 번째 블록으로 전달 되기 때문에이 코드는 버전 3.0에서 다르게 동작 합니다. Throw 식의 결과입니다.

[!code-cpp[NVC_MFCExceptions#19](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_2.cpp)]

는로 생성 되더라도로 throw 됩니다 `CException*` `CCustomException` . MFC 버전 2.5 및 이전 버전의 **CATCH** 매크로는를 사용 하 여 `CObject::IsKindOf` 런타임에 형식을 테스트 합니다. 식

[!code-cpp[NVC_MFCExceptions#20](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_3.cpp)]

이 true 인 경우 첫 번째 catch 블록에서 예외를 catch 합니다. C + + 예외를 사용 하 여 많은 예외 처리 매크로를 구현 하는 버전 3.0에서는 두 번째 catch 블록이 throw 된와 일치 합니다 `CException` .

이와 같은 코드는 일반적이 지 않습니다. 일반적으로 예외 개체가 제네릭을 허용 하는 다른 함수에 전달 되 `CException*` 고, "사전 throw" 처리를 수행 하 고, 마지막으로 예외를 throw 하는 경우에 나타납니다.

이 문제를 해결 하려면 throw 식을 함수에서 호출 코드로 이동 하 고 예외가 생성 될 때 컴파일러에 알려진 실제 형식의 예외를 throw 합니다.

## <a name="re-throwing-exceptions"></a><a name="_core_re.2d.throwing_exceptions"></a> Re-Throwing 예외

Catch 블록에서 catch 한 것과 동일한 예외 포인터를 throw 할 수 없습니다.

예를 들어이 코드는 이전 버전에서 유효 하지만 3.0 버전의 예기치 않은 결과를 포함 합니다.

[!code-cpp[NVC_MFCExceptions#2](codesnippet/cpp/exceptions-changes-to-exception-macros-in-version-3-0_4.cpp)]

Catch 블록에서 **THROW** 를 사용 하면 `e` 외부 catch 사이트에서 잘못 된 포인터를 받을 수 있도록 포인터가 삭제 됩니다. **THROW_LAST** 를 사용 하 여 다시 THROW `e` 합니다.

자세한 내용은 [예외: 예외 catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
