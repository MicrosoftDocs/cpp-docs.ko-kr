---
description: '자세한 정보: 컴파일러 오류 C2838'
title: 컴파일러 오류 C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 70bc1fa038df33cfe63fccd7dc3db8983950b525
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194399"
---
# <a name="compiler-error-c2838"></a>컴파일러 오류 C2838

' member ': 멤버 선언에 정규화 된 이름이 잘못 되었습니다.

클래스, 구조체 또는 공용 구조체는 정규화 된 이름을 사용 하 여 다른 클래스, 구조체 또는 공용 구조체의 멤버를 다시 선언 합니다.

다음 샘플에서는 C2838를 생성 합니다.

```cpp
// C2838.cpp
// compile with: /c
class Bellini {
public:
    void Norma();
};

class Bottesini {
   Bellini::Norma();  // C2838
};
```
