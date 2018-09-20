---
title: '예외: 예외 내용 검사 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f5fb0df0c16e9aea2f334b6c08f92a3bef4ea486
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378388"
---
# <a name="exceptions-examining-exception-contents"></a>예외: 예외 내용 검사

하지만 한 **catch** 블록의 인수는 거의 모든 데이터 형식일 수 있습니다, MFC 함수 형식 클래스에서 파생 된 예외를 throw `CException`합니다. MFC 함수에 의해 throw 된 예외를 catch 하려면 다음을 작성을 **catch** 인수가 포인터 블록에는 `CException` 개체 (에서 파생 된 개체 또는 `CException`와 같은 `CMemoryException`). 예외의 정확한 형식에 따라 예외의 특정 원인에 대 한 정보를 수집 하는 예외 개체의 데이터 멤버를 검사할 수 있습니다.

예를 들어 합니다 `CFileException` 형식에는 `m_cause` 파일 예외의 원인을 지정 하는 열거 형식을 포함 하는 데이터 멤버입니다. 일부의 가능한 반환 값은 `CFileException::fileNotFound` 고 `CFileException::readOnly`입니다.

다음 예제에서는의 내용을 검사 하는 방법을 보여 줍니다는 `CFileException`합니다. 마찬가지로 다른 예외 형식을 검사할 수 있습니다.

[!code-cpp[NVC_MFCExceptions#13](../mfc/codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

자세한 내용은 [예외: 예외의 개체 해제](../mfc/exceptions-freeing-objects-in-exceptions.md) 하 고 [예외: 예외를 catch 하면 및 삭제](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>참고 항목

[예외 처리](../mfc/exception-handling-in-mfc.md)

