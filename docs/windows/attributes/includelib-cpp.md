---
description: '자세히 알아보기: includelib (c + +)'
title: includelib (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.includelib
helpviewer_keywords:
- includelib attribute
ms.assetid: cd90ea6e-5ae8-4f11-b8d1-662db95412b2
ms.openlocfilehash: 9a7565a931a865b69f0da95da9e92481b27de3b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321352"
---
# <a name="includelib-c"></a>includelib(C++)

.Idl 또는 .h 파일을 생성 된 .idl 파일에 포함 시킵니다.

## <a name="syntax"></a>구문

```cpp
[ includelib(name.idl) ];
```

### <a name="parameters"></a>매개 변수

*이름 .idl*<br/>
생성 된 .idl 파일의 일부로 포함 하려는 .idl 파일의 이름입니다.

## <a name="remarks"></a>설명

**Includelib** c + + 특성을 만들면 .idl 또는 .h 파일이 문 다음에 생성 된 .idl 파일에 포함 됩니다. `importlib`

## <a name="example"></a>예제

다음 코드는 .cpp 파일에 표시 됩니다.

```cpp
// cpp_attr_ref_includelib.cpp
// compile with: /LD
[module(name="MyLib")];
[includelib("includelib.idl")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|예|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[되어야](include-cpp.md)<br/>
[importlib](importlib.md)
