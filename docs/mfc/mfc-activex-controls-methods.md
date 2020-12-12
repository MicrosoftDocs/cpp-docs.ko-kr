---
description: '자세한 정보: MFC ActiveX 컨트롤: 메서드'
title: 'MFC ActiveX 컨트롤: 메서드'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 27e56653e8a3cf3ebd7ab182b633a1c3ba0b99b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97236934"
---
# <a name="mfc-activex-controls-methods"></a>MFC ActiveX 컨트롤: 메서드

ActiveX 컨트롤은 이벤트와 해당 컨트롤 컨테이너 간에 통신 하는 이벤트를 발생 시킵니다. 또한 컨테이너는 메서드와 속성을 사용 하 여 컨트롤과 통신할 수 있습니다. 메서드를 함수 라고도 합니다.

메서드 및 속성은 자동화 클라이언트 및 ActiveX 컨트롤 컨테이너와 같은 다른 응용 프로그램에서 사용할 내보낸 인터페이스를 제공 합니다. ActiveX 컨트롤 속성에 대 한 자세한 내용은 [MFC Activex 컨트롤: 속성](mfc-activex-controls-properties.md)문서를 참조 하세요.

메서드는 c + + 클래스의 멤버 함수를 사용 하 여 사용 하는 것과 비슷합니다. 컨트롤에서 구현 하는 메서드는 스톡 및 사용자 지정의 두 가지 유형이 있습니다. 스톡 이벤트와 마찬가지로, stock 메서드는 [COleControl](reference/colecontrol-class.md) 에서 구현을 제공 하는 메서드입니다. 스톡 메서드에 대 한 자세한 내용은 [MFC ActiveX 컨트롤: 스톡 메서드 추가](mfc-activex-controls-adding-stock-methods.md)문서를 참조 하세요. 개발자가 정의한 사용자 지정 메서드는 컨트롤의 추가 사용자 지정을 허용 합니다. 자세한 내용은 [MFC ActiveX 컨트롤: 사용자 지정 메서드 추가](mfc-activex-controls-adding-custom-methods.md)문서를 참조 하세요.

MFC 라이브러리 (MFC)는 컨트롤이 스톡 및 사용자 지정 메서드를 지원할 수 있도록 하는 메커니즘을 구현 합니다. 첫 번째 부분은 클래스 `COleControl` 입니다. 에서 파생 `CWnd` 된 `COleControl` 멤버 함수는 모든 ActiveX 컨트롤에 공통적인 스톡 메서드를 지원 합니다. 이 메커니즘의 두 번째 부분은 디스패치 맵입니다. 디스패치 맵은 메시지 맵과 유사 합니다. 그러나 Windows 메시지 ID에 함수를 매핑하는 대신 디스패치 맵은 가상 멤버 함수를 IDispatch ID에 매핑합니다.

컨트롤에서 다양 한 메서드를 제대로 지원 하려면 해당 클래스에서 디스패치 맵을 선언 해야 합니다. 이는 컨트롤 클래스 헤더 (에 있는 다음 코드 줄에 의해 수행 됩니다. H) 파일:

[!code-cpp[NVC_MFC_AxUI#13](codesnippet/cpp/mfc-activex-controls-methods_1.h)]

디스패치 맵의 주요 목적은 외부 호출자 (예: 컨테이너)에서 사용 하는 메서드 이름과 메서드를 구현 하는 컨트롤 클래스의 멤버 함수 간의 관계를 설정 하는 것입니다. 디스패치 맵이 선언 된 후에는 컨트롤의 구현 ()에서 정의 해야 합니다. CPP) 파일입니다. 다음 코드 줄은 디스패치 맵을 정의 합니다.

[!code-cpp[NVC_MFC_AxUI#14](codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

[MFC ActiveX 컨트롤 마법사](reference/mfc-activex-control-wizard.md) 를 사용 하 여 프로젝트를 만든 경우 이러한 줄은 자동으로 추가 됩니다. MFC ActiveX 컨트롤 마법사를 사용 하지 않은 경우에는 이러한 줄을 수동으로 추가 해야 합니다.

다음 문서에서는 메서드에 대해 자세히 설명 합니다.

- [MFC ActiveX 컨트롤: 스톡 메서드 추가](mfc-activex-controls-adding-stock-methods.md)

- [MFC ActiveX 컨트롤: 사용자 지정 메서드 추가](mfc-activex-controls-adding-custom-methods.md)

- [MFC ActiveX 컨트롤: 메서드에서 오류 코드 반환](mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>참고 항목

[MFC ActiveX 컨트롤](mfc-activex-controls.md)
