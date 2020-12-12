---
description: '자세히 알아보기: 메뉴 및 리소스: 서버 추가'
title: '메뉴 및 리소스: 서버 추가'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: e53031fd030efa498bd80bdb191f76f66f63d343
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122878"
---
# <a name="menus-and-resources-server-additions"></a>메뉴 및 리소스: 서버 추가

이 문서에서는 비주얼 편집 서버 (구성 요소) 응용 프로그램에서 메뉴 및 기타 리소스에 적용 해야 하는 변경 사항을 설명 합니다. 서버 응용 프로그램을 사용 하려면 메뉴 구조와 기타 리소스를 추가 해야 합니다 .이 모드는 독립 실행형, 포함 또는 현재 위치 중 하나로 시작할 수 있습니다. [메뉴 및 리소스 (OLE)](menus-and-resources-ole.md) 문서에 설명 된 대로 최대 4 개의 메뉴 집합이 있습니다. 네 가지 모두 MDI 전체 서버 응용 프로그램에 사용 되지만 미니 서버에는 3 개만 사용 됩니다. 응용 프로그램 마법사가 원하는 서버 유형에 필요한 메뉴 레이아웃을 만듭니다. 일부 사용자 지정이 필요할 수 있습니다.

응용 프로그램 마법사를 사용 하지 않는 경우 HIERSVR를 확인 하는 것이 좋습니다. MFC 샘플 응용 프로그램에 대 한 리소스 [스크립트로, 이러한](../overview/visual-cpp-samples.md)변경 내용을 구현 하는 방법을 확인 하는 데 사용할 수 있습니다.

이 문서에서 다루는 항목은 다음과 같습니다.

- [서버 메뉴 추가](#_core_server_menu_additions)

- [액셀러레이터 키 테이블 추가](#_core_server_application_accelerator_table_additions)

- [문자열 테이블 추가](menus-and-resources-container-additions.md)

- [미니 미니 추가](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a> 서버 메뉴 추가

OLE 비주얼 편집을 지원 하기 위해 서버 (구성 요소) 응용 프로그램에 메뉴 리소스가 추가 되어 있어야 합니다. 독립 실행형 모드에서 응용 프로그램을 실행할 때 사용 되는 메뉴는 변경할 필요가 없지만 응용 프로그램을 빌드하기 전에 두 개의 새 메뉴 리소스를 추가 해야 합니다. 응용 프로그램은 내부 활성화를 지원 하 고 다른 하나는 완전히 열려 있는 서버를 지원 합니다. 모든 메뉴 리소스는 전체 및 미니 응용 프로그램 응용 프로그램에서 사용 됩니다.

- 내부 활성화를 지원 하려면 독립 실행형 모드에서 실행할 때 사용 되는 메뉴 리소스와 매우 유사한 메뉴 리소스를 만들어야 합니다. 이 메뉴의 차이점은 파일 및 창 항목 (및 데이터가 아닌 응용 프로그램을 처리 하는 다른 모든 메뉴 항목)이 누락 되었다는 것입니다. 컨테이너 응용 프로그램은 이러한 메뉴 항목을 제공 합니다. 이 메뉴 병합 기술에 대 한 자세한 내용 및 예제는 메뉴 [및 리소스: 메뉴 병합](menus-and-resources-menu-merging.md)문서를 참조 하세요.

- 완전히 열린 활성화를 지원 하려면 독립 실행형 모드에서 실행할 때 사용 되는 메뉴 리소스와 거의 동일한 메뉴 리소스를 만들어야 합니다. 이 메뉴 리소스를 수정 하는 유일한 방법은 서버가 복합 문서에 포함 된 항목에서 작동 한다는 사실을 반영 하기 위해 일부 항목을 다시 작성 하는 것입니다.

이 문서에 나열 된 변경 내용 외에도 리소스 파일은 AFXOLESV를 포함 해야 합니다. RC는 MFC 라이브러리 구현에 필요 합니다. 이 파일은 MFC\Include 하위 디렉터리에 있습니다.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a> 서버 응용 프로그램 액셀러레이터 키 테이블 추가

서버 응용 프로그램에 두 개의 새로운 액셀러레이터 키 테이블 리소스를 추가 해야 합니다. 앞서 설명한 새 메뉴 리소스에 직접 대응 합니다. 첫 번째 액셀러레이터 키 테이블은 서버 응용 프로그램이 현재 활성화 되어 있을 때 사용 됩니다. 이 클래스는 파일 및 창 메뉴에 연결 된 항목을 제외 하 고 뷰의 액셀러레이터 키 테이블에 있는 모든 항목으로 구성 됩니다.

두 번째 테이블은 거의 뷰의 액셀러레이터 키 테이블과 정확히 같은 복사본입니다. [서버 메뉴 추가](#_core_server_menu_additions)에 설명 된 전체 열기 메뉴에서 수행 되는 모든 차이의 병렬 변경 내용

이러한 액셀러레이터 키 테이블 변경에 대 한 예를 보려면 IDR_HIERSVRTYPE_SRVR_IP 및 IDR_HIERSVRTYPE_SRVR_EMB accelerator 테이블을 HIERSVR의 IDR_MAINFRAME와 비교 합니다. MFC OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md)에 포함 된 RC 파일입니다. 현재 위치의 테이블에는 파일 및 창 액셀러레이터 키가 없고 해당 파일의 정확한 복사본이 포함 된 테이블에 있습니다.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a> 서버 응용 프로그램에 대 한 문자열 테이블 추가

서버 응용 프로그램에는 하나의 문자열 테이블 추가만 필요 합니다. 즉, OLE 초기화가 실패 한 것으로 나타내는 문자열입니다. 예를 들어 응용 프로그램 마법사에서 생성 하는 문자열 테이블 항목은 다음과 같습니다.

|ID|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|OLE를 초기화 하지 못했습니다. OLE 라이브러리 버전이 올바른지 확인 하십시오.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a> 미니 미니 추가

전체 서버에 대해 위에 나열 된 것과 같은 추가 항목이 미니 서버에 적용 됩니다. 미니 미니는 독립 실행형 모드에서 실행할 수 없기 때문에 주 메뉴가 훨씬 더 작습니다. 응용 프로그램 마법사에서 만든 주 메뉴에는 끝내기 및 정보 항목만 포함 하는 파일 메뉴만 있습니다. 미니 서버에 포함 된 메뉴와 바로 가기는 전체 서버와 동일 합니다.

## <a name="see-also"></a>참고 항목

[메뉴 및 리소스 (OLE)](menus-and-resources-ole.md)<br/>
[메뉴 및 리소스: 메뉴 병합](menus-and-resources-menu-merging.md)
