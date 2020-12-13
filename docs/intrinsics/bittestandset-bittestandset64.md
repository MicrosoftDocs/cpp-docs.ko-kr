---
description: '자세히 알아보기: _bittestandset, _bittestandset64'
title: _bittestandset, _bittestandset64
ms.date: 09/02/2019
f1_keywords:
- _bittestandset_cpp
- _bittestandset64_cpp
- _bittestandset64
- _bittestandset
helpviewer_keywords:
- bts instruction
- _bittestandset intrinsic
- _bittestandset64 intrinsic
ms.assetid: 6d6c8670-fea0-4c1c-9aad-2bb842715203
ms.openlocfilehash: 69d1c8569a228ed4994343e12ef769710bd06ad5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337150"
---
# <a name="_bittestandset-_bittestandset64"></a>_bittestandset, _bittestandset64

**Microsoft 전용**

주소의 비트를 검사 하 `b` `a` 고 현재 값을 반환 하 고 비트를 1로 설정 하는 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
unsigned char _bittestandset(
   long *a,
   long b
);
unsigned char _bittestandset64(
   __int64 *a,
   __int64 b
);
```

### <a name="parameters"></a>매개 변수

*은*\
[in, out] 검사할 메모리에 대 한 포인터입니다.

*b*\
진행 테스트할 비트 위치입니다.

## <a name="return-value"></a>반환 값

지정한 위치에 있는 비트입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`_bittestandset`|x86, ARM, x64, ARM64|
|`_bittestandset64`|x64, ARM64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```cpp
// bittestandset.cpp
// processor: x86, ARM, x64
// This example uses several of the _bittest family of intrinsics
// to implement a Flags class that allows bit level access to an
// integer field.
#include <stdio.h>
#include <intrin.h>

#pragma intrinsic(_bittestandset, _bittestandreset,\
                  _bittestandcomplement, _bittest)

class Flags
{
private:
    long flags;
    long* oldValues;

public:
    Flags() : flags(0)
    {
        oldValues = new long[32];
    }

    ~Flags()
    {
        delete oldValues;
    }

    void SetFlagBit(long nBit)
    {
        // We omit range checks on the argument
        oldValues[nBit] = _bittestandset(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
    }
    void ClearFlagBit(long nBit)
    {
        oldValues[nBit] = _bittestandreset(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
    }
    unsigned char GetFlagBit(long nBit)
    {
        unsigned char result = _bittest(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
        return result;
    }
    void RestoreFlagBit(long nBit)
    {
        if (oldValues[nBit])
            oldValues[nBit] = _bittestandset(&flags, nBit);
        else
            oldValues[nBit] = _bittestandreset(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
    }
    unsigned char ToggleBit(long nBit)
    {
        unsigned char result = _bittestandcomplement(&flags, nBit);
        printf_s("Flags: 0x%x\n", flags);
        return result;
    }
};

int main()
{
    Flags f;
    f.SetFlagBit(1);
    f.SetFlagBit(2);
    f.SetFlagBit(3);
    f.ClearFlagBit(3);
    f.ToggleBit(1);
    f.RestoreFlagBit(2);
}
```

```Output
Flags: 0x2
Flags: 0x6
Flags: 0xe
Flags: 0x6
Flags: 0x4
Flags: 0x0
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
