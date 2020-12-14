---
description: '자세히 알아보기: 메뉴 및 리소스: 컨테이너 추가'
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
ms.openlocfilehash: e32167e66693587a32732c1c20fc6d85d3010ecb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253366"
---
# <a name="menus-and-resources-container-additions"></a>메뉴 및 리소스: 컨테이너 추가

이 문서에서는 시각적 편집 컨테이너 응용 프로그램에서 메뉴 및 기타 리소스에 적용 해야 하는 변경 사항을 설명 합니다.

컨테이너 응용 프로그램에서 두 가지 유형의 변경 작업을 수행 해야 합니다. OLE 비주얼 편집을 지원 하기 위해 기존 리소스를 수정 하 고 내부 활성화에 사용 되는 새 리소스를 추가 해야 합니다. 응용 프로그램 마법사를 사용 하 여 컨테이너 응용 프로그램을 만드는 경우에는 이러한 단계가 수행 되지만 일부 사용자 지정이 필요할 수 있습니다.

응용 프로그램 마법사를 사용 하지 않는 경우 OCLIENT를 확인 하는 것이 좋습니다. RC는이 변경 내용을 구현 하는 방법을 확인 하기 위해 OCLIENT 샘플 응용 프로그램에 대 한 리소스 스크립트입니다. MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md)를 참조 하십시오.

이 문서에서 다루는 항목은 다음과 같습니다.

- [컨테이너 메뉴 추가](#_core_container_menu_additions)

- [액셀러레이터 키 테이블 추가](#_core_container_application_accelerator_table_additions)

- [문자열 테이블 추가](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a> 컨테이너 메뉴 추가

편집 메뉴에 다음 항목을 추가 해야 합니다.

|항목|목적|
|----------|-------------|
|**새 개체 삽입**|OLE 개체 삽입 대화 상자를 열어 링크 된 항목이 나 포함 된 항목을 문서에 삽입 합니다.|
|**링크 붙여넣기**|클립보드에 있는 항목에 대 한 링크를 문서에 붙여 넣습니다.|
|**OLE 동사**|선택한 항목의 기본 동사를 호출 합니다. 이 메뉴 항목의 텍스트는 선택한 항목의 기본 동사를 반영 하도록 변경 됩니다.|
|**연결**|OLE 링크 편집 대화 상자를 열어 기존 연결 된 항목을 변경 합니다.|

이 문서에 나열 된 변경 내용 외에도 소스 파일에는 AFXOLECL이 포함 되어야 합니다. RC는 MFC 라이브러리 구현에 필요 합니다. 새 개체 삽입은 유일 하 게 필요한 메뉴 추가입니다. 다른 항목을 추가할 수 있지만 여기에 나열 된 항목은 가장 일반적입니다.

포함 된 항목의 내부 활성화를 지원 하려면 컨테이너 응용 프로그램에 대 한 새 메뉴를 만들어야 합니다. 이 메뉴는 파일이 열려 있을 때 사용 되는 것과 동일한 파일 메뉴 및 창 팝업 메뉴로 구성 되어 있지만 두 개의 구분 기호를 포함 합니다. 이러한 구분 기호는 활성화 된 서버 (구성 요소) 항목 (응용 프로그램)에서 메뉴를 어디에 배치할지를 나타내는 데 사용 됩니다. 이 메뉴 병합 기술에 대 한 자세한 내용은 메뉴 [및 리소스: 메뉴 병합](menus-and-resources-menu-merging.md)을 참조 하세요.

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a> 컨테이너 응용 프로그램 액셀러레이터 키 테이블 추가

내부 활성화를 지 원하는 경우 컨테이너 응용 프로그램의 액셀러레이터 테이블 리소스가 약간 변경 해야 합니다. 첫 번째 변경을 통해 사용자는 ESC 키를 눌러 내부 편집 모드를 취소할 수 있습니다. 기본 액셀러레이터 키 테이블에 다음 항목을 추가 합니다.

|ID|키|형식|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

두 번째 변경 내용은 내부 활성화를 위해 만든 새 메뉴 리소스에 해당 하는 새 액셀러레이터 키 테이블을 만드는 것입니다. 이 테이블에는 위의 VK_ESCAPE 항목 외에도 파일 및 창 메뉴에 대 한 항목이 있습니다. 다음 예제는 MFC 샘플 [컨테이너](../overview/visual-cpp-samples.md)에서 내부 활성화를 위해 만든 액셀러레이터 키 테이블입니다.

|ID|키|형식|
|--------|---------|----------|
|ID_FILE_NEW|CTRL+N|**VIRTKEY**|
|ID_FILE_OPEN|Ctrl+O|**VIRTKEY**|
|ID_FILE_SAVE|Ctrl+S|**VIRTKEY**|
|ID_FILE_PRINT|Ctrl+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a> 컨테이너 응용 프로그램에 대 한 문자열 테이블 추가

컨테이너 응용 프로그램에 대 한 문자열 테이블에 대 한 대부분의 변경 내용은 [컨테이너 메뉴](#_core_container_menu_additions)추가 항목에 설명 된 추가 메뉴 항목에 해당 합니다. 각 메뉴 항목이 표시 될 때 상태 표시줄에 표시 되는 텍스트를 제공 합니다. 예를 들어 응용 프로그램 마법사에서 생성 하는 문자열 테이블 항목은 다음과 같습니다.

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE를 초기화 하지 못했습니다. OLE 라이브러리 버전이 올바른지 확인 하십시오.|
|IDP_FAILED_TO_CREATE|개체를 만들지 못했습니다. 개체가 시스템 레지스트리에 입력 되어 있는지 확인 합니다.|

## <a name="see-also"></a>참고 항목

[메뉴 및 리소스 (OLE)](menus-and-resources-ole.md)<br/>
[메뉴 및 리소스: 서버 추가](menus-and-resources-server-additions.md)
