---
description: '다음에 대 한 자세한 정보: 연산자&gt;='
title: operator&gt;=
ms.date: 11/04/2016
f1_keywords:
- operator>=
- std::>=
- std.operator>=
- '>='
- std.>=
- std::operator>=
helpviewer_keywords:
- '>= operator, comparing specific objects'
- operator >=
- operator>=
ms.assetid: 14fbebf5-8b75-4afa-a51b-3112d31c07cf
ms.openlocfilehash: 1821647ebb281020cef1798cf056fbf816aa855c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297072"
---
# <a name="operatorgt"></a>operator&gt;=

> [!NOTE]
> 이 항목은 c + + 표준 라이브러리에서 사용 되는 컨테이너의 작동 하지 않는 예제로 Microsoft c + + 설명서에 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

오버 로드 **연산자>=** 클래스 템플릿 [컨테이너](../standard-library/sample-container-class.md)의 두 개체를 비교 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
bool operator>=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Return Value

`!(left < right)`를 반환합니다.

## <a name="see-also"></a>참고 항목

[\<sample container>](../standard-library/sample-container.md)
