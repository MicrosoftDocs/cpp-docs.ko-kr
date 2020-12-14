---
description: Sequenced_policy 클래스에 대해 자세히 알아보세요.
title: sequenced_policy 클래스
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::sequenced_policy
ms.openlocfilehash: e4d19e3649e3c768e8efc062baaf735e28a8fc22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250415"
---
# <a name="sequenced_policy-class"></a>sequenced_policy 클래스

병렬 알고리즘 오버 로드를 명확 하 게 구분 하기 위해 고유한 형식으로 사용 되며 병렬 알고리즘의 실행이 병렬화 될 수 있어야 합니다.

## <a name="syntax"></a>구문

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>설명

정책을 사용 하 여 병렬 알고리즘을 실행 하는 동안 `execution::sequenced_policy` 요소 액세스 함수 호출이 catch 되지 않은 예외를 통해 종료 되는 경우가 `terminate()` 호출 됩니다.
