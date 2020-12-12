---
description: '자세히 알아보기: in (c + +)'
title: in (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.in
helpviewer_keywords:
- in attribute
ms.assetid: 7b450cc4-4d2e-4910-a195-7487c6b7c373
ms.openlocfilehash: c4d19fcf7adc767986306a3ef55b26a2cc91dccf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97321378"
---
# <a name="in-c"></a>in(C++)

호출 하는 프로시저에서 호출 되는 프로시저로 매개 변수가 전달 됨을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
[in]
```

## <a name="remarks"></a>설명

**In** c + + 특성에는 [in](/windows/win32/Midl/in) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**에서** 를 사용 하는 방법에 대 한 예제는 [바인딩](bindable.md) 가능을 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|인터페이스 매개 변수, 인터페이스 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|**retval**|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[id](id.md)<br/>
[out](out-cpp.md)
