---
description: '자세히 알아보기: 등록'
title: 등록
ms.date: 11/04/2016
helpviewer_keywords:
- servers [MFC], initializing
- initializing servers [MFC]
- OLE, registration
- installing servers [MFC]
- registry [MFC], OLE item database
- registration databases [MFC]
- servers [MFC], installing
- OLE server applications [MFC], registering servers
ms.assetid: 991d5684-72c1-4f9e-a09a-9184ed12bbb9
ms.openlocfilehash: 8254f4b1ab8a005623650794adc8be0bd06cfdff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218123"
---
# <a name="registration"></a>등록

사용자가 OLE 항목을 응용 프로그램에 삽입 하려고 하면 OLE에서 선택할 개체 유형 목록을 표시 합니다. OLE는 모든 서버 응용 프로그램에서 제공 하는 정보를 포함 하는 시스템 등록 데이터베이스에서이 목록을 가져옵니다. 서버 자체를 등록 하면 시스템 등록 데이터베이스 (레지스트리)에 배치 하는 항목에 의해 제공 되는 각 개체 유형, 파일 확장명 및 기타 정보 중에 해당 하는 경로가 설명 됩니다.

프레임 워크와 OLE 시스템 DLL (동적 연결 라이브러리)은이 레지스트리를 사용 하 여 시스템에서 사용할 수 있는 OLE 항목의 유형을 결정 합니다. 또한 OLE 시스템 Dll은이 레지스트리를 사용 하 여 연결 된 개체 또는 포함 된 개체가 활성화 될 때 서버 응용 프로그램을 시작 하는 방법을 결정 합니다.

이 문서에서는 각 서버 응용 프로그램이 설치 될 때와 실행 될 때마다 수행 해야 하는 작업을 설명 합니다.

시스템 등록 데이터베이스와 해당 데이터베이스를 업데이트 하는 데 사용 되는 .reg 파일의 형식에 대 한 자세한 내용은 *OLE 프로그래머 참조* 를 참조 하십시오.

## <a name="server-installation"></a><a name="_core_server_installation"></a> 서버 설치

서버 응용 프로그램을 처음 설치 하는 경우 지원 되는 모든 유형의 OLE 항목을 등록 해야 합니다. 서버에서 독립 실행형 응용 프로그램으로 실행 될 때마다 시스템 등록 데이터베이스를 업데이트 하도록 할 수도 있습니다. 이렇게 하면 서버의 실행 파일을 이동 하는 경우 등록 데이터베이스가 최신 상태로 유지 됩니다.

> [!NOTE]
> 응용 프로그램 마법사에서 생성 된 MFC 응용 프로그램은 독립 실행형 응용 프로그램으로 실행 될 때 자동으로 등록 됩니다.

설치 하는 동안 응용 프로그램을 등록 하려면 RegEdit.exe 프로그램을 사용 합니다. 응용 프로그램에 설치 프로그램을 포함 하는 경우 설치 프로그램에서 "RegEdit/S *appname*.reg"을 실행 하도록 합니다. (/S 플래그는 자동 작업을 나타냅니다. 즉, 명령이 성공적으로 완료 되었음을 보고 하는 대화 상자를 표시 하지 않습니다.) 그렇지 않으면 사용자에 게 RegEdit를 수동으로 실행 하도록 지시 합니다.

> [!NOTE]
> 응용 프로그램 마법사에서 생성 된 .reg 파일에는 실행 파일의 전체 경로가 포함 되지 않습니다. 설치 프로그램은 실행 파일의 전체 경로를 포함 하도록 .reg 파일을 수정 하거나 설치 디렉터리를 포함 하도록 PATH 환경 변수를 수정 해야 합니다.

RegEdit는 .reg 텍스트 파일의 내용을 등록 데이터베이스에 병합 합니다. 데이터베이스를 확인 하거나 복구 하려면 레지스트리 편집기를 사용 합니다. 필수 OLE 항목은 삭제 하지 않도록 주의 해야 합니다.

## <a name="server-initialization"></a><a name="_core_server_initialization"></a> 서버 초기화

