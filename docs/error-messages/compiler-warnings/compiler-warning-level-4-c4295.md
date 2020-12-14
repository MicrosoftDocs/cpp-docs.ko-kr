---
description: '자세한 정보: 컴파일러 경고 (수준 4) C4295'
title: 컴파일러 경고(수준 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: 77f94d96d7ce5659652296e814777341a310a19f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97294589"
---
# <a name="compiler-warning-level-4-c4295"></a>컴파일러 경고(수준 4) C4295

> '*array*': 배열이 너무 작아서 null 종결 문자를 포함할 수 없습니다.

배열이 초기화 되었지만 배열의 마지막 문자는 null이 아닙니다. 배열에 문자열로 액세스 하면 예기치 않은 결과가 발생할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4295를 생성 합니다. 이 문제를 해결 하려면 배열 크기를 더 크게 선언 하거나, 이니셜라이저 문자열에서 종료 null을 보유 하거나, 배열 이니셜라이저 목록을 사용 하 여 **`char`** null로 끝나는 문자열이 아닌의 배열인 의도를 명확 하 게 만들 수 있습니다.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
