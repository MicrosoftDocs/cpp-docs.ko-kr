---
description: '다음에 대 한 자세한 정보: #ifdef 및 #ifndef 지시문 (C/c + +)'
title: '#ifdef 및 #ifndef 지시문(C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#ifndef'
- '#ifdef'
helpviewer_keywords:
- '#ifdef directive'
- preprocessor, directives
- ifdef directive (#ifdef)
- ifndef directive (#ifndef)
- '#ifndef directive'
ms.assetid: 2b0be69d-9e72-45d8-8e24-e4130fb2455b
ms.openlocfilehash: 4888e4516b57465974d99b1c9e8e6393e02f68c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97269291"
---
# <a name="ifdef-and-ifndef-directives-cc"></a>#ifdef 및 #ifndef 지시문 (C/c + +)

**#Ifdef** 및 **#ifndef** 지시문은 **정의 된** 연산자와 함께 사용 될 때 [#if](hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) 지시어와 동일한 효과를 가집니다.

## <a name="syntax"></a>Syntax

> **#ifdef** *식별자*\
> **#ifndef** *식별자*

이러한 지시문은 다음과 같습니다.

> **#if 정의 된** *식별자*\
> **#if! 정의 된** *식별자*

## <a name="remarks"></a>설명

언제 어디서 나 **#ifdef** 및 **#ifndef** 지시문을 사용할 수 있습니다 `#if` . 식별자가 정의 된 경우에는 **#ifdef** *식별자* 문이와 동일 합니다 `#if 1` .  `#if 0` *식별자* 가 정의 되지 않았거나 지시문으로 정의 되지 않은 경우와 동일 `#undef` 합니다. 이러한 지시문은 C 또는 C++ 소스 코드에서 선언된 식별자가 아니라 `#define`으로 정의된 식별자가 있는지 여부만 검사합니다.

이러한 지시문은 이전 버전 언어와의 호환성을 위해서만 제공됩니다. 지시문과 함께 사용 되는 **정의 된 (** *식별자* **)** 상수 식을 사용 하는 `#if` 것이 좋습니다.

**#Ifndef** 지시문은 **#ifdef** 에 의해 확인 된 조건의 반대 인지 확인 합니다. 식별자가 정의 되지 않았거나 해당 정의가를 통해 제거 된 경우 `#undef` 조건은 true (0이 아님)입니다. 그렇지 않으면 조건은 false(0)입니다.

**Microsoft 전용**

*식별자* 는 [/d](../build/reference/d-preprocessor-definitions.md) 옵션을 사용 하 여 명령줄에서 전달할 수 있습니다. 에서 최대 30 개의 매크로를 지정할 수 있습니다 `/D` .

**#Ifdef** 지시어는 명령줄에서 정의를 전달할 수 있으므로 정의가 존재 하는지 여부를 확인 하는 데 유용 합니다. 예를 들어:

```cpp
// ifdef_ifndef.CPP
// compile with: /Dtest /c
#ifndef test
#define final
#endif
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[전처리기 지시문](../preprocessor/preprocessor-directives.md)