응용 프로그램 마법사를 사용 하 여 서버 응용 프로그램을 만들면 마법사에서 자동으로 모든 초기화 태스크를 완료 합니다. 이 섹션에서는 서버 응용 프로그램을 수동으로 작성 하는 경우 수행 해야 하는 작업에 대해 설명 합니다.

컨테이너 응용 프로그램에서 서버 응용 프로그램을 시작 하는 경우 OLE 시스템 Dll은 서버 명령줄에 "프로그램이/embedding" 옵션을 추가 합니다. 서버 응용 프로그램의 동작은 컨테이너에 의해 시작 되었는지 여부에 따라 달라 지지만 응용 프로그램이 실행을 시작할 때 첫 번째로 수행 해야 하는 작업은 명령줄에서 "프로그램이/embedding" 또는 "-포함" 옵션을 확인 하는 것입니다. 이 스위치가 있으면 서버를 전체 활성 또는 전체 열기 중 하나로 표시 하는 다른 리소스 집합을 로드 합니다. 자세한 내용은 [메뉴 및 리소스: 서버 추가](../mfc/menus-and-resources-server-additions.md)를 참조 하세요.

서버 응용 프로그램은 또한 명령줄을 `CWinApp::RunEmbedded` 구문 분석 하는 함수를 호출 해야 합니다. 0이 아닌 값을 반환 하는 경우 응용 프로그램은 독립 실행형 응용 프로그램이 아니라 컨테이너 응용 프로그램에서 실행 되었으므로 해당 창을 표시 해서는 안 됩니다. 이 함수는 시스템 등록 데이터베이스에서 서버 항목을 업데이트 하 고 멤버 함수를 호출 하 여 `RegisterAll` 인스턴스 등록을 수행 합니다.

서버 응용 프로그램을 시작 하는 경우 인스턴스 등록을 수행할 수 있는지 확인 해야 합니다. 인스턴스 등록은 서버가 활성 상태이 고 컨테이너에서 요청을 받을 준비가 되었음을 OLE 시스템 Dll에 알립니다. 등록 데이터베이스에 항목을 추가 하지 않습니다. 로 정의 된 멤버 함수를 호출 하 여 서버의 인스턴스 등록을 수행 `ConnectTemplate` `COleTemplateServer` 합니다. 개체를 `CDocTemplate` 개체에 연결 `COleTemplateServer` 합니다.

`ConnectTemplate`함수는 세 개의 매개 변수, 즉 서버의 *CLSID*, 개체에 대 한 포인터 `CDocTemplate` 및 서버에서 여러 인스턴스를 지원 하는지 여부를 나타내는 플래그를 사용 합니다. 미니 서버는 여러 인스턴스를 지원할 수 있어야 합니다. 즉, 각 컨테이너에 대해 하나씩, 여러 서버 인스턴스가 동시에 실행 될 수 있어야 합니다. 따라서 미니 미니를 시작할 때이 플래그에 대해 **TRUE** 를 전달 합니다.

미니 파일을 작성 하는 경우 정의는 항상 컨테이너에 의해 시작 됩니다. "프로그램이/embedding" 옵션을 확인 하려면 여전히 명령줄을 구문 분석 해야 합니다. 명령줄에이 옵션을 사용 하지 않으면 사용자가 미니 사용자를 독립 실행형 응용 프로그램으로 시작 하는 것을 의미 합니다. 이 문제가 발생 하면 시스템 등록 데이터베이스에 서버를 등록 한 다음 컨테이너 응용 프로그램에서 미니 서버를 시작 하는 메시지 상자를 표시 합니다.

## <a name="see-also"></a>참고 항목

[OLE](../mfc/ole-in-mfc.md)<br/>
[서버](../mfc/servers.md)<br/>
[CWinApp:: RunAutomated](../mfc/reference/cwinapp-class.md#runautomated)<br/>
[CWinApp:: RunEmbedded](../mfc/reference/cwinapp-class.md#runembedded)<br/>
[COleTemplateServer 클래스](../mfc/reference/coletemplateserver-class.md)
