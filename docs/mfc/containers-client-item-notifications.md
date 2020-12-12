---
description: '다음에 대 한 자세한 정보: 컨테이너: Client-Item 알림'
title: '컨테이너: 클라이언트 항목 알림'
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], container client item
- OLE containers [MFC], client-item notifications
- client items and OLE containers
ms.assetid: e1f1c427-01f5-45f2-b496-c5bce3d76340
ms.openlocfilehash: 2918ea29bcd656e76735db8e003d33dce21c6b63
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310475"
---
# <a name="containers-client-item-notifications"></a>컨테이너: 클라이언트 항목 알림

이 문서에서는 서버 응용 프로그램이 클라이언트 응용 프로그램의 문서에 있는 항목을 수정할 때 MFC 프레임 워크에서 호출 하는 재정의 가능한 함수에 대해 설명 합니다.

[COleClientItem](reference/coleclientitem-class.md) 는 서버 응용 프로그램이 라고도 하는 구성 요소 응용 프로그램의 요청에 대 한 응답으로 호출 되는 재정의 가능한 여러 함수를 정의 합니다. 이러한 재정의 가능는 일반적으로 알림 역할을 합니다. 스크롤, 활성화, 위치 변경 및 사용자가 항목을 편집 하거나 조작 하는 경우 수행 하는 변경 내용 등과 같은 다양 한 이벤트를 컨테이너 응용 프로그램에 알려 줍니다.

프레임 워크는 구현이 필요한 재정의 가능한 함수인를 호출 하 여 컨테이너 응용 프로그램에 변경 내용을 알립니다 `COleClientItem::OnChange` . 이 protected 함수는 두 개의 인수를 받습니다. 첫 번째는 서버가 항목을 변경한 이유를 지정 합니다.

|알림|의미|
|------------------|-------------|
|**OLE_CHANGED**|OLE 항목의 모양이 변경 되었습니다.|
|**OLE_SAVED**|OLE 항목이 저장 되었습니다.|
|**OLE_CLOSED**|OLE 항목이 닫혔습니다.|
|**OLE_RENAMED**|OLE 항목을 포함 하는 서버 문서의 이름이 변경 되었습니다.|
|**OLE_CHANGED_STATE**|OLE 항목이 한 상태에서 다른 상태로 변경 되었습니다.|
|**OLE_CHANGED_ASPECT**|프레임 워크에서 OLE 항목의 그리기 측면을 변경 했습니다.|

이러한 값은 AFXOLE에 정의 된 **OLE_NOTIFICATION** 열거형에서 가져온 것입니다.

이 함수에 대 한 두 번째 인수는 항목이 변경 된 방법 또는 입력 한 상태를 지정 합니다.

|첫 번째 인수가 인 경우|두 번째 인수|
|----------------------------|---------------------|
|**OLE_SAVED** 또는 **OLE_CLOSED**|는 사용 되지 않습니다.|
|**OLE_CHANGED**|변경 된 OLE 항목의 측면을 지정 합니다.|
|**OLE_CHANGED_STATE**|입력 중인 상태 (*emptyState*, *loadedState*, *Openstate*, *activestate* 또는 *activeUIState*)를 설명 합니다.|

클라이언트 항목에서 가정할 수 있는 상태에 대 한 자세한 내용은 [컨테이너: Client-Item 상태](containers-client-item-states.md)를 참조 하세요.

프레임 워크는 `COleClientItem::OnGetItemPosition` 내부 편집을 위해 항목을 활성화할 때를 호출 합니다. 내부 편집을 지 원하는 응용 프로그램의 경우 구현이 필요 합니다. MFC 응용 프로그램 마법사는 `CRect` 에 대 한 인수로 전달 되는 개체에 항목의 좌표를 할당 하는 기본 구현을 제공 합니다 `OnGetItemPosition` .

내부 편집 중에 OLE 항목의 위치 또는 크기가 변경 되는 경우 항목의 위치 및 클리핑 사각형에 대 한 컨테이너 정보를 업데이트 하 고 서버에서 변경 내용에 대 한 정보를 받아야 합니다. 프레임 워크는 `COleClientItem::OnChangeItemPosition` 이 목적을 위해를 호출 합니다. MFC 응용 프로그램 마법사는 기본 클래스의 함수를 호출 하는 재정의를 제공 합니다. `COleClientItem`함수가 클라이언트-항목 개체에 의해 유지 되는 정보를 업데이트 하도록 응용 프로그램 마법사가 파생 클래스에 대해 작성 하는 함수를 편집 해야 합니다.

## <a name="see-also"></a>참고 항목

[컨테이너](containers.md)<br/>
[컨테이너: Client-Item 상태](containers-client-item-states.md)<br/>
[COleClientItem:: OnChangeItemPosition](reference/coleclientitem-class.md#onchangeitemposition)
