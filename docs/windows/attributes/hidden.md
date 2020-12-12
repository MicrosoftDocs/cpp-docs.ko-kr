---
description: '자세히 알아보기: 숨김'
title: hidden (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 0609ef8b0dedb08e26e5442fd5070ca6a29e11d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97180229"
---
# <a name="hidden"></a>hidden

항목이 존재 하지만 사용자 지향 브라우저에 표시 되지 않음을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
[hidden]
```

## <a name="remarks"></a>설명

**Hidden** c + + 특성에는 [hidden](/windows/win32/Midl/hidden) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**Hidden** 을 사용 하는 방법에 대 한 예제는 [바인딩](bindable.md) 가능의 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**인터페이스**, **`class`** , **`struct`** , 메서드, 속성|
|**불가능**|아니요|
|**필수 특성**|**coclass** (또는에 적용 된 경우 **`class`** **`struct`** )|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[클래스 특성](class-attributes.md)<br/>
[메서드 특성](method-attributes.md)
