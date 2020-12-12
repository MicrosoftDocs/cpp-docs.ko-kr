---
description: '자세한 정보: 예외: 생성자의 예외'
title: '예외: 생성자의 예외'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 69393cc6a5cf709d359ccbdb572406e91c6788ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290598"
---
# <a name="exceptions-exceptions-in-constructors"></a>예외: 생성자의 예외

생성자에서 예외를 throw 하는 경우 예외 [: 자체 함수에서 예외 throw](exceptions-throwing-exceptions-from-your-own-functions.md)에 설명 된 대로 예외를 throw 하기 전에 만든 개체 및 메모리 할당을 모두 정리 합니다.

생성자에서 예외를 throw 할 때 개체 자체의 메모리는 생성자가 호출 될 때까지 이미 할당 되었습니다. 따라서 컴파일러는 예외가 throw 된 후 개체가 차지 하는 메모리의 할당을 자동으로 취소 합니다.

자세한 내용은 [예외: 예외에서 개체 해제](exceptions-freeing-objects-in-exceptions.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
