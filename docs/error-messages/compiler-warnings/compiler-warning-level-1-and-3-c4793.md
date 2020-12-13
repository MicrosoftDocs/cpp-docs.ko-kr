---
description: '자세한 정보: 컴파일러 경고 (수준 1 및 3) C4793'
title: 컴파일러 경고(수준 1 및 3) C4793
ms.date: 11/04/2016
f1_keywords:
- C4793
helpviewer_keywords:
- C6634
- C6635
- C6640
- C6630
- C6639
- C6636
- C6638
- C6631
- C6637
- C4793
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
ms.openlocfilehash: 00d8a8c3c0537b1960ee287b2ec5fea25491d87e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336027"
---
# <a name="compiler-warning-level-1-and-3-c4793"></a>컴파일러 경고(수준 1 및 3) C4793

> '*function*': 함수가 네이티브 코드로 컴파일 되었습니다. '*reason*'

## <a name="remarks"></a>설명

[/Clr](../../build/reference/clr-common-language-runtime-compilation.md) 컴파일러 옵션이 지정 된 경우에도 컴파일러는 *함수* 를 관리 코드로 컴파일할 수 없습니다. 대신 컴파일러는 경고 C4793 및 설명 연속 메시지를 내보낸 다음 *함수* 를 네이티브 코드로 컴파일합니다. 연속 메시지는 *함수* 를 컴파일할 수 없는 이유에 대해 설명 하는 *이유* 텍스트를 포함 합니다 `MSIL` .

**/Clr: pure** 컴파일러 옵션을 지정 하는 경우이는 수준 1 경고입니다.  **/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

다음 표에서는 가능한 연속 메시지를 모두 나열 합니다.

|이유 메시지|설명|
|--------------------|-------------|
|관리 코드에서는 정렬 된 데이터 형식이 지원 되지 않습니다.|CLR은 필요에 따라 데이터를 할당할 수 있어야 합니다 .이는 데이터를 [__m128](../../cpp/m128.md) 또는 [align](../../cpp/align-cpp.md)과 같은 선언에 정렬 하는 경우에는 불가능 합니다.|
|' __ImageBase '를 사용 하는 함수는 관리 코드에서 지원 되지 않습니다.|`__ImageBase` 는 일반적으로 하위 수준 네이티브 코드 에서만 DLL을 로드 하는 데 사용 되는 특수 링커 기호입니다.|
|'/clr ' 컴파일러 옵션은 varargs를 지원 하지 않습니다.|함수의 스택 레이아웃 요구 사항이 서로 다르므로 네이티브 함수는 [가변 인수 목록](../../cpp/functions-with-variable-argument-lists-cpp.md) (varargs)을 가진 관리 되는 함수를 호출할 수 없습니다. 그러나 **/clr: pure** 컴파일러 옵션을 지정 하는 경우 어셈블리에 관리 되는 함수만 포함 될 수 있으므로 가변 인수 목록이 지원 됩니다. 자세한 내용은 [순수형 및 안정형 코드 (c + +/cli)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)를 참조 하세요.|
|64 비트 CLR은 __ptr32 한정자로 선언 된 데이터를 지원 하지 않습니다.|포인터는 현재 플랫폼의 네이티브 포인터와 크기가 같아야 합니다. 자세한 내용은 [__ptr32, \_ _ptr64을](../../cpp/ptr32-ptr64.md)참조 하세요.|
|32 비트 CLR은 __ptr64 한정자로 선언 된 데이터를 지원 하지 않습니다.|포인터는 현재 플랫폼의 네이티브 포인터와 크기가 같아야 합니다. 자세한 내용은 [__ptr32, \_ _ptr64을](../../cpp/ptr32-ptr64.md)참조 하세요.|
|하나 이상의 내장 함수는 관리 코드에서 지원 되지 않습니다.|내장 함수 이름은 메시지를 내보낼 때 사용할 수 없습니다. 그러나이 메시지를 발생 시키는 내장 함수는 일반적으로 하위 수준 컴퓨터 명령을 나타냅니다.|
|관리 코드에서는 인라인 네이티브 어셈블리 (' __asm ')가 지원 되지 않습니다.|[인라인 어셈블리 코드](../../assembler/inline/asm.md) 는 관리할 수 없는 임의의 네이티브 코드를 포함할 수 있습니다.|
|__Clrcall 아닌 가상 함수 썽크는 네이티브로 컴파일해야 합니다.|[__Clrcall](../../cpp/clrcall.md) 되지 않은 가상 함수 썽크는 관리 되지 않는 주소를 사용 해야 합니다.|
|' _Setjmp '를 사용 하는 함수는 네이티브로 컴파일해야 합니다.|CLR에서 프로그램 실행을 제어할 수 있어야 합니다. 그러나 [setjmp](../../cpp/using-setjmp-longjmp.md) 함수는 레지스터 및 실행 상태와 같은 하위 수준 정보를 저장 하 고 복원 하 여 일반 프로그램 실행을 무시 합니다.|

## <a name="example"></a>예제

다음 샘플에서는 C4793를 생성 합니다.

```cpp
// C4793.cpp
// compile with: /c /clr /W3
// processor: x86
int asmfunc(void) {   // C4793, compiled as unmanaged, native code
   __asm {
      mov eax, 0
   }
}
```

```Output
warning C4793: 'asmfunc' : function is compiled as native code:
        Inline native assembly ('__asm') is not supported in managed code
```

다음 샘플에서는 C4793를 생성 합니다.

```cpp
// C4793_b.cpp
// compile with: /c /clr /W3
#include <setjmp.h>
jmp_buf test_buf;

void f() {
   setjmp(test_buf);   // C4793 warning
}
```

```Output
warning C4793: 'f' : function is compiled as native code:
        A function using '_setjmp' must be compiled as native
```
