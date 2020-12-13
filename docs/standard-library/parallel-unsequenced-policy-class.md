---
description: Parallel_unsequenced_policy 클래스에 대해 자세히 알아보세요.
title: parallel_unsequenced_policy 클래스
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: e39edc0979bf1374bc6092dbadb032811180f668
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340790"
---
# <a name="parallel_unsequenced_policy-class"></a>parallel_unsequenced_policy 클래스

병렬 알고리즘 오버 로드를 명확 하 게 구분 하는 고유한 형식으로 사용 되며 병렬 알고리즘의 실행이 병렬화 되 고 벡터화 수 있음을 표시 합니다.

## <a name="syntax"></a>구문

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>설명

정책을 사용 하 여 병렬 알고리즘을 실행 하는 동안 `execution::parallel_unsequenced_policy` 요소 액세스 함수 호출이 catch 되지 않은 예외를 통해 종료 되는 경우가 `terminate()` 호출 됩니다.
