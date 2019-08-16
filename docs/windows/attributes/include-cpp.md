---
title: include (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: ece88ebd7b5d9d81beb871427b58a72b2cf02022
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514559"
---
# <a name="include-c"></a>include(C++)

생성 된 .idl 파일에 포함할 하나 이상의 헤더 파일을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>매개 변수

*header_file*<br/>
생성 된 .idl 파일에 포함할 파일의 이름입니다.

## <a name="remarks"></a>설명

**Include** C++ 특성을`import "docobj.idl"` 통해 문이 생성 된 .idl 파일의 문 아래에 배치 됩니다. `#include`

**Include** C++ 특성에는 [include](/windows/win32/Midl/include) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

다음 코드에서는 **include**를 사용 하는 방법의 예를 보여 줍니다. 이 예에서 파일에는 `#include` 문만 포함 되어 있습니다.

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|원하는 위치|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[독립 실행형 특성](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)