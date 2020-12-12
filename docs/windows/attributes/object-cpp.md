---
description: '다음에 대 한 자세한 정보: 개체 (c + +)'
title: object (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.object
helpviewer_keywords:
- object attribute
ms.assetid: f2d3c231-630d-4b4c-bd15-b1c30df362dd
ms.openlocfilehash: 82f259f6ca36c44f33eb68970d8b76ae2acc5853
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329752"
---
# <a name="object-c"></a>object(C++)

사용자 지정 인터페이스를 식별 합니다.

## <a name="syntax"></a>구문

```cpp
[object]
```

## <a name="remarks"></a>설명

인터페이스 정의 앞에 **개체** c + + 특성을 지정 하면 인터페이스가 .idl 파일에 사용자 지정 인터페이스로 배치 됩니다.

개체로 표시 된 인터페이스는에서 상속 해야 합니다 `IUnknown` . 기본 인터페이스가에서 상속 되는 경우이 조건이 충족 됩니다 `IUnknown` . 에서 상속 되는 기본 인터페이스가 없는 경우 `IUnknown` 컴파일러는 **개체로** 표시 된 인터페이스를 파생 시킵니다 `IUnknown` .

## <a name="example"></a>예제

**개체** 를 사용 하는 방법에 대 한 예제를 보려면 [nonbrowsable](nonbrowsable.md) 수 없음을 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**interface**|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[복수](dual.md)<br/>
[dispinterface](dispinterface.md)<br/>
[재구성](custom-cpp.md)<br/>
[__interface](../../cpp/interface.md)
