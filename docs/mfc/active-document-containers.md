---
description: '자세한 정보: 액티브 문서 컨테이너'
title: 액티브 문서 컨테이너
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: 31cf2739595cb7a48b152dcefb6c21970b95f8bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150412"
---
# <a name="active-document-containers"></a>액티브 문서 컨테이너

Microsoft Office 바인더 또는 Internet Explorer와 같은 액티브 문서 컨테이너를 사용 하면 각 문서 유형에 대해 여러 응용 프로그램 프레임을 만들고 사용 하는 대신 단일 프레임 내에서 다양 한 응용 프로그램 유형의 여러 문서로 작업할 수 있습니다.

MFC는 클래스의 액티브 문서 컨테이너를 완벽 하 게 지원 합니다 `COleDocObjectItem` . Mfc 응용 프로그램 마법사를 사용 하 여 MFC 응용 프로그램 마법사의 **복합 문서 지원** 페이지에서 **액티브 문서 컨테이너** 확인란을 선택 하 여 액티브 문서 컨테이너를 만들 수 있습니다. 자세한 내용은 [액티브 문서 컨테이너 응용 프로그램 만들기](creating-an-active-document-container-application.md)를 참조 하세요.

액티브 문서 컨테이너에 대 한 자세한 내용은 다음을 참조 하세요.

