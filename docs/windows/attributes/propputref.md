---
description: '자세히 알아보기: propputref'
title: propputref (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 5f09d742ef0df75df03e4f4d740181cfcaaa8f2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329670"
---
# <a name="propputref"></a>propputref

값 대신 참조를 사용 하는 속성 설정 함수를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[propputref]
```

## <a name="remarks"></a>설명

**Propputref** c + + 특성에는 [propputref](/windows/win32/Midl/propputref) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**Propputref** 의 샘플 사용에 대 한 [바인딩](bindable.md) 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`propget`, `propput`|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)
