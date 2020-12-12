---
description: '자세한 정보: Platform:: Metadata:: RuntimeClassName'
title: Platform::Metadata::RuntimeClassName
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Metadata::RuntimeClassName
helpviewer_keywords:
- RuntimeClassName
- Platform::Metadata::RuntimeClassName
ms.assetid: fdef8f85-ab94-4edd-ba50-ee0da9358ff6
ms.openlocfilehash: 25d6f3ae6b7509029b08f809fa20d5bd0ca5e735
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308382"
---
# <a name="platformmetadataruntimeclassname"></a>Platform::Metadata::RuntimeClassName

클래스 정의에 적용될 경우 private 클래스가 GetRuntimeClassName 함수에서 유효한 이름을 반환하는지 확인합니다.

## <a name="syntax"></a>구문

```cpp
[Platform::Metadata::RuntimeClassName] name
```

#### <a name="parameters"></a>매개 변수

*name*<br/>
Windows Runtime에 표시되는 기존 공용 형식의 이름입니다.

### <a name="remarks"></a>설명

이 특성을 private ref 클래스에 사용하여 사용자 지정 런타임 형식 및/또는 기존 이름이 요구 사항을 충족하지 않는 시기를 지정합니다. 클래스가 구현하는 공용 인터페이스를 이름으로 지정합니다.

### <a name="example"></a>예제

다음 예제에서는 이 특성을 사용하는 방법을 보여 줍니다. 이 예제에서는 HellowWorldImpl의 런타임 형식 이름이 Test::Native::MyComponent::IHelloWorld입니다.

```cpp
namespace Test
{
    namespace Native
    {
        namespace MyComponent
        {
            public interface class IHelloWorld
            {
                Platform::String^ SayHello();
            };

            private ref class HelloWorldImpl sealed :[Platform::Metadata::RuntimeClassName] IHelloWorld
            {
            public:
                HelloWorldImpl();
                virtual Platform::String^ SayHello();
            };

            Platform::String^ HelloWorldImpl::SayHello()
            {
                return L"Hello World!";
            }
        }
    }
}
```

## <a name="see-also"></a>참고 항목

[Platform:: Metadata 네임 스페이스](../cppcx/platform-metadata-namespace.md)
