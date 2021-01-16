---
description: '다음에 대 한 자세한 정보: __pctype_func'
title: __pctype_func
ms.date: 1/14/2021
api_name:
- __pctype_func
- _o___pctype_func
api_location:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- api-ms-win-crt-private-l1-1-0.dll
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __pctype_func
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
ms.openlocfilehash: 492f4a4c6ff5a23c05c15267d7ac00f72bc6eb94
ms.sourcegitcommit: 1cd8f8a75fd036ffa57bc70f3ca869042d8019d4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2021
ms.locfileid: "98242958"
---
# <a name="__pctype_func"></a>__pctype_func

문자 분류 정보 배열에 대한 포인터를 검색합니다.

## <a name="syntax"></a>구문

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>Return Value

문자 분류 정보 배열에 대한 포인터입니다.

## <a name="remarks"></a>설명

문자 분류 테이블의 정보는 내부 전용 이며, 형식의 문자를 분류 하는 다양 한 함수에 사용 됩니다 **`char`** . 자세한 내용은 [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)의 `Remarks` 섹션을 참조하세요.

기본적으로이 함수의 전역 상태는 응용 프로그램으로 범위가 지정 됩니다. 이를 변경 하려면 [CRT의 전역 상태](global-state.md)를 참조 하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>참고 항목

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)
