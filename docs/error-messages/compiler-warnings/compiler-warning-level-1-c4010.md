---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4010'
title: 컴파일러 경고 (수준 1) C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 899e34e0835cce02ab5d11b6c64ae604369f93d9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241588"
---
# <a name="compiler-warning-level-1-c4010"></a>컴파일러 경고 (수준 1) C4010

한 줄로 된 주석에 줄 연속 문자가 있습니다.

//에 의해 도입 된 한 줄로 된 주석에는 \\ 줄 연속 문자 역할을 하는 백슬래시 ()가 포함 되어 있습니다. 컴파일러는 다음 줄을 연속 하는 것으로 간주 하 여 주석으로 처리 합니다.

일부 구문 전달 편집기는 연속 문자 다음의 줄을 주석으로 나타내지 않습니다. 이 경고를 발생 시키는 줄에서 구문 색 지정을 무시 합니다.

다음 샘플에서는 C4010를 생성 합니다.

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