- [컨테이너 요구 사항](#container_requirements)

- [문서 사이트 개체](#document_site_objects)

- [사이트 개체 보기](#view_site_objects)

- [프레임 개체](#frame_object)

- [도움말 메뉴 병합](help-menu-merging.md)

- [프로그래밍 방식 인쇄](programmatic-printing.md)

- [명령 대상](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a> 컨테이너 요구 사항

액티브 문서 컨테이너의 액티브 문서 지원은 인터페이스 구현 뿐만 아니라 포함 된 개체의 인터페이스 사용에 대 한 지식이 필요 합니다. 활성 문서 확장에도 마찬가지입니다. 컨테이너는 활성 문서 자체에서 해당 확장 인터페이스를 사용 하는 방법을 알고 있어야 합니다.

활성 문서를 통합 하는 액티브 문서 컨테이너는 다음을 수행 해야 합니다.

- 인터페이스를 통해 개체 저장소를 처리할 수 있어야 합니다 `IPersistStorage` . 즉, `IStorage` 각 활성 문서에 대 한 인스턴스를 제공 해야 합니다.

- 및를 구현 하는 "사이트" 개체 (문서 당 하나 또는 포함)의 기본 포함 기능을 지원 합니다 `IOleClientSite` `IAdviseSink` .

- 포함 된 개체 또는 활성 문서의 내부 활성화를 지원 합니다. 컨테이너의 사이트 개체는를 구현 해야 `IOleInPlaceSite` 하며 컨테이너의 프레임 개체는를 제공 해야 합니다 `IOleInPlaceFrame` .

- `IOleDocumentSite`컨테이너에서 문서와 통신할 수 있는 메커니즘을 제공 하기 위해를 구현 하 여 활성 문서의 확장을 지원 합니다. 필요에 따라 컨테이너는 액티브 문서 인터페이스를 구현 하 `IOleCommandTarget` 고 `IContinueCallback` 인쇄 또는 저장 등의 간단한 명령을 선택할 수 있습니다.

`IOleCommandTarget` [명령 대상](message-handling-and-command-targets.md)에 설명 된 것 처럼 프레임 개체, 뷰 개체 및 컨테이너 개체가 선택적으로를 구현 하 여 특정 명령의 디스패치를 지원할 수 있습니다. 뷰 및 컨테이너 개체는 `IPrint` `IContinueCallback` [프로그래밍 방식 인쇄](programmatic-printing.md)에서 설명한 대로 프로그래밍 방식 인쇄를 지원 하기 위해 및를 선택적으로 구현할 수도 있습니다.

다음 그림에서는 컨테이너와 해당 구성 요소 (왼쪽) 및 활성 문서와 해당 보기 (오른쪽) 간의 개념적 관계를 보여 줍니다. 활성 문서는 저장소 및 데이터를 관리 하 고 보기는 해당 데이터를 표시 하거나 선택적으로 인쇄 합니다. 굵게 표시 된 인터페이스는 액티브 문서 참여에 필요한 인터페이스입니다. 이러한 굵게 및 기울임꼴 옵션은 선택 사항입니다. 다른 모든 인터페이스는 필수입니다.

![활성 문서 컨테이너 인터페이스](../mfc/media/vc37gj1.gif "활성 문서 컨테이너 인터페이스")

단일 보기만 지 원하는 문서에서는 단일 구체적 클래스에서 뷰와 문서 구성 요소 (즉, 해당 인터페이스)를 모두 구현할 수 있습니다. 또한 한 번에 하나의 보기만 지 원하는 컨테이너 사이트는 문서 사이트와 보기 사이트를 단일 구체적 사이트 클래스로 결합할 수 있습니다. 그러나 컨테이너의 frame 개체는 고유 하 게 유지 되어야 하며, 컨테이너의 문서 구성 요소가 여기에 포함 되어 아키텍처의 전체 그림을 제공 합니다. 활성 문서 포함 아키텍처의 영향을 받지 않습니다.

## <a name="document-site-objects"></a><a name="document_site_objects"></a> 문서 사이트 개체

액티브 문서 포함 아키텍처에서 문서 사이트는 인터페이스가 추가 된 OLE 문서의 클라이언트 사이트 개체와 동일 합니다 `IOleDocument` .

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

문서 사이트는 개념적으로 하나 이상의 "사이트 보기" 개체에 대 한 컨테이너입니다. 각 보기 사이트 개체는 문서 사이트에서 관리 하는 문서의 개별 뷰 개체와 연결 됩니다. 컨테이너가 문서 사이트별로 하나의 보기만 지 원하는 경우 문서 사이트와 뷰 사이트를 단일 구체적 클래스로 구현할 수 있습니다.

## <a name="view-site-objects"></a><a name="view_site_objects"></a> 사이트 개체 보기

컨테이너의 뷰 사이트 개체는 문서의 특정 보기에 대 한 표시 공간을 관리 합니다. 표준 인터페이스를 지 원하는 것 외에 `IOleInPlaceSite` 도 뷰 사이트는 일반적으로 `IContinueCallback` 프로그래밍 방식의 인쇄 컨트롤에 대해를 구현 합니다. (뷰 개체는에 대 한 쿼리를 하지 않으므로 `IContinueCallback` 컨테이너가 원하는 모든 개체에서 실제로 구현 될 수 있습니다.)

여러 뷰를 지 원하는 컨테이너는 문서 사이트 내에서 여러 뷰 사이트 개체를 만들 수 있어야 합니다. 이는를 통해 제공 되는 별도의 활성화 및 비활성화 서비스를 사용 하 여 각 뷰를 제공 `IOleInPlaceSite` 합니다.

## <a name="frame-object"></a><a name="frame_object"></a> Frame 개체

컨테이너의 frame 개체는 대부분 메뉴와 도구 모음 협상을 처리 하는 OLE 문서에서 내부 활성화에 사용 되는 프레임입니다. View 개체는을 통해이 프레임 개체에 액세스할 수 있습니다 .이 개체는 `IOleInPlaceSite::GetWindowContext` 컨테이너 문서를 나타내는 컨테이너 개체에 대 한 액세스도 제공 합니다 .이 개체는 창 수준 도구 모음 협상 및 포함 된 개체 열거를 처리할 수 있습니다.

액티브 문서 컨테이너는를 추가 하 여 프레임을 확대할 수 있습니다 `IOleCommandTarget` . 이 인터페이스를 사용 하면 컨테이너에서 동일한 명령 (예: **파일 새로 만들기**, **열기**, 다른 **이름으로 저장**, **인쇄** 등)을 보낼 수 있는 것과 같은 방식으로 활성 문서의 사용자 인터페이스에서 발생 하는 명령을 받을 수 있습니다. 활성 문서에 대 한 복사, **붙여넣기**, **실행 취소** 및 기타를 **편집** 합니다. 자세한 내용은 [명령 대상](message-handling-and-command-targets.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[액티브 문서 포함](active-document-containment.md)
