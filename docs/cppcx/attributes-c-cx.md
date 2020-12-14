---
description: '자세히 알아보기: 특성 (c + +/CX)'
title: 특성(C++/CX)
ms.date: 12/30/2016
ms.assetid: 4438e03c-4de3-433d-abcc-31aa863bc0e0
ms.openlocfilehash: 82299db6b5c11521584b8dd400b401ec0df78c72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302779"
---
# <a name="attributes-ccx"></a>특성(C++/CX)

특성은 메타 데이터 생성에서 특정 동작을 지정 하기 위해 Windows 런타임 형식 및 메서드를 대괄호로 앞에 추가할 수 있는 특수 한 종류의 ref 클래스입니다. 몇 가지 미리 정의 된 특성 (예:  [Windows:: Foundation:: Metadata:: WebHostHidden](/uwp/api/windows.foundation.metadata.webhosthiddenattribute))은 c + +/cx 코드에서 일반적으로 사용 됩니다. 이 예제에서는 특성이 클래스에 적용되는 방식을 보여 줍니다.

[!code-cpp[cx_attributes#01](../cppcx/codesnippet/CPP/cx_attributes/class1.h#01)]

## <a name="custom-attributes"></a>사용자 지정 특성

사용자 지정 특성을 정의할 수도 있습니다. 사용자 지정 특성은 다음 Windows 런타임 규칙을 준수 해야 합니다.

- 사용자 지정 특성에는 공용 필드만 포함될 수 있습니다.

- 사용자 지정 특성 필드는 특성이 클래스에 적용될 때 초기화될 수 있습니다.

- 필드는 다음 형식 중 하나일 수 있습니다.

  - int32(int)

  - uint32(unsigned int)

  - bool

  - Platform::String^

  - Windows::Foundation::HResult

  - Platform::Type^

  - public enum 클래스(사용자 정의 열거형 포함)

다음 예제에서는 사용자 지정 특성을 정의한 다음 사용할 때 초기화하는 방법을 보여 줍니다.

[!code-cpp[cx_attributes#02](../cppcx/codesnippet/CPP/cx_attributes/class1.h#02)]

## <a name="see-also"></a>참고 항목

[형식 시스템 (c + +/CX)](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
