---
description: '다음에 대 한 자세한 정보: __debugbreak'
title: __debugbreak
ms.date: 09/02/2019
f1_keywords:
- __debugbreak_cpp
- __debugbreak
helpviewer_keywords:
- breakpoints, __debugbreak intrinsic
- __debugbreak intrinsic
ms.assetid: 1d1e1c0c-891a-4613-ae4b-d790094ba830
ms.openlocfilehash: 83a670d9fa9c1f6b41c1c405c59af71c7aa0c8a1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337107"
---
# <a name="__debugbreak"></a>__debugbreak

**Microsoft 전용**

코드에서 중단점이 발생하며 사용자에게 디버거를 실행하라는 메시지가 표시됩니다.

## <a name="syntax"></a>Syntax

```C
void __debugbreak();
```

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|헤더|
|---------------|------------------|------------|
|`__debugbreak`|x86, x64, ARM, ARM64|\<intrin.h>|

## <a name="remarks"></a>설명

`__debugbreak` [Debugbreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak)와 유사한 컴파일러 내장 함수는 중단점을 발생 시키는 이식 가능한 Win32 방법입니다.

> [!NOTE]
> **/Clr** 을 사용 하 여 컴파일하는 경우를 포함 하는 함수가 `__debugbreak` MSIL로 컴파일됩니다. `asm int 3`은 함수를 네이티브로 컴파일하도록 합니다. 자세한 내용은 [__asm](../assembler/inline/asm.md)를 참조 하세요.

예를 들어:

```C
main() {
   __debugbreak();
}
```

위의 예는 아래 예와 유사합니다.

```C
main() {
   __asm {
      int 3
   }
}
```

x86 컴퓨터의 경우

ARM64에서 `__debugbreak` 내장 함수는 명령으로 컴파일됩니다 `brk #0xF000` .

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[키워드](../cpp/keywords-cpp.md)
