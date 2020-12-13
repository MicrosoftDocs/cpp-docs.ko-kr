---
description: '자세한 정보: operator = = ( &lt; 샘플 컨테이너 &gt; )'
title: operator==(&lt;sample container&gt;)
ms.date: 11/04/2016
f1_keywords:
- std.==
- std::==
- operator==
- std.operator==
- std::operator==
- ==
helpviewer_keywords:
- operator ==, containers
- operator==, containers
- == operator, with specific standard C++ objects
ms.assetid: d3d8754e-5157-4b8b-bf9c-da41856f5eed
ms.openlocfilehash: b2fb296feb76536c28dd45e631af8071efa16939
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337983"
---
# <a name="operator-ltsample-containergt"></a>operator==(&lt;sample container&gt;)

> [!NOTE]
> 이 항목은 c + + 표준 라이브러리에서 사용 되는 컨테이너의 작동 하지 않는 예제로 Microsoft c + + 설명서에 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

`operator==`클래스 템플릿 [컨테이너](../standard-library/sample-container-class.md)의 두 개체를 비교 하는 오버 로드입니다.

## <a name="syntax"></a>구문

```cpp
template <class Ty>
bool operator==(
    const Container <Ty>& left,
    const Container <Ty>& right);
```

## <a name="return-value"></a>Return Value

`left.` [Size](../standard-library/container-class-size.md) `== right.size && equal(left.` [begin](../standard-library/container-class-begin.md) `, left.` [end](../standard-library/container-class-end.md) `, right.begin)` 를 반환 합니다.

## <a name="see-also"></a>참고 항목

[\<sample container>](../standard-library/sample-container.md)
