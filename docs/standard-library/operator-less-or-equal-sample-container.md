---
description: '자세한 정보: operator &lt; = ( &lt; 샘플 컨테이너 &gt; )'
title: operator&lt;=(&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::<=
- std.operator<=
- operator<=
- std.<=
- std::operator<=
- <=
helpviewer_keywords:
- operator<=
- operator <=
- <= operator, with specific objects
- <= operator
ms.assetid: 338577dd-dc88-4a2b-9e12-0379c54fc8a2
ms.openlocfilehash: 4455efcbd5b3ccca262265f44414b46d3e97f57d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337988"
---
# <a name="operatorlt-ltsample-containergt"></a>operator&lt;=(&lt;sample container&gt;)

> [!NOTE]
> 이 항목은 c + + 표준 라이브러리에서 사용 되는 컨테이너의 작동 하지 않는 예제로 Microsoft c + + 설명서에 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

오버 로드 **연산자<=** 클래스 템플릿 [컨테이너](../standard-library/sample-container-class.md)의 두 개체를 비교 합니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
bool operator<=(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Return Value

`!(right < left)`를 반환합니다.

## <a name="see-also"></a>참고 항목

[\<sample container>](../standard-library/sample-container.md)
