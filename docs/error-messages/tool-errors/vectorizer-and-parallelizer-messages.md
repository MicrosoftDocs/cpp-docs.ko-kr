---
description: '자세한 정보: 벡터화 및 평행 화 도우미 메시지'
title: 벡터화 도우미 및 병렬화 도우미 메시지
ms.date: 02/16/2021
f1_keywords:
- C5011
- C5002
- C5021
- C5001
- C5012
ms.openlocfilehash: 9cfafe9af4859a2bb4dbd7897a14003d85052f63
ms.sourcegitcommit: 5efc34c2b98d4d0d3e41aec38b213f062c19d078
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844548"
---
# <a name="vectorizer-and-parallelizer-messages"></a>벡터화 도우미 및 병렬화 도우미 메시지

Microsoft c + + 컴파일러 옵션을 사용 하 여 [`/Qpar-report`](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md) [`/Qvec-report`](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md) [자동 병렬화 및 자동 벡터화](../../parallel/auto-parallelization-and-auto-vectorization.md) 를 설정 하 여 해당 활동에 대 한 이유 코드 및 정보 메시지를 출력할 수 있습니다. 이 문서는 이유 코드 및 메시지를 설명합니다.

## <a name="informational-messages"></a><a name="BKMK_InformationalMessages"></a> 정보 메시지

지정한 보고 수준에 따라 각 루프에 대해 다음과 같은 정보 메시지 중 하나가 표시됩니다.

이유 코드에 대한 정보는 이 문서의 다음 부분을 참조하십시오.

| 정보 메시지 | Description |
|--|--|
| 5001 | 루프가 벡터화되었습니다. |
| 5002 | '*Description*' 때문에 루프가 벡터화 되지 않습니다. |
| 5011 | 루프가 병렬화되었습니다. |
| 5012 | '*Description*' 이유로 인해 루프가 병렬화 되지 않았습니다. |
| 5021 | Pragma를 사용하여 루프를 연결할 수 없습니다. |

다음 섹션에서는 평행 화 도우미 및 벡터화에 대 한 가능한 이유 코드를 나열 합니다.

## <a name="5xx-reason-codes"></a><a name="BKMK_ReasonCode50x"></a> 5xx 이유 코드

5 *xx* 이유 코드는 평행 화 도우미 및 벡터화에 모두 적용 됩니다.

| 이유 코드 | 설명 |
|--|--|
| 500 | 여러 가지 사례를 포함 하는 일반 메시지: 예를 들어 루프가 여러 번 종료 되거나, 루프 헤더가 유도 변수를 증가 시켜 끝나지 않습니다. |
| 501 | 유도 변수가 로컬이 아닙니다. 또는 상한이 루프 고정이 아닙니다. |
| 502 | 유도 변수는 단순한 +1 이외의 다른 방법으로도 실행됩니다. |
| 503 | 루프는 예외 처리 또는 switch 문을 포함합니다. |
| 504 | 루프 본문은 C++ 개체의 소멸을 요구하는 예외를 던질 수 있습니다. |
| 505 | 외부 루프에는 미리 증가 된 유도 변수가 있습니다. 분석 종료. |

