---
description: '자세한 정보: 컴파일러 오류 C2612'
title: 컴파일러 오류 C2612
ms.date: 11/04/2016
f1_keywords:
- C2612
helpviewer_keywords:
- C2612
ms.assetid: 6faacfd6-4455-41a2-808e-0f6799f84d6d
ms.openlocfilehash: 34ff229f493ccbab8c41e011caaabea818d79de9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338680"
---
# <a name="compiler-error-c2612"></a>컴파일러 오류 C2612

기본/멤버 이니셜라이저 목록에 후행 ' char '가 잘못 되었습니다.

이니셜라이저 목록에서 마지막 기본 또는 멤버 뒤에 문자가 표시 됩니다.

다음 샘플에서는 C2612를 생성 합니다.

```cpp
// C2612.cpp
class A {
public:
   int i;
   A( int ia ) : i( ia ) + {};   // C2612
};
```
