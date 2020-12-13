---
description: '자세한 정보: __writegsbyte, __writegsdword, __writegsqword, __writegsword'
title: __writegsbyte, __writegsdword, __writegsqword, __writegsword
ms.date: 09/02/2019
f1_keywords:
- __writegsbyte
- __writegsqword
- __writegsdword
- __writegsword
helpviewer_keywords:
- __writegsqword intrinsic
- __writegsbyte intrinsic
- __writegsword intrinsic
- __writegsdword intrinsic
ms.assetid: 7746cf6d-2259-4139-9aab-c07dd75c8037
ms.openlocfilehash: e3dd3284d38f4c1518fbf5f7184d15fc0c9d67d0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331837"
---
# <a name="__writegsbyte-__writegsdword-__writegsqword-__writegsword"></a>__writegsbyte, __writegsdword, __writegsqword, __writegsword

**Microsoft 전용**

GS 세그먼트의 시작을 기준으로 하는 오프셋으로 지정 된 위치에 메모리를 씁니다.

## <a name="syntax"></a>구문

```C
void __writegsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writegsword(
   unsigned long Offset,
   unsigned short Data
);
void __writegsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writegsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>매개 변수

*이동*\
진행 쓸 GS의 시작 부분에서의 오프셋입니다.

*데이터*\
진행 쓸 값입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__writegsbyte`|X64|
|`__writegsdword`|X64|
|`__writegsqword`|X64|
|`__writegsword`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[__readgsbyte, \_ _readgsdword, \_ _readgsqword, \_ _readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