```cpp
void code_500(int *A)
{
    // Code 500 is emitted if the loop has non-vectorizable flow.
    // This can include "if", "break", "continue", the conditional
    // operator "?", or function calls.
    // It also encompasses correct definition and use of the induction
    // variable "i", in that the increment "++i" or "i++" must be the last
    // statement in the loop.

    int i = 0;
    while (i<1000)
    {
        if (i == 4)
        {
            break;
        }

        ++i;

        A[i] = A[i] + 1;
    }
    // To resolve code 500, use a 'for' loop with single increment of
    // induction variable.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

int bound();
void code_501_example1(int *A)
{
    // Code 501 is emitted if the compiler cannot discern the
    // induction variable of this loop. In this case, when it checks
    // the upper bound of 'i', the compiler cannot prove that the
    // function call "bound()" returns the same value each time.
    // Also, the compiler cannot prove that the call to "bound()"
    // does not modify the values of array A.

    for (int i=0; i<bound(); ++i)
    {
        A[i] = A[i] + 1;
    }

    // To resolve code 501, ensure that the induction variable is
    // a local variable, and ensure that the upper bound is a
    // provably loop invariant value.

    for (int i=0, imax = bound(); i<imax; ++i)
    {
        A[i] = A[i] + 1;
    }
}

int i;
void code_501_example2(int *A)
{
    // Code 501 is emitted if the compiler cannot discern the
    // induction variable of this loop. In this case, 'i' is
    // a global.

    for (i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }

    // To resolve code 501, ensure that the induction variable is
    // a local variable, and ensure that the upper bound is a
    // provably loop invariant value.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_502(int *A)
{
    // Code 502 is emitted if the compiler cannot discern
    // the induction variable of the loop. In this case,
    // there are three increments to "i", one of which
    // is conditional.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
        ++i;

        if (i < 100)
        {
            ++i;
        }
    }

    // To resolve code 502, ensure that there is just one
    // increment of the induction variable, placed in the usual
    // spot in the "for" loop.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_503(int *A, int x)
{
    // Code 503 is emitted if there are inadmissible
    // operations in the loop - for example, exception handling and
    // switch statements.

    for (int i = 0; i<1000; ++i)
    {
        switch (x)
        {
        case 1: A[i] = A[i] + 1;
        case 2: A[i] = A[i] + 2;
        case 3: A[i] = A[i] + 3;
            break;
        }
    }

    // To resolve code 503, try to remove as many switch statements
    // and exception handling constructs as possible.
}

// compile with /EHsc

int code_504_helper();
class C504
{
public:
    C504();
    ~C504();
};

void code_504(int *A)
{
    // Code 504 is emitted if a C++ object was created and
    // that object requires EH unwind tracking information under
    // /EHs or /EHsc.

    for(int i = 0; i < 1000; ++i)
    {
        C504 c;
        A[i] = code_504_helper();
    }

}

void code_505(int *A)
{
    // Code 505 is emitted on outer loops with pre-incremented
    // induction variables. The vectorizer/parallelizer analysis
    // package doesn't support these loops, and they are
    // intentionally not converted to post-increment loops to
    // prevent a performance degradation.

    // To parallelize an outer loop that causes code 505, change
    // it to a post-incremented loop.

    for (int i=100; i--; )
        for (int j=0; j<100; j++) { // this loop is still vectorized
            A[j] = A[j] + 1;
        }                    
}
```

## <a name="10xx-reason-codes"></a><a name="BKMK_ReasonCode100x"></a> 10xx 이유 코드

10 *xx* 이유 코드는 평행 화 도우미에 적용 됩니다.

| 이유 코드 | 설명 |
|--|--|
| 1000 | 컴파일러가 루프 본문에서 데이터 종속성을 발견했습니다. |
| 1001 | 컴파일러가 루프 본문에서 스칼라 변수를 저장하고 해당 스칼라를 루프 외에서 사용하는 것을 발견했습니다. |
| 1002 | 컴파일러가 이미 병렬화된 내부 루프가 있는 루프를 병렬화하려 했습니다. |
| 1003 | 루프 본문이 메모리를 읽거나 쓰는 내장 호출을 포함합니다. |
| 1004 | 루프 본문에 스칼라 축소가 있습니다. 루프가 벡터화되면 스칼라 감소가 발생할 수 있습니다. |
| 1005 | `no_parallel`Pragma가 지정 되었습니다. |
| 1006 | 이 함수는 OpenMP를 포함 합니다. 이 함수에서 OpenMP를 제거 하 여 문제를 해결 합니다. |
| 1007 | Loop 유도 변수 또는 루프 범위는 32 비트 숫자 (또는)에 서명 되지 않습니다 `int` `long` . 유도 변수의 유형을 변경 하 여 문제를 해결 합니다. |
| 1008 | 컴파일러가이 루프에서 자동 병렬화를 정당화 하기에 충분 한 작업을 수행 하지 않음을 감지 했습니다. |
| 1009 | 컴파일러가 "" 루프를 병렬화 하려고 했습니다 `do` - `while` . 자동 평행 화 도우미는 "" 루프를 대상으로 `for` 합니다. |
| 1010 | 컴파일러가 루프에서 조건에 대해 "같지 않음" ()을 사용 하 고 있음을 감지 했습니다 `!=` . |

