---
description: '자세한 정보: 식 계산기 오류 CXX0015'
title: 식 계산기 오류 CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: c5d6e0ba5407646b1e3c835053f1f115dabf4fe7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228328"
---
# <a name="expression-evaluator-error-cxx0015"></a>식 계산기 오류 CXX0015

식이 너무 복잡 합니다 (스택 오버플로).

입력 한 식이 너무 복잡 하거나 C 식 계산기에 사용할 수 있는 저장소 크기에 너무 많이 중첩 되었습니다.

오버플로는 일반적으로 보류 중인 계산이 너무 많기 때문에 발생 합니다.

식의 다른 부분이 계산 될 때까지 기다릴 필요 없이 식의 각 구성 요소가 발생할 때이를 평가할 수 있도록 식을 다시 정렬 합니다.

식을 여러 개의 명령으로 나눕니다.

이 오류는 CAN0015와 동일 합니다.
