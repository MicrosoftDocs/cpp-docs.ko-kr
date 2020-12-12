---
description: '자세히 알아보기: alignof 연산자'
title: alignof 연산자
ms.date: 12/17/2018
f1_keywords:
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: b7e053b932ed631d8b03dc1b89f6857905740e5a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288310"
---
# <a name="alignof-operator"></a>alignof 연산자

**`alignof`** 연산자는 지정 된 형식의 맞춤 (바이트)을 형식의 값으로 반환 합니다 **`size_t`** .

## <a name="syntax"></a>구문

```cpp
alignof( type )
```

## <a name="remarks"></a>설명

예를 들어:

| 식 | 값 |
|--|--|
| **`alignof( char )`** | 1 |
| **`alignof( short )`** | 2 |
| **`alignof( int )`** | 4 |
| **`alignof( long long )`** | 8 |
| **`alignof( float )`** | 4 |
| **`alignof( double )`** | 8 |

**`alignof`** 값은 기본 형식의의 값과 동일 합니다 **`sizeof`** . 그러나 다음과 같은 예제를 고려해야 합니다.

```cpp
typedef struct { int a; double b; } S;
// alignof(S) == 8
```

이 경우 **`alignof`** 값은 구조체에서 가장 큰 요소의 맞춤 요구 사항입니다.

마찬가지로

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`alignof(S)`이(가) `32`와 같은 경우.

에서 사용 하는 한 가지 용도는 **`alignof`** 사용자 고유의 메모리 할당 루틴 중 하나에 대 한 매개 변수입니다. 예를 들어, 다음의 정의된 구조인 `S`가 지정된 경우 `aligned_malloc`이라는 메모리 할당 루틴을 호출하여 특정한 할당 경계에서 메모리를 할당할 수 있습니다.

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), alignof(S));
```

맞춤 수정에 대한 자세한 내용은 다음을 참조하세요.

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (구조체 멤버 맞춤)](../build/reference/zp-struct-member-alignment.md)

- [구조 맞춤 예](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64 특정)

X86 및 x64 관련 코드에서 맞춤의 차이점에 대한 자세한 내용은 다음을 참조하세요.

- [X86 컴파일러와 충돌](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

### <a name="microsoft-specific"></a>Microsoft 전용

**`alignof`** 및 **`__alignof`** 는 Microsoft 컴파일러의 동의어입니다. C + + 11에서는 표준의 일부가 되기 전에 Microsoft 전용 **`__alignof`** 운영자가이 기능을 제공 했습니다. 이식성을 최대화 하려면 **`alignof`** Microsoft 전용 연산자 대신 연산자를 사용 해야 합니다 **`__alignof`** .

이전 버전과의 호환성을 위해 **`_alignof`** 는 **`__alignof`** 컴파일러 옵션 [ `/Za` \( 언어 확장 사용 안 함](../build/reference/za-ze-disable-language-extensions.md) 을 지정 하지 않는 경우의 동의어입니다.

## <a name="see-also"></a>참조

[단항 연산자가 있는 식](../cpp/expressions-with-unary-operators.md)<br/>
[키워드](../cpp/keywords-cpp.md)
