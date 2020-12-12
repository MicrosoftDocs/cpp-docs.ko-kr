---
description: '자세히 알아보기: 메뉴 및 리소스 (OLE)'
title: 메뉴 및 리소스(OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
ms.openlocfilehash: a6ec4f2750a99935cb0113a3ad607be8a80d4bfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133148"
---
# <a name="menus-and-resources-ole"></a>메뉴 및 리소스(OLE)

이 문서 그룹에서는 MFC OLE 문서 응용 프로그램에서 메뉴와 리소스를 사용 하는 방법을 설명 합니다.

OLE 시각적 편집에는 컨테이너 및 서버 (구성 요소) 응용 프로그램을 시작 하 고 사용할 수 있는 여러 가지 모드가 있으므로 OLE 문서 응용 프로그램에서 제공 하는 메뉴 및 기타 리소스에 대 한 추가 요구 사항이 있습니다. 예를 들어 전체 서버 응용 프로그램은 다음과 같은 세 가지 모드 중 하나에서 실행할 수 있습니다.

- 독립적입니다.

- 컨테이너의 컨텍스트 내에서 항목을 편집 하기 위한 것입니다.

- 컨테이너의 컨텍스트 외부에 있는 항목을 편집 하기 위해 (일반적으로 별도의 창에서)를 엽니다.

이렇게 하려면 응용 프로그램의 가능한 각 모드에 대해 하나씩, 세 개의 개별 메뉴 레이아웃이 필요 합니다. 액셀러레이터 키 테이블은 각 새 모드에도 필요 합니다. 컨테이너 응용 프로그램은 내부 활성화를 지원 하거나 지원 하지 않을 수 있습니다. 이 경우 새 메뉴 구조와 연결 된 액셀러레이터 키 테이블이 필요 합니다.

내부 활성화를 사용 하려면 컨테이너 및 서버 응용 프로그램에서 메뉴, 도구 모음 및 상태 표시줄 공간을 협상 해야 합니다. 모든 리소스를 염두에 두면 디자인 해야 합니다. [메뉴 및 리소스 문서: 메뉴 병합](menus-and-resources-menu-merging.md) 에서는이 항목에 대해 자세히 설명 합니다.

이러한 문제로 인해 응용 프로그램 마법사를 사용 하 여 만든 OLE 문서 응용 프로그램은 최대 4 개의 개별 메뉴 및 액셀러레이터 키 테이블 리소스를 가질 수 있습니다. 이러한 작업은 다음과 같은 이유로 사용 됩니다.

|리소스 이름|기능|
|-------------------|---------|
|IDR_MAINFRAME|열려 있는 파일에 관계 없이 파일이 열려 있지 않거나 SDI 응용 프로그램에 있는 경우 MDI 응용 프로그램에서 사용 됩니다. 이는 비 OLE 응용 프로그램에서 사용 되는 표준 메뉴입니다.|
|IDR_ \<project> 형식|파일이 열려 있는 경우 MDI 응용 프로그램에서 사용 됩니다. 응용 프로그램에서 독립 실행형으로 실행 하는 경우 사용 됩니다. 이는 비 OLE 응용 프로그램에서 사용 되는 표준 메뉴입니다.|
|IDR_ \<project> TYPE_SRVR_IP|서버 또는 컨테이너에서 개체가 열려 있을 때 사용 됩니다.|
|IDR_ \<project> TYPE_SRVR_EMB|내부 활성화를 사용 하지 않고 개체를 연 경우 서버 응용 프로그램에서 사용 됩니다.|

이러한 각 리소스 이름은 메뉴 및 일반적으로 액셀러레이터 키 테이블을 나타냅니다. 응용 프로그램 마법사를 사용 하 여 만들지 않은 MFC 응용 프로그램에서 유사한 체계를 사용 해야 합니다.

다음 문서에서는 컨테이너, 서버 및 내부 활성화를 구현 하는 데 필요한 메뉴 병합과 관련 된 항목을 설명 합니다.

- [메뉴 및 리소스: 컨테이너 추가](menus-and-resources-container-additions.md)

- [메뉴 및 리소스: 서버 추가](menus-and-resources-server-additions.md)

- [메뉴 및 리소스: 메뉴 병합](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>참고 항목

[OLE](ole-in-mfc.md)
