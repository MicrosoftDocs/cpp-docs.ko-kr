---
description: '자세한 정보: 호출 규칙'
title: 호출 규칙
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: bb5dab14e9d046b6ccee75a4fb37bd7b105902dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97308655"
---
# <a name="calling-conventions"></a>호출 규칙

Visual C/C++ 컴파일러는 내부 및 외부 함수 호출에 몇 가지 다양한 규칙을 제공합니다. 이러한 다양한 접근 방법에 대한 이해는 프로그램을 디버깅하고 어셈블리 언어 루틴에 코드를 연결하는 데 도움이 됩니다.

이 주제의 항목에서는 호출 규칙간의 차이점, 인수를 전달하는 방식, 함수가 값을 반환하는 방식에 대해 설명합니다. 또한 고급 기능인 naked 함수 호출에 대한 설명을 통해 사용자 지정 프롤로그 및 에필로그 코드를 작성할 수 있도록 합니다.

X64 프로세서의 호출 규칙에 대 한 자세한 내용은 [호출 규칙](../build/x64-calling-convention.md)을 참조 하세요.

## <a name="topics-in-this-section"></a>이 섹션의 항목

- [인수 전달 및 명명 규칙](../cpp/argument-passing-and-naming-conventions.md) ( **`__cdecl`** , **`__stdcall`** , **`__fastcall`** 및 기타)

- [호출 예제: 함수 프로토타입 및 호출](../cpp/calling-example-function-prototype-and-call.md)

- [naked 함수 호출을 사용하여 사용자 지정 프롤로그/에필로그 코드 작성](../cpp/naked-function-calls.md)

- [부동 소수점 보조 프로세서 및 호출 규칙](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [사용되지 않는 호출 규칙](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>참고 항목

[Microsoft 전용 한정자](../cpp/microsoft-specific-modifiers.md)
