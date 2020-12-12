---
description: '자세히 알아보기: RuntimeClassFlags Structure'
title: RuntimeClassFlags 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 7874447fbbbe429884c5a79d0c70bb93e617ec61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209271"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 구조체

[RuntimeClass](runtimeclass-class.md)인스턴스의 유형을 포함 합니다.

## <a name="syntax"></a>구문

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>매개 변수

*flags*<br/>
[RuntimeClassType 열거형](runtimeclasstype-enumeration.md) 값입니다.

## <a name="members"></a>멤버

### <a name="public-constants"></a>공용 상수

|Name|설명|
|----------|-----------------|
|[RuntimeClassFlags::value 상수](#value-constant)|[RuntimeClassType 열거](runtimeclasstype-enumeration.md) 값을 포함 합니다.|

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`RuntimeClassFlags`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="runtimeclassflagsvalue-constant"></a><a name="value-constant"></a> RuntimeClassFlags:: value 상수

[RuntimeClassType 열거](runtimeclasstype-enumeration.md) 값을 포함 하는 필드입니다.

```cpp
static const unsigned int value = flags;
```
