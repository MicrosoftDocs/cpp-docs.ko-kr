---
description: '자세한 정보: 레코드 스크롤에 대 한 명령 처리기 (MFC Data Access)'
title: 레코드 스크롤에 대한 명령 처리기  (MFC Data Access)
ms.date: 11/04/2016
helpviewer_keywords:
- record views [C++], scrolling
- record scrolling [C++]
- scrolling records
ms.assetid: f8b13477-2a37-459e-a30c-806fb78165ac
ms.openlocfilehash: 03fce51e7b045df0ae5ad1ceb0fa99eb98d0b7c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97181386"
---
# <a name="command-handlers-for-record-scrolling--mfc-data-access"></a>레코드 스크롤에 대한 명령 처리기  (MFC Data Access)

[CRecordView](../mfc/reference/crecordview-class.md) 클래스는 다음 표준 명령에 대 한 기본 명령 처리를 제공 합니다.

- ID_RECORD_MOVE_FIRST

- ID_RECORD_MOVE_LAST

- ID_RECORD_MOVE_NEXT

- ID_RECORD_MOVE_PREV

`OnMove`멤버 함수는 레코드에서 레코드로 이동 하는 네 개의 모든 명령에 대 한 기본 명령 처리를 제공 합니다. 이러한 명령을 실행하면 RFX 또는 DFX는 새 레코드를 레코드 집합의 필드에 로드하고 DDX는 레코드 폼의 컨트롤로 값을 이동합니다. RFX에 대 한 자세한 내용은 [rfx (레코드 필드 교환)](../data/odbc/record-field-exchange-rfx.md)를 참조 하세요.

> [!NOTE]
> 표준 레코드 탐색 명령과 연결된 모든 사용자 인터페이스 개체에 대해 이러한 표준 명령 ID를 사용해야 합니다.

## <a name="see-also"></a>참고 항목

[레코드 뷰에서의 탐색 지원](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)
