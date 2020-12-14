---
description: '자세한 정보: 컴파일러 오류 C2435'
title: 컴파일러 오류 C2435
ms.date: 11/04/2016
f1_keywords:
- C2435
helpviewer_keywords:
- C2435
ms.assetid: be6aa8f8-579b-42ea-bdd8-2d01393646ad
ms.openlocfilehash: d0ab5d8c7c45c9636a5e48acc17d3ac379c755a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97189940"
---
# <a name="compiler-error-c2435"></a>컴파일러 오류 C2435

> '*var*': 동적 초기화를 수행 하려면 관리 되는 CRT가 필요 합니다./clr: safe로 컴파일할 수 없습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

전역 응용 프로그램별 도메인 변수를 초기화 하려면를 사용 하 여 컴파일된 CRT가 있어야 하며 `/clr:pure` ,이는 확인할 수 있는 이미지를 생성 하지 않습니다.

자세한 내용은 [appdomain](../../cpp/appdomain.md) 및 [process](../../cpp/process.md)를 참조하세요.

## <a name="example"></a>예제

다음 샘플에서는 C2435를 생성 합니다.

```cpp
// C2435.cpp
// compile with: /clr:safe /c
int globalvar = 0;   // C2435

__declspec(process)
int globalvar2 = 0;
```
