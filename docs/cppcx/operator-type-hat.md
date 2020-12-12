---
description: '자세한 정보: 연산자 유형 ^'
title: 연산자 Type^
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 6258da5f276313d28f56fe470849c929cc057a47
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276805"
---
# <a name="operator-type"></a>연산자 Type^

[Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) 을 `Platform::Type`으로 변환할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>Return Value

`Platform::Type` Windows::UI::Xaml::Interop::TypeName [이 제공되면](/uwp/api/windows.ui.xaml.interop.typename)을 반환합니다.

### <a name="remarks"></a>설명

`TypeName` 은 형식 정보를 나타내기 위한 언어 중립 Windows 런타임 구조체입니다. [Platform::Type](../cppcx/platform-type-class.md) 은 C++에서만 사용되며 ABI(애플리케이션 이진 인터페이스) 전반에서 전달될 수 없습니다. 다음은 `TypeName`Navigate [함수에서](/uwp/api/windows.ui.xaml.controls.frame.navigate) 을 사용하는 한 가지 방법입니다.

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>예제

다음 예제에서는 `TypeName` 과 `Type`간을 변환하는 방법을 보여 줍니다.

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값

.NET Framework `TypeName` 프로그램 프로젝트 <xref:System.Type>

### <a name="requirements"></a>요구 사항

## <a name="see-also"></a>참고 항목

[연산자 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform:: Type 클래스](../cppcx/platform-type-class.md)
