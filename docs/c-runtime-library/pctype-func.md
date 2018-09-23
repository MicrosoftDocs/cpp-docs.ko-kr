---
title: __pctype_func | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __pctype_func
apilocation:
- msvcrt.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- __pctype_func
dev_langs:
- C++
helpviewer_keywords:
- __pctype_func
ms.assetid: d52b8add-d07d-4516-a22f-e836cde0c57f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 36c8dd0467dc50c9eba9db954f28711aa8525cd2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46034293"
---
# <a name="pctypefunc"></a>__pctype_func

문자 분류 정보 배열에 대한 포인터를 검색합니다.

## <a name="syntax"></a>구문

```cpp
const unsigned short *__pctype_func(
   )
```

## <a name="return-value"></a>반환 값

문자 분류 정보 배열에 대한 포인터입니다.

## <a name="remarks"></a>설명

문자 분류 테이블의 정보는 내부 전용이며, `char` 형식의 문자를 분류하는 다양한 함수에 사용됩니다. 자세한 내용은 [_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)의 `Remarks` 섹션을 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__pctype_func|ctype.h|

## <a name="see-also"></a>참고 항목

[_pctype, _pwctype, _wctype, _mbctype, _mbcasemap](../c-runtime-library/pctype-pwctype-wctype-mbctype-mbcasemap.md)