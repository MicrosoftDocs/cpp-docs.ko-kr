---
description: '자세히 알아보기: FactoryCacheFlags 열거형'
title: FactoryCacheFlags 열거형
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
ms.openlocfilehash: 68a86049bf1f6287a84ae4df2e27dbe3c63c91c5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198507"
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags 열거형

팩터리 개체를 캐시하는지 여부를 결정합니다.

## <a name="syntax"></a>구문

```cpp
enum FactoryCacheFlags;
```

## <a name="remarks"></a>설명

기본적으로 팩터리 캐싱 정책은 [Module](module-class.md) 개체를 만들 때 [ModuleType](moduletype-enumeration.md) 템플릿 매개 변수로 지정 됩니다. 이 정책을 재정의 하려면 팩터리 개체를 만들 때 **FactoryCacheFlags** 값을 지정 합니다.

| 정책 | 설명 |
|-|-|
|`FactoryCacheDefault`|`Module` 개체의 캐싱 정책이 사용됩니다.|
|`FactoryCacheEnabled`|`ModuleType` 개체를 만드는 데 사용된 `Module` 템플릿 매개 변수에 관계없이 팩터리 캐싱을 사용합니다.|
|`FactoryCacheDisabled`|`ModuleType` 개체를 만드는 데 사용된 `Module` 템플릿 매개 변수에 관계없이 팩터리 캐싱을 사용하지 않습니다.|

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="see-also"></a>참고 항목

[Microsoft:: WRL 네임 스페이스](microsoft-wrl-namespace.md)
