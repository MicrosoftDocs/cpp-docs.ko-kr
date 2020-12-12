---
description: '자세한 정보: 컴파일러 오류 C2268'
title: 컴파일러 오류 C2268
ms.date: 11/04/2016
f1_keywords:
- C2268
helpviewer_keywords:
- C2268
ms.assetid: 0ed055c9-3c6f-4df2-a5b6-85cf0e01a249
ms.openlocfilehash: 2ce70c43cc9365aebdf8441b916715ac67731c49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295044"
---
# <a name="compiler-error-c2268"></a>컴파일러 오류 C2268

'function'은 컴파일러에서 미리 정의한 라이브러리 도우미입니다. /GL 옵션을 지정하면 라이브러리 도우미가 지원되지 않습니다. /GL을 지정하지 않고 개체 파일 'file'을 컴파일하세요.

소스 코드에 정의된 함수가 내부 컴파일러 함수와 이름이 같습니다. [/GL](../../build/reference/gl-whole-program-optimization.md)없이 함수를 포함하는 모듈을 컴파일합니다.

다음 샘플에서는 C2268을 생성합니다.

```c
// C2268.c
// compile with: /c
// processor: x86
extern int SHFusionLoadLibrary(int lpLibFileName);

int __cdecl _except_handler3(void) {
   return SHFusionLoadLibrary(0);
}

extern int main(void);

void* mainCRTStartup(void* p) {
   p = main;
   return p;
}
```

그리고

```c
// C2268b.c
// compile with: C2268.c /EHsc /GL /Ob0 /O2 /Fa /GS- /link /nodefaultlib
// processor: x86
extern int SHFusionLoadLibrary(int lpLibFileName);

extern int __cdecl _except_handler3(void);
extern void mainCRTStartup(void*);
int g = 2;

#define ENTERCONTEXT(fail) \
   int ulCookie = 0;\
   if (!SHActivateContext(&ulCookie)) \
      return fail;\
   __try {

#define LEAVECONTEXT \
    } __finally {SHDeactivateContext(ulCookie);}

int SHActivateContext(int* a) {
    return *a == g || !*a ||_except_handler3();
}

void SHDeactivateContext(int a) {
    g = a;
}

int SHFusionLoadLibrary(int lpLibFileName) {   // C2268
    ENTERCONTEXT(0)
    g = lpLibFileName;
    LEAVECONTEXT

    return lpLibFileName;
}

int main(void) {
    g = SHFusionLoadLibrary(10);
    return 0;
}
```
