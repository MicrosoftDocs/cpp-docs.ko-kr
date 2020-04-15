---
title: '메뉴 및 리소스: 컨테이너 추가'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364787"
---
# <a name="menus-and-resources-container-additions"></a>메뉴 및 리소스: 컨테이너 추가

이 문서에서는 시각적 편집 컨테이너 응용 프로그램의 메뉴 및 기타 리소스에 대해 수행해야 하는 변경 사항에 대해 설명합니다.

컨테이너 응용 프로그램에서는 OLE 시각적 편집을 지원하기 위해 기존 리소스를 수정하고 내부 활성화에 사용되는 새 리소스를 추가하는 두 가지 유형의 변경이 필요합니다. 응용 프로그램 마법사를 사용하여 컨테이너 응용 프로그램을 만드는 경우 이러한 단계는 수행되지만 일부 사용자 지정이 필요할 수 있습니다.

응용 프로그램 마법사를 사용하지 않는 경우 OCLIENT를 살펴볼 수 있습니다. OCLIENT 샘플 응용 프로그램의 리소스 스크립트인 RC를 사용하여 이러한 변경 내용이 구현되는 방법을 확인합니다. MFC OLE 샘플 [OCLIENT를](../overview/visual-cpp-samples.md)참조하십시오.

이 문서에서 다루는 주제는 다음과 같습니다.

- [컨테이너 메뉴 추가](#_core_container_menu_additions)

- [가속기 테이블 추가](#_core_container_application_accelerator_table_additions)

- [문자열 테이블 추가](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>컨테이너 메뉴 추가

편집 메뉴에 다음 항목을 추가해야 합니다.

|항목|용도|
|----------|-------------|
|**새 개체 삽입**|OLE 객체 삽입 대화 상자를 열어 링크된 항목이나 포함된 항목을 문서에 삽입합니다.|
|**링크 붙여넣기**|클립보드의 항목에 대한 링크를 문서에 붙여넣습니다.|
|**올레 동사**|선택한 항목의 기본 동사를 호출합니다. 이 메뉴 항목의 텍스트가 선택한 항목의 기본 동사를 반영하도록 변경됩니다.|
|**링크**|OLE 편집 링크 대화 상자를 열어 기존 링크된 항목을 변경합니다.|

이 문서에 나열된 변경 내용 외에도 소스 파일에는 AFXOLECL이 포함되어야 합니다. Microsoft 재단 클래스 라이브러리 구현에 필요한 RC입니다. 새 개체 삽입은 필요한 메뉴 추가만 입니다. 다른 항목을 추가할 수 있지만 여기에 나열된 항목이 가장 일반적입니다.

포함된 항목의 내부 활성화를 지원하려면 컨테이너 응용 프로그램에 대한 새 메뉴를 만들어야 합니다. 이 메뉴는 파일이 열려 있을 때 사용되는 동일한 파일 메뉴와 창 팝업 메뉴로 구성되지만 둘 사이에 두 개의 구분 기호가 있습니다. 이러한 구분 기호는 서버(구성 요소) 항목(응용 프로그램)이 활성화될 때 메뉴를 배치해야 하는 위치를 나타내는 데 사용됩니다. 이 메뉴 병합 기술에 대한 자세한 내용은 [메뉴 및 리소스: 메뉴 병합](../mfc/menus-and-resources-menu-merging.md)을 참조하십시오.

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>컨테이너 응용 프로그램 가속기 테이블 추가

내부 활성화를 지원하는 경우 컨테이너 응용 프로그램의 액셀러레이터 테이블 리소스를 조금씩 변경해야 합니다. 첫 번째 변경 을 통해 사용자는 ESC(이스케이프 키)를 눌러 현재 편집 모드를 취소할 수 있습니다. 주 가속기 테이블에 다음 항목을 추가합니다.

|ID|키|Type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

두 번째 변경 사항은 내부 활성화를 위해 만든 새 메뉴 리소스에 해당하는 새 가속기 테이블을 만드는 것입니다. 이 테이블에는 위의 VK_ESCAPE 항목 외에 파일 및 창 메뉴에 대한 항목이 있습니다. 다음 예제는 MFC 샘플 [컨테이너에서](../overview/visual-cpp-samples.md)내부 활성화를 위해 만든 가속기 테이블입니다.

|ID|키|Type|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|CTRL+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|시프트+VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>컨테이너 응용 프로그램에 대한 문자열 테이블 추가

컨테이너 응용 프로그램에 대한 문자열 테이블에 대한 대부분의 변경 내용은 컨테이너 메뉴 추가에 언급된 추가 메뉴 항목에 [해당합니다.](#_core_container_menu_additions) 각 메뉴 항목이 표시될 때 상태 표시줄에 표시되는 텍스트를 제공합니다. 예를 들어 응용 프로그램 마법사가 생성하는 문자열 테이블 항목은 다음과 같습니다.

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE 초기화가 실패했습니다. OLE 라이브러리가 올바른 버전인지 확인합니다.|
|IDP_FAILED_TO_CREATE|개체를 만들지 못했습니다. 개체가 시스템 레지스트리에 입력되어 있는지 확인합니다.|

## <a name="see-also"></a>참고 항목

[메뉴 및 리소스(OLE)](../mfc/menus-and-resources-ole.md)<br/>
[메뉴 및 리소스: 서버 추가](../mfc/menus-and-resources-server-additions.md)
