---
description: '자세히 알아보기: 활성화 (c + +)'
title: 활성화(C++)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], activation
- OLE items [MFC], visual editing
- activation [MFC]
- OLE [MFC], in-place activation
- OLE [MFC], activation
- in-place activation, embedded and linked items
- activating objects
- visual editing, activation
- visual editing
- documents [MFC], OLE
- embedded objects [MFC]
- OLE [MFC], editing
- in-place activation
- activation [MFC], embedded OLE items
- OLE activation [MFC]
ms.assetid: ed8357d9-e487-4aaa-aa6b-2edc4de25dfa
ms.openlocfilehash: 726c64344f684c8ca9e79d9296daea80882af08f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197726"
---
# <a name="activation-c"></a>활성화(C++)

이 문서에서는 OLE 항목을 시각적으로 편집할 때 활성화의 역할을 설명 합니다. 사용자가 컨테이너 문서에 OLE 항목을 포함 한 후에는 해당 항목을 사용 해야 할 수 있습니다. 이렇게 하려면 사용자가 항목을 두 번 클릭 하면 해당 항목이 활성화 됩니다. 활성화에 대해 가장 자주 수행 하는 작업은 편집입니다. 편집을 위해 활성화 된 현재 OLE 항목은 대부분 현재 프레임 창의 메뉴 및 도구 모음이 항목을 만든 서버 응용 프로그램에 속하는 항목을 반영 하도록 변경 됩니다. 내부 활성화 라고 하는이 동작을 통해 사용자는 컨테이너 문서의 창을 벗어나지 않고 복합 문서의 포함 된 항목을 편집할 수 있습니다.

별도의 창에서 포함 된 OLE 항목을 편집할 수도 있습니다. 이는 컨테이너 또는 서버 응용 프로그램에서 내부 활성화를 지원 하지 않는 경우에 발생 합니다. 이 경우 사용자가 포함 된 항목을 두 번 클릭 하면 서버 응용 프로그램이 별도의 창에서 시작 되 고 포함 된 항목이 자체 문서로 표시 됩니다. 사용자가이 창의 항목을 편집 합니다. 편집이 완료 되 면 사용자가 서버 응용 프로그램을 닫고 컨테이너 응용 프로그램으로 돌아갑니다.

사용자가 **편집** 메뉴에서 **\<object> 열기** 명령을 사용 하 여 "편집 열기"를 선택할 수도 있습니다. 이렇게 하면 개체가 별도의 창에서 열립니다.

> [!NOTE]
> 별도의 창에 포함 된 항목을 편집 하는 것은 OLE 버전 1에서 표준 동작 이었습니다. 일부 OLE 응용 프로그램은이 스타일의 편집만 지원할 수 있습니다.

내부 활성화를 사용 하면 문서 중심의 문서 생성 방식을 높일 수 있습니다. 사용자는 응용 프로그램 간에 전환 하지 않고 복합 문서를 단일 엔터티로 취급할 수 있습니다. 그러나 내부 활성화는 링크 된 항목이 아닌 포함 된 항목에만 사용 됩니다. 별도의 창에서 편집 해야 합니다. 이는 연결 된 항목이 실제로 다른 장소에 저장 되기 때문입니다. 연결 된 항목의 편집은 데이터의 실제 컨텍스트, 즉 데이터가 저장 되는 위치에서 수행 됩니다. 별도의 창에서 연결 된 항목을 편집 하면 데이터가 다른 문서에 속하는지 사용자에 게 알려 줍니다.

MFC에서는 중첩 된 내부 활성화를 지원 하지 않습니다. 컨테이너/서버 응용 프로그램을 빌드하는 경우 컨테이너/서버가 다른 컨테이너에 포함 되 고 내부 활성화 된 경우 내부 활성화 개체가 내부에 포함 될 수 없습니다.

사용자가 두 번 클릭할 때 포함 된 항목은 항목에 대해 정의 된 동사에 따라 달라 집니다. 자세한 내용은 [활성화: 동사](activation-verbs.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE](ole-in-mfc.md)<br/>
[컨테이너](containers.md)<br/>
[서버](servers.md)
