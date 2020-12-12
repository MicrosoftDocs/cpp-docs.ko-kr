---
description: '다음에 대 한 자세한 정보: AsyncResultType 열거형'
title: AsyncResultType 열거형
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncResultType
helpviewer_keywords:
- AsyncResultType enumeration
ms.assetid: 4195d234-3f3f-4363-9118-6ad2a7551cf2
ms.openlocfilehash: 431c0cabf98b3636bbae02b2f05a14d11d122740
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175822"
---
# <a name="asyncresulttype-enumeration"></a>AsyncResultType 열거형

메서드에서 반환 하는 결과의 형식을 지정 합니다 `GetResults()` .

## <a name="syntax"></a>구문

```cpp
enum AsyncResultType;
```

## <a name="members"></a>멤버

### <a name="values"></a>값

|이름|설명|
|----------|-----------------|
|`MultipleResults`|`Start`상태와가 호출 되기 전에 점진적으로 표시 되는 여러 결과 집합입니다 `Close()` .|
|`SingleResult`|이벤트가 발생 한 후 표시 되는 단일 결과입니다 `Complete` .|

## <a name="requirements"></a>요구 사항

**헤더:** async. h

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
