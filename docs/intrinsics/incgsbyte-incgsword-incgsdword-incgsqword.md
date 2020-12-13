---
description: '자세한 정보: __incgsbyte, __incgsword, __incgsdword, __incgsqword'
title: __incgsbyte, __incgsword, __incgsdword, __incgsqword
ms.date: 09/02/2019
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
ms.openlocfilehash: a19c266c936875765c5681a47845be1a53f18c83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336938"
---
# <a name="__incgsbyte-__incgsword-__incgsdword-__incgsqword"></a>__incgsbyte, __incgsword, __incgsdword, __incgsqword

**Microsoft 전용**

세그먼트의 시작을 기준으로 하는 오프셋으로 지정 된 메모리 위치에 있는 값에 하나를 추가 `GS` 합니다.

## <a name="syntax"></a>구문

```C
void __incgsbyte(
   unsigned long Offset
);
void __incgsword(
   unsigned long Offset
);
void __incgsdword(
   unsigned long Offset
);
void __incgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>매개 변수

*이동*\
진행 의 시작 부분부터의 오프셋 `GS` 입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__incgsbyte`|X64|
|`__incgsword`|X64|
|`__incgsdword`|X64|
|`__incgsqword`|X64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이러한 루틴은 내장 함수로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[\__addgsbyte, \_ _addgsword, \_ _addgsdword, \_ _addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)\
[\__readgsbyte, \_ _readgsdword, \_ _readgsqword, \_ _readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[\__writegsbyte, \_ _writegsdword, \_ _writegsqword, \_ _writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
