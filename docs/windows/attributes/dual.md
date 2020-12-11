---
description: '자세히 알아보기: 이중'
title: dual (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.dual
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
ms.openlocfilehash: d1e72bd787bc73042b4f4a180ea119712021edaf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112026"
---
# <a name="dual"></a>dual

인터페이스를 .idl 파일에 이중 인터페이스로 배치 합니다.

## <a name="syntax"></a>구문

```cpp
[dual]
```

## <a name="remarks"></a>설명

**이중** c + + 특성이 인터페이스 앞에 오면 생성 된 .idl 파일의 라이브러리 블록 안에 인터페이스가 배치 됩니다.

## <a name="example"></a>예제

다음 코드는 인터페이스 정의 앞에 **이중** 을 사용 하는 특성 블록입니다.

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,    id(1),    bindable,    displaybind,    defaultbind,    requestedit
   ]
   HRESULT P1([in] long nSize);
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**interface**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`dispinterface`|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[사용 별 특성](attributes-by-usage.md)<br/>
[재구성](custom-cpp.md)<br/>
[dispinterface](dispinterface.md)<br/>
[object](object-cpp.md)<br/>
[__interface](../../cpp/interface.md)
