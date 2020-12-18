---
description: '자세한 정보: 함수 개요'
title: 함수 개요
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++]
- control flow, function calls
ms.assetid: b6f4637f-02b9-49d8-8601-1f886bd2cfb9
ms.openlocfilehash: b68591d9300cb1a2f63c37c78f4cc03406e9d68f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97243148"
---
# <a name="overview-of-functions"></a>함수 개요

함수가 호출되기 전에 선언이 나타나는 경우 정의가 선언으로 사용될 수 있긴 하지만 함수에는 정의와 선언이 반드시 있어야 합니다. 함수 정의에는 함수가 호출될 때 실행되는 코드인 함수 본문이 포함됩니다.

함수 선언은 이름, 반환 형식 및 프로그램의 다른 곳에 정의된 함수의 특성을 설정합니다. 함수 선언은 함수 호출 앞에 나와야 합니다. 이 때문에 코드에서 런타임 함수의 선언이 포함된 헤더 파일이 런타임 함수 호출 전에 포함됩니다. 매개 변수의 형식 및 개수에 대한 정보가 있는 선언은 프로토타입입니다. 자세한 내용은 [함수 프로토타입](../c-language/function-prototypes.md)을 참조하세요.

컴파일러는 프로토타입을 사용하여 이후 함수 호출의 인수 형식을 함수의 매개 변수와 비교하고 필요한 경우 인수의 형식을 매개 변수의 형식으로 변환합니다.

함수 호출은 호출하는 함수에서 호출된 함수로 실행 제어를 전달합니다. 인수(있는 경우)는 호출된 함수에 값으로 전달됩니다. 호출된 함수에서 **`return`** 문이 실행되면 호출하는 함수에 제어가 반환되며 값이 함께 반환될 수도 있습니다.

## <a name="see-also"></a>참조

[함수](../c-language/functions-c.md)
