---
description: '자세한 정보: 컴파일러 오류 C2085'
title: 컴파일러 오류 C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 2cd828c9a18c06c5794bef01ba861f702af2e096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97252118"
---
# <a name="compiler-error-c2085"></a>컴파일러 오류 C2085

' identifier ': 정식 매개 변수 목록에 없습니다.

식별자가 함수 정의에서 선언 되었지만 형식 매개 변수 목록에는 선언 되지 않았습니다. (ANSI C만 해당)

다음 샘플에서는 C2085를 생성 합니다.

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

해결 방법:

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

세미콜론이 누락 된 경우 `func1()` 은 프로토타입이 아닌 함수 정의 처럼 보이지만 `main` `func1()` 식별자에 대 한 오류 C2085를 생성 하 여 내에서 정의 됩니다 `main` .
