---
description: '자세히 알아보기: offsetof 매크로'
title: offsetof 매크로
ms.date: 11/04/2016
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: 055bda67bae178143561acd91b517c431f77cac0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97256271"
---
# <a name="offsetof-macro"></a>offsetof 매크로

부모 구조의 시작 부분에서 멤버의 오프셋을 검색합니다.

## <a name="syntax"></a>구문

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>매개 변수

*structName*<br/>
부모 데이터 구조의 이름입니다.

*memberName*<br/>
부모 데이터 구조에서 오프셋을 결정할 멤버의 이름입니다.

## <a name="return-value"></a>반환 값

**offsetof** 는 부모 데이터 구조의 시작 부분에서 지정 된 멤버의 오프셋 (바이트)을 반환 합니다. 이는 비트 필드의 경우 정의되지 않습니다.

## <a name="remarks"></a>설명

**Offsetof** 매크로는 *structName* 에 의해 지정 된 구조의 시작 부분에서 **size_t** 형식 값으로 *memberName* 의 오프셋 (바이트)을 반환 합니다. 키워드를 사용 하 여 형식을 지정할 수 있습니다 **`struct`** .

> [!NOTE]
> **offsetof** 는 함수가 아니므로 C 프로토타입을 사용 하 여 설명할 수 없습니다.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="libraries"></a>라이브러리

모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.

## <a name="see-also"></a>참고 항목

[메모리 할당](../../c-runtime-library/memory-allocation.md)<br/>
