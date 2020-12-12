---
description: '자세히 알아보기: propget'
title: propget (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 9fe284fb35d4753fbc3e124458200a9882838450
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327412"
---
# <a name="propget"></a>propget

속성 접근자 함수를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[propget]
```

## <a name="remarks"></a>설명

**Propget** c + + 특성에는 [propget](/windows/win32/Midl/propget) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**Propget** 의 샘플 사용에 대 한 [바인딩](bindable.md) 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`propput`, `propputref`|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)