```cpp
int A[1000];
void func();
void code_1000()
{
    // Code 1000 is emitted if the compiler detects a
    // data dependence in the loop body.

    // You can resolve this by using the ivdep pragma.
    // CAUTION -- the compiler will trust your
    // assertion that there are no data dependencies
    // in the loop body. If there are, you are generating
    // code that may have race conditions.

#pragma loop(hint_parallel(0))
    //#pragma loop(ivdep) // ivdep will force this through.
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i-1] + 1;  // data dependence here
        func();             // data dependence here
    }
}

int code_1001()
{
    // Code 1001 is emitted if the compiler detects
    // a store to a scalar variable in the loop
    // body, and that scalar has a use beyond the loop.

    // Resolve this by rewriting your code so
    // that the scalar is not needed.

    int s = 0;
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i)
    {
        s = A[i];
    }
    return s;
}

void code_1002()
{
    // Code 1002 is emitted when the compiler tries to
    // parallelize a loop that has an inner loop that
    // has already been parallelized.

#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i) // emit code 1002 for this loop
    {
#pragma loop(hint_parallel(0))
        for (int j=0; j<1000; ++j) // this loop gets parallelized
        {
            A[j] = A[j] + 1;
        }
    }
}

extern "C" void __stosb(unsigned char*, unsigned char, size_t);
void code_1003(unsigned char *dst)
{
    // Code 1003 is emitted when the loop body contains an intrinsic
    // call that may read or write to memory.

    // This can be resolved by using the ivdep pragma.
    // CAUTION -- the compiler will trust your
    // assertion that there are no data dependencies
    // in the loop body. If there are, you are generating
    // code that may have race conditions.

#pragma loop(hint_parallel(0))
    //#pragma loop(ivdep) // ivdep will force this through.
    for (int i=0; i<1000; ++i)
    {
        __stosb(dst, 'c', 10);
        A[i] = A[i] + 1;
    }
}

int code_1004()
{
    // Code 1004 is emitted when there is a scalar reduction
    // in the loop body, which can occur if the loop has been
    // vectorized.

    // You can resolve this by rewriting your code so that it
    // does not have a scalar reduction.

    int s = 0;
#pragma loop(hint_parallel(0))
    for (int i=0; i<1000; ++i)
    {
        s += A[i];
    }
    return s;
}

void code_1005()
{
    // Code 1005 is emitted when the
    // no_parallel pragma is specified.

#pragma loop(no_parallel)
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

#include <omp.h>

// Compile with /openmp
void code_1006()
{
    // Code 1006 is emitted when this function contains
    // openmp. Resolve this by removing any openmp in this
    // function.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }

#pragma omp parallel num_threads(4)
    {
        int i = omp_get_thread_num();
        A[i] = A[i] + 1;
    }
}

void code_1007()
{
    // Code 1007 is emitted when the loop induction variable
    // or the loop bounds are not signed 32-bit numbers (int
    // or long). Resolve this by changing the type of the
    // induction variable.

#pragma loop(hint_parallel(0))
    for (unsigned int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_1008()
{
    // Code 1008 is emitted when the compiler detects that
    // this loop does not perform enough work to warrant
    // auto-parallelization.

    // You can resolve this by specifying the hint_parallel
    // pragma. CAUTION -- if the loop does not perform
    // enough work, parallelizing might cause a potentially
    // large performance penalty.

    // #pragma loop(hint_parallel(0)) //  hint_parallel will force this through
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

void code_1009()
{
    // Code 1009 is emitted when the compiler tries to parallelize a
    // "do-while" loop. The auto-parallelizer only targets "for" loops.

    int i = 0;
#pragma loop(hint_parallel(0))
    do
    {
        A[i] = A[i] + 1;
    }
    while (++i < 1000);
}

void code_1010()
{
    // Code 1010 is emitted when the compiler tries to parallelize a
    // loop with a condition code of "!=".

    // You can resolve this by replacing it with an ordering comparator
    // like "<".
#pragma loop(hint_parallel(0))
    for (int i = 0; i != 1000; ++i)
    {
        A[i]++;
    }
}
```

## <a name="11xx-reason-codes"></a><a name="BKMK_ReasonCode110x"></a> 11xx 이유 코드

11 *xx* 이유 코드는 벡터화에 적용 됩니다.

