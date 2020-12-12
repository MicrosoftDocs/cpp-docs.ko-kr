---
description: '자세한 정보: 컴파일러 오류 C2393'
title: 컴파일러 오류 C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 7cf1b333afac9f976bb4bf38ce769e6982255959
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318990"
---
# <a name="compiler-error-c2393"></a>컴파일러 오류 C2393

> '*symbol*': '*segment*' 세그먼트에 appdomain 별 기호를 할당할 수 없습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

[Appdomain](../../cpp/appdomain.md) 변수는 **/clr: pure** 또는 **/clr: safe** 를 사용 하 여 컴파일하는 것을 의미 하 고 safe 또는 pure 이미지는 데이터 세그먼트를 포함할 수 없습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2393를 생성 합니다. 이 문제를 해결 하려면 데이터 세그먼트를 만들지 마십시오.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
