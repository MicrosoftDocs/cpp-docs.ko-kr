---
description: '자세히 알아보기: TN032: MFC 예외 메커니즘'
title: 'TN032: MFC 예외 메커니즘'
ms.date: 11/04/2016
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: 847d78762aaf5e04c8a0c1eb2170e951d0b867bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215536"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: MFC 예외 메커니즘

이전 버전의 Visual C++는 표준 c + + 예외 메커니즘을 지원 하지 않으며 MFC에서 사용 된 **TRY/CATCH/THROW** 매크로를 대신 사용 했습니다. 이 버전의 Visual C++에서는 C++ 예외가 완전히 지원됩니다. 이 설명서에서는 스택 기반 개체를 자동으로 정리하는 방법을 포함해서 이전 매크로의 고급 구현 세부 정보를 다룹니다. C++ 예외 스택은 기본적으로 스택 해제가 지원되기 때문에 이 기술 설명은 더 이상 필요하지 않습니다.

MFC 매크로와 새 c + + 키워드 간의 차이점에 대 한 자세한 내용은 [예외: Mfc 매크로 및 c + + 예외 사용](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
