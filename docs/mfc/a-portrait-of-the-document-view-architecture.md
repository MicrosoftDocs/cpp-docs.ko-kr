---
description: '자세히 알아보기: 문서/뷰 아키텍처의 세로'
title: Document-View 아키텍처의 세로
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], views
- multiple views [MFC], updating from document
- document/view architecture [MFC]
- views [MFC], and user input
- documents [MFC], accessing data from view
- views [MFC], updating
- input [MFC], view class
- documents [MFC], multiple views
- document/view architecture [MFC], accessing data from view
- document/view architecture [MFC], about document/view architecture
- views [MFC], accessing document data from
ms.assetid: 4e7f65dc-b166-45d8-bcd5-9bb0d399b946
ms.openlocfilehash: e4f8fc636349aaa12ee4481c7f6223c343b6d406
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97169634"
---
# <a name="a-portrait-of-the-documentview-architecture"></a>문서/뷰 아키텍처에 대한 자세한 설명

문서와 보기는 일반적인 MFC 응용 프로그램에서 쌍으로 연결 됩니다. 데이터는 문서에 저장 되지만 뷰에는 데이터에 대 한 특권 수준의 액세스 권한이 있습니다. 문서를 뷰에서 분리 하 여 데이터의 저장 및 유지 관리를 표시 합니다.

## <a name="gaining-access-to-document-data-from-the-view"></a>뷰에서 문서 데이터에 대 한 액세스 권한 얻기

뷰는 문서에 대 한 포인터를 반환 하는 [Getdocument](reference/cview-class.md#getdocument) 함수와 문서 클래스의 c + +로 뷰 클래스를 만들어 문서 데이터에 액세스 합니다 **`friend`** . 그런 다음 뷰는 데이터에 대 한 액세스를 사용 하 여 데이터를 그리거나 조작할 준비가 되 면 데이터를 가져옵니다.

예를 들어 뷰의 [OnDraw](reference/cview-class.md#ondraw) 멤버 함수에서 뷰는를 사용 하 여 `GetDocument` 문서 포인터를 가져옵니다. 그런 다음 해당 포인터를 사용 하 여 `CString` 문서의 데이터 멤버에 액세스 합니다. 뷰가 문자열을 함수에 전달 `TextOut` 합니다. 이 예제에 대 한 코드를 보려면 [뷰에서 그리기](drawing-in-a-view.md)를 참조 하세요.

## <a name="user-input-to-the-view"></a>보기에 대 한 사용자 입력

뷰는 데이터를 선택 하거나 편집 하는 것 처럼 자체 내에서 마우스 클릭을 해석할 수도 있습니다. 마찬가지로 데이터 입력 또는 편집으로 키 입력을 해석할 수도 있습니다. 사용자가 텍스트를 관리 하는 보기에 문자열을 입력 한다고 가정 합니다. 뷰는 문서에 대 한 포인터를 가져오고 포인터를 사용 하 여 새 데이터를 문서에 전달 합니다. 그러면이 문서를 일부 데이터 구조에 저장 합니다.

## <a name="updating-multiple-views-of-the-same-document"></a>동일한 문서의 여러 뷰 업데이트

텍스트 편집기의 분할자 창과 같은 문서에 대 한 여러 뷰가 있는 응용 프로그램에서 뷰는 먼저 새 데이터를 문서에 전달 합니다. 그런 다음 문서의 [UpdateAllViews](reference/cdocument-class.md#updateallviews) 멤버 함수를 호출 하 여 새 데이터를 반영 하는 문서의 모든 보기를 업데이트 합니다. 그러면 보기가 동기화 됩니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [문서/뷰 아키텍처의 이점](advantages-of-the-document-view-architecture.md)

- [문서/뷰 아키텍처에 대 한 대안](alternatives-to-the-document-view-architecture.md)

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](document-view-architecture.md)
