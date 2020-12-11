---
description: '자세히 알아보기: 문서 사용'
title: 문서 사용
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], C++ applications
- data [MFC], reading
- documents [MFC]
- files [MFC], writing to
- data [MFC], documents
- files [MFC]
- views [MFC], C++ applications
- document/view architecture [MFC], documents
- reading data [MFC], documents and views
- printing [MFC], documents
- writing to files [MFC]
ms.assetid: f390d6d8-d0e1-4497-9b6a-435f7ce0776c
ms.openlocfilehash: 486604733808fb027d6dd0fbf81bb670c85313f8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154502"
---
# <a name="using-documents"></a>문서 사용

공동 작업, 문서 및 보기:

- 응용 프로그램 관련 [데이터](../mfc/managing-data-with-document-data-variables.md)를 포함 하 고 관리 하 고 표시 합니다.

- 데이터 조작을 위한 [문서 데이터 변수로](../mfc/managing-data-with-document-data-variables.md) 구성 된 인터페이스를 제공 합니다.

- [파일 작성 및 읽기](../mfc/serializing-data-to-and-from-files.md)에 참여 합니다.

- [인쇄](../mfc/role-of-the-view-in-printing.md)에 참여 합니다.

- 대부분의 응용 프로그램 명령 및 메시지를 [처리](../mfc/handling-commands-in-the-document.md) 합니다.

문서는 특히 데이터 관리와 관련이 있습니다. 일반적으로 문서 클래스 멤버 변수에 데이터를 저장 합니다. 뷰는 이러한 변수를 사용 하 여 표시 및 업데이트를 위해 데이터에 액세스 합니다. 문서의 기본 serialization 메커니즘은 파일에 대 한 데이터 읽기 및 쓰기를 관리 합니다. 문서는 또한 명령을 처리할 수 있지만 WM_COMMAND 아닌 Windows 메시지는 처리할 수 없습니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [CDocument에서 문서 클래스 파생시키기](../mfc/deriving-a-document-class-from-cdocument.md)

- [문서 데이터 변수로 데이터 관리](../mfc/managing-data-with-document-data-variables.md)

- [파일로/파일에서 데이터 Serialize](../mfc/serializing-data-to-and-from-files.md)

- [Serialization 메커니즘 건너뛰기](../mfc/bypassing-the-serialization-mechanism.md)

- [문서에서 명령 처리](../mfc/handling-commands-in-the-document.md)

- [OnNewDocument 멤버 함수](../mfc/reference/cdocument-class.md#onnewdocument)

- [DeleteContents 멤버 함수](../mfc/reference/cdocument-class.md#deletecontents)

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](../mfc/document-view-architecture.md)