| 이유 코드 | 설명 |
|--|--|
| 1100 | 루프는 제어 흐름 (예: " `if` " 또는 "")을 포함 `?:` 합니다. |
| 1101 | 루프에는 벡터화 수 없는 암시적 데이터 형식 변환이 포함 되어 있습니다. |
| 1102 | 루프는 비산술적이거나 다른 비벡터화 작업을 포함합니다. |
| 1103 | 루프 본문이 루프 내에서 크기가 다를 수 있는 시프트 연산을 포함합니다. |
| 1104 | 루프 본문은 스칼라 변수를 포함합니다. |
| 1105 | 루프에 인식할 수 없는 감소 작업이 포함 되어 있습니다. |
| 1106 | 외부 루프는 벡터화되지 않습니다. |

```cpp
void code_1100(int *A, int x)
{
    // Code 1100 is emitted when the compiler detects control flow
    // in the loop - for example, "if", the ternary operator "?", and
    // the like. Resolve this by flattening or removing control
    // flow in the loop body.

    // Not all control flow causes 1100; some is indeed
    // vectorized.

    for (int i=0; i<1000; ++i)
    {
        // straight line code is more amenable to vectorization
        if (x)
        {
            A[i] = A[i] + 1;
        }
    }
}

extern "C" int __readcr0();
void code_1102(int *A)
{
    // Code 1102 is emitted when the compiler is unable to vectorize
    // an operation in the loop body. For example, intrinsics and other
    // non-arithmetic, non-logical, and non-memory operations are not
    // vectorizable.

    // Resolve this by removing as many non-vectorizable operations
    // as possible from the loop body.

    for (int i=0; i<1000; ++i)
    {
        A[i] = __readcr0();
    }
}

void code_1103(int *A, int *B)
{
    // Code 1103 is emitted when the compiler is unable to vectorize
    // a "shift" operation. In this example, there are two shifts
    // that cannot be vectorized.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] >> B[i]; // not vectorizable

        int x = B[i];
        A[i] = A[i] >> x; // not vectorizable
    }

    // To resolve this, ensure that your shift amounts are loop
    // invariant. If the shift amounts cannot be loop invariant,
    // it may not be possible to vectorize this loop.

    int x = B[0];
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] >> x; // vectorizable
    }
}

int code_1104(int *A, int *B)
{
    // When it vectorizes a loop, the compiler must 'expand' scalar
    // variables to a vector size such that they can fit in
    // vector registers. Code 1104 is emitted when the compiler
    // cannot 'expand' such scalars.

    // In this example, we try to 'expand' x to be used in the
    // vectorized loop. However, there is a use of 'x'
    // beyond the loop body, which prohibits this expansion.

    // To resolve this, try to limit scalars to be used only in
    // the loop body and not beyond, and try to keep their types
    // consistent with the loop types.

    int x;
    for (int i=0; i<1000; ++i)
    {
        x = B[i];
        A[i] = A[i] + x;
    }

    return x;
}

int code_1105(int *A)
{
    // The compiler performs an optimization that's known as "reduction"
    // when it operates on each element of an array and computes
    // a resulting scalar value - for example, in this piece of code, which
    // computes the sum of each element in the array:

    int s = 0;
    for (int i=0; i<1000; ++i)
    {
        s += A[i]; // vectorizable
    }

    // The reduction pattern must resemble the loop in the example. The
    // compiler emits code 1105 if it cannot deduce the reduction
    // pattern, as shown in this example:

    for (int i=0; i<1000; ++i)
    {
        s += A[i] + s;  // code 1105
    }

    // Similarly, reductions of "float" or "double" types require
    // that the /fp:fast switch is thrown. Strictly speaking,
    // the reduction optimization that the compiler performs uses
    // "floating point reassociation". Reassociation is only
    // allowed when /fp:fast is thrown.

    return s;
}

void code_1106(int *A)
{
    // Code 1106 is emitted when the compiler tries to vectorize
    // an outer loop.

    for (int i=0; i<1000; ++i) // this loop is not vectorized
    {
        for (int j=0; j<1000; ++j) // this loop is vectorized
        {
            A[j] = A[j] + 1;
        }
    }
}
```

## <a name="12xx-reason-codes"></a><a name="BKMK_ReasonCode120x"></a> 12xx 이유 코드

12 *xx* 이유 코드는 벡터화에 적용 됩니다.

