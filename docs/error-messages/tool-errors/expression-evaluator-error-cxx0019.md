---
description: '자세한 정보: 식 계산기 오류 CXX0019'
title: 식 계산기 오류 CXX0019
ms.date: 11/04/2016
f1_keywords:
- CXX0019
helpviewer_keywords:
- CXX0019
- CAN0019
ms.assetid: 4c6431fd-3310-4a61-934d-58b070b330fe
ms.openlocfilehash: 1caf4714c1fc719883ee889c14225e4f69e961a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228237"
---
# <a name="expression-evaluator-error-cxx0019"></a>식 계산기 오류 CXX0019

잘못 된 형식 캐스트

C 식 계산기는 작성 된 형식 캐스트를 수행할 수 없습니다.

이 오류는 CAN0019와 동일 합니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 지정 된 유형을 알 수 없습니다.

1. 포인터 형식 수준이 너무 많습니다. 예를 들어 형식 캐스팅

    ```
    (char **)h_message
    ```

   는 C 식 계산기로 평가할 수 없습니다.
