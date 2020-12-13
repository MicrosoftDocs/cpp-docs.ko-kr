---
description: '자세한 정보: COM 및 .NET에 대 한 c + + 특성'
title: COM 및 .NET의 C++ 특성
ms.custom: index-page
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI], reference topics
ms.assetid: 613a3611-b3eb-4347-aa38-99b654600e1c
ms.openlocfilehash: 6fc791f81ddc43f9f91c8ab46db6aebf1959d16b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333218"
---
# <a name="c-attributes-for-com-and-net"></a>COM 및 .NET의 C++ 특성

Microsoft에서는 COM 프로그래밍을 간소화 하 고 공용 언어 런타임 개발을 .NET Framework 하는 c + + 특성 집합을 정의 합니다. 소스 파일에 특성을 포함 하는 경우 컴파일러는 공급자 Dll을 사용 하 여 코드를 삽입 하거나 생성 된 개체 파일의 코드를 수정 합니다. 이러한 특성은 .idl 파일, 인터페이스, 형식 라이브러리 및 기타 COM 요소를 만드는 데 도움이 됩니다. IDE (통합 개발 환경)에서 특성은 마법사와 속성 창에서 지원 됩니다.

특성은 COM 개체를 작성 하는 데 필요한 몇 가지 세부적인 코딩을 제거 하는 반면,이를 사용 하려면 [com 기본 사항](/windows/win32/com/the-component-object-model) 에 대 한 배경 지식이 필요 합니다.

> [!NOTE]
> C + + 표준 특성을 찾고 있는 경우 [특성](../../cpp/attributes.md)을 참조 하세요.

## <a name="purpose-of-attributes"></a>특성의 용도

특성은 언어의 클래식 구조를 중단 하지 않고 현재 사용할 수 없는 방향으로 c + +를 확장 합니다. 특성을 사용 하면 공급자 (개별 Dll)가 언어 기능을 동적으로 확장할 수 있습니다. 특성의 주요 목표는 구성 요소 개발자의 생산성 수준을 높일 뿐만 아니라 COM 구성 요소의 제작을 간소화 하는 것입니다. 특성은 클래스, 데이터 멤버 또는 멤버 함수와 같은 거의 모든 c + + 구문에 적용할 수 있습니다. 다음은이 새 기술에서 제공 하는 이점에 대 한 강조입니다.

- 친숙 하 고 간단한 호출 규칙을 노출 합니다.

- 매크로가 아닌 삽입 된 코드를 사용 하 여 디버거에서 인식 합니다.

- 작업이 부담이 구현 세부 정보를 제외 하 고 기본 클래스에서 쉽게 파생 될 수 있습니다.

- COM 구성 요소에 필요한 많은 양의 IDL 코드를 몇 가지 간결한 특성으로 바꿉니다.

예를 들어 일반 ATL 클래스에 대 한 간단한 이벤트 싱크를 구현 하려면와 같은 특정 클래스에 [event_receiver](event-receiver.md) 특성을 적용할 수 있습니다 `CMyReceiver` . `event_receiver`그런 다음 특성은 Microsoft c + + 컴파일러에서 컴파일되며 개체 파일에 적절 한 코드를 삽입 합니다.

```cpp
[event_receiver(com)]
class CMyReceiver
{
   void handler1(int i) { ... }
   void handler2(int i, float j) { ... }
}
```

그런 다음 `CMyReceiver` `handler1` `handler2` [event_source](event-source.md)를 사용 하 여 만들 수 있는 이벤트 소스에서 메서드를 설정 하 고 [__hook](../../cpp/hook.md)내장 함수를 사용 하 여 이벤트를 처리할 수 있습니다.

## <a name="basic-mechanics-of-attributes"></a>특성의 기본 메커니즘

프로젝트에 특성을 삽입 하는 방법에는 세 가지가 있습니다. 먼저 소스 코드에 직접 삽입할 수 있습니다. 둘째, 프로젝트에서 개체의 속성 그리드를 사용 하 여 삽입할 수 있습니다. 마지막으로 다양 한 마법사를 사용 하 여 삽입할 수 있습니다. **속성** 창 및 다양 한 마법사 사용에 대 한 자세한 내용은 [Visual Studio 프로젝트-c + +](../../build/creating-and-managing-visual-cpp-projects.md)를 참조 하세요.

이전과 마찬가지로, 프로젝트를 빌드할 때 컴파일러는 각 c + + 소스 파일을 구문 분석 하 여 개체 파일을 생성 합니다. 그러나 컴파일러가 특성을 발견 하면 구문 분석 되 고 구문적으로 확인 됩니다. 그런 다음 컴파일러는 특성 공급자를 동적으로 호출 하 여 컴파일 타임에 코드를 삽입 하거나 다른 수정 작업을 수행 합니다. 공급자의 구현은 특성의 형식에 따라 달라 집니다. 예를 들어 ATL 관련 특성은 Atlprov.dll에 의해 구현 됩니다.

다음 그림에서는 컴파일러와 특성 공급자 간의 관계를 보여 줍니다.

