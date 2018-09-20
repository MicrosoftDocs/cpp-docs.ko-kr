---
title: _AddressOfReturnAddress | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- _AddressOfReturnAddress_cpp
- _AddressOfReturnAddress
dev_langs:
- C++
helpviewer_keywords:
- _AddressOfReturnAddress intrinsic
- AddressOfReturnAddress intrinsic
ms.assetid: c7e10b8c-445e-4236-a602-e2d90200f70a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 694b9fead94bee55e1337df9511f59237ed88b57
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425810"
---
# <a name="addressofreturnaddress"></a>_AddressOfReturnAddress

**Microsoft 전용**

현재 함수의 반환 주소를 보유 하는 메모리 위치의 주소를 제공 합니다. 다른 메모리 위치 (예: 함수의 인수)에 액세스 하려면이 주소를 사용할 수 있습니다.

## <a name="syntax"></a>구문

```
void * _AddressOfReturnAddress();
```

## <a name="requirements"></a>요구 사항

|내장 함수|아키텍처|
|---------------|------------------|
|`_AddressOfReturnAddress`|x86, x64|

**헤더 파일** \<intrin.h >

## <a name="remarks"></a>설명

때 `_AddressOfReturnAddress` 로 컴파일된 프로그램에서 사용 됩니다 [/clr](../build/reference/clr-common-language-runtime-compilation.md)를 포함 하는 함수는 `_AddressOfReturnAddress` 네이티브 함수로 호출 컴파일됩니다. 포함 하는 함수에 대 한 호출은 관리 되는 함수를 컴파일할 때 `_AddressOfReturnAddress`, `_AddressOfReturnAddress` 예상 대로 작동 하지 않을 수 있습니다.

이 루틴은 내장 루틴으로만 사용할 수 있습니다.

## <a name="example"></a>예제

```
// compiler_intrinsics_AddressOfReturnAddress.cpp
// processor: x86, x64
#include <stdio.h>
#include <intrin.h>

// This function will print three values:
//   (1) The address retrieved from _AddressOfReturnAdress
//   (2) The return address stored at the location returned in (1)
//   (3) The return address retrieved the _ReturnAddress* intrinsic
// Note that (2) and (3) should be the same address.
__declspec(noinline)
void func() {
   void* pvAddressOfReturnAddress = _AddressOfReturnAddress();
   printf_s("%p\n", pvAddressOfReturnAddress);
   printf_s("%p\n", *((void**) pvAddressOfReturnAddress));
   printf_s("%p\n", _ReturnAddress());
}

int main() {
   func();
}
```

```Output
0012FF78
00401058
00401058
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)<br/>
[키워드](../cpp/keywords-cpp.md)