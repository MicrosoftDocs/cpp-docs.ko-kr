---
description: '다음에 대 한 자세한 정보: library_block'
title: library_block (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.library_block
helpviewer_keywords:
- library_block attribute
ms.assetid: ae7a7ebe-5e1a-4eda-a058-11bbd058ece8
ms.openlocfilehash: 486c40fa8641e74b6e3bc72bc7f980e3ee1216e1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329822"
---
# <a name="library_block"></a>library_block

구문을 IDL 라이브러리 블록 안에 배치 합니다.

## <a name="syntax"></a>구문

```cpp
[library_block]
```

## <a name="remarks"></a>설명

구조체를 라이브러리 블록 내에 저장 하는 경우 참조 여부와 관계 없이 형식 라이브러리로 전달 됩니다. 기본적으로 [coclass](coclass.md) [, 특성 및](dispinterface.md) [idl_module](idl-module.md) 특성에 의해 수정 된 구문만 라이브러리 블록에 배치 됩니다.

## <a name="example"></a>예제

다음 코드에서는 사용자 지정 인터페이스가 라이브러리 블록 내부에 배치 됩니다.

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

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)
