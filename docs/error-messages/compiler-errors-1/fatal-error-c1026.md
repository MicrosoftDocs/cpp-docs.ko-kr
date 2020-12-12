---
description: '자세한 정보: 심각한 오류 C1026'
title: 심각한 오류 C1026
ms.date: 11/04/2016
f1_keywords:
- C1026
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
ms.openlocfilehash: 08816f21879cf6dfbeb0389700d9a8ffdc7a40d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345513"
---
# <a name="fatal-error-c1026"></a>심각한 오류 C1026

파서 스택 오버플로입니다. 프로그램이 너무 복잡합니다.

프로그램을 구문 분석 하는 데 필요한 공간에 컴파일러 스택 오버플로가 발생 했습니다.

식의 복잡성을 다음과 같이 줄입니다.

- **`for`** 및 문의 중첩 감소 **`switch`** . 좀 더 깊게 중첩 된 문을 별도의 함수에 배치 합니다.

- 쉼표 연산자 또는 함수 호출을 포함 하는 긴 식을 분리 합니다.
