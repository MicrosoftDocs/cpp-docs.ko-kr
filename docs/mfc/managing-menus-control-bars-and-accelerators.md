---
description: '자세히 알아보기: 메뉴, 컨트롤 막대 및 액셀러레이터 관리'
title: 메뉴, 컨트롤 막대 및 액셀러레이터 관리
ms.date: 11/04/2016
helpviewer_keywords:
- MDI [MFC], frame windows
- control bars [MFC], updating in frame windows
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- accelerator tables [MFC]
- sharing menus [MFC]
- updating user-interface objects [MFC]
- frame windows [MFC], updating
- status bars [MFC], updating
ms.assetid: 97ca1997-06df-4373-b023-4f7ecd81047b
ms.openlocfilehash: 21c3791bff00c33db50efbe391863169606fde80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244175"
---
# <a name="managing-menus-control-bars-and-accelerators"></a>메뉴, 컨트롤 막대 및 액셀러레이터 관리

프레임 창에서는 메뉴, 도구 모음 단추, 상태 표시줄 및 액셀러레이터 키를 비롯 한 사용자 인터페이스 개체의 업데이트를 관리 합니다. 또한 MDI 응용 프로그램에서 메뉴 모음의 공유를 관리 합니다.

## <a name="managing-menus"></a>메뉴 관리

프레임 창은 [User-Interface 개체를 업데이트 하는 방법](how-to-update-user-interface-objects.md)에 설명 된 ON_UPDATE_COMMAND_UI 메커니즘을 사용 하 여 사용자 인터페이스 항목 업데이트에 참여 합니다. 도구 모음 및 기타 컨트롤 막대의 단추는 유휴 루프 중에 업데이트 됩니다. 메뉴 모음의 드롭다운 메뉴에 있는 메뉴 항목은 메뉴가 축소 되기 직전에 업데이트 됩니다.

MDI 응용 프로그램의 경우 MDI 프레임 창은 메뉴 모음과 캡션을 관리 합니다. MDI 프레임 창은 활성 MDI 자식 창이 없는 경우 메뉴 모음으로 사용 되는 기본 메뉴를 하나 소유 합니다. 활성 자식이 있으면 MDI 프레임 창의 메뉴 모음이 활성 MDI 자식 창에 대 한 메뉴에 표시 됩니다. MDI 응용 프로그램에서 차트 및 워크시트 문서와 같은 여러 문서 유형을 지 원하는 경우 각 유형은 메뉴 모음에 자체 메뉴를 배치 하 고 주 프레임 창의 캡션을 변경 합니다.

[CMDIFrameWnd](reference/cmdiframewnd-class.md) 는 MDI 응용 프로그램에 대해 표시 되는 창 메뉴의 표준 명령에 대 한 기본 구현을 제공 합니다. 특히 새 창 명령 (ID_WINDOW_NEW)은 새 프레임 창 및 현재 문서에 대 한 뷰를 만들기 위해 구현 됩니다. 고급 사용자 지정이 필요한 경우에만 이러한 구현을 재정의 해야 합니다.

동일한 문서 형식의 여러 MDI 자식 창은 메뉴 리소스를 공유 합니다. 여러 MDI 자식 창이 동일한 문서 템플릿에서 만들어지는 경우 모두 동일한 메뉴 리소스를 사용 하 여 Windows의 시스템 리소스에 저장할 수 있습니다.

## <a name="managing-the-status-bar"></a>상태 표시줄 관리

또한 프레임 창에는 상태 표시줄이 클라이언트 영역에 배치 되 고 상태 표시줄의 표시기가 관리 됩니다. [상태 표시줄에 명령 정보를 표시 하는 방법](how-to-display-command-information-in-the-status-bar.md)에 설명 된 대로 프레임 창은 필요에 따라 상태 표시줄의 메시지 영역을 지우고 업데이트 하 고 사용자가 메뉴 항목 또는 도구 모음 단추를 선택할 때 프롬프트 문자열을 표시 합니다.

## <a name="managing-accelerators"></a>가속기 관리

각 프레임 창은 자동으로 키보드 액셀러레이터를 변환 하는 선택적 액셀러레이터 키 테이블을 유지 합니다. 이 메커니즘을 사용 하면 메뉴 명령을 호출 하는 액셀러레이터 키 (바로 가기 키 라고도 함)를 쉽게 정의할 수 있습니다.

## <a name="see-also"></a>참고 항목

[프레임 창 사용](using-frame-windows.md)
