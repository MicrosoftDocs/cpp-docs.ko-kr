---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4129'
title: 컴파일러 경고 (수준 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: 27ae487016a5d9a60a95e4715261ec5ba9171db4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155282"
---
# <a name="compiler-warning-level-1-c4129"></a>컴파일러 경고 (수준 1) C4129

' character ': 문자 이스케이프 시퀀스를 인식할 수 없습니다.

`character` \\ 문자 또는 문자열 상수에서 다음과 같은 백슬래시 ()는 유효한 이스케이프 시퀀스로 인식 되지 않습니다. 백슬래시는 무시 되 고 인쇄 되지 않습니다. 백슬래시 다음에 나오는 문자가 인쇄 됩니다.

단일 백슬래시를 인쇄 하려면 이중 백슬래시 ()를 지정 \\ \\ 합니다.

2.13.2 섹션의 c + + 표준에서는 이스케이프 시퀀스에 대해 설명 합니다.

다음 샘플에서는 C4129를 생성 합니다.

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```
