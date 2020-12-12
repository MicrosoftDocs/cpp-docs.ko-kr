---
description: '자세히 알아보기: 컨테이너: 컨테이너 구현'
title: '컨테이너: 컨테이너 구현'
ms.date: 11/04/2016
helpviewer_keywords:
- applications [OLE], OLE container
- OLE containers [MFC], implementing
ms.assetid: af1e2079-619a-4eac-9327-985ad875823a
ms.openlocfilehash: 24e3c7f7d4546ebe9b103af0e9ca0d9694b25d2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310325"
---
# <a name="containers-implementing-a-container"></a>컨테이너: 컨테이너 구현

이 문서에서는 컨테이너를 구현 하는 절차를 요약 하 고 컨테이너 구현에 대 한 자세한 설명을 제공 하는 다른 문서를 가리킵니다. 또한 구현할 수 있는 몇 가지 선택적 OLE 기능과 이러한 기능을 설명 하는 문서를 나열 합니다.

#### <a name="to-prepare-your-cwinapp-derived-class"></a>CWinApp 파생 클래스를 준비 하려면

1. 멤버 함수에서를 호출 하 여 OLE 라이브러리를 초기화 `AfxOleInit` `InitInstance` 합니다.

1. 에서를 호출 `CDocTemplate::SetContainerInfo` `InitInstance` 하 여 포함 된 항목이 내부에서 활성화 될 때 사용 되는 메뉴 및 액셀러레이터 리소스를 할당 합니다. 이 항목에 대 한 자세한 내용은 [활성화](activation-cpp.md)를 참조 하십시오.

이러한 기능은 MFC 응용 프로그램 마법사를 사용 하 여 컨테이너 응용 프로그램을 만들 때 자동으로 제공 됩니다. [MFC EXE 프로그램 만들기](reference/mfc-application-wizard.md)를 참조 하세요.

#### <a name="to-prepare-your-view-class"></a>보기 클래스를 준비 하려면

1. 선택한 항목에 대 한 포인터 또는 여러 선택을 지 원하는 경우 포인터 목록을 유지 하 여 선택한 항목을 추적 합니다. `OnDraw`함수는 모든 OLE 항목을 그려야 합니다.

1. `IsSelected`전달 된 항목이 현재 선택 되어 있는지 여부를 확인 하려면를 재정의 합니다.

1. `OnInsertObject`메시지 처리기를 구현 하 여 **개체 삽입** 대화 상자를 표시 합니다.

1. `OnSetFocus`보기에서 내부 활성 OLE 포함 항목으로 포커스를 전송 하는 메시지 처리기를 구현 합니다.

1. 포함 하는 `OnSize` 뷰의 크기가 변경 되는 것을 반영 하도록 해당 사각형을 변경 해야 한다는 것을 OLE 포함 항목에 알리기 위해 메시지 처리기를 구현 합니다.

이러한 기능의 구현은 응용 프로그램 마다 크게 다르지만 응용 프로그램 마법사는 기본 구현만 제공 합니다. 응용 프로그램이 제대로 작동 하도록 하려면 이러한 함수를 사용자 지정 해야 할 가능성이 높습니다. 이에 대 한 예제는 [컨테이너](../overview/visual-cpp-samples.md) 샘플을 참조 하세요.

#### <a name="to-handle-embedded-and-linked-items"></a>포함 된 항목과 연결 된 항목을 처리 하려면

1. [COleClientItem](reference/coleclientitem-class.md)에서 클래스를 파생 시킵니다. 이 클래스의 개체는 OLE 문서에 포함 되거나 연결 된 항목을 나타냅니다.

1. `OnChange`, `OnChangeItemPosition` 및를 재정의 `OnGetItemPosition` 합니다. 이러한 함수는 포함 된 항목과 연결 된 항목의 크기 조정, 위치 지정 및 수정을 처리 합니다.

응용 프로그램 마법사는 클래스를 파생 하지만 `OnChange` 앞의 절차에서 2 단계에 나열 된 다른 함수 및를 재정의 해야 할 수 있습니다. 이러한 함수는 응용 프로그램 마다 다르게 구현 되기 때문에 대부분의 응용 프로그램에 대해 기본 구현을 사용자 지정 해야 합니다. 이에 대 한 예제는 MFC 샘플 [DRAWCLI](../overview/visual-cpp-samples.md) 및 [컨테이너](../overview/visual-cpp-samples.md)를 참조 하세요.

OLE를 지원 하려면 컨테이너 응용 프로그램의 메뉴 구조에 많은 항목을 추가 해야 합니다. 이러한 항목에 대 한 자세한 내용은 [메뉴 및 리소스: 컨테이너 추가](menus-and-resources-container-additions.md)를 참조 하세요.

컨테이너 응용 프로그램에서 다음 기능 중 일부를 지원할 수도 있습니다.

- 포함 된 항목을 편집할 때 내부 활성화

   자세한 내용은 [활성화](activation-cpp.md)를 참조 하십시오.

- 서버 응용 프로그램에서 선택 항목을 끌어서 놓는 방법으로 OLE 항목을 만듭니다.

   자세한 내용은 [OLE 끌어서 놓기](drag-and-drop-ole.md)를 참조 하세요.

- 포함 된 개체 또는 조합 컨테이너/서버 응용 프로그램에 대 한 링크입니다.

   자세한 내용은 [컨테이너: 고급 기능](containers-advanced-features.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[컨테이너](containers.md)<br/>
[컨테이너: 클라이언트 항목](containers-client-items.md)
