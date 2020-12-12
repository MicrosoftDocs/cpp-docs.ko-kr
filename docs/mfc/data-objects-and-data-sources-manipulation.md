---
description: '자세한 정보: 데이터 개체 및 데이터 소스: 조작'
title: '데이터 개체 및 데이터 소스: 조작'
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
ms.openlocfilehash: a9611fefc94e8437f9e0e5361e0d95972f867984
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97291235"
---
# <a name="data-objects-and-data-sources-manipulation"></a>데이터 개체 및 데이터 소스: 조작

데이터 개체 또는 데이터 원본을 만든 후 데이터 삽입 및 제거, 데이터의 형식 열거 등 데이터에 대 한 여러 가지 일반적인 작업을 수행할 수 있습니다. 이 문서에서는 가장 일반적인 작업을 완료 하는 데 필요한 기술을 설명 합니다. 다룰 주제는 다음과 같습니다.

- [데이터 원본에 데이터 삽입](#_core_inserting_data_into_a_data_source)

- [데이터 개체에서 사용할 수 있는 형식 확인](#_core_determining_the_formats_available_in_a_data_object)

- [데이터 개체에서 데이터 검색](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a> 데이터 원본에 데이터 삽입

데이터를 데이터 원본에 삽입 하는 방법은 데이터가 즉시 제공 되는지, 아니면 요청 시 제공 되는지, 그리고 중간에 제공 되는지 여부에 따라 달라 집니다. 가능한 원인은 다음과 같습니다.

### <a name="supplying-data-immediately-immediate-rendering"></a>즉시 데이터 제공 (즉시 렌더링)

- `COleDataSource::CacheGlobalData`데이터를 제공 하는 모든 클립보드 형식에 대해를 반복적으로 호출 합니다. 사용할 클립보드 형식을 전달 하 고, 데이터를 포함 하는 메모리에 대 한 핸들을 전달 하 고, 필요에 따라 데이터를 설명 하는 **FORMATETC** 구조를 전달 합니다.

     또는

- **STGMEDIUM** 구조를 직접 사용 하려는 경우 `COleDataSource::CacheData` 위의 옵션 대신를 호출 합니다 `COleDataSource::CacheGlobalData` .

### <a name="supplying-data-on-demand-delayed-rendering"></a>주문형 데이터 제공 (지연 렌더링)

이는 고급 항목입니다.

- `COleDataSource::DelayRenderData`데이터를 제공 하는 모든 클립보드 형식에 대해를 반복적으로 호출 합니다. 사용할 클립보드 형식을 전달 하 고 필요에 따라 데이터를 설명 하는 **FORMATETC** 구조를 전달 합니다. 데이터가 요청 될 때 프레임 워크는 `COleDataSource::OnRenderData` 를 호출 합니다 .이는를 재정의 해야 합니다.

     또는

- 개체를 사용 하 여 데이터를 제공 하는 경우 `CFile` `COleDataSource::DelayRenderFileData` 이전 옵션 대신을 호출 `COleDataSource::DelayRenderData` 합니다. 데이터가 요청 될 때 프레임 워크는 `COleDataSource::OnRenderFileData` 를 호출 합니다 .이는를 재정의 해야 합니다.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a> 데이터 개체에서 사용할 수 있는 형식 확인

사용자가 응용 프로그램에 데이터를 붙여 넣을 수 있도록 하려면 클립보드에 처리할 수 있는 형식이 있는지 확인 해야 합니다. 이렇게 하려면 응용 프로그램에서 다음을 수행 해야 합니다.

1. `COleDataObject`개체 및 **FORMATETC** 구조를 만듭니다.

1. 데이터 개체의 `AttachClipboard` 멤버 함수를 호출 하 여 데이터 개체를 클립보드의 데이터와 연결 합니다.

1. 다음 작업 중 하나를 수행합니다.

   - `IsDataAvailable`필요한 형식이 하나 또는 두 개인 경우 데이터 개체의 멤버 함수를 호출 합니다. 이렇게 하면 클립보드의 데이터가 응용 프로그램 보다 훨씬 더 많은 형식을 지 원하는 경우 시간이 절약 됩니다.

     \-또는-

   - 데이터 개체의 `BeginEnumFormats` 멤버 함수를 호출 하 여 클립보드에서 사용할 수 있는 형식의 열거를 시작 합니다. 그런 다음 `GetNextFormat` 클립보드가 응용 프로그램에서 지 원하는 형식을 반환 하거나 추가 형식이 없는 경우를 호출 합니다.

**ON_UPDATE_COMMAND_UI** 를 사용 하는 경우 이제 편집 메뉴에 붙여넣기 및 가능한 한 특수 항목 붙여넣기를 사용 하도록 설정할 수 있습니다. 이렇게 하려면 또는를 호출 `CMenu::EnableMenuItem` `CCmdUI::Enable` 합니다. 컨테이너 응용 프로그램에서 메뉴 항목과 시기를 수행 해야 하는 항목에 대 한 자세한 내용은 [메뉴 및 리소스: 컨테이너 추가](menus-and-resources-container-additions.md)를 참조 하세요.

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a> 데이터 개체에서 데이터 검색

데이터 형식을 결정 한 후에는 데이터 개체에서 데이터를 검색 하는 것만 남았습니다. 이렇게 하기 위해 사용자는 데이터를 넣을 위치를 결정 하 고 응용 프로그램은 적절 한 함수를 호출 합니다. 다음 미디어 중 하나에서 데이터를 사용할 수 있습니다.

|중간|호출할 함수|
|------------|----------------------|
|전역 메모리 ( `HGLOBAL` )|`COleDataObject::GetGlobalData`|
|File ( `CFile` )|`COleDataObject::GetFileData`|
|**STGMEDIUM** 구조체 ( `IStorage` )|`COleDataObject::GetData`|

일반적으로 미디어는 클립보드 형식과 함께 지정 됩니다. 예를 들어 **CF_EMBEDDEDSTRUCT** 개체는 항상 `IStorage` **STGMEDIUM** 구조가 필요한 중간에 있습니다. 따라서 `GetData` **STGMEDIUM** 구조체를 수락할 수 있는이 함수 중 유일한 함수 이기 때문에을 사용 합니다.

클립보드 형식이 또는 미디어에 있는 경우 `IStream` `HGLOBAL` 프레임 워크는 `CFile` 데이터를 참조 하는 포인터를 제공할 수 있습니다. 그러면 응용 프로그램에서 파일 읽기를 사용 하 여 파일에서 데이터를 가져올 때와 거의 동일한 방식으로 데이터를 가져올 수 있습니다. 기본적으로 `OnRenderData` 데이터 소스의 및 루틴에 대 한 클라이언트 쪽 인터페이스입니다 `OnRenderFileData` .

이제 사용자는 동일한 형식의 다른 데이터와 마찬가지로 문서에 데이터를 삽입할 수 있습니다.

### <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [끌어서 놓기](drag-and-drop-ole.md)

- [클립보드](clipboard.md)

## <a name="see-also"></a>참고 항목

[데이터 개체 및 데이터 원본 (OLE)](data-objects-and-data-sources-ole.md)<br/>
[COleDataObject 클래스](reference/coledataobject-class.md)<br/>
[COleDataSource 클래스](reference/coledatasource-class.md)
