---
title: 이중 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.dual
dev_langs:
- C++
helpviewer_keywords:
- dual attribute
ms.assetid: 5d4a9069-d819-42cd-ba56-bbcda17157d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6af52fab983f93964ba33cf59ca38783df66b5da
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373583"
---
# <a name="dual"></a>dual

.Idl 파일에 이중 인터페이스와 인터페이스를 배치합니다.

## <a name="syntax"></a>구문

```cpp
[dual]
```

## <a name="remarks"></a>설명

경우는 **이중** c + + 특성이 인터페이스 앞에 오면, 생성된 된.idl 파일의 라이브러리 블록 안에 배치 하는 인터페이스입니다.

## <a name="example"></a>예제

다음 코드는 사용 하는 특성 블록 **이중** 인터페이스 정의 하기 전에:

```cpp
// cpp_attr_ref_dual.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLibrary")];

[uuid("2F5F63F1-16DA-11d2-9E7B-00C04FB926DA"), dual]

__interface IStatic : IDispatch
{
   HRESULT Func1(int i);
   [   propget,
      id(1),
      bindable,
      displaybind,
      defaultbind,
      requestedit
   ]
   HRESULT P1([out, retval] long *nSize);
   [   propput,
      id(1),
      bindable,
      displaybind,
      defaultbind,
      requestedit
   ]
   HRESULT P1([in] long nSize); 
};

[cpp_quote("#include file.h")];
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**interface**|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`dispinterface`|

자세한 내용은 [특성 컨텍스트](../windows/attribute-contexts.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](../windows/idl-attributes.md)<br/>
[용도별 특성](../windows/attributes-by-usage.md)<br/>
[custom](../windows/custom-cpp.md)<br/>
[dispinterface](../windows/dispinterface.md)<br/>
[object](../windows/object-cpp.md)<br/>
[__interface](../cpp/interface.md)  