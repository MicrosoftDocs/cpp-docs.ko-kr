---
title: CDocument에서에서 문서 클래스 파생 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CDocument class [MFC], deriving from
- classes [MFC], deriving from CDocument
- document objects [MFC], derived
- derived classes [MFC], functions often overridden
- document classes [MFC], functions often overridden
ms.assetid: e6a198e0-9799-43c0-83c5-04174d8b532c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b45dadbc062bbba61cdcb4c883f91943b1b18ba8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429827"
---
# <a name="deriving-a-document-class-from-cdocument"></a>CDocument에서 문서 클래스 파생시키기

문서를 포함 하 고 응용 프로그램의 데이터를 관리 합니다. MFC 응용 프로그램 마법사가 제공 문서 클래스를 사용 하려면 다음을 수행 해야 합니다.

- 클래스를 파생 `CDocument` 각 문서 유형에 대 한 합니다.

- 각 문서의 데이터를 저장 하는 멤버 변수를 추가 합니다.

- 재정의 `CDocument`의 `Serialize` 문서 클래스에서 멤버 함수입니다. `Serialize` 작성 하 고 문서의 데이터를 디스크에서 읽습니다.

## <a name="other-document-functions-often-overridden"></a>자주 재정의 되는 다른 문서 함수

다른 재정의 하려면 `CDocument` 멤버 함수입니다. 특히 재정의 해야 경우가 많습니다 [OnNewDocument](../mfc/reference/cdocument-class.md#onnewdocument) 및 [OnOpenDocument](../mfc/reference/cdocument-class.md#onopendocument) 문서의 데이터 멤버를 초기화 하 고 [DeleteContents](../mfc/reference/cdocument-class.md#deletecontents) 삭제 하려면 동적으로 할당 된 데이터입니다. 재정의 가능한 멤버에 대 한 내용은 클래스를 참조 하세요 [CDocument](../mfc/reference/cdocument-class.md) 에 *MFC 참조*합니다.

## <a name="see-also"></a>참고 항목

[문서 사용](../mfc/using-documents.md)

