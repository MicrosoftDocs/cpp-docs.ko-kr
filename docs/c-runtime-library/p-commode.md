---
title: __p__commode
ms.date: 11/04/2016
apiname:
- __p__commode
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __p__commode
helpviewer_keywords:
- __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
ms.openlocfilehash: 3a565a179077635438c03539cefa83823603bb00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482705"
---
# <a name="pcommode"></a>__p__commode

파일 I/O 연산에 대한 기본 *파일 커밋 모드*를 지정하는 `_commode` 전역 변수에 대한 포인터입니다.

## <a name="syntax"></a>구문

```cpp
int * __p__commode(
   );
```

## <a name="return-value"></a>반환 값

`_commode` 전역 변수에 대한 포인터입니다.

## <a name="remarks"></a>설명

`__p__commode` 함수는 내부용이며 사용자 코드에서 호출할 수 없습니다.

파일 커밋 모드에서는 중요한 데이터를 디스크에 쓰는 시기를 지정합니다. 자세한 내용은 [fflush](../c-runtime-library/reference/fflush.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|
|-------------|---------------------|
|__p\__commode|internal.h|