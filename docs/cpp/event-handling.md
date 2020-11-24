---
title: 이벤트 처리
description: Microsoft c + + 확장에서 COM 및 네이티브 이벤트 처리를 모두 지 원하는 방법에 대해 알아봅니다.
ms.date: 11/20/2020
helpviewer_keywords:
- event handling [C++]
ms.openlocfilehash: de8cd6dfac2b83e850ec62ff88e192d1c60e427e
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483132"
---
# <a name="event-handling"></a>이벤트 처리

이벤트 처리는 기본적으로 com 클래스 (일반적으로 ATL 클래스 또는 [coclass](../windows/attributes/coclass.md) 특성을 사용 하 여 com 개체를 구현 하는 c + + 클래스)에 대해 지원 됩니다. 자세한 내용은 [COM에서 이벤트 처리](../cpp/event-handling-in-com.md)를 참조 하세요.

네이티브 c + + 클래스 (COM 개체를 구현 하지 않는 c + + 클래스)에 대해서도 이벤트 처리가 지원 됩니다. 네이티브 c + + 이벤트 처리 지원은 더 이상 사용 되지 않으며 이후 릴리스에서 제거 될 예정입니다. 자세한 내용은 [Native c + +에서 이벤트 처리](../cpp/event-handling-in-native-cpp.md)를 참조 하세요.

> [!NOTE]
> 네이티브 c + +의 이벤트 특성은 표준 c + +와 호환 되지 않습니다. 규칙 모드를 지정 하는 경우에는 컴파일되지 않습니다 [`/permissive-`](../build/reference/permissive-standards-conformance.md) .

이벤트 처리는 단일 및 다중 스레드 사용을 모두 지원 합니다. 동시 다중 스레드 액세스 로부터 데이터를 보호 합니다. 이벤트 소스 또는 받는 사람 클래스에서 서브 클래스를 파생할 수 있습니다. 이러한 서브 클래스는 확장 이벤트 소싱 및 수신을 지원 합니다.

Microsoft c + + 컴파일러에는 이벤트 및 이벤트 처리기를 선언 하는 특성 및 키워드가 포함 되어 있습니다. CLR 프로그램과 네이티브 C++ 프로그램에서 이벤트 특성과 키워드를 사용할 수 있습니다.

| 아티클 | 설명 |
|--|--|
| [`event_source`](../windows/attributes/event-source.md) | 이벤트 소스를 만듭니다. |
| [`event_receiver`](../windows/attributes/event-receiver.md) | 이벤트 수신기(싱크)를 만듭니다. |
| [`__event`](../cpp/event.md) | 이벤트를 선언합니다. |
| [`__raise`](../cpp/raise.md) | 이벤트의 호출 사이트를 강조합니다. |
| [`__hook`](../cpp/hook.md) | 처리기 메서드를 이벤트와 연결합니다. |
| [`__unhook`](../cpp/unhook.md) | 이벤트에서 처리기 메서드를 분리 합니다. |

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)\
[키워드](../cpp/keywords-cpp.md)
