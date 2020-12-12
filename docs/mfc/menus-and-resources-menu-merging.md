---
description: '자세히 알아보기: 메뉴 및 리소스: 메뉴 병합'
title: '메뉴 및 리소스: 메뉴 병합'
ms.date: 11/04/2016
helpviewer_keywords:
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- coordinating menu layouts [MFC]
- OLE containers [MFC], menus and resources
- toolbars [MFC], OLE document applications
- merging toolbar and status bar [MFC]
- menus [MFC], OLE document applications
ms.assetid: 80b6bb17-d830-4122-83f0-651fc112d4d1
ms.openlocfilehash: b326e02fb4dbdaaef0ae6015fef6b647cc85b907
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227977"
---
# <a name="menus-and-resources-menu-merging"></a>메뉴 및 리소스: 메뉴 병합

이 문서에서는 OLE 문서 응용 프로그램에서 시각적 편집 및 내부 활성화를 제대로 처리 하는 데 필요한 단계를 자세히 설명 합니다. 내부 활성화는 컨테이너 및 서버 (구성 요소) 응용 프로그램 모두에 대 한 문제입니다. 사용자가 컨테이너 문서의 컨텍스트 내에서 동일한 프레임 창에 남아 있지만 실제로 다른 응용 프로그램 (서버)을 실행 하 고 있습니다. 이렇게 하려면 컨테이너와 서버 응용 프로그램의 리소스를 조정 해야 합니다.

이 문서에서 다루는 항목은 다음과 같습니다.

- [메뉴 레이아웃](#_core_menu_layouts)

- [도구 모음 및 상태 표시줄](#_core_toolbars_and_status_bars)

## <a name="menu-layouts"></a><a name="_core_menu_layouts"></a> 메뉴 레이아웃

첫 번째 단계는 메뉴 레이아웃을 조정 하는 것입니다. 컨테이너 응용 프로그램은 포함 된 항목이 현재 활성화 된 경우에만 사용할 새 메뉴를 만들어야 합니다. 최소한이 메뉴는 다음 순서로 나열 됩니다.

1. 파일이 열려 있을 때 사용 되는 것과 동일한 파일 메뉴입니다. (일반적으로 다음 항목 앞에 다른 메뉴 항목이 배치 되지 않습니다.)

1. 연속 된 두 개의 구분 기호입니다.

1. 창 메뉴는 파일이 열려 있을 때 사용 되는 것과 동일 합니다 (MDI 응용 프로그램의 컨테이너 응용 프로그램이 있는 경우에만 해당). 일부 응용 프로그램에는이 그룹에 속하는 옵션 메뉴와 같은 다른 메뉴가 있을 수 있습니다 .이 메뉴는 포함 된 항목이 활성화 될 때 메뉴에 남아 있습니다.

    > [!NOTE]
    >  확대/축소와 같은 컨테이너 문서의 보기에 영향을 주는 다른 메뉴가 있을 수 있습니다. 이러한 컨테이너 메뉴는이 메뉴 리소스의 두 구분 기호 사이에 표시 됩니다.

서버 (구성 요소) 응용 프로그램 에서도 내부 활성화를 위한 새 메뉴를 만들어야 합니다. 파일이 열려 있을 때 사용 되는 메뉴와 동일 하지만, 데이터 대신 서버 문서를 조작 하는 파일 및 창과 같은 메뉴 항목이 없으면 사용 됩니다. 일반적으로이 메뉴는 다음으로 구성 됩니다.

1. 파일이 열려 있을 때 사용 되는 것과 동일한 편집 메뉴입니다.

1. 구분선입니다.

1. Scribble 샘플 응용 프로그램의 펜 메뉴와 같은 개체 편집 메뉴

1. 구분선입니다.

1. 도움말 메뉴.

예를 들어 컨테이너 및 서버에 대 한 몇 가지 샘플 내부 메뉴의 레이아웃을 확인 합니다. 예제를 보다 명확 하 게 하기 위해 각 메뉴 항목의 세부 정보가 제거 되었습니다. 컨테이너의 내부 메뉴에는 다음과 같은 항목이 있습니다.

```
IDR_CONTAINERTYPE_CNTR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&File C1"
    MENUITEM SEPARATOR
    POPUP "&Zoom C2"
    MENUITEM SEPARATOR
    POPUP "&Options C3"
    POPUP "&Window C3"
END
```

연속 된 구분 기호는 서버 메뉴의 첫 번째 부분이 이동 해야 하는 위치를 표시 합니다. 이제 서버의 바로 메뉴를 살펴보겠습니다.

```
IDR_SERVERTYPE_SRVR_IP MENU PRELOAD DISCARDABLE
BEGIN
    POPUP "&Edit S1"
    MENUITEM SEPARATOR
    POPUP "&Format S2"
    MENUITEM SEPARATOR
    POPUP "&Help S3"
END
```

여기에 표시 된 구분 기호는 컨테이너 메뉴 항목의 두 번째 그룹을 이동할 위치를 표시 합니다. 이 컨테이너 내에서이 서버의 개체가 활성화 되는 경우 결과 메뉴 구조는 다음과 같습니다.

```
BEGIN
    POPUP "&File C1"
    POPUP "&Edit S1"
    POPUP "&Zoom C2"
    POPUP "&Format S2"
    POPUP "&Options C3
    POPUP "&Window C3"
    POPUP "&Help S3"
END
```

여기서 볼 수 있듯이 구분 기호는 각 응용 프로그램 메뉴의 여러 그룹으로 대체 되었습니다.

내부 메뉴와 연결 된 액셀러레이터 키 테이블은 서버 응용 프로그램 에서도 제공 되어야 합니다. 컨테이너는 자체 액셀러레이터 키 테이블에 통합 됩니다.

포함 된 항목이 활성화 되 면 프레임 워크에서 내부 메뉴를 로드 합니다. 그런 다음 서버 응용 프로그램에서 해당 메뉴에 대 한 내부 활성화를 요청 하 고 구분 기호를 삽입 합니다. 메뉴를 결합 하는 방법입니다. 컨테이너의 메뉴에서 파일 및 창 배치 작업을 시작 하 고, 해당 항목에 대해 작동 하는 메뉴를 서버에서 가져올 수 있습니다.

## <a name="toolbars-and-status-bars"></a><a name="_core_toolbars_and_status_bars"></a> 도구 모음 및 상태 표시줄

서버 응용 프로그램은 새 도구 모음을 만들고 비트맵을 별도 파일에 저장 해야 합니다. 응용 프로그램 마법사에서 생성 된 응용 프로그램은이 비트맵을 ITOOLBAR.BMP 이라는 파일에 저장 합니다. 새 도구 모음은 서버 항목이 현재 활성화 되어 있을 때 컨테이너 응용 프로그램의 도구 모음을 대체 하며, 일반 도구 모음과 동일한 항목을 포함 해야 하지만 파일 및 창 메뉴에서 항목을 나타내는 아이콘은 제거 합니다.

이 도구 모음은 파생 클래스에서 로드 되며 `COleIPFrameWnd` 응용 프로그램 마법사에서 생성 됩니다. 상태 표시줄은 컨테이너 응용 프로그램에 의해 처리 됩니다. 내부 프레임 창의 구현에 대 한 자세한 내용은 서버 [: 서버 구현](servers-implementing-a-server.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[메뉴 및 리소스 (OLE)](menus-and-resources-ole.md)<br/>
[활성화](activation-cpp.md)<br/>
[서버](servers.md)<br/>
[컨테이너](containers.md)
