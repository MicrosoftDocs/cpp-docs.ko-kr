---
title: 특성의 용도 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++], about attributes
ms.assetid: 3aff8bfa-a2a3-4fcb-a2c6-1d96a2b4c68d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2b34ff9641df4d102c2902e5b8ea42a80db4db50
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607102"
---
# <a name="purpose-of-attributes"></a>특성의 용도

언어의 기본 구조를 중단 하지 않고 현재 불가능 방향으로 c + +를 확장 하는 특성입니다. 특성을 통해 공급자 (별도 Dll) 언어 기능을 동적으로 확장 합니다. 특성의 기본 목적은 구성 요소 개발자의 생산성 수준을 증가 하는 것 외에도 COM 구성 요소 작성을 간소화 하기 위해. 특성을 적용할 수 클래스, 데이터 멤버, 멤버 함수 등 거의 모든 c + + 구문에 있습니다. 다음은이 새 기술을 통해 제공 되는 혜택을 강조 표시 합니다.

- 친숙 하 고 간단한 호출 규칙을 표시합니다.

- 사용 하 여 매크로 달리 디버거에서 인식 하는 코드를 삽입 합니다.

- 세부적인 구현 하지 않는 기본 클래스에서 쉽게 파생을 허용합니다.

- 몇 가지 간단한 특성을 사용 하 여 COM 구성 요소에서 필요한 IDL 코드의 양이 대체 합니다.

예를 들어 제네릭 ATL 클래스에 대 한 간단한 이벤트 싱크를 구현 하려면 적용할 수 있습니다 합니다 [event_receiver](../windows/event-receiver.md) 와 같은 특정 클래스에 특성 `CMyReceiver`합니다. `event_receiver` 특성은 개체 파일에 적절 한 코드를 삽입 하는 Visual c + + 컴파일러에 의해 컴파일됩니다.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

설정할 수 있습니다 합니다 `CMyReceiver` 메서드 `handler1` 하 고 `handler2` 이벤트를 처리할 (내장 함수를 사용 하 여 [__hook](../cpp/hook.md))를 사용 하 여 만들 수 있는 이벤트 원본에서 [event_source](../windows/event-source.md).

## <a name="see-also"></a>참고 항목

[개념](../windows/attributed-programming-concepts.md)