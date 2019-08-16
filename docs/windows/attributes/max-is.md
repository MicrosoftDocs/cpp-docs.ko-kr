---
title: max_is (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: f2e6db997891817620c1b2c1f70cb310818dd346
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514419"
---
# <a name="max_is"></a>max_is

유효한 배열 인덱스에 대 한 최대값을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>매개 변수

*expression*<br/>
하나 이상의 C 언어 식입니다. 빈 인수 슬롯을 사용할 수 있습니다.

## <a name="remarks"></a>설명

**Max_is** C++ 특성은 [max_is](/windows/win32/Midl/max-is) MIDL 특성과 동일한 기능을 포함 합니다.

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**구조체** 또는 **공용 구조체**의 필드, 인터페이스 매개 변수, 인터페이스 메서드|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|**size_is**|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="example"></a>예제

배열의 섹션을 지정 하는 방법에 대 한 예제는 [first_is](first-is.md) 를 참조 하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)<br/>
[매개 변수 특성](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)