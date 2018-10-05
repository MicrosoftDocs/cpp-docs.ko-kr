---
title: DontUseNewUseMake 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1f3a57401a3ab2efd45cab2dace127010c24e6
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235284"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake 클래스

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>설명

연산자를 사용 하는 것을 금지 `new` 에서 `RuntimeClass`합니다. 결과적으로 사용 해야 합니다 [함수](../windows/make-function.md) 대신 합니다.

## <a name="members"></a>멤버

### <a name="public-operators"></a>Public 연산자

이름                                             | 설명
------------------------------------------------ | ---------------------------------------------------------------------------
[Dontusenewusemake:: Operator 새](#operator-new) | 연산자 오버 로드 `new` 에서 사용 되지 않도록 방지 하 고 `RuntimeClass`입니다.

## <a name="inheritance-hierarchy"></a>상속 계층

`DontUseNewUseMake`

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="operator-new"></a>Dontusenewusemake:: Operator 새

WRL 인프라를 지원하며 사용자 코드에서 직접 사용할 수 없습니다.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>매개 변수

*__unnamed0*<br/>
할당할 메모리의 바이트 수를 지정 하는 명명 되지 않은 매개 변수입니다.

*배치*<br/>
할당할 형식입니다.

### <a name="return-value"></a>반환 값

연산자를 오버 로드 하는 경우 추가 인수를 전달 하는 방법을 제공 `new`합니다.

### <a name="remarks"></a>설명

연산자 오버 로드 `new` 에서 사용 되지 않도록 방지 하 고 `RuntimeClass`입니다.
