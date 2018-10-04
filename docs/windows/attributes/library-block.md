---
title: library_block (c + + COM 특성) | Microsoft Docs
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.library_block
dev_langs:
- C++
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cf4bcdd9290817bb77eeb20f1a014bd537d15d8b
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/04/2018
ms.locfileid: "48791720"
---
# <a name="libraryblock"></a>library_block

IDL 라이브러리 블록 내에서 생성자를 배치합니다.

## <a name="syntax"></a>구문

```cpp
[library_block]
```

## <a name="remarks"></a>설명

라이브러리 블록 내부에 구문에 배치 하는 경우 참조 되는 여부에 관계 없이 형식 라이브러리로 전달 되는 확인할 수 있습니다. 기본적으로 유일한 구문에 의해 수정 된 [coclass](coclass.md)를 [dispinterface](dispinterface.md), 및 [idl_module](idl-module.md) 특성 라이브러리 블록에 배치 됩니다.

## <a name="example"></a>예제

다음 코드에서 사용자 지정 인터페이스가 라이브러리 블록 내부에 배치 됩니다.

```cpp
// cpp_attr_ref_library_block.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib")];
[object, library_block, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface IMyInterface {
   HRESULT f1();
};
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|원하는 위치|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)합니다.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[독립 실행형 특성](stand-alone-attributes.md)  