| 이유 코드 | 설명 |
|--|--|
| 1200 | 루프에는 벡터화를 방지 하는 루프 전달 데이터 종속성이 포함 되어 있습니다. 루프의 각 반복이 서로 충돌 하 여 루프 벡터화에서 잘못 된 응답을 생성 하 고 자동 벡터화가 이러한 데이터 종속성이 없다는 것을 입증할 수 없습니다. |
| 1201 | 배열의 시작점이 루프 도중에 변경됩니다. |
| 1202 | 구조체의 필드는 32 또는 64 비트 너비가 아닙니다. |
| 1203 | 루프 본문이 연속되지 않은 배열 액세스를 포함합니다. |
| 1204 | 컴파일러 내부 데이터 구조 제한 적중: 데이터 종속성 가장자리가 너무 많습니다. |

```cpp
void fn();
void code_1200(int *A)
{
    // Code 1200 is emitted when data dependence is prohibiting
    // vectorization. This can only be resolved by rewriting the
    // loop, and considering the marking of loop function calls as
    // __forceinline.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i-1] + 1; // vectorization-prohibiting
        fn();               // vectorization-prohibiting
    }
}

void code_1201(int *A)
{
    // Code 1201 is emitted when an array base changes
    // in the loop body. Resolve this by rewriting your
    // code so that varying the array base is not necessary.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
        A++;
    }
}

struct S_1202
{
    short a;
    short b;
} s[1000];

short sA[1000], sB[1000], sC[1000];

void code_1202(S_1202 *s)
{
    // Code 1202 is emitted when non-vectorizable struct accesses
    // are present in the loop body. Only struct accesses
    // that are 32 or 64 bits are vectorized.

    for (int i=0; i<1000; ++i)
    {
        s[i].a = s[i].b + 1; // this 16 bit struct access is not vectorizable
        sA[i] += sB[i] * sC[i]; // this ensures we don't emit reason code '1300'
    }
}

void code_1203(int *A)
{
    // Code 1203 is emitted when non-vectorizable memory references
    // are present in the loop body. Vectorization of some non-contiguous
    // memory access is supported - for example, the gather/scatter pattern.

    for (int i=0; i<1000; ++i)
    {
        A[i] += A[0] + 1;       // constant memory access not vectorized
        A[i] += A[i*2+2] + 2;  // non-contiguous memory access not vectorized
    }
}

void code_1204(int *A)
{
    // Code 1204 is emitted when internal compiler data structures
    // hit a limit on the number of data dependence edges recorded.
    // Resolve this by moving the innermost loop to another function.

    for (int i=0; i<1000; i++)
        for (int j=0; j<1000; j++)
            for (int k=0; k<1000; k++)
                for (int l=0; l<1000; l++)
                {
                    for (int m=0; m<1000; m++)
                        A[m] = A[m+i] + A[m+j] + A[m+k] + A[m+l];
                }
}
```

## <a name="13xx-reason-codes"></a><a name="BKMK_ReasonCode130x"></a> 13xx 이유 코드

13 *xx* 이유 코드는 벡터화에 적용 됩니다.

| 이유 코드 | 설명 |
|--|--|
| 1300 | 루프 본문에는 계산이 거의 포함 되지 않습니다. |
| 1301 | 루프 스트라이드는 + 1이 아닙니다. |
| 1302 | Loop는 " `do` - `while` "입니다. |
| 1303 | 벡터화하여 값을 제공하기에는 너무 적은 루프 반복입니다. |
| 1304 | 루프는 다양한 크기의 할당을 포함합니다. |
| 1305 | 형식 정보가 충분하지 않습니다. |

