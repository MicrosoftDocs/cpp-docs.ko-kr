---
description: '자세히 알아보기: GetModuleBase 함수'
title: GetModuleBase 함수
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: cdedaf905da194400209840b6bd84fa8e626eb0a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295200"
---
# <a name="getmodulebase-function"></a>GetModuleBase 함수

[RuntimeClass](runtimeclass-class.md) 개체의 참조 횟수를 증가 및 감소 시키는 데 사용할 수 있는 [modulebase](modulebase-class.md) 포인터를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>반환 값

`ModuleBase` 개체에 대한 포인터입니다.

## <a name="remarks"></a>설명

이 함수는 개체 참조 횟수를 증가 및 감소 시키기 위해 내부적으로 사용 됩니다.

이 함수를 사용 하 여 [Modulebase:: IncrementObjectCount](modulebase-class.md#incrementobjectcount) 및 [modulebase::D ecrementobjectcount](modulebase-class.md#decrementobjectcount)를 호출 하 여 참조 횟수를 제어할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
