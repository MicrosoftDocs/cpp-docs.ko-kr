---
description: '자세한 정보: 심각한 오류 C1509'
title: 심각한 오류 C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: dc2483ae96f599912b3ba6d1594257fec81ac251
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97276350"
---
# <a name="fatal-error-c1509"></a>심각한 오류 C1509

컴파일러 한계: ' function ' 함수에 예외 처리기 상태가 너무 많습니다. 단순화 함수

코드가 예외 처리기 상태 (32768 상태)의 내부 제한을 초과 합니다.

가장 일반적인 원인은 함수에 사용자 정의 클래스 변수 및 산술 연산자의 복잡 한 식이 포함 되어 있기 때문입니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 임시 변수에 공통 부분식을 할당 하 여 식을 단순화 합니다.

1. 함수를 더 작은 함수로 분할 합니다.
