---
title: __RTDynamicCast | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __RTDynamicCast
apilocation:
- msvcr90.dll
- msvcr110.dll
- msvcr120.dll
- msvcrt.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
apitype: DLLExport
f1_keywords:
- __RTDynamicCast
dev_langs:
- C++
helpviewer_keywords:
- __RTDynamicCast
ms.assetid: 56aa2d7a-aa47-46ef-830d-e37175611239
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 85f8b31ee9faec433fa0c9f1ff64d5bfa1e9665a
ms.sourcegitcommit: 8480f16893f09911f08a58caf684405404f7ac8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49161257"
---
# <a name="rtdynamiccast"></a>__RTDynamicCast

[dynamic_cast](../cpp/dynamic-cast-operator.md) 연산자의 런타임 구현입니다.

## <a name="syntax"></a>구문

```cpp
PVOID __RTDynamicCast (
   PVOID inptr,
   LONG VfDelta,
   PVOID SrcType,
   PVOID TargetType,
   BOOL isReference
   ) throw(...)
```

#### <a name="parameters"></a>매개 변수

*inptr*<br/>
다형 개체에 대한 포인터입니다.

*VfDelta*<br/>
개체 내 가상 함수 포인터의 오프셋입니다.

*SrcType*<br/>
`inptr` 매개 변수가 가리키는 개체의 정적 형식입니다.

*TargetType*<br/>
캐스트의 의도된 결과입니다.

*isReference*<br/>
입력이 참조인 경우 **true**이고, 입력이 포인터인 경우 **false** 입니다.

## <a name="return-value"></a>반환 값

성공한 경우 적절한 하위 개체에 대한 포인터입니다. 그렇지 않으면 **NULL**입니다.

## <a name="exceptions"></a>예외

`bad_cast()`에 대한 입력이 참조이고 캐스팅이 실패한 경우 `dynamic_cast<>`입니다.

## <a name="remarks"></a>설명

`inptr`을 `TargetType` 형식의 개체로 변환합니다. `TargetType`이 포인터인 경우 `inptr`의 형식은 포인터여야 하며 `TargetType`이 참조인 경우에는 l 값이어야 합니다. `TargetType`은 포인터, 이전에 정의한 클래스 형식에 대한 참조 또는 void에 대한 포인터여야 합니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__RTDynamicCast|rtti.h|