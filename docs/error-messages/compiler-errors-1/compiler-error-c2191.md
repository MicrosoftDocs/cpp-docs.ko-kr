---
description: '자세한 정보: 컴파일러 오류 C2191'
title: 컴파일러 오류 C2191
ms.date: 11/04/2016
f1_keywords:
- C2191
helpviewer_keywords:
- C2191
ms.assetid: 051b8350-e5de-4f51-ab6e-96d32366bcef
ms.openlocfilehash: b3b2133e70eeae566a972b0e5db11105b316d6f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337674"
---
# <a name="compiler-error-c2191"></a>컴파일러 오류 C2191

둘째 매개 변수 목록이 첫째 보다 깁니다.

C 함수가 더 긴 매개 변수 목록을 사용 하 여 두 번 선언 되었습니다. C는 오버 로드 된 함수를 지원 하지 않습니다.

## <a name="example"></a>예제

다음 샘플에서는 C2191를 생성 합니다.

```c
// C2191.c
// compile with: /Za /c
void func( int );
void func( int, float );   // C2191 different parameter list
void func2( int, float );   // OK
```
