---
title: 부동 소수점 값 언더플로
ms.date: 11/04/2016
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
ms.openlocfilehash: cd4aadc5ab006b79a43e31348fa101d40e8ca03a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477365"
---
# <a name="underflow-of-floating-point-values"></a>부동 소수점 값 언더플로

**ANSI 4.5.1** 수학 함수가 정수 식 `errno`를 언더플로 범위 오류에 대한 `ERANGE` 매크로의 값으로 설정하는지 여부

부동 소수점 언더플로는 `errno` 식을 `ERANGE`로 설정하지 않습니다. 값이 0이고 결국 언더플로로 가까워지면 값이 0으로 설정됩니다.

## <a name="see-also"></a>참고 항목

[라이브러리 함수](../c-language/library-functions.md)