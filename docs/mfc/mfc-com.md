---
description: '자세한 정보: MFC COM'
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: a7f4387aa692eb0610052f85870127ac54761437
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97280666"
---
# <a name="mfc-com"></a>MFC COM

MFC의 하위 집합은 COM을 지원 하도록 디자인 되었지만 대부분의 ATL (액티브 템플릿 라이브러리)은 COM 프로그래밍을 위해 설계 되었습니다. 항목의이 섹션에서는 MFC의 COM 지원에 대해 설명 합니다.

액티브 기술 (예: ActiveX 컨트롤, 액티브 문서 포함, OLE 등)은 COM (구성 요소 개체 모델)을 사용 하 여 소프트웨어 구성 요소가 생성 된 언어에 관계 없이 네트워크 환경에서 서로 상호 작용할 수 있도록 합니다. 액티브 기술은 데스크톱 또는 인터넷에서 실행 되는 응용 프로그램을 만드는 데 사용할 수 있습니다. 자세한 내용은 [COM 소개](../atl/introduction-to-com.md) 또는 [구성 요소 개체 모델](/windows/win32/com/the-component-object-model)을 참조 하세요.

활성 기술에는 다음을 포함 하 여 클라이언트 및 서버 기술이 모두 포함 됩니다.

- ActiveX 컨트롤은 웹 사이트와 같은 컨테이너에서 사용할 수 있는 대화형 개체입니다. ActiveX 컨트롤에 대 한 자세한 내용은 다음을 참조 하세요.

  - [MFC ActiveX 컨트롤](mfc-activex-controls.md)

  - [인터넷의 ActiveX 컨트롤](activex-controls-on-the-internet.md)

  - [개요: 인터넷](mfc-internet-programming-basics.md)

  - [인터넷에서 사용할 기존 ActiveX 컨트롤 업그레이드](upgrading-an-existing-activex-control.md)

  - [ActiveX 컨트롤 디버깅](/visualstudio/debugger/how-to-debug-an-activex-control)

- 액티브 스크립팅은 브라우저나 서버에서 하나 이상의 ActiveX 컨트롤에 대 한 통합 동작을 제어 합니다. 액티브 스크립팅에 대 한 자세한 내용은 [인터넷의 활성 기술](active-technology-on-the-internet.md)(영문)을 참조 하십시오.

- [자동화](automation.md) (이전의 OLE 자동화)를 사용 하면 한 응용 프로그램에서 다른 응용 프로그램에 구현 된 개체를 조작 하거나 개체를 조작할 수 있도록 "노출" 할 수 있습니다.

   자동 개체는 로컬 또는 원격 (네트워크를 통해 액세스할 수 있는 다른 컴퓨터) 일 수 있습니다. 자동화는 OLE 및 COM 개체 모두에 대해 사용할 수 있습니다.

- 이 단원에서는 예를 들어 [연결 점에서](connection-points.md)MFC를 사용 하 여 COM 구성 요소를 작성 하는 방법에 대해서도 설명 합니다.

여전히 OLE (현재 활성화 된 기술)와 호출 되는 항목에 대 한 자세한 내용은 [ole](ole-in-mfc.md)의 항목을 참조 하십시오.

## <a name="in-this-section"></a>섹션 내용

[액티브 문서 포함](active-document-containment.md)

[Automation](automation.md)

[연결 요소](connection-points.md)

[MFC ActiveX 컨트롤](mfc-activex-controls.md)

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)
