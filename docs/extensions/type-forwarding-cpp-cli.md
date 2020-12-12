---
description: '자세한 정보: 형식 전달 (c + +/CLI)'
title: 형식 전달(C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- type forwarding, C++
ms.assetid: ae730b69-0c27-41cc-84e1-3132783866ea
ms.openlocfilehash: 360ca624103c8021c17300f897b1091c13e898a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172884"
---
# <a name="type-forwarding-ccli"></a>형식 전달(C++/CLI)

‘형식 전달’을 사용하면 한 어셈블리(어셈블리 A)의 형식을 다른 어셈블리(어셈블리 B)로 이동할 수 있으며, 어셈블리 A를 사용하는 클라이언트를 다시 컴파일하지 않아도 됩니다.

## <a name="windows-runtime"></a>Windows 런타임

Windows 런타임에서는 이 기능이 지원되지 않습니다.

## <a name="common-language-runtime"></a>공용 언어 런타임

다음 코드 예제에서는 형식 전달을 사용하는 방법을 보여 줍니다.

### <a name="syntax"></a>구문

```cpp
#using "new.dll"
[assembly:TypeForwardedTo(type::typeid)];
```

### <a name="parameters"></a>매개 변수

*new*<br/>
형식 정의를 이동하는 대상 어셈블리입니다.

*type*<br/>
정의를 다른 어셈블리로 이동하는 형식입니다.

### <a name="remarks"></a>설명

구성 요소(어셈블리)가 제공되고 클라이언트 애플리케이션에서 사용된 후에 형식 전달을 사용하여 구성 요소(어셈블리)의 형식을 다른 어셈블리로 이동하고 업데이트된 구성 요소(및 필요한 추가 어셈블리)를 제공할 수 있으며, 다시 컴파일하지 않고도 클라이언트 애플리케이션이 계속 실행됩니다.

형식 전달은 기존 애플리케이션에서 참조된 구성 요소에 대해서만 실행됩니다. 애플리케이션을 다시 빌드하는 경우 애플리케이션에서 사용된 형식에 적합한 어셈블리 참조가 있어야 합니다.

어셈블리에서 형식(형식 A)을 전달하는 경우 해당 형식의 `TypeForwardedTo` 특성과 어셈블리 참조를 추가해야 합니다. 참조하는 어셈블리에 다음 중 하나가 있어야 합니다.

- 형식 A에 대한 정의

- 형식 A의 `TypeForwardedTo` 특성 및 어셈블리 참조

전달할 수 있는 형식의 예는 다음과 같습니다.

- ref 클래스

- 값 클래스

- 열거형

- interfaces

다음 형식은 전달할 수 없습니다.

- 제네릭 형식

- 네이티브 형식

- 중첩 형식(중첩 형식을 전달하려는 경우 바깥쪽 형식을 전달해야 함)

공용 언어 런타임을 대상으로 하는 언어로 작성된 어셈블리에 형식을 전달할 수 있습니다.

따라서 어셈블리 A.dll을 빌드하는 데 사용되는 소스 코드 파일에 형식 정의(`ref class MyClass`)가 있고 해당 형식 정의를 어셈블리 B.dll로 이동하려는 경우 다음을 수행합니다.

1. B.dll을 빌드하는 데 사용되는 소스 코드 파일로 `MyClass` 형식 정의를 이동합니다.

2. 어셈블리 B.dll 빌드

3. A.dll을 빌드하는 데 사용되는 소스 코드에서 `MyClass` 형식 정의를 삭제하고 다음으로 바꿉니다.

    ```cpp
    #using "B.dll"
    [assembly:TypeForwardedTo(MyClass::typeid)];
    ```

4. 어셈블리 A.dll을 빌드합니다.

5. 클라이언트 애플리케이션을 다시 컴파일하지 않고 A.dll을 사용합니다.

### <a name="requirements"></a>요구 사항

컴파일러 옵션: `/clr`
