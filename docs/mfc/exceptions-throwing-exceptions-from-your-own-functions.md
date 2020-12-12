---
description: '다음에 대 한 자세한 정보: 예외: 자체 함수에서 예외 Throw'
title: '예외: 자체 함수에서 예외 Throw'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], from functions
- functions [MFC], throwing exceptions
- exceptions [MFC], throwing
ms.assetid: 492976e8-8804-4234-8e8f-30dffd0501be
ms.openlocfilehash: 5a9d789680eeba218370471b1259c8c664f3c3cd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290468"
---
# <a name="exceptions-throwing-exceptions-from-your-own-functions"></a>예외: 자체 함수에서 예외 Throw

Mfc 예외 처리 패러다임을 단독으로 사용 하 여 MFC 또는 다른 라이브러리의 함수에 의해 throw 된 예외를 catch 할 수 있습니다. 예외 조건을 발생 시킬 수 있는 함수를 작성 하는 경우 라이브러리 코드에서 throw 된 예외를 catch 하는 것 외에도 사용자 고유의 코드에서 예외를 throw 할 수 있습니다.

예외가 throw 되 면 현재 함수의 실행이 중지 되 고 **`catch`** 가장 안쪽의 예외 프레임 블록으로 직접 이동 합니다. 예외 메커니즘은 함수에서 정상적인 끝내기 경로를 무시 합니다. 따라서 일반적인 종료에서 삭제 되는 메모리 블록을 삭제 해야 합니다.

#### <a name="to-throw-an-exception"></a>예외를 throw 하려면

1. 와 같은 MFC 도우미 함수 중 하나를 사용 `AfxThrowMemoryException` 합니다. 이러한 함수는 적절 한 형식의 미리 할당 된 exception 개체를 throw 합니다.

   다음 예제에서 함수는 두 개의 메모리 블록을 할당 하려고 시도 하 고 할당이 실패 하는 경우 예외를 throw 합니다.

   [!code-cpp[NVC_MFCExceptions#17](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_1.cpp)]

   첫 번째 할당이 실패 하면 메모리 예외를 throw 할 수 있습니다. 첫 번째 할당이 성공 하지만 두 번째 할당이 실패 한 경우에는 예외를 throw 하기 전에 첫 번째 할당 블록을 해제 해야 합니다. 두 할당이 모두 성공 하면 정상적으로 진행 하 고 함수를 종료할 때 블록을 해제할 수 있습니다.

     - 또는

1. 사용자 정의 예외를 사용 하 여 문제 조건을 표시 합니다. 전체 클래스를 비롯 하 여 모든 형식의 항목을 예외로 throw 할 수 있습니다.

   다음 예제에서는 웨이브 장치를 통해 소리를 재생 하려고 시도 하 고 오류가 발생 하는 경우 예외를 throw 합니다.

   [!code-cpp[NVC_MFCExceptions#18](codesnippet/cpp/exceptions-throwing-exceptions-from-your-own-functions_2.cpp)]

> [!NOTE]
> MFC의 기본 예외 처리는 개체에 대 한 포인터 `CException` 및 파생 클래스의 개체에만 적용 됩니다 `CException` . 위의 예제에서는 MFC의 예외 메커니즘을 무시 합니다.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
