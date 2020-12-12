---
description: '자세한 정보: ActiveX 컨트롤을 만드는 작업 시퀀스'
title: ActiveX 컨트롤을 만드는 작업 시퀀스
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], creating
- ActiveX controls [MFC], creating
- sequence [MFC], for creating ActiveX controls
- OLE controls [MFC], MFC
- sequence [MFC]
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
ms.openlocfilehash: 15b81716f5feee4dfd4d0ebf47ee4d0d648c4536
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217630"
---
# <a name="sequence-of-operations-for-creating-activex-controls"></a>ActiveX 컨트롤을 만드는 작업 시퀀스

다음 표에서는 ActiveX 컨트롤 (이전의 OLE 컨트롤 이라고 함)을 만들 때의 역할 및 프레임 워크의 역할을 보여 줍니다.

### <a name="creating-activex-controls"></a>ActiveX 컨트롤 만들기

|작업|너 해|프레임 워크는|
|----------|------------|------------------------|
|ActiveX 컨트롤 프레임 워크를 만듭니다.|MFC ActiveX 컨트롤 마법사를 실행 하 여 컨트롤을 만듭니다. 옵션 페이지에서 원하는 옵션을 지정 합니다. 옵션에는 프로젝트의 컨트롤 형식 및 이름, 라이선스, 서브클래싱 및 정보 상자 메서드가 포함 됩니다.|MFC ActiveX 컨트롤 마법사는 응용 프로그램, 컨트롤 및 속성 페이지에 대 한 소스 파일을 포함 하 여 기본 기능을 사용 하 여 ActiveX 컨트롤에 대 한 파일을 만듭니다. 리소스 파일입니다. 프로젝트 파일 그리고 다른 사용자가 사양에 맞게 조정 되었습니다.|
|사용자 고유의 코드 줄을 추가 하지 않고도 컨트롤 및 ActiveX 컨트롤 마법사에서 제공 하는 기능을 확인 합니다.|ActiveX 컨트롤을 빌드하고 Internet Explorer 또는 [TSTCON 샘플](../overview/visual-cpp-samples.md)을 사용 하 여 테스트 합니다.|실행 중인 컨트롤의 크기를 조정 하 고 이동할 수 있습니다. 호출할 수 있는 **About Box** 메서드 (선택 된 경우)도 있습니다.|
|컨트롤의 메서드 및 속성을 구현 합니다.|컨트롤의 데이터에 노출 된 인터페이스를 제공 하는 멤버 함수를 추가 하 여 컨트롤별 메서드 및 속성을 구현 합니다. 멤버 변수를 추가 하 여 데이터 구조를 유지 하 고, 이벤트 처리기를 사용 하 여를 결정할 때 이벤트를 발생 시킵니다.|프레임 워크에서 컨트롤의 이벤트, 속성 및 메서드를 지원 하기 위해 맵을 이미 정의 했으므로 속성 및 메서드를 구현 하는 방법에 중점을 둘 수 있습니다. 기본 속성 페이지를 볼 수 있으며 기본 정보 Box 메서드가 제공 됩니다.|
|컨트롤의 속성 페이지를 생성 합니다.|Visual C++ 리소스 편집기를 사용 하 여 컨트롤의 속성 페이지 인터페이스를 시각적으로 편집 합니다.<br /><br />-추가 속성 페이지를 만듭니다.<br />-비트맵, 아이콘 및 커서를 만들고 편집 합니다.<br /><br /> 대화 상자 편집기에서 속성 페이지를 테스트할 수도 있습니다.|MFC 응용 프로그램 마법사에서 만든 기본 리소스 파일은 필요한 많은 리소스를 제공 합니다. Visual C++를 사용 하 여 기존 리소스를 편집 하 고 쉽고 시각적으로 새 리소스를 추가할 수 있습니다.|
|컨트롤의 이벤트, 메서드 및 속성을 테스트 합니다.|컨트롤을 다시 빌드하고 테스트 컨테이너를 사용 하 여 처리기가 제대로 작동 하는지 테스트 합니다.|컨트롤의 메서드를 호출 하 고 속성 페이지 인터페이스 또는 테스트 컨테이너를 통해 해당 속성을 조작할 수 있습니다. 또한 테스트 컨테이너를 사용 하 여 컨트롤에서 발생 한 이벤트 및 컨트롤의 컨테이너에서 받은 알림을 추적 합니다.|

## <a name="see-also"></a>참고 항목

[프레임 워크를 기반으로 빌드](../mfc/building-on-the-framework.md)<br/>
[MFC 응용 프로그램을 빌드하기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-building-mfc-applications.md)<br/>
[OLE 응용 프로그램을 만들기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-creating-ole-applications.md)<br/>
[데이터베이스 응용 프로그램을 만들기 위한 작업 시퀀스](../mfc/sequence-of-operations-for-creating-database-applications.md)
