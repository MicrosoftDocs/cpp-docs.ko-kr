---
description: '자세히 알아보기: importidl'
title: importidl (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.importidl
helpviewer_keywords:
- importidl attribute
ms.assetid: 4b0a4b55-6c57-4e6e-bc7b-a12cc8063941
ms.openlocfilehash: b10caa9f4b1467727c70b6d968ca6aa33b58da0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329878"
---
# <a name="importidl"></a>importidl

지정 된 .idl 파일을 생성 된 .idl 파일에 삽입 합니다.

## <a name="syntax"></a>구문

```cpp
[ importidl(idl_file) ];
```

### <a name="parameters"></a>매개 변수

*idl_file*<br/>
응용 프로그램에 대해 생성 될 .idl 파일과 병합 하려는 .idl 파일의 이름을 식별 합니다.

## <a name="remarks"></a>설명

**Importidl** c + + 특성은 프로그램의 생성 된 .idl 파일 및 라이브러리 섹션 ( *idl_file*)에서 프로그램의 생성 된 .idl 파일의 라이브러리 섹션에 섹션을 배치 합니다 ( *idl_file*).

예를 들어, 생성 된 .idl 파일에 직접 코딩 된 .idl 파일을 사용 하려는 경우 **importidl** 를 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// cpp_attr_ref_importidl.cpp
// compile with: /LD
[module(name="MyLib")];
[importidl("import.idl")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importlib](importlib.md)<br/>
[되어야](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
