---
description: '자세한 정보: 컴파일러 오류 C2434'
title: 컴파일러 오류 C2434
ms.date: 11/04/2016
f1_keywords:
- C2434
helpviewer_keywords:
- C2434
ms.assetid: 01329e26-7c74-4219-b74f-69e3a40c9738
ms.openlocfilehash: e24eb3fdf2ae60dadc270bed1bdda251acfc70a3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189966"
---
# <a name="compiler-error-c2434"></a>컴파일러 오류 C2434

> '*symbol*': __declspec (process)로 선언 된 기호는/clr: pure 모드에서 동적으로 초기화할 수 없습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

**/Clr: pure** 에서 프로세스별 변수를 동적으로 초기화할 수 없습니다. 자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 및 [프로세스](../../cpp/process.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2434를 생성 합니다. 이 문제를 해결 하려면 상수를 사용 하 여 변수를 초기화 `process` 합니다.

```cpp
// C2434.cpp
// compile with: /clr:pure /c
int f() { return 0; }
__declspec(process) int i = f();   // C2434
__declspec(process) int i2 = 0;   // OK
```
