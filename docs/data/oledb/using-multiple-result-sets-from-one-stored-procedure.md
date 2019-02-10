---
title: 저장 프로시저 하나에서 여러 결과 집합 사용
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: fe41bfe1d9fb0207f55d2cd653a56a1ff00ce2d1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570680"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>저장 프로시저 하나에서 여러 결과 집합 사용

대부분의 저장 프로시저는 여러 결과 집합을 반환합니다. 이러한 저장 프로시저에는 대개 하나 이상의 select 문이 포함되어 있습니다. 모든 결과 집합을 처리하기 위해서는 소비자가 이 점을 고려해야 합니다.

## <a name="to-handle-multiple-result-sets"></a>여러 결과 집합을 처리하려면

1. `CMultipleResults`를 템플릿 인수로 하고 선택한 접근자를 가진 `CCommand` 클래스를 만듭니다. 일반적으로, 접근자는 자동 또는 수동 접근자일 수 있으며, 다른 접근자 형식을 사용할 경우에는 각 행 집합의 출력 열을 결정하지 못할 수도 있습니다.

1. 저장 프로시저를 정상적으로 실행하고 열을 바인딩합니다( [데이터 페치](../../data/oledb/fetching-data.md) 참조).

1. 데이터를 사용합니다.

1. `CCommand` 클래스에서 `GetNextResult`를 호출합니다. 다른 결과 행 집합을 사용할 수 있는 경우, `GetNextResult`는 S_OK를 반환하며 사용자는 수동 접근자를 사용하고 있는 경우 열을 다시 바인딩해야 합니다. `GetNextResult`에서 오류를 반환하면 사용할 수 있는 결과 집합이 더 이상 없습니다.

## <a name="see-also"></a>참고 항목

[저장 프로시저 사용](../../data/oledb/using-stored-procedures.md)
