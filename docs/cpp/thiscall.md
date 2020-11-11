---
title: __thiscall
description: Microsoft c + +에서 x86 클래스 멤버 함수에 대 한 Microsoft 관련 __thiscall 호출 규칙에 대해 알아봅니다.
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 9b11dcf8dee928b687f942639ed72ead3659614b
ms.sourcegitcommit: 25f6d52eb9e5d84bd0218c46372db85572af81da
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94448453"
---
# `__thiscall`

**Microsoft 전용** **`__thiscall`** 호출 규칙은 X86 아키텍처의 c + + 클래스 멤버 함수에 사용 됩니다. 변수 인수 (함수)를 사용 하지 않는 멤버 함수에서 사용 하는 기본 호출 규칙 `vararg` 입니다.

에서 **`__thiscall`** 호출 수신자는 함수에 대해 불가능 한 스택을 정리 합니다 `vararg` . 인수는 오른쪽에서 왼쪽으로 스택에 푸시됩니다. **`this`** 포인터는 스택이 아니라 레지스터 ECX를 통해 전달 됩니다.

ARM, ARM64 및 x64 컴퓨터에 **`__thiscall`** 는 컴파일러에서 허용 되 고 무시 됩니다. 이는 기본적으로 레지스터 기반 호출 규칙을 사용 하기 때문입니다.

를 사용 하는 한 가지 이유 **`__thiscall`** 는 멤버 함수가 기본적으로를 사용 하는 클래스입니다 **`__clrcall`** . 이 경우를 사용 **`__thiscall`** 하 여 네이티브 코드에서 개별 멤버 함수를 호출할 수 있게 할 수 있습니다.

를 사용 하 여 컴파일하는 경우에 [`/clr:pure`](../build/reference/clr-common-language-runtime-compilation.md) 는 별도로 **`__clrcall`** 지정 하지 않는 한 모든 함수와 함수 포인터가 됩니다. **`/clr:pure`** 및 **`/clr:safe`** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

`vararg` 멤버 함수는 **`__cdecl`** 호출 규칙을 사용 합니다. 모든 함수 인수는 스택에 푸시되 고 **`this`** 포인터는 마지막 스택에 배치 됩니다.

이 호출 규칙은 c + +에만 적용 되기 때문에 C 이름 데코레이션 체계가 없습니다.

비정적 클래스 멤버 함수를 아웃오브 라인으로 정의 하는 경우 선언에만 호출 규칙 한정자를 지정 합니다. 아웃오브 라인 정의에서 다시 지정할 필요가 없습니다. 컴파일러는 정의 지점에서 선언 중에 지정 된 호출 규칙을 사용 합니다.

## <a name="see-also"></a>참조

[인수 전달 및 명명 규칙](../cpp/argument-passing-and-naming-conventions.md)
