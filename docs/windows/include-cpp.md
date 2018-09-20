---
title: include (c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.include
dev_langs:
- C++
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 617747a9eda77d8dc2ba21006b649daead9546d3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419323"
---
# <a name="include-c"></a>include(C++)

생성된 된.idl 파일에 포함할 하나 이상의 헤더 파일을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ include(
   header_file
) ];
```

### <a name="parameters"></a>매개 변수

*header_file*<br/>
생성된 된.idl 파일에 포함 하려는 파일의 이름입니다.

## <a name="remarks"></a>설명

**포함** c + + 특성을 사용 하면는 `#include` 문 아래에 배치 하는 `import "docobj.idl"` 생성 된.idl 파일의 문.

합니다 **포함** c + + 특성에 동일한 기능을 합니다 [포함](/windows/desktop/Midl/include) MIDL 특성입니다.

## <a name="example"></a>예제

다음 코드를 사용 하는 방법의 예를 보여 줍니다 **포함**합니다. 예를 들어 파일 include.h만 포함 된 `#include` 문입니다.

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

자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](../windows/idl-attributes.md)<br/>
[독립 실행형 특성](../windows/stand-alone-attributes.md)<br/>
[import](../windows/import.md)<br/>
[importidl](../windows/importidl.md)<br/>
[includelib](../windows/includelib-cpp.md)<br/>
[importlib](../windows/importlib.md)  