![구성 요소 특성 통신](../media/vccompattrcomm.gif "구성 요소 특성 통신")

> [!NOTE]
> 특성 사용은 원본 파일의 내용을 변경 하지 않습니다. 생성 된 특성 코드가 표시 되는 유일한 시간은 디버깅 세션 중입니다. 또한 프로젝트의 각 소스 파일에 대해 특성 대체의 결과를 표시 하는 텍스트 파일을 생성할 수 있습니다. 이 절차에 대 한 자세한 내용은 [/fx (삽입 된 코드 병합)](../../build/reference/fx-merge-injected-code.md) 및 [삽입 된 코드 디버그](/visualstudio/debugger/how-to-debug-injected-code)를 참조 하세요.

대부분의 c + + 구문과 마찬가지로 특성에는 적절 한 사용을 정의 하는 특성 집합이 있습니다. 이를 특성의 컨텍스트 라고 하며 각 특성 참조 항목에 대 한 특성 컨텍스트 테이블에서 주소를 지정 합니다. 예를 들어 [coclass](coclass.md) 특성은 c + + 소스 파일 내의 아무 곳에 나 삽입할 수 있는 [cpp_quote](cpp-quote.md) 특성과 달리 기존 클래스 또는 구조체에만 적용할 수 있습니다.

## <a name="building-an-attributed-program"></a>특성을 사용하는 프로그램 빌드

소스 코드에 Visual C++ 특성을 추가한 후에는 Microsoft c + + 컴파일러가 형식 라이브러리 및 .idl 파일을 생성 하도록 할 수 있습니다. 다음 링커 옵션을 통해 .tlb 및 .idl 파일을 빌드할 수 있습니다.

- [/IDLOUT](../../build/reference/idlout-name-midl-output-files.md)

- [/IGNOREIDL](../../build/reference/ignoreidl-don-t-process-attributes-into-midl.md)

- [/MIDL](../../build/reference/midl-specify-midl-command-line-options.md)

- [/TLBOUT](../../build/reference/tlbout-name-dot-tlb-file.md)

일부 프로젝트에는 독립적인 .idl 파일이 여러 개 포함 되어 있습니다. 이러한 파일은 두 개 이상의 .tlb 파일을 생성 하 고 선택적으로 리소스 블록에 바인딩하는 데 사용 됩니다. 이 시나리오는 현재 Visual C++에서 지원 되지 않습니다.

또한 Visual C++ 링커는 모든 IDL 관련 특성 정보를 단일 MIDL 파일에 출력 합니다. 단일 프로젝트에서 두 개의 형식 라이브러리를 생성 하는 방법은 없습니다.

## <a name="attribute-contexts"></a><a name="contexts"></a> 특성 컨텍스트

C + + 특성은 네 가지 기본 필드를 사용 하 여 설명할 수 있습니다. 즉, 적용할 수 있는 대상 (**에 적용** 됨), 반복 가능한 상태 (**반복** 가능한 경우), 다른 특성의 필수 상태 (**필수 특성**) 및 기타 특성과의 비호환 (**잘못 된 특성**)을 사용할 수 있습니다. 이러한 필드는 각 특성의 참조 항목에서 함께 제공 되는 테이블에 나열 됩니다. 이러한 각 필드에 대해서는 아래에서 설명 합니다.

### <a name="applies-to"></a>적용 대상

이 필드는 지정 된 특성의 올바른 대상이 되는 다양 한 c + + 언어 요소를 설명 합니다. 예를 들어, 특성이 **적용 대상** 필드에서 "클래스"를 지정 하는 경우이는 특성을 올바른 c + + 클래스에만 적용할 수 있음을 나타냅니다. 특성이 클래스의 멤버 함수에 적용 되는 경우 구문 오류가 발생 합니다.

자세한 내용은 [사용 별 특성](attributes-by-usage.md)을 참조 하세요.

### <a name="repeatable"></a>반복 가능

이 필드는 동일한 대상에 특성을 반복적으로 적용할 수 있는지 여부를 나타냅니다. 대부분의 특성은 반복할 수 없습니다.

### <a name="required-attributes"></a>필수 특성

이 필드에는 지정 된 특성이 제대로 작동 하기 위해 존재 해야 하는 다른 특성 (동일한 대상에 적용 됨)이 나열 됩니다. 일반적으로 특성에는이 필드에 대 한 항목이 포함 되지 않습니다.

### <a name="invalid-attributes"></a>잘못 된 특성

이 필드에는 지정 된 특성과 호환 되지 않는 다른 특성이 나열 됩니다. 일반적으로 특성에는이 필드에 대 한 항목이 포함 되지 않습니다.

## <a name="in-this-section"></a>섹션 내용

[특성 프로그래밍 FAQ](attribute-programming-faq.md)<br/>
[그룹별 특성](attributes-by-group.md)<br/>
[사용 별 특성](attributes-by-usage.md)<br/>
[특성 사전순 참조](attributes-alphabetical-reference.md)
