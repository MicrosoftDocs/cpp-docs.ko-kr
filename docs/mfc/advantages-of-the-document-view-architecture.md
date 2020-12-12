---
description: '자세히 알아보기: 문서/뷰 아키텍처의 장점'
title: Document-View 아키텍처의 장점
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], advantages
- document/view architecture [MFC], advantages of
ms.assetid: 0bc27071-e120-4889-939c-ce1e61fb9cb3
ms.openlocfilehash: 54ff7cc0e4717f7f487ece3acee79f39ad7dfa3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185455"
---
# <a name="advantages-of-the-documentview-architecture"></a>문서/뷰 아키텍처의 이점

MFC 문서/뷰 아키텍처를 사용 하는 경우의 주요 이점은 아키텍처에서 동일한 문서에 대 한 여러 뷰를 지원 한다는 것입니다. 여러 뷰가 필요 없고 문서/뷰의 작은 오버 헤드가 응용 프로그램에서 과도 하 게 사용 되는 경우 아키텍처를 피할 수 있습니다. [문서/뷰 아키텍처에 대 한 대안](alternatives-to-the-document-view-architecture.md)입니다.

응용 프로그램에서 사용자가 스프레드시트 양식이 나 차트 형식으로 숫자 데이터를 볼 수 있다고 가정 합니다. 사용자는 스프레드시트 형식으로 원시 데이터와 데이터의 결과로 생성 되는 차트를 동시에 볼 수 있습니다. 별도의 프레임 창 또는 분할자 창에서 단일 창에 이러한 별도의 뷰를 표시 합니다. 이제 사용자가 스프레드시트의 데이터를 편집 하 고 차트에 즉시 반영 된 변경 내용을 볼 수 있다고 가정 합니다.

MFC에서 스프레드시트 뷰와 차트 뷰는 CView에서 파생 된 여러 클래스를 기반으로 합니다. 두 뷰 모두 단일 문서 개체와 연결 됩니다. 문서는 데이터를 저장 하거나 데이터베이스에서 가져옵니다. 두 보기 모두 문서에 액세스 하 여 검색 한 데이터를 표시 합니다.

사용자가 뷰 중 하나를 업데이트 하면 해당 view 개체는를 호출 `CDocument::UpdateAllViews` 합니다. 이 함수는 모든 문서의 뷰를 알리고 각 보기는 문서의 최신 데이터를 사용 하 여 자신을 업데이트 합니다. 에 대 한 단일 호출은 `UpdateAllViews` 여러 뷰를 동기화 합니다.

특히 뷰가 데이터 자체를 저장 한 경우에는 뷰에서 데이터를 분리 하지 않고 코드를 사용 하는 것이 어렵습니다. 문서/뷰를 사용 하면 간단 합니다. 프레임 워크는 대부분의 조정 작업을 수행 합니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [문서/보기에 대 한 대안](alternatives-to-the-document-view-architecture.md)

- [CDocument](reference/cdocument-class.md)

- [CView](reference/cview-class.md)

- [CDocument:: UpdateAllViews](reference/cdocument-class.md#updateallviews)

- [CView:: GetDocument](reference/cview-class.md#getdocument)

## <a name="see-also"></a>참고 항목

[문서/뷰 아키텍처](document-view-architecture.md)