```cpp
void code_1300(int *A, int *B)
{
    // Code 1300 is emitted when the compiler detects that there is
    // no computation in the loop body.

    for (int i=0; i<1000; ++i)
    {
        A[i] = B[i]; // Do not vectorize, instead emit memcpy
    }
}

void code_1301(int *A)
{
    // Code 1301 is emitted when the stride of a loop is not positive 1.
    // Only loops that have a stride of positive 1 are vectorized;
    // rewriting your loop may be required.

    for (int i=0; i<1000; i += 2)
    {
        A[i] = A[i] + 1;
    }
}

void code_1302(int *A)
{
    // Code 1302 is emitted for "do-while" loops. Only "while"
    // and "for" loops are vectorized.

    int i = 0;
    do
    {
        A[i] = A[i] + 1;
    } while (++i < 1000);
}

int code_1303(int *A, int *B)
{
    // Code 1303 is emitted when the compiler detects that
    // the number of iterations of the loop is too small to
    // make vectorization profitable.

    // If the loop computation fits perfectly in
    // vector registers - for example, the upper bound is 4, or 8 in
    // this case - then the loop _may_ be vectorized.

    // This loop is not vectorized because there are 5 iterations

    for (int i=0; i<5; ++i)
    {
        A[i] = A[i] + 1;
    }

    // This loop is vectorized

    for (int i=0; i<4; ++i)
    {
        A[i] = A[i] + 1;
    }

    // This loop is not vectorized because runtime pointer checks
    // are required to check that A and B don't overlap. It is not
    // worth it to vectorize this loop.

    for (int i=0; i<4; ++i)
    {
        A[i] = B[i] + 1;
    }

    // This loop is not vectorized because of the scalar reduction.

    int s = 0;
    for (int i=0; i<4; ++i)
    {
        s += A[i];
    }
    return s;
}

void code_1304(int *A, short *B)
{
    // Code 1304 is emitted when the compiler detects
    // different sized statements in the loop body.
    // In this case, there is an 32-bit statement and a
    // 16-bit statement.

    // In cases like this consider splitting the loop into loops to
    // maximize vector register utilization.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
        B[i] = B[i] + 1;
    }
}

typedef struct S_1305
{
    int a;
    int b;
} S_1305;

void code_1305( S_1305 *s, S_1305 x)
{
    // Code 1305 is emitted when the compiler can't discern
    // proper vectorizable type information for this loop.
    // This includes non-scalar loop types such as struct
    // assignments, as in this example.

    // Resolve this by ensuring that your loops have statements
    // that operate on integers or floating point types.

    for (int i=0; i<1000; ++i)
    {
        s[i] = x;
    }
}
```

## <a name="14xx-reason-codes"></a><a name="BKMK_ReasonCode140x"></a> 14xx 이유 코드

14 *xx* 이유 코드는 벡터화와 호환 되지 않는 일부 옵션이 지정 된 경우에 발생 합니다.

| 이유 코드 | 설명 |
|--|--|
| 1400 | `#pragma loop(no_vector)`가 지정됩니다. |
| 1401 | `/kernel` 스위치가 x86 혹은 ARM을 대상으로 할 때 지정됩니다. |
| 1402 | `/arch:SSE2` x 86을 대상으로 하는 경우 이상 스위치가 지정 되지 않습니다. |
| 1403 | `/arch:ATOM` switch가 지정 되 고 반복에 두 번째 작업이 포함 됩니다. |
| 1404 | `/O1` 또는 `/Os` 스위치를 지정 합니다. |
| 1405 | 벡터화가 동적 초기화에서 정적 초기화로의 최적화를 돕기 위해서 비활성화됩니다. |

```cpp
void code_1400(int *A)
{
    // Code 1400 is emitted when the no_vector pragma
    // is specified.

#pragma loop(no_vector)
    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /kernel
void code_1401(int *A)
{
    // Code 1401 is emitted when /kernel is specified.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /arch:IA32
void code_1402(int *A)
{
    // Code 1401 is emitted when /arch:IA32 is specified.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /favor:ATOM
void code_1403(double *A)
{
    // Code 1401 is emitted when /favor:ATOM is specified, and
    // the loop contains operations on "double" arrays.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}

// Compile with /O1 or /Os
void code_1404(int *A)
{
    // Code 1401 is emitted when compiling for size.

    for (int i=0; i<1000; ++i)
    {
        A[i] = A[i] + 1;
    }
}
```

## <a name="15xx-reason-codes"></a><a name="BKMK_ReasonCode150x"></a> 15xx 이유 코드

15 *xx* 이유 코드는 앨리어싱에 적용 됩니다. 앨리어싱은 메모리의 한 영역에 두 가지 다른 이름으로 접근할 때 일어납니다.

