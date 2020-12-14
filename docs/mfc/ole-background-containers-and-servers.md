---
description: '자세한 정보: OLE 백그라운드: 컨테이너 및 서버'
title: 'OLE 백그라운드: 컨테이너 및 서버'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: 3ea578ce14165b16e84520b22bc545fc5d2a8882
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254779"
---
# <a name="ole-background-containers-and-servers"></a>OLE 백그라운드: 컨테이너 및 서버

컨테이너 응용 프로그램은 포함 된 항목 또는 연결 된 항목을 자체 문서에 통합할 수 있는 응용 프로그램입니다. 컨테이너 응용 프로그램에서 관리 하는 문서는 응용 프로그램 자체에서 만든 데이터 뿐만 아니라 OLE 문서 구성 요소를 저장 하 고 표시할 수 있어야 합니다. 또한 컨테이너 응용 프로그램은 사용자가 필요한 경우 서버 응용 프로그램을 활성화 하 여 새 항목을 삽입 하거나 기존 항목을 편집할 수 있도록 해야 합니다. 컨테이너 응용 프로그램의 사용자 인터페이스 요구 사항은 [컨테이너: User-Interface 문제](containers-user-interface-issues.md)문서에 나열 되어 있습니다.

서버 응용 프로그램 또는 구성 요소 응용 프로그램은 컨테이너 응용 프로그램에서 사용할 OLE 문서 구성 요소를 만들 수 있는 응용 프로그램입니다. 서버 응용 프로그램은 일반적으로 컨테이너 응용 프로그램이 데이터를 포함 된 항목 또는 연결 된 항목으로 삽입할 수 있도록 데이터를 클립보드에 끌어서 놓거나 복사 하거나 복사할 수 있도록 지원 합니다. 응용 프로그램은 컨테이너와 서버 모두 일 수 있습니다.

대부분의 서버는 독립 실행형 응용 프로그램 이거나 전체 서버입니다. 이러한 응용 프로그램은 독립 실행형 응용 프로그램으로 실행 되거나 컨테이너 응용 프로그램에서 시작할 수 있습니다. 미니 서버는 컨테이너 에서만 실행할 수 있는 특수 한 유형의 서버 응용 프로그램입니다. 독립 실행형 응용 프로그램으로 실행할 수 없습니다. Microsoft Draw 및 Microsoft Graph 서버는 미니 서버의 예입니다.

컨테이너 및 서버는 직접 통신 하지 않습니다. 대신 OLE 시스템 DLL (동적 연결 라이브러리)을 통해 통신 합니다. 이러한 Dll은 컨테이너와 서버에서 호출 하는 함수를 제공 하며 컨테이너와 서버는 Dll이 호출 하는 콜백 함수를 제공 합니다.

이러한 통신 수단을 사용 하면 컨테이너에서 서버 응용 프로그램의 구현 세부 정보를 알 필요가 없습니다. 이를 통해 컨테이너는 사용할 수 있는 서버 유형을 정의 하지 않고도 서버에서 만든 항목을 허용할 수 있습니다. 따라서 컨테이너 응용 프로그램의 사용자는 향후 응용 프로그램 및 데이터 형식을 활용할 수 있습니다. 이러한 새 응용 프로그램이 OLE 구성 요소인 경우 복합 문서는 해당 응용 프로그램에서 만든 항목을 통합할 수 있습니다.

## <a name="see-also"></a>참고 항목

[OLE 배경](ole-background.md)<br/>
[OLE 백그라운드: MFC 구현](ole-background-mfc-implementation.md)<br/>
[컨테이너](containers.md)<br/>
[서버](servers.md)<br/>
[컨테이너: 클라이언트 항목](containers-client-items.md)<br/>
[서버: 서버 항목](servers-server-items.md)
