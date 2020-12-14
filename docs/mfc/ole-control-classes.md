---
description: '자세한 정보: OLE 컨트롤 클래스'
title: OLE 컨트롤 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- custom controls [MFC], classes
- ActiveX controls [MFC], OLE control classes
- ActiveX control classes [MFC]
- OLE controls [MFC], classes
- OLE control classes [MFC]
- reusable component classes [MFC]
ms.assetid: 96495ec3-319e-4163-b839-1af0428ed9dd
ms.openlocfilehash: da59fcd66fa21602ad864deecac9f568bd5123bc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244149"
---
# <a name="ole-control-classes"></a>OLE 컨트롤 클래스

이러한 클래스는 OLE 컨트롤을 작성할 때 사용 하는 기본 클래스입니다. `COleControlModule`OLE 컨트롤 모듈의 클래스는 응용 프로그램의 [CWinApp](reference/cwinapp-class.md) 클래스와 같습니다. 각 모듈은 하나 이상의 OLE 컨트롤을 구현 합니다. 이러한 컨트롤은 개체로 표시 됩니다 `COleControl` . 이러한 컨트롤은 개체를 사용 하 여 해당 컨테이너와 통신 `CConnectionPoint` 합니다.

및 클래스는 `CPictureHolder` `CFontHolder` 그림 및 글꼴에 대 한 COM 인터페이스를 캡슐화 하는 반면 `COlePropertyPage` 및 `CPropExchange` 클래스는 컨트롤에 대 한 속성 페이지와 속성 지 속성을 구현 하는 데 도움이 됩니다.

[COleControlModule](reference/colecontrolmodule-class.md)<br/>
`CWinApp`OLE 컨트롤 모듈의 클래스를 바꿉니다. 클래스에서 파생 `COleControlModule` 하 여 OLE 컨트롤 모듈 개체를 개발 합니다. OLE 컨트롤의 모듈을 초기화 하는 데 사용할 수 있는 멤버 함수를 제공 합니다.

[COleControl](reference/colecontrol-class.md)<br/>
클래스에서 파생 `COleControl` 하 여 OLE 컨트롤을 개발 합니다. 에서 파생 `CWnd` 되는이 클래스는 Windows 창 개체의 모든 기능과 이벤트 실행과 같은 추가 OLE 관련 기능 및 메서드 및 속성을 지 원하는 기능을 상속 합니다.

[CConnectionPoint](reference/cconnectionpoint-class.md)<br/>
`CConnectionPoint`클래스는 연결 지점 이라고 하는 다른 OLE 개체와 통신 하는 데 사용 되는 특별 한 형식의 인터페이스를 정의 합니다. 연결 지점은 이벤트 발생 및 변경 알림과 같은 다른 개체에 대 한 작업을 시작할 수 있는 송신 인터페이스를 구현 합니다.

[CPictureHolder](reference/cpictureholder-class.md)<br/>
Windows 그림 개체와 COM 인터페이스의 기능을 캡슐화 합니다. `IPicture` OLE 컨트롤의 사용자 지정 그림 속성을 구현 하는 데 사용 됩니다.

[CFontHolder](reference/cfontholder-class.md)<br/>
Windows 글꼴 개체와 COM 인터페이스의 기능을 캡슐화 합니다. `IFont` OLE 컨트롤의 스톡 글꼴 속성을 구현 하는 데 사용 됩니다.

[COlePropertyPage](reference/colepropertypage-class.md)<br/>
대화 상자와 유사한 그래픽 인터페이스의 OLE 컨트롤 속성을 표시 합니다.

[CPropExchange](reference/cpropexchange-class.md)<br/>
OLE 컨트롤에 대 한 속성 지 속성 구현을 지원 합니다. 대화 상자에 대 한 [CDataExchange](reference/cdataexchange-class.md) 와 유사 합니다.

[CMonikerFile](reference/cmonikerfile-class.md)<br/>
모니커 또는 모니커에 만들 수 있는 문자열 표현을 사용 하 여 모니커가 이름인 스트림에 동기적으로 바인딩합니다.

[CAsyncMonikerFile](reference/casyncmonikerfile-class.md)<br/>
는와 유사 하 게 작동 `CMonikerFile` 하지만 모니커가 이름인 스트림에 비동기적으로 모니커를 바인딩합니다.

[CDataPathProperty](reference/cdatapathproperty-class.md)<br/>
비동기적으로 로드할 수 있는 OLE 컨트롤 속성을 구현합니다.

[CCachedDataPathProperty](reference/ccacheddatapathproperty-class.md)<br/>
비동기적으로 전송되고 메모리 파일에 캐싱되는 OLE 컨트롤 속성을 구현합니다.

[COleCmdUI](reference/colecmdui-class.md)<br/>
활성 문서가 컨테이너의 사용자 인터페이스에서 시작 되는 명령 (예: FileNew, Open, Print 등)을 받아 컨테이너가 활성 문서의 사용자 인터페이스에서 발생 하는 명령을 받을 수 있도록 허용 합니다.

[COleSafeArray](reference/colesafearray-class.md)<br/>
임의의 형식 및 차원 배열에서 작동 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
