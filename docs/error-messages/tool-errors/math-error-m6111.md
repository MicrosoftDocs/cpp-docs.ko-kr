---
description: '자세한 정보: 수학 오류 M6111'
title: 수학 오류 M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 9bf2d620a0df18752b74aaacd4d2415510407f0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97244344"
---
# <a name="math-error-m6111"></a>수학 오류 M6111

스택 언더플로

부동 소수점 연산으로 인해 8087/287/387 보조 프로세서 또는 에뮬레이터에서 스택 언더플로가 발생 했습니다.

이 오류는 **`long double`** 값을 반환 하지 않는 함수에 대 한 호출로 인해 발생 하는 경우가 많습니다. 예를 들어 다음은 컴파일되고 실행 될 때이 오류를 생성 합니다.

```
long double ld() {};
main ()
{
  ld();
}
```

프로그램이 종료 코드 139를 사용 하 여 종료 됩니다.
