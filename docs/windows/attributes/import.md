---
description: '자세한 정보: 가져오기'
title: import (c + + COM 특성)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.import
helpviewer_keywords:
- import attribute
ms.assetid: ebf07cae-39fb-4047-8b57-54af0a9a83de
ms.openlocfilehash: a3ebb7aa625c0a422197662973985275647a049f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321404"
---
# <a name="import"></a>import

주 IDL에서 참조 하려는 정의가 포함 된 다른 .idl, odl 또는 헤더 파일을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ import(
   idl_file
) ];
```

### <a name="parameters"></a>매개 변수

*idl_file*<br/>
현재 프로젝트의 형식 라이브러리로 가져올 .idl 파일의 이름입니다.

## <a name="remarks"></a>설명

C  + + 특성을 가져오면 `#import` `import "docobj.idl"` 생성 된 .idl 파일의 문 아래에 문이 배치 됩니다. **가져오기** 특성은 [가져오기](/windows/win32/Midl/import) MIDL 특성과 동일한 기능을 포함 합니다.

**가져오기** 특성은 지정 된 파일을 프로젝트에 의해 생성 되는 .idl 파일에만 배치 합니다. **가져오기** 특성을 사용 하면 프로젝트의 소스 코드에서 지정 된 파일의 구문을 호출할 수 없습니다.  프로젝트의 소스 코드에서 지정 된 파일의 구문을 호출 하려면 [#import](../../preprocessor/hash-import-directive-cpp.md) 및 특성을 사용 `embedded_idl` 하거나 .h 파일이 있는 경우 *idl_file* 에 대 한 .h 파일을 포함할 수 있습니다.

## <a name="example"></a>예제

코드는 다음과 같습니다.

```cpp
// cpp_attr_ref_import.cpp
// compile with: /LD
[module(name="MyLib")];
[import(import.idl)];
```

는 생성 된 .idl 파일에서 다음 코드를 생성 합니다.

```
import "docobj.idl";
import "import.idl";

[ uuid(EED3644C-8488-3ECD-BA97-147DB3CDB499), version(1.0) ]
library MyLib {
   importlib("stdole2.tlb");
   importlib("olepro32.dll");
...
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

[IDL 특성](idl-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)<br/>
[importidl](importidl.md)<br/>
[importlib](importlib.md)<br/>
[되어야](include-cpp.md)<br/>
[includelib](includelib-cpp.md)
