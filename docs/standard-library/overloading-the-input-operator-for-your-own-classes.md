---
description: '자세한 정보: &gt; &gt; 클래스에 대 한 연산자 오버 로드'
title: 고유 클래스에 대해 &gt;&gt; 연산자 오버로드
ms.date: 11/04/2016
helpviewer_keywords:
- operator>>
- operator>>, overloading for your own classes
- operator >>, overloading for your own classes
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
ms.openlocfilehash: 4de7c16dd1c42f85f169da50f11a514eb245b47c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340855"
---
# <a name="overloading-the-gtgt-operator-for-your-own-classes"></a>고유 클래스에 대해 &gt;&gt; 연산자 오버로드

입력 스트림은 표준 형식에 대해 추출(`>>`) 연산자를 사용합니다. 고유 형식용으로 유사한 추출 연산자를 작성할 수 있으며, 이 경우 공백을 정확하게 사용해야 합니다.

앞에서 살펴보았던 `Date` 클래스에 대한 추출 연산자의 한 예가 아래에 나와 있습니다.

```cpp
istream& operator>> (istream& is, Date& dt)
{
    is>> dt.mo>> dt.da>> dt.yr;
    return is;
}
```

## <a name="see-also"></a>참고 항목

[입력 스트림](../standard-library/input-streams.md)
