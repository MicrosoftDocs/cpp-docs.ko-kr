---
description: '자세한 정보: Boxing (c + +/CX)'
title: Boxing(C++/CX)
ms.date: 12/30/2016
ms.assetid: edfb12fa-2a9b-42f6-bdac-d4d76cb8274e
ms.openlocfilehash: 50b7f3f071fcd0109a85fb24985024666bd8fad3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302740"
---
# <a name="boxing-ccx"></a>Boxing(C++/CX)

*Boxing* 은 변수가 Platform:: Object ^을 해당 입력 형식으로 사용 하는 메서드에 전달 될 때 [Windows:: Foundation::D atetime](/uwp/api/windows.foundation.datetime)또는와 같은 기본 스칼라 형식 등의 값 형식 변수를 **`int`** ref 클래스에 래핑합니다. [](../cppcx/platform-object-class.md)

## <a name="passing-a-value-type-to-an-object-parameter"></a>Object^ 매개 변수에 값 형식 전달

[Platform::Object^](../cppcx/platform-object-class.md)형식의 메서드 매개 변수에 전달하기 위해 명시적으로 변수를 boxing할 필요는 없지만 이전에 boxing된 값을 검색할 때는 명시적으로 원래 형식으로 캐스팅해야 합니다.

[!code-cpp[cx_boxing#01](../cppcx/codesnippet/CPP/cx_boxing/class1.cpp#01)]

### <a name="using-platformiboxt-to-support-nullable-value-types"></a>Platform:: IBox를 사용 하 여 \<T> nullable 값 형식 지원

C# 및 Visual Basic에서는 null 허용 값 형식의 개념을 지원합니다. C + +/CX에서는 형식을 사용 하 여 `Platform::IBox<T>` nullable 값 형식 매개 변수를 지 원하는 공용 메서드를 노출할 수 있습니다. 다음 예제에서는 c # 호출자가 인수 중 하나에 대해 null을 전달 하는 경우 null을 반환 하는 c + +/CX public 메서드를 보여 줍니다.

[!code-cpp[cx_boxing#02](../cppcx/codesnippet/CPP/cx_boxing/class1.h#02)]

C# XAML 클라이언트에서 이러한 메서드를 다음과 같이 사용할 수 있습니다.

```

// C# client code
    BoxingDemo.Class1 obj = new BoxingDemo.Class1();
    int? a = null;
    int? b = 5;
    var result = obj.Multiply(a,b); //result = null
```

## <a name="see-also"></a>참고 항목

[형식 시스템 (c + +/CX)](../cppcx/type-system-c-cx.md)<br/>
[캐스팅(C++/CX)](../cppcx/casting-c-cx.md)<br/>
[C + +/CX 언어 참조](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md)
