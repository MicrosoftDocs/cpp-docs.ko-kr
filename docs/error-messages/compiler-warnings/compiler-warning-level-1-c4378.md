---
title: 컴파일러 경고 (수준 1) C4378
ms.date: 11/04/2016
f1_keywords:
- C4378
helpviewer_keywords:
- C4378
ms.assetid: d08e11ef-891a-4752-9a5e-360e7394acf7
ms.openlocfilehash: cc5e5365ffb53125085ce7b374f1362e93f4bb03
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966490"
---
# <a name="compiler-warning-level-1-c4378"></a>컴파일러 경고 (수준 1) C4378

이니셜라이저를 실행 하려면 함수 포인터를 가져와야 합니다. System:: ModuleHandle:: ResolveMethodHandle을 고려 합니다.

**/Clr**에서 이니셜라이저 기호에는 함수 포인터가 아닌 함수 토큰이 포함 되어 있습니다.  <xref:System.ModuleHandle.ResolveMethodHandle%2A>를 사용 하 여 토큰을 포인터로 변환 해야 합니다.

## <a name="example"></a>예제

다음 샘플에서는 C4378를 생성 합니다.

```cpp
// C4378.cpp
// compile with: /W1 /clr /c
typedef void (__cdecl *PF)(void);
int cxpf = 0;   // number of destructors to call
PF pfx[200];   // ptrs to those dtors, watch for overflow

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() {}
   ~A() {}
};

A aaaa;

#pragma data_seg(".mine$a")
PF InitSegStart = (PF)1;
#pragma data_seg(".mine$z")
PF InitSegEnd = (PF)1;
#pragma data_seg()

void InitializeObjects () {
   PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if (*x)
         (*x)();
}

#pragma init_seg(".mine$m",myexit)   // C4378
A bbbb;   // crash

int main () {
   InitializeObjects();
}
```

## <a name="example"></a>예제

다음 샘플에서는 C4378를 해결 하는 방법을 보여 줍니다.

```cpp
// C4378_b.cpp
// compile with: /clr
#pragma warning(disable:4378)
using namespace System;
typedef void (__cdecl *PF)(void);
typedef void (__clrcall * CLRPF)(void);

int cxpf = 0;  // number of destructors we need to call
PF pfx[200];   // ptrs to those dtors. Watch out for overflow!

ref class TypeClassHolder {
public:
   static TypeClassHolder ^typeClass = gcnew TypeClassHolder();
};

CLRPF FuncTokenToFuncPtr(PF tknFunc) {
   ModuleHandle type =
      Type::GetTypeFromHandle(Type::GetTypeHandle(TypeClassHolder::typeClass))->Module->ModuleHandle;
   return (CLRPF)type.ResolveMethodHandle((int)(size_t)(tknFunc)).GetFunctionPointer().ToPointer();
}

int myexit (PF pf) {
   pfx[cxpf++] = pf;
   return 0;
}

struct A {
   A() {}
   ~A() {}
};

A aaaa;

#pragma data_seg(".mine$a")
PF InitSegStart = (PF)1;
#pragma data_seg(".mine$z")
PF InitSegEnd = (PF)1;
#pragma data_seg()

void InitializeObjects () {
   PF *x = &InitSegStart;
   for (++x ; x < &InitSegEnd ; ++x)
      if(*x) {
         CLRPF realppfunc;
         realppfunc = FuncTokenToFuncPtr(*x);
         (realppfunc)();
      }
}

#pragma init_seg(".mine$m",myexit)
A bbbb; // constructor call succeeds

int main () {
   InitializeObjects();
}
```