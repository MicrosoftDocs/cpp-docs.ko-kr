---
description: '자세히 알아보기: 항목'
title: entry (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.entry
helpviewer_keywords:
- entry attribute
ms.assetid: ba4843e3-d7ad-4b86-9a15-0b4192f0f698
ms.openlocfilehash: fbceea4c23d730ceba780ce68398a9d78fa9c33b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259229"
---
# <a name="entry"></a>entry

DLL의 진입점을 식별 하 여 모듈에서 내보낸 함수 또는 상수를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[ entry(id) ]
```

### <a name="parameters"></a>매개 변수

*id*<br/>
진입점의 ID입니다.

## <a name="remarks"></a>설명

**항목** c + + 특성에는 [항목](/windows/win32/Midl/entry) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**항목** 을 사용 하는 예제는 [idl_module](idl-module.md) 의 예제를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|`idl_module` 특성|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)
