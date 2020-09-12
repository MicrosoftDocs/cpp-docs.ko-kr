---
title: 형식 및 멤버가 사용되지 않도록 지정(C++/CX)
ms.date: 12/30/2016
ms.assetid: b20b01c1-a439-4ff0-8cf3-d7280c492813
ms.openlocfilehash: 6d61b00690cc087c3baced6d96d0b6c8d73b5850
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040329"
---
# <a name="deprecating-types-and-members-ccx"></a>형식 및 멤버가 사용되지 않도록 지정(C++/CX)

C + +/CX에서는 [더 이상 사용 되지 않는](/uwp/api/windows.foundation.metadata.deprecatedattribute) 특성을 사용 하 여 생산자 및 소비자에 대 한 Windows 런타임 형식 및 멤버를 사용할 수 없습니다. 이 속성이 적용된 API를 사용하는 경우 API가 더 이상 사용되지 않음을 나타내고 대체 API를 사용하도록 권장하는 컴파일 타임 경고 메시지가 나타납니다. public 형식 및 메서드에서 이 특성을 적용하고 사용자 지정 메시지를 제공할 수 있습니다.

> [!CAUTION]
> 사용 [되지 않는](/uwp/api/windows.foundation.metadata.deprecatedattribute) 특성은 Windows 런타임 형식만 사용 하기 위한 것입니다. 표준 C++ 클래스 및 멤버에는 [__declspec(deprecated)](../cpp/deprecated-cpp.md)를 사용하세요.

### <a name="example"></a>예제

다음 예제에서는 Windows 런타임 구성 요소에서 사용자 고유의 공용 API를 사용할 수 없게 하는 방법을 보여 줍니다. [Windows:Foundation::Metadata::DeprecationType](/uwp/api/windows.foundation.metadata.deprecationtype) 형식의 두 번째 매개 변수는 API를 사용할 수 없게 할지 제거할지 여부를 지정합니다. 현재는 DeprecationType::Deprecated 값만 지원됩니다. 특성의 세 번째 매개 변수는 특성이 적용되는 [Windows::Foundation::Metadata::Platform](/uwp/api/windows.foundation.metadata.platformattribute) 을 지정합니다.

```

namespace wfm = Windows::Foundation::Metadata;

public ref class Bicycle sealed
{

public:
    property double Speed;

    [wfm::Deprecated("Use the Speed property to compute the angular speed of the wheel", wfm::DeprecationType::Deprecate, 0x0)]
    double ComputeAngularVelocity();
};
```

## <a name="supported-targets"></a>지원되는 대상

다음 표에서는 Deprecated 특성이 적용될 수 있는 구문을 보여 줍니다.

:::row:::
   :::column span="":::
      클래스
      대리자나
      열거형
      열거형 필드 \
      이벤트
      interface(인터페이스)
   :::column-end:::
   :::column span="":::
      방법이
      매개 변수가 있는 생성자 \
      property\
      구조체
      구조체 필드 \
      XAML 컨트롤
   :::column-end:::
:::row-end:::

## <a name="see-also"></a>참고 항목

[유형 시스템](../cppcx/type-system-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
