---
description: '자세히 알아보기: IDispEventImpl 지원'
title: IDispEventImpl 지원
ms.date: 11/04/2016
helpviewer_keywords:
- event sink maps, declaring
- IDispEventImpl class, advising and unadvising
- SINK_ENTRY macro
- type libraries, importing
- ATL, IDispEventImpl support in COM objects
- BEGIN_SINK_MAP macro
- IDispEventImpl class, declaring
ms.assetid: b957f930-6a5b-4598-8e4d-8027759957e7
ms.openlocfilehash: 6a5c12e011ad0dc0f27594325a22dadddd5b92c0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157375"
---
# <a name="supporting-idispeventimpl"></a>IDispEventImpl 지원

[IDispEventImpl](../atl/reference/idispeventimpl-class.md) 템플릿 클래스를 사용 하 여 ATL 클래스의 연결 지점 싱크에 대 한 지원을 제공할 수 있습니다. 연결 지점 싱크를 사용 하 여 클래스는 외부 COM 개체에서 발생 한 이벤트를 처리할 수 있습니다. 이러한 연결 지점 싱크는 클래스에서 제공 하는 이벤트 싱크 맵과 매핑됩니다.

클래스에 대 한 연결 지점 싱크를 올바르게 구현 하려면 다음 단계를 완료 해야 합니다.

- 각 외부 개체에 대 한 형식 라이브러리 가져오기

- 인터페이스 선언 `IDispEventImpl`

- 이벤트 싱크 맵 선언

- 연결 지점의 Advise 및 unadvise

연결 지점 싱크를 구현 하는 단계는 모두 클래스의 헤더 파일 (.h)만 수정 하 여 수행 됩니다.

## <a name="importing-the-type-libraries"></a>형식 라이브러리 가져오기

처리할 이벤트를 포함 하는 각 외부 개체에 대해 형식 라이브러리를 가져와야 합니다. 이 단계에서는 처리할 수 있는 이벤트를 정의 하 고 이벤트 싱크 맵을 선언할 때 사용 되는 정보를 제공 합니다. [#Import](../preprocessor/hash-import-directive-cpp.md) 지시어를 사용 하 여이를 수행할 수 있습니다. `#import`지원할 각 디스패치 인터페이스에 필요한 지시문 줄을 클래스의 헤더 파일 (.h)에 추가 합니다.

다음 예제에서는 외부 COM 서버의 형식 라이브러리 ()를 가져옵니다 `MSCAL.Calendar.7` .

[!code-cpp[NVC_ATL_Windowing#141](../atl/codesnippet/cpp/supporting-idispeventimpl_1.h)]

> [!NOTE]
> `#import`지원할 각 외부 형식 라이브러리에 대 한 별도의 문이 있어야 합니다.

## <a name="declaring-the-idispeventimpl-interfaces"></a>IDispEventImpl 인터페이스 선언

이제 각 디스패치 인터페이스의 형식 라이브러리를 가져왔지만 `IDispEventImpl` 각 외부 디스패치 인터페이스에 대해 별도의 인터페이스를 선언 해야 합니다. `IDispEventImpl`각 외부 개체에 대 한 인터페이스 선언을 추가 하 여 클래스의 선언을 수정 합니다. 매개 변수에 대 한 자세한 내용은 [IDispEventImpl](../atl/reference/idispeventimpl-class.md)를 참조 하세요.

다음 코드에서는 `DCalendarEvents` 클래스에서 구현 하는 COM 개체에 대 한 두 개의 연결 지점 싱크를 인터페이스에 대해 선언 합니다 `CMyCompositCtrl2` .

[!code-cpp[NVC_ATL_Windowing#142](../atl/codesnippet/cpp/supporting-idispeventimpl_2.h)]

## <a name="declaring-an-event-sink-map"></a>이벤트 싱크 맵 선언

이벤트 알림이 적절 한 함수에 의해 처리 되려면 클래스가 각 이벤트를 올바른 처리기로 라우팅해야 합니다. 이는 이벤트 싱크 맵을 선언 하 여 수행 됩니다.

ATL은이 매핑을 더 쉽게 만드는 여러 매크로, [BEGIN_SINK_MAP](reference/composite-control-macros.md#begin_sink_map), [END_SINK_MAP](reference/composite-control-macros.md#end_sink_map)및 [SINK_ENTRY_EX](reference/composite-control-macros.md#sink_entry_ex)를 제공 합니다. 표준 형식은 다음과 같습니다.

```cpp
BEGIN_SINK_MAP(comClass)
  SINK_ENTRY_EX(id, iid, dispid, func)
  . . . //additional external event entries
END_SINK_MAP()
```

다음 예제에서는 두 개의 이벤트 처리기를 사용 하 여 이벤트 싱크 맵을 선언 합니다.

[!code-cpp[NVC_ATL_Windowing#136](../atl/codesnippet/cpp/supporting-idispeventimpl_3.h)]

구현이 거의 완료 되었습니다. 마지막 단계에서는 외부 인터페이스를 unadvising 하 고이에 대해 다룹니다.

## <a name="advising-and-unadvising-the-idispeventimpl-interfaces"></a>IDispEventImpl 인터페이스에 대해 조언 및 Unadvising

최종 단계는 적절 한 시간에 모든 연결 지점에 대해 advise 하거나 unadvise 하는 메서드를 구현 하는 것입니다. 외부 클라이언트와 개체 간의 통신을 수행 하려면 먼저이를 수행 해야 합니다. 개체를 표시 하기 전에 개체에서 지 원하는 각 외부 디스패치 인터페이스를 나가는 인터페이스에 대해 쿼리 합니다. 연결이 설정 되 고 나가는 인터페이스에 대 한 참조가 개체의 이벤트를 처리 하는 데 사용 됩니다. 이 절차를 "소개" 라고 합니다.

외부 인터페이스를 사용 하 여 개체를 완성 한 후에는 나가는 인터페이스가 클래스에서 더 이상 사용 되지 않음을 알려 줍니다. 이 프로세스를 "unadvising" 라고 합니다.

COM 개체의 고유한 특성 때문에이 프로시저는 구현 간에 세부 정보 및 실행이 다릅니다. 이러한 세부 정보는이 항목의 범위를 벗어나 해결 되지 않습니다.

## <a name="see-also"></a>참고 항목

[ATL COM 개체의 기본 사항](../atl/fundamentals-of-atl-com-objects.md)
