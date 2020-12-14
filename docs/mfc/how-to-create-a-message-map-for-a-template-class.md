---
description: '자세한 정보: 방법: 템플릿 클래스에 대 한 메시지 맵 만들기'
title: '방법: 템플릿 클래스에 대한 메시지 맵 만들기'
ms.date: 11/04/2016
helpviewer_keywords:
- template classes [MFC], creating message maps
- message maps [MFC], template classes
ms.assetid: 4e7e24f8-06df-4b46-82aa-7435c8650de3
ms.openlocfilehash: 16d1d486bae77d0e580521ba71d29216701c4481
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253431"
---
# <a name="how-to-create-a-message-map-for-a-template-class"></a>방법: 템플릿 클래스에 대한 메시지 맵 만들기

MFC의 메시지 매핑은 Windows 메시지를 적절 한 c + + 개체 인스턴스로 직접 전달 하는 효율적인 방법을 제공 합니다. MFC 메시지 맵 대상의 예로는 응용 프로그램 클래스, 문서 및 뷰 클래스, 컨트롤 클래스 등이 있습니다.

기존 MFC 메시지 맵은 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) 매크로를 사용 하 여 메시지 맵의 시작을 선언 하 고, 각 메시지 처리기 클래스 메서드에 대 한 매크로 항목을 선언 하 고, 마지막으로 메시지 맵의 끝을 선언 하는 [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map) 매크로를 사용 하 여 선언 됩니다.

템플릿 인수를 포함 하는 클래스와 함께 사용 하는 경우 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map) 매크로에 대 한 한 가지 제한이 있습니다. 템플릿 클래스와 함께 사용 하는 경우이 매크로는 매크로 확장 중에 누락 된 템플릿 매개 변수로 인해 컴파일 시간 오류가 발생 합니다. [BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map) 매크로는 단일 템플릿 인수를 포함 하는 클래스가 자체 메시지 맵을 선언할 수 있도록 설계 되었습니다.

## <a name="example"></a>예제

외부 데이터 원본과의 동기화를 제공 하도록 MFC [CListBox](reference/clistbox-class.md) 클래스를 확장 하는 예를 살펴보겠습니다. 가상 클래스는 다음과 `CSyncListBox` 같이 선언 됩니다.

[!code-cpp[NVC_MFC_CListBox#42](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_1.h)]

`CSyncListBox`클래스는 동기화 할 데이터 소스를 설명 하는 단일 형식으로 템플릿 사용 됩니다. 또한 클래스의 메시지 맵에 참여 하는 세 가지 메서드인 `OnPaint` , 및를 선언 `OnDestroy` `OnSynchronize` 합니다. 메서드는 다음과 `OnSynchronize` 같이 구현 됩니다.

[!code-cpp[NVC_MFC_CListBox#43](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_2.cpp)]

위의 구현을 사용 하면 `CSyncListBox` ,, 등의 메서드를 구현 하는 모든 클래스 형식에서 클래스를 특수화할 수 있습니다 `GetCount` `CArray` `CList` `CMap` . `StringizeElement`함수는 다음에 의해 프로토타입화 된 템플릿 함수입니다.

[!code-cpp[NVC_MFC_CListBox#44](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_3.cpp)]

일반적으로이 클래스의 메시지 맵은 다음과 같이 정의 됩니다.

```cpp
BEGIN_MESSAGE_MAP(CSyncListBox, CListBox)
  ON_WM_PAINT()
  ON_WM_DESTROY()
  ON_MESSAGE(LBN_SYNCHRONIZE, OnSynchronize)
END_MESSAGE_MAP()
```

여기서 **LBN_SYNCHRONIZE** 는 응용 프로그램에서 정의 하는 다음과 같은 사용자 지정 사용자 메시지입니다.

[!code-cpp[NVC_MFC_CListBox#45](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_4.cpp)]

매크로를 확장 하는 동안 클래스에 대 한 템플릿 사양이 누락 되기 때문에 위의 매크로 맵은 컴파일되지 않습니다 `CSyncListBox` . **BEGIN_TEMPLATE_MESSAGE_MAP** 매크로는 지정 된 템플릿 매개 변수를 확장 된 매크로 맵에 통합 하 여이를 해결 합니다. 이 클래스의 메시지 맵은 다음과 같이 됩니다.

[!code-cpp[NVC_MFC_CListBox#46](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_5.cpp)]

다음은 `CSyncListBox` 개체를 사용 하는 클래스의 샘플 사용을 보여 줍니다 `CStringList` .

[!code-cpp[NVC_MFC_CListBox#47](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_6.cpp)]

테스트를 완료 하려면 함수를 `StringizeElement` 클래스와 함께 사용 하도록 특수화 해야 합니다 `CStringList` .

[!code-cpp[NVC_MFC_CListBox#48](codesnippet/cpp/how-to-create-a-message-map-for-a-template-class_7.cpp)]

## <a name="see-also"></a>참고 항목

[BEGIN_TEMPLATE_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_template_message_map)<br/>
[메시지 처리 및 매핑](message-handling-and-mapping.md)
