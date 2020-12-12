---
description: '데이터 개체 및 데이터 소스: 생성 및 소멸에 대 한 자세한 정보'
title: '데이터 개체 및 데이터 소스: 생성 및 소멸'
ms.date: 11/04/2016
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
ms.openlocfilehash: a19c7c2125c7d591bc4df4b3f01553a54de6a18b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206190"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>데이터 개체 및 데이터 소스: 생성 및 소멸

데이터 [개체 및 데이터 원본 (OLE)](data-objects-and-data-sources-ole.md)문서에 설명 된 대로 데이터 개체와 데이터 원본은 데이터 전송의 양쪽을 모두 나타냅니다. 이 문서에서는 다음을 포함하여 데이터 전송을 제대로 수행하기 위해 이들 개체 및 소스를 만들고 제거할 경우에 대해 설명합니다.

- [데이터 개체 만들기](#_core_creating_data_objects)

- [데이터 개체 제거](#_core_destroying_data_objects)

- [데이터 원본 만들기](#_core_creating_data_sources)

- [데이터 소스 제거](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a> 데이터 개체 만들기

데이터 개체는 대상 애플리케이션인 클라이언트 또는 서버에서 사용됩니다. 대상 애플리케이션의 데이터 개체는 소스 애플리케이션과 대상 애플리케이션 간 연결의 한쪽 끝입니다. 대상 애플리케이션의 데이터 개체는 데이터 소스의 데이터에 액세스하고 데이터와 상호 작용하는 데 사용됩니다.

데이터 개체를 필요한 두 가지 일반적인 경우가 있습니다. 첫 번째 상황은 끌어서 놓기를 사용하여 애플리케이션에서 데이터를 드롭하는 경우입니다. 두 번째 상황은 편집 메뉴에서 붙여넣기 또는 선택하여 붙여넣기를 선택하는 경우입니다.

끌어서 놓기 상황에서는 데이터 개체를 만들 필요가 없습니다. 기존 데이터 개체에 대한 포인터는 `OnDrop` 함수에 전달됩니다. 이 데이터 개체는 프레임워크를 통해 끌어서 놓기 작업 일부로 만들어지고 프레임워크를 통해 제거됩니다. 다른 메서드에서 붙여넣기가 수행될 때 항상 이 경우에 해당하는 것은 아닙니다. 자세한 내용은 [데이터 개체](#_core_destroying_data_objects)제거를 참조 하세요.

애플리케이션에서 붙여넣기 또는 선택하여 붙여넣기 작업을 수행할 경우 `COleDataObject` 개체를 만들고 해당 `AttachClipboard` 멤버 함수를 호출해야 합니다. 이렇게 하면 데이터 개체가 클립보드의 데이터와 연결됩니다. 그런 다음 붙여넣기 함수에서 이 데이터 개체를 사용할 수 있습니다.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a> 데이터 개체 제거

데이터 [개체 만들기](#_core_creating_data_objects)에 설명 된 스키마를 따르는 경우 데이터 개체를 제거 하는 것은 데이터 전송의 간단한 측면입니다. 붙여넣기 함수에서 만들어진 데이터 개체는 붙여넣기 함수가 반환될 때 MFC를 통해 제거됩니다.

붙여넣기 작업을 처리하는 또 다른 방법을 따를 경우 붙여넣기 작업이 완료된 후 데이터 개체가 제거되어야 합니다. 데이터 개체가 제거될 때까지 애플리케이션에서는 데이터를 클립보드에 복사할 수 없습니다.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a> 데이터 원본 만들기

데이터 소스는 데이터 전송의 클라이언트 또는 서버 쪽이 될 수 있는 데이터 전송의 소스에서 사용됩니다. 소스 애플리케이션의 데이터 소스는 소스 애플리케이션과 대상 애플리케이션 간 연결의 한쪽 끝입니다. 대상 애플리케이션의 데이터 개체는 데이터 소스의 데이터와 상호 작용하는 데 사용됩니다.

데이터 소스는 애플리케이션에서 데이터를 클립보드에 복사해야 할 때 생성됩니다. 다음과 같은 일반적인 시나리오가 실행됩니다.

1. 사용자가 일부 데이터를 선택합니다.

1. 사용자가 **편집** 메뉴에서 **복사** (또는 **잘라내기**)를 선택 하거나 끌어서 놓기 작업을 시작 합니다.

1. 프로그램의 디자인에 따라 애플리케이션에서는 `COleDataSource` 개체 또는 `COleDataSource`에서 파생 클래스 개체를 만듭니다.

1. 선택한 데이터는 `COleDataSource::CacheData` 또는 `COleDataSource::DelayRenderData` 그룹의 함수 중 하나를 호출하는 방식으로 데이터 소스에 삽입됩니다.

1. 애플리케이션에서는 3단계에서 생성된 개체에 속한 `SetClipboard` 멤버 함수(또는 끌어서 놓기 작업인 경우 `DoDragDrop` 멤버 함수)를 호출합니다.

1. **잘라내기** 작업 이거나 `DoDragDrop` **DROPEFFECT_MOVE** 을 반환 하는 경우 1 단계에서 선택한 데이터가 문서에서 삭제 됩니다.

이 시나리오는 MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 및 [HIERSVR](../overview/visual-cpp-samples.md)에서 구현 됩니다. `GetClipboardData` 및 `OnGetClipboardData` 함수 외에 모든 함수에 대한 각 애플리케이션의 `CView` 파생 클래스 소스를 살펴봅니다. 이들 두 함수는 `COleClientItem` 또는 `COleServerItem` 파생 클래스 구현이 포함됩니다. 이들 샘플 프로그램에서는 이러한 개념을 구현하는 방법의 좋은 예를 제공합니다.

`COleDataSource` 개체를 만들어야 할 한 가지 다른 상황은 끌어서 놓기 작업의 기본 동작을 수정할 경우 발생합니다. 자세한 내용은 [OLE 끌어서 놓기: 끌어서 놓기 사용자 지정](drag-and-drop-ole.md#customize-drag-and-drop) 문서를 참조 하세요.

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a> 데이터 원본 삭제

데이터 소스는 현재 데이터 소스를 처리해야 하는 애플리케이션을 통해 제거되어야 합니다. 데이터 원본을 OLE에 전달 하는 경우 (예: [Coledatasource::D oDragDrop](reference/coledatasource-class.md#dodragdrop)호출)를 호출 해야 `pDataSrc->InternalRelease` 합니다. 예를 들어:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

데이터를 OLE에 전달하지 않은 경우에는 사용자가 일반적인 C++ 개체를 제거하는 것처럼 데이터 소스를 제거해야 합니다.

자세한 내용은 [데이터 개체 및 데이터 소스](data-objects-and-data-sources-manipulation.md) [끌어서 놓기](drag-and-drop-ole.md), [클립보드](clipboard.md)및 조작을 참조 하세요.

## <a name="see-also"></a>참고 항목

[데이터 개체 및 데이터 원본 (OLE)](data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 클래스](reference/coledataobject-class.md)<br/>
[COleDataSource 클래스](reference/coledatasource-class.md)
