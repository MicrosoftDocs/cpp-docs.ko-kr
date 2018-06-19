---
title: '데이터 개체 및 데이터 소스: 생성 및 소멸 | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b226c115ce148fa29b5d93cb60af8498b63fdee9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347950"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>데이터 개체 및 데이터 소스: 생성 및 소멸
문서에 설명 된 대로 [데이터 개체 및 데이터 소스 (OLE)](../mfc/data-objects-and-data-sources-ole.md), 데이터 개체 및 데이터 소스는 데이터 전송의 양쪽을 나타냅니다. 이 문서에서는 다음을 포함하여 데이터 전송을 제대로 수행하기 위해 이들 개체 및 소스를 만들고 제거할 경우에 대해 설명합니다.  
  
-   [데이터 개체 만들기](#_core_creating_data_objects)  
  
-   [데이터 개체 제거](#_core_destroying_data_objects)  
  
-   [데이터 소스 만들기](#_core_creating_data_sources)  
  
-   [데이터 소스 제거](#_core_destroying_data_sources)  
  
##  <a name="_core_creating_data_objects"></a> 데이터 개체 만들기  
 데이터 개체는 대상 응용 프로그램인 클라이언트 또는 서버에서 사용됩니다. 대상 응용 프로그램의 데이터 개체는 소스 응용 프로그램과 대상 응용 프로그램 간 연결의 한쪽 끝입니다. 대상 응용 프로그램의 데이터 개체는 데이터 소스의 데이터에 액세스하고 데이터와 상호 작용하는 데 사용됩니다.  
  
 데이터 개체를 필요한 두 가지 일반적인 경우가 있습니다. 첫 번째 상황은 끌어서 놓기를 사용하여 응용 프로그램에서 데이터를 삭제하는 경우입니다. 두 번째 상황은 편집 메뉴에서 붙여넣기 또는 선택하여 붙여넣기를 선택하는 경우입니다.  
  
 끌어서 놓기 상황에서는 데이터 개체를 만들 필요가 없습니다. 기존 데이터 개체에 대한 포인터는 `OnDrop` 함수에 전달됩니다. 이 데이터 개체는 프레임워크를 통해 끌어서 놓기 작업 일부로 만들어지고 프레임워크를 통해 제거됩니다. 다른 메서드에서 붙여넣기가 수행될 때 항상 이 경우에 해당하는 것은 아닙니다. 자세한 내용은 참조 [데이터 개체 제거](#_core_destroying_data_objects)합니다.  
  
 응용 프로그램에서 붙여넣기 또는 선택하여 붙여넣기 작업을 수행할 경우 `COleDataObject` 개체를 만들고 해당 `AttachClipboard` 멤버 함수를 호출해야 합니다. 이렇게 하면 데이터 개체가 클립보드의 데이터와 연결됩니다. 그런 다음 붙여넣기 함수에서 이 데이터 개체를 사용할 수 있습니다.  
  
##  <a name="_core_destroying_data_objects"></a> 데이터 개체 제거  
 에 설명 된 체계를 따를 경우 [데이터 개체 만들기](#_core_creating_data_objects), 데이터 개체 제거는 데이터 전송의 사소한 측면입니다. 붙여넣기 함수에서 만들어진 데이터 개체는 붙여넣기 함수가 반환될 때 MFC를 통해 제거됩니다.  
  
 붙여넣기 작업을 처리하는 또 다른 방법을 따를 경우 붙여넣기 작업이 완료된 후 데이터 개체가 제거되어야 합니다. 데이터 개체가 제거될 때까지 응용 프로그램에서는 데이터를 클립보드에 복사할 수 없습니다.  
  
##  <a name="_core_creating_data_sources"></a> 데이터 소스 만들기  
 데이터 소스는 데이터 전송의 클라이언트 또는 서버 쪽이 될 수 있는 데이터 전송의 소스에서 사용됩니다. 소스 응용 프로그램의 데이터 소스는 소스 응용 프로그램과 대상 응용 프로그램 간 연결의 한쪽 끝입니다. 대상 응용 프로그램의 데이터 개체는 데이터 소스의 데이터와 상호 작용하는 데 사용됩니다.  
  
 데이터 소스는 응용 프로그램에서 데이터를 클립보드에 복사해야 할 때 생성됩니다. 다음과 같은 일반적인 시나리오가 실행됩니다.  
  
1.  사용자가 일부 데이터를 선택합니다.  
  
2.  사용자가 선택 **복사** (또는 **잘라내기**)에서 고 **편집** 메뉴 하거나 끌어서 놓기 작업을 시작 합니다.  
  
3.  프로그램의 디자인에 따라 응용 프로그램에서는 `COleDataSource` 개체 또는 `COleDataSource`에서 파생 클래스 개체를 만듭니다.  
  
4.  선택한 데이터는 `COleDataSource::CacheData` 또는 `COleDataSource::DelayRenderData` 그룹의 함수 중 하나를 호출하는 방식으로 데이터 소스에 삽입됩니다.  
  
5.  응용 프로그램에서는 3단계에서 생성된 개체에 속한 `SetClipboard` 멤버 함수(또는 끌어서 놓기 작업인 경우 `DoDragDrop` 멤버 함수)를 호출합니다.  
  
6.  이것이 **잘라내기** 작업 또는 `DoDragDrop` 반환 `DROPEFFECT_MOVE`, 1 단계에서 선택한 데이터가 문서에서 삭제 됩니다.  
  
 이 시나리오는 MFC OLE 샘플에서 구현 [OCLIENT](../visual-cpp-samples.md) 및 [HIERSVR](../visual-cpp-samples.md)합니다. `GetClipboardData` 및 `OnGetClipboardData` 함수 외에 모든 함수에 대한 각 응용 프로그램의 `CView` 파생 클래스 소스를 살펴봅니다. 이들 두 함수는 `COleClientItem` 또는 `COleServerItem` 파생 클래스 구현이 포함됩니다. 이들 샘플 프로그램에서는 이러한 개념을 구현하는 방법의 좋은 예를 제공합니다.  
  
 `COleDataSource` 개체를 만들어야 할 한 가지 다른 상황은 끌어서 놓기 작업의 기본 동작을 수정할 경우 발생합니다. 자세한 내용은 참조는 [끌어서 놓기: 사용자 지정](../mfc/drag-and-drop-customizing.md) 문서.  
  
##  <a name="_core_destroying_data_sources"></a> 데이터 소스 제거  
 데이터 소스는 현재 데이터 소스를 처리해야 하는 응용 프로그램을 통해 제거되어야 합니다. 데이터 소스를 OLE 전달 하는 경우에서와 같은 호출 [coledatasource:: Dodragdrop](../mfc/reference/coledatasource-class.md#dodragdrop)를를 호출 해야 **pdatasrc->internalrelease**합니다. 예를 들어:  
  
 [!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]  
  
 데이터를 OLE에 전달하지 않은 경우에는 사용자가 일반적인 C++ 개체를 제거하는 것처럼 데이터 소스를 제거해야 합니다.  
  
 자세한 내용은 참조 [끌어서 놓기](../mfc/drag-and-drop-ole.md), [클립보드](../mfc/clipboard.md), 및 [데이터 개체 및 데이터 소스 조작](../mfc/data-objects-and-data-sources-manipulation.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 개체 및 데이터 소스 (OLE)](../mfc/data-objects-and-data-sources-ole.md)   
 [COleDataObject 클래스](../mfc/reference/coledataobject-class.md)   
 [COleDataSource 클래스](../mfc/reference/coledatasource-class.md)
