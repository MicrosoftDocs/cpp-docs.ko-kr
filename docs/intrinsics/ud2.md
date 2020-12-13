---
description: '다음에 대 한 자세한 정보: __ud2'
title: __ud2
ms.date: 09/02/2019
f1_keywords:
- __ud2
helpviewer_keywords:
- UD2 instruction
- __ud2 intrinsic
ms.assetid: 0831cd5a-8b65-402e-bb57-11e1d5d7ffd2
ms.openlocfilehash: 2b5f0b9ffec066baa3eb2fa212dfc7baf3a6cb49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333661"
---
# <a name="__ud2"></a>__ud2

**Microsoft 전용**

정의 되지 않은 명령을 생성 합니다.

## <a name="syntax"></a>구문

```C
void __ud2();
```

## <a name="remarks"></a>설명

정의 되지 않은 명령을 실행 하는 경우 프로세서가 잘못 된 opcode 예외를 발생 시킵니다.

`__ud2`함수는 `UD2` 컴퓨터 명령과 같으며 커널 모드 에서만 사용할 수 있습니다. 자세한 내용을 보려면 [Intel Corporation](https://software.intel.com/articles/intel-sdm) 사이트에서 "Intel 아키텍처 소프트웨어 개발자 설명서, 볼륨 2: 명령 집합 참조" 문서를 검색 하십시오.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__ud2`|x86, x64|

**헤더 파일** \<intrin.h>

**Microsoft 전용 종료**

## <a name="example"></a>예제

다음 예제에서는 예외를 발생 시키는 정의 되지 않은 명령을 실행 합니다. 그런 다음 예외 처리기는 반환 코드를 0에서 1로 변경 합니다.

```cpp
// __ud2_intrinsic.cpp
#include <stdio.h>
#include <intrin.h>
#include <excpt.h>
// compile with /EHa

int main() {

// Initialize the return code to 0.
int ret = 0;

// Attempt to execute an undefined instruction.
  printf("Before __ud2(). Return code = %d.\n", ret);
  __try {
  __ud2();
  }

// Catch any exceptions and set the return code to 1.
  __except(EXCEPTION_EXECUTE_HANDLER){
  printf("  In the exception handler.\n");
  ret = 1;
  }

// Report the value of the return code.
  printf("After __ud2().  Return code = %d.\n", ret);
  return ret;
}
```

```Output
Before __ud2(). Return code = 0.
  In the exception handler.
After __ud2().  Return code = 1.
```

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
