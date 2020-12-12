---
description: '자세한 정보: 예외: 예외 내용 검사'
title: '예외: 예외 내용 검사'
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [MFC], MFC
- try-catch exception handling [MFC], MFC function exceptions
- catch blocks, MFC function exceptions
- CException class [MFC], class exceptions
- try-catch exception handling [MFC], exception contents
- throwing exceptions [MFC], exception contents
ms.assetid: dfda4782-b969-4f60-b867-cc204ea7f33a
ms.openlocfilehash: aef28d79bd6cad1d810700015930b14b5fdedddc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290624"
---
# <a name="exceptions-examining-exception-contents"></a>예외: 예외 내용 검사

**`catch`** 블록의 인수는 거의 모든 데이터 형식이 될 수 있지만 MFC 함수는 클래스에서 파생 된 형식의 예외를 throw 합니다 `CException` . MFC 함수에서 throw 된 예외를 catch 하려면 **`catch`** 인수가 개체에 대 한 포인터 `CException` (또는와 같은에서 파생 된 개체) 인 블록을 작성 `CException` `CMemoryException` 합니다. 예외의 정확한 형식에 따라 예외 개체의 데이터 멤버를 검사 하 여 예외의 특정 원인에 대 한 정보를 수집할 수 있습니다.

예를 `CFileException` 들어 형식에는 `m_cause` 파일 예외의 원인을 지정 하는 열거형 형식이 포함 된 데이터 멤버가 있습니다. 가능한 반환 값의 몇 가지 예는 `CFileException::fileNotFound` 및 `CFileException::readOnly` 입니다.

다음 예제에서는의 콘텐츠를 검사 하는 방법을 보여 줍니다 `CFileException` . 다른 예외 형식은 유사 하 게 검사할 수 있습니다.

[!code-cpp[NVC_MFCExceptions#13](codesnippet/cpp/exceptions-examining-exception-contents_1.cpp)]

자세한 내용은 예외: 예외 및 예외 [에서 개체 해제](exceptions-freeing-objects-in-exceptions.md) [: 예외 catch 및 삭제](exceptions-catching-and-deleting-exceptions.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[예외 처리](exception-handling-in-mfc.md)
