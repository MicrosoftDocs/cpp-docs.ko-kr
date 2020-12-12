---
description: '자세히 알아보기: 복합 컨트롤에 기능 추가'
title: 복합 컨트롤에 기능 추가
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
ms.openlocfilehash: 90e1f6b0adfc33817f9fa5a6de6fbdcd276241e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166124"
---
# <a name="adding-functionality-to-the-composite-control"></a>복합 컨트롤에 기능 추가

필요한 컨트롤을 복합 컨트롤에 삽입 한 후에는 다음 단계에서 새로운 기능을 추가 합니다. 이 새로운 기능은 일반적으로 다음과 같은 두 가지 범주로 나뉩니다.

- 추가 인터페이스를 지원 하 고 추가 특정 기능을 사용 하 여 복합 컨트롤의 동작을 사용자 지정 합니다.

- 포함 된 ActiveX 컨트롤 (또는 컨트롤)에서 이벤트 처리

이 문서의 목적과 범위에 대해이 섹션의 나머지 부분에서는 ActiveX 컨트롤의 이벤트 처리만 중점적으로 다룹니다.

> [!NOTE]
> Windows 컨트롤에서 메시지를 처리 해야 하는 경우 ATL에서 메시지 처리에 대 한 자세한 내용은 [창 구현](../atl/implementing-a-window.md) 을 참조 하세요.

대화 상자 리소스에 ActiveX 컨트롤을 삽입 한 후 컨트롤을 마우스 오른쪽 단추로 클릭 하 고 **이벤트 처리기 추가** 를 클릭 합니다. 처리할 이벤트를 선택 하 고 **추가 및 편집** 을 클릭 합니다. 이벤트 처리기 코드는 컨트롤의 .h 파일에 추가 됩니다.

복합 컨트롤의 ActiveX 컨트롤에 대 한 연결 지점은 자동으로 연결 되 고 [CComCompositeControl:: AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap)호출을 통해 연결이 끊어집니다.

## <a name="see-also"></a>참고 항목

[복합 컨트롤 기본 사항](../atl/atl-composite-control-fundamentals.md)
