---
title: hidden (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501456"
---
# <a name="hidden"></a>hidden

항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
[hidden]
```

## <a name="remarks"></a>설명

**Hidden** C++ 특성에는 [hidden](/windows/win32/Midl/hidden) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**Hidden**을 사용 하는 방법에 대 한 예제는 [바인딩](bindable.md) 가능의 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**인터페이스**, **클래스**, **구조체**, 메서드, 속성|
|**반복 가능**|아니요|
|**필수 특성**|**coclass** ( **클래스** 또는 **구조체**에 적용 된 경우)|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[메서드 특성](method-attributes.md)