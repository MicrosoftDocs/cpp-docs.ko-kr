---
description: '자세히 알아보기: propput'
title: propput (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propput
helpviewer_keywords:
- propput attribute
ms.assetid: 1f84dda9-9cce-4e16-aaf0-b2c5219827f2
ms.openlocfilehash: f7b33996c4575de6b94fc3127c33a88c6f791aed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327382"
---
# <a name="propput"></a>propput

속성 설정 함수를 지정합니다.

## <a name="syntax"></a>구문

```cpp
[propput]
```

## <a name="remarks"></a>설명

**Propput** c + + 특성에는 [propput](/windows/win32/Midl/propput) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**Propput** 의 샘플 사용에 대 한 [바인딩](bindable.md) 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`propget`, `propputref`|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propputref](propputref.md)
