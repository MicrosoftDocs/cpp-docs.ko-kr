---
description: '컨테이너: 고급 기능에 대 한 자세한 정보'
title: '컨테이너: 고급 기능'
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: d49f699ec0349e5c53b95996c6ee4b5d151dce5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310514"
---
# <a name="containers-advanced-features"></a>컨테이너: 고급 기능

이 문서에서는 기존 컨테이너 응용 프로그램에 선택적 고급 기능을 통합 하는 데 필요한 단계를 설명 합니다. 이러한 기능은 다음과 같습니다.

- [컨테이너 및 서버인 응용 프로그램](#_core_creating_a_container_server_application)

- [포함 된 개체에 대 한 OLE 링크](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a> 컨테이너/서버 응용 프로그램 만들기

컨테이너/서버 응용 프로그램은 컨테이너와 서버 역할을 모두 수행 하는 응용 프로그램입니다. 이에 대 한 예는 Windows 용 Microsoft Word입니다. 다른 응용 프로그램에 Windows 문서에 대 한 Word를 포함할 수 있으며 Windows 문서용 Word에 항목을 포함할 수도 있습니다. 컨테이너 응용 프로그램을 컨테이너 및 전체 서버 (조합 컨테이너/미니 서버 응용 프로그램을 만들 수 없음)로 수정 하는 프로세스는 전체 서버를 만드는 프로세스와 유사 합니다.

서버 [: 서버 구현](servers-implementing-a-server.md) 문서에는 서버 응용 프로그램을 구현 하는 데 필요한 많은 태스크가 나열 되어 있습니다. 컨테이너 응용 프로그램을 컨테이너/서버 응용 프로그램으로 변환 하는 경우 컨테이너에 코드를 추가 하 여 이와 동일한 작업을 수행 해야 합니다. 다음은 고려해 야 할 중요 사항 목록입니다.

- 응용 프로그램 마법사에서 만든 컨테이너 코드는 이미 OLE 하위 시스템을 초기화 합니다. 해당 지원에 대 한 모든 항목을 변경 하거나 추가할 필요는 없습니다.

- 문서 클래스의 기본 클래스가 어디에 있든 `COleDocument` 기본 클래스를로 변경 `COleServerDoc` 합니다.

- 서버 자체를 사용 하 여 현재 위치의 항목을 편집 하는 `COleClientItem::CanActivate` 것을 방지 하기 위해를 재정의 합니다.

   예를 들어, MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 에는 컨테이너/서버 응용 프로그램에서 만든 항목이 포함 되어 있습니다. OCLIENT 응용 프로그램을 열고 컨테이너/서버 응용 프로그램에서 만든 항목을 내부에서 편집 합니다. 응용 프로그램의 항목을 편집 하는 동안 MFC OLE 샘플 [HIERSVR](../overview/visual-cpp-samples.md)에서 만든 항목을 포함 하려는 경우를 결정 합니다. 이렇게 하려면 내부 활성화를 사용할 수 없습니다. 이 항목을 활성화 하려면 HIERSVR를 완전히 열어야 합니다. MFC 라이브러리는이 OLE 기능을 지원 하지 않으므로 재정의를 `COleClientItem::CanActivate` 사용 하 여 이러한 상황을 확인 하 고 응용 프로그램에서 런타임 오류를 방지할 수 있습니다.

새 응용 프로그램을 만들고 컨테이너/서버 응용 프로그램으로 작동 하 게 하려면 응용 프로그램 마법사의 OLE 옵션 대화 상자에서 해당 옵션을 선택 합니다. 그러면이 지원이 자동으로 생성 됩니다. 자세한 내용은 [개요: ActiveX 컨트롤 컨테이너 만들기](reference/creating-an-mfc-activex-control-container.md)문서를 참조 하세요. MFC 샘플에 대 한 자세한 내용은 [Mfc 샘플](../overview/visual-cpp-samples.md#mfc-samples)을 참조 하세요.

MDI 응용 프로그램은 자체에 삽입할 수 없습니다. 컨테이너/서버 응용 프로그램은 SDI 응용 프로그램이 아닌 경우 자체에 삽입할 수 없습니다.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a> 포함 된 개체에 대 한 링크

포함 된 개체에 대 한 링크 기능을 사용 하면 사용자가 컨테이너 응용 프로그램 내에 포함 된 개체에 대 한 OLE 링크를 사용 하 여 문서를 만들 수 있습니다. 예를 들어 포함 된 스프레드시트를 포함 하는 워드 프로세서에서 문서를 만듭니다. 응용 프로그램에서 포함 된 개체에 대 한 링크를 지 원하는 경우 워드 프로세서의 문서에 포함 된 스프레드시트에 링크를 붙여 넣을 수 있습니다. 이 기능을 사용 하면 응용 프로그램에서 word 프로세서의 원래 위치를 모르는 상태에서 스프레드시트에 포함 된 정보를 사용할 수 있습니다.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>응용 프로그램의 포함 된 개체에 연결 하려면

1. 대신에서 문서 클래스를 파생 시킵니다 `COleLinkingDoc` `COleDocument` .

1. OLE 개발 도구에 포함 된 클래스 ID 생성기를 사용 하 여 응용 프로그램에 대 한 OLE 클래스 ID (**CLSID**)를 만듭니다.

1. OLE에 응용 프로그램을 등록 합니다.

1. 개체를 `COleTemplateServer` 응용 프로그램 클래스의 멤버로 만듭니다.

1. 응용 프로그램 클래스의 `InitInstance` 멤버 함수에서 다음을 수행 합니다.

   - `COleTemplateServer`개체의 멤버 함수를 호출 하 여 개체를 문서 템플릿에 연결 `ConnectTemplate` 합니다.

   - `COleTemplateServer::RegisterAll`멤버 함수를 호출 하 여 OLE 시스템에 모든 클래스 개체를 등록 합니다.

   - `COleTemplateServer::UpdateRegistry`을 호출합니다. `UpdateRegistry`응용 프로그램이 "/포함" 스위치를 사용 하 여 시작 되지 않은 경우에만 매개 변수를 *OAT_CONTAINER* 해야 합니다. 이렇게 하면 포함 된 개체에 대 한 링크를 지원할 수 있는 컨테이너로 응용 프로그램이 등록 됩니다.

      응용 프로그램이 "/포함" 스위치를 사용 하 여 시작 되는 경우 서버 응용 프로그램과 유사한 주 창을 표시 해서는 안 됩니다.

MFC OLE 샘플 [OCLIENT](../overview/visual-cpp-samples.md) 는이 기능을 구현 합니다. 이 작업을 수행 하는 방법에 대 한 예제는 `InitInstance` OCLIENT에서 함수를 참조 하세요 *.* 이 샘플 응용 프로그램의 CPP 파일입니다.

## <a name="see-also"></a>참고 항목

[컨테이너](containers.md)<br/>
[서버](servers.md)
