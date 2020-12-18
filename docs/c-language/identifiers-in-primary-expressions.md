---
description: '자세한 정보: 기본 식의 식별자'
title: 기본 식의 식별자
ms.date: 11/04/2016
helpviewer_keywords:
- identifiers, designating objects
ms.assetid: d4602fe6-e7e6-40cc-9823-3b1ebf5d3d38
ms.openlocfilehash: 63fbadeb786edda232282a5073dd85b22f487e9b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182179"
---
# <a name="identifiers-in-primary-expressions"></a>기본 식의 식별자

식별자는 integral, **`float`** , **`enum`** , **`struct`** , **`union`** , array, pointer 또는 function 형식일 수 있습니다. 식별자는 개체를 지정하는 것(이 경우 l-value임)으로 선언되거나 함수(이 경우 함수 지정자임)로 선언된 경우에 기본 식입니다. l-value의 정의는 [L-Value 및 R-Value 식](../c-language/l-value-and-r-value-expressions.md)을 참조하세요.

배열 식별자가 나타내는 포인터 값은 변수가 아닙니다. 따라서 배열 식별자는 할당 연산의 왼쪽 피연산자가 될 수 없으므로 수정 가능한 l-value가 아닙니다.

함수로 선언된 식별자는 값이 함수의 주소인 포인터를 나타냅니다. 포인터는 지정된 형식의 값을 반환하는 함수의 주소를 지정합니다. 따라서 함수 식별자도 할당 연산에서 l-value일 수 없습니다. 자세한 내용은 [Identifiers](../c-language/c-identifiers.md)를 참조하세요.

## <a name="see-also"></a>참조

[C 기본 식](../c-language/c-primary-expressions.md)
