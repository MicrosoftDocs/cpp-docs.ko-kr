---
title: InspectableClass 매크로
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
ms.openlocfilehash: ee2a76edb967923a03ce6720b4163baf1cc48c32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500486"
---
# <a name="inspectableclass-macro"></a>InspectableClass 매크로

런타임 클래스 이름 및 신뢰 수준을 설정 합니다.

## <a name="syntax"></a>구문

```cpp
InspectableClass(
   runtimeClassName,
   trustLevel)
```

### <a name="parameters"></a>매개 변수

*runtimeClassName*<br/>
런타임 클래스의 전체 텍스트 이름입니다.

*trustLevel*<br/>
[TrustLevel](/windows/win32/api/inspectable/ne-inspectable-trustlevel) 열거형 값 중 하나입니다.

## <a name="remarks"></a>설명

**InspectableClass** 매크로는 Windows 런타임 형식에만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고자료

[RuntimeClass 클래스](runtimeclass-class.md)