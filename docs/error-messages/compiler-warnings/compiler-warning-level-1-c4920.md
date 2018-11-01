---
title: 컴파일러 경고(수준 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: cd501cf0e3b434523623276027056c93c77fc278
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580692"
---
# <a name="compiler-warning-level-1-c4920"></a>컴파일러 경고(수준 1) C4920

enum enum 멤버 member=value는 이미 enum enum에 member=value로 존재합니다.

#import에 전달한 .tlb가 둘 이상의 열거형으로 정의된 동일한 기호를 사용할 경우 이 경고에서 뒤에 오는 동일한 기호가 무시되고 .tlh 파일에서 주석 처리됨을 나타냅니다.

다음을 포함하는 .tlb를 가정합니다.

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

다음 샘플에서는 C4920을 생성합니다.

```
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```