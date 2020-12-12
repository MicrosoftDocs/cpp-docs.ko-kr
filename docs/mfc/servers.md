---
description: '서버에 대 한 자세한 정보: 서버'
title: 서버
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC]
- OLE server applications [MFC], activation
- full-server
- servers
- mini-server
- OLE server applications [MFC], server types
- server applications [MFC]
ms.assetid: e45172e8-eae3-400a-8139-0fa009a42fdc
ms.openlocfilehash: 5e9a9dd7cbb1ab237712b5ad0c84e3114a119ee3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97217304"
---
# <a name="servers"></a>서버

서버 응용 프로그램 (또는 구성 요소 응용 프로그램)은 컨테이너 응용 프로그램에서 사용할 OLE 항목 (또는 구성 요소)을 만듭니다. 시각적 편집 서버 응용 프로그램 에서도 시각적 편집 또는 내부 활성화를 지원 합니다. 다른 형태의 OLE 서버는 [자동화 서버](../mfc/automation-servers.md)입니다. 일부 서버 응용 프로그램은 포함 된 항목 만들기만 지원 합니다. 다른 사용자는 포함 된 항목과 연결 된 항목을 모두 만들 수 있습니다. 일부 경우에만 연결을 지원 합니다. 사용자가 항목을 편집 하려는 경우 모든 서버 응용 프로그램은 컨테이너 응용 프로그램에의 한 활성화를 지원 해야 합니다. 응용 프로그램은 컨테이너와 서버 모두 일 수 있습니다. 즉, 해당 문서에 데이터를 통합 하 고 다른 응용 프로그램의 문서에 항목으로 통합할 수 있는 데이터를 만들 수 있습니다.

미니 서버는 컨테이너 에서만 실행할 수 있는 특수 한 유형의 서버 응용 프로그램입니다. Microsoft Draw 및 Microsoft Graph은 미니 서버의 예입니다. 미니 파일은 문서를 디스크에 파일로 저장 하지 않습니다. 대신에서 해당 문서를 읽고 컨테이너에 속한 문서의 항목에 씁니다. 따라서 미니 미니는 연결을 지원 하지 않고 포함만 지원 합니다.

전체 서버는 독립 실행형 응용 프로그램으로 실행 하거나 컨테이너 응용 프로그램에서 시작할 수 있습니다. 전체 서버는 문서를 디스크에 파일로 저장할 수 있습니다. 포함 및 연결 또는 링크를 포함 하 여 포함만 지원할 수 있습니다. 컨테이너 응용 프로그램의 사용자는 서버에서 잘라내기 또는 복사 명령과 컨테이너의 붙여넣기 명령을 선택 하 여 포함 된 항목을 만들 수 있습니다. 연결 된 항목은 서버에서 복사 명령을 선택 하 고 컨테이너에서 링크 붙여넣기 명령을 선택 하 여 만듭니다. 또는 사용자가 개체 삽입 대화 상자를 사용 하 여 포함 되거나 연결 된 항목을 만들 수 있습니다.

다음 표에서는 다양 한 유형의 서버에 대 한 특성을 요약 합니다.

### <a name="server-characteristics"></a>서버 특징

|서버 유형|여러 인스턴스 지원|문서당 항목 수|인스턴스당 문서 수|
|--------------------|---------------------------------|------------------------|----------------------------|
|미니|예|1|1|
|SDI 전체 서버|예|1 (연결이 지원 되는 경우 1 개 이상)|1|
|MDI 전체 서버|아니요 (필수 아님)|1 (연결이 지원 되는 경우 1 개 이상)|0개 이상|

서버 응용 프로그램은 둘 이상의 컨테이너를 사용 하 여 포함 되거나 연결 된 항목을 편집 하는 경우 여러 컨테이너를 동시에 지원 해야 합니다. 서버가 SDI 응용 프로그램 (또는 대화 상자 인터페이스가 있는 미니 서버) 인 경우 서버 인스턴스를 여러 개 동시에 실행할 수 있어야 합니다. 이렇게 하면 응용 프로그램의 개별 인스턴스가 각 컨테이너 요청을 처리할 수 있습니다.

서버가 MDI 응용 프로그램 인 경우 컨테이너에서 항목을 편집 해야 할 때마다 새 MDI 자식 창을 만들 수 있습니다. 이러한 방식으로 응용 프로그램의 단일 인스턴스는 여러 컨테이너를 지원할 수 있습니다.

서버 응용 프로그램은 다른 컨테이너에서 서비스를 요청할 때 서버 인스턴스가 이미 실행 중인 경우 (서버의 새 인스턴스를 시작 하거나 모든 컨테이너의 요청을 서버 인스턴스로 보낼 때) 수행할 작업을 OLE 시스템 Dll에 알려야 합니다.

서버에 대 한 자세한 내용은 다음을 참조 하세요.

- [서버: 서버 구현](../mfc/servers-implementing-a-server.md)

- [서버: 서버 문서 구현](../mfc/servers-implementing-server-documents.md)

- [서버: In-Place 프레임 창 구현](../mfc/servers-implementing-in-place-frame-windows.md)

- [서버: 서버 항목](../mfc/servers-server-items.md)

- [서버: User-Interface 문제](../mfc/servers-user-interface-issues.md)

## <a name="see-also"></a>참고 항목

[OLE](../mfc/ole-in-mfc.md)<br/>
[컨테이너](../mfc/containers.md)<br/>
[컨테이너: 고급 기능](../mfc/containers-advanced-features.md)<br/>
[메뉴 및 리소스 (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[등록](../mfc/registration.md)<br/>
[자동화 서버](../mfc/automation-servers.md)
