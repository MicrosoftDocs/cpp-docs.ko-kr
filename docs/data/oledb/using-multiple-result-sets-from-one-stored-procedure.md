---
description: '자세한 정보: 하나의 저장 프로시저에서 여러 결과 집합 사용'
title: 저장 프로시저 하나에서 여러 결과 집합 사용
ms.date: 10/24/2018
helpviewer_keywords:
- stored procedures, returning result sets
- multiple result sets
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
ms.openlocfilehash: 8e6b7a51635caf9ddfd86dddcad0e2a3f94bb7dd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97319120"
---
# <a name="using-multiple-result-sets-from-one-stored-procedure"></a>저장 프로시저 하나에서 여러 결과 집합 사용

대부분의 저장 프로시저는 여러 결과 집합을 반환 합니다. 이러한 저장 프로시저는 일반적으로 하나 이상의 select 문을 포함 합니다. 소비자는 모든 결과 집합을 처리 하기 위해이 포함을 고려해 야 합니다.

## <a name="to-handle-multiple-result-sets"></a>여러 결과 집합을 처리 하려면

1. 사용자가 `CCommand` `CMultipleResults` 선택한 접근자 (일반적으로 동적 또는 수동 접근자)를 사용 하 여를 템플릿 인수로 사용 하 여 클래스를 만듭니다. 다른 형식의 접근자를 사용 하는 경우 각 행 집합에 대 한 출력 열을 확인 하지 못할 수 있습니다.

1. 일반적인 방법으로 저장 프로시저를 실행 하 고 열을 바인딩합니다 ( [데이터를 인출 하려면 어떻게 해야 하나요?](../../data/oledb/fetching-data.md)참조).

1. 데이터를 사용 합니다.

1. `GetNextResult`클래스에서를 호출 `CCommand` 합니다. 다른 결과 행 집합을 사용할 수 있는 경우는 `GetNextResult` S_OK을 반환 하 고 수동 접근자를 사용 하는 경우 열을 다시 바인딩해야 합니다. `GetNextResult`에서 오류를 반환 하는 경우 더 이상 사용할 수 있는 결과 집합이 없습니다.

## <a name="see-also"></a>참고 항목

[저장 프로시저 사용](../../data/oledb/using-stored-procedures.md)