| 이유 코드 | 설명 |
|--|--|
| 1500 | 다차원 배열에서 앨리어싱이 가능합니다. |
| 1501 | 구조체의 배열에 앨리어싱이 가능합니다. |
| 1502 | 가능한 앨리어싱 및 배열 인덱스는 n + K 외의 다른 것입니다. |
| 1503 | 가능한 앨리어싱 및 배열 인덱스는 여러 오프셋을 가집니다. |
| 1504 | 앨리어싱이 가능합니다. 너무 많은 런타임 검사가 필요합니다. |
| 1505 | 앨리어싱이 가능합니다. 하지만 런타임 검사가 너무 복잡합니다. |

```cpp
void code_1500(int A[100][100], int B[100][100])
{
    // Code 1500 is emitted when runtime pointer
    // disambiguation checks are required, and
    // there are multidimensional array references.

    for (int i=0; i<100; ++i)
    {
        for (int j=0; j<100; ++j)
        {
            A[i][j] = B[i][j] + 1;
        }
    }
}

typedef struct S_1501
{
    int a;
    int b;
} S_1501;

int iA[1000], iB[1000], iC[1000];

void code_1501(S_1501 *s1, S_1501 *s2)
{
    // Code 1501 is emitted when runtime pointer
    // disambiguation checks are required, and
    // there are array-of-struct accesses in the
    // loop body.

    for (int i=0; i<100; ++i)
    {
        s1[i].a = s2[i].b + 1;
        iA[i] += iB[i] * iC[i]; // this is to ensure we don't emit reason code '1300'
    }
}

void code_1502(int *A, int *B)
{
    // Code 1502 is emitted when runtime pointer
    // disambiguation checks are required, and
    // an array reference has an offset that varies
    // in the loop.

    int x = 0;
    for (int i=0; i<100; ++i)
    {
        A[i] = B[i + x] + 1;
        ++x;                   // 'x' varies in the loop
    }
}

void code_1503(int *A, int *B, int x, int y)
{
    // Code 1503 is emitted when runtime pointer
    // disambiguation checks are required, and
    // an array reference has multiple offsets.

    for (int i=0; i<100; ++i)
    {
        A[i] = B[i+x] + B[i+y] + 1;   // multiple offsets when addressing 'B': {x, y}
        A[i] = B[i+x] + B[i] + 1;     // multiple offsets when addressing 'B': {x, 0}
        A[i] = B[i+x] + B[i+x] + 1;   // this is vectorized
    }
}

void code_1504(int *A1, int *A2, int *A3, int *A4,
               int *A5, int *A6, int *A7, int *A8,
               int *A9, int *A10, int *A11, int *A12,
               int *A13, int *A14, int *A15, int *A16)
{
    // Code 1504 is emitted when too many runtime
    // pointer disambiguation checks are required.

    for (int i=0; i<100; ++i)
    {
        ++A1[i];
        ++A2[i];
        ++A3[i];
        ++A4[i];
        ++A5[i];
        ++A6[i];
        ++A7[i];
        ++A8[i];
        ++A9[i];
        ++A10[i];
        ++A11[i];
        ++A12[i];
        ++A13[i];
        ++A14[i];
        ++A15[i];
        ++A16[i];
    }
}

void code_1505(int *A, int *B)
{
    // Code 1505 is emitted when runtime pointer
    // disambiguation checks are required, but are
    // too complex for the compiler to discern.

    for (int i=0; i<100; ++i)
    {
        for (int j=0; j<100; ++j)
        {
            for (int k=0; k<100; ++k)
            {
                A[i+j-k] = B[i-j+k] * 2;
            }
        }
    }
}
```

## <a name="see-also"></a>참고 항목

[C/c + + 컴파일러 및 빌드 도구 오류 및 경고](../compiler-errors-1/c-cpp-build-errors.md)\
[자동 병렬화 및 자동 벡터화](../../parallel/auto-parallelization-and-auto-vectorization.md)\
[Visual Studio 2012의 자동 벡터화-개요](/archive/blogs/nativeconcurrency/auto-vectorizer-in-visual-studio-2012-overview)\
[`#pragma loop()`](../../preprocessor/loop.md)\
[`/Q` 옵션 (하위 수준 작업)](../../build/reference/q-options-low-level-operations.md)\
[`/Qpar-report` (자동 평행 화 도우미 보고 수준)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md)\
[`/Qvec-report` (자동 벡터화 도우미 보고 수준)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md)
