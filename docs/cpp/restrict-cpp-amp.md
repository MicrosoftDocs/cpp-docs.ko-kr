---
description: '자세히 알아보기: restrict (C++ AMP)'
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 928d4f9dde9421d2c5ab244af26a688a9828881e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151453"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

제한 지정자는 함수 및 람다 선언에 적용할 수 있습니다. 제한 지정자는 C++ AMP(C++ Accelerated Massive Parallelism) 런타임을 사용하는 애플리케이션의 함수 동작 및 함수의 코드에 제한을 적용합니다.

> [!NOTE]
> **`restrict`** 저장소 클래스 특성의 일부인 키워드에 대 한 자세한 내용은 **`__declspec`** [restrict](../cpp/restrict.md)를 참조 하세요.

**`restrict`** 절은 다음 형식을 사용 합니다.

|절|Description|
|------------|-----------------|
|`restrict(cpu)`|이 함수는 전체 C++ 언어를 사용할 수 있습니다. restrict(cpu) 함수를 사용하여 선언된 다른 함수만 이 함수를 호출할 수 있습니다.|
|`restrict(amp)`|이 함수는 C++ AMP를 통해 가속할 수 있는 C++ 언어의 하위 집합만 사용할 수 있습니다.|
|`restrict(cpu)` 및 `restrict(amp)`의 시퀀스입니다.|이 함수는 `restrict(cpu)` 및 `restrict(amp)` 둘 다의 제한을 따라야 합니다. 이 함수는 `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` 또는 `restrict(amp, cpu)`를 사용하여 선언된 함수를 통해 호출할 수 있습니다.<br /><br /> `restrict(A) restrict(B)` 형식을 `restrict(A,B)`로 작성할 수 있습니다.|

## <a name="remarks"></a>설명

**`restrict`** 키워드는 상황별 키워드입니다. 제한 지정자인 `cpu` 및 `amp`는 예약어가 아닙니다. 지정자 목록은 확장할 수 없습니다. 절이 없는 함수는 **`restrict`** 절이 있는 함수와 동일 합니다 `restrict(cpu)` .

`restrict(amp)` 절이 있는 함수에는 다음 제한이 적용됩니다.

- 이 함수는 `restrict(amp)` 절이 포함된 함수만 호출할 수 있습니다.

- 함수 인라이닝 처리 가능해야 합니다.

- 함수는,, 및 변수만 선언할 수 있으며 **`int`** **`unsigned int`** **`float`** **`double`** 이러한 형식만 포함 하는 클래스 및 구조체를 선언할 수 있습니다. **`bool`** 도 허용 되지만 복합 형식에서 사용 하는 경우 4 바이트로 정렬 되어야 합니다.

- 람다 함수는 참조로 캡처할 수 없으며 포인터를 캡처할 수 없습니다.

- 참조 및 단일 간접 포인터는 로컬 변수, 함수 인수 및 반환 형식으로만 지원됩니다.

- 다음은 허용되지 않습니다.

  - 재귀

  - [Volatile](../cpp/volatile-cpp.md) 키워드를 사용 하 여 선언 된 변수입니다.

  - 가상 함수

  - 함수에 대한 포인터

  - 멤버 함수에 대한 포인터

  - 구조체의 포인터

  - 포인터에 대한 포인터

  - **`goto`** 할당문.

  - 레이블 문

  - **`try`**, **`catch`** 또는 **`throw`** 문

  - 전역 변수

  - 정적 변수 대신 [Tile_static 키워드](../cpp/tile-static-keyword.md) 를 사용 해야 합니다.

  - **`dynamic_cast`** 경향성.

  - **`typeid`** 연산자입니다.

  - asm 선언

  - vararg

함수 제한 사항에 대 한 설명은 [restrict (amp) 제한](/archive/blogs/nativeconcurrency/restrictamp-restrictions-part-0-of-n-introduction)을 참조 하세요.

## <a name="example"></a>예제

다음 예에서는 절을 사용 하는 방법을 보여 줍니다 `restrict(amp)` .

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>참고 항목

[C++ AMP(C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
