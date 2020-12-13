---
description: '자세히 알아보기: 수동 접근자 사용'
title: 수동 접근자 사용
ms.date: 10/24/2018
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
ms.openlocfilehash: 73363be83e06a3eeced114dc90c65f82601a4a16
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332477"
---
# <a name="using-manual-accessors"></a>수동 접근자 사용

알 수 없는 명령을 처리할 때 다음 네 가지 작업을 수행 해야 합니다.

- 매개 변수 확인

- 명령 실행

- 출력 열 확인

- 반환 행 집합이 여러 개 있는지 확인

OLE DB 소비자 템플릿으로 이러한 작업을 수행 하려면 클래스를 사용 하 `CManualAccessor` 고 다음 단계를 수행 합니다.

1. 를 `CCommand` 템플릿 매개 변수로 사용 하 여 개체를 엽니다 `CManualAccessor` .

    ```cpp
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;
    ```

1. 인터페이스에 대 한 세션을 쿼리하고 `IDBSchemaRowset` 프로시저 매개 변수 행 집합을 사용 합니다. 인터페이스를 `IDBSchemaRowset` 사용할 수 없는 경우 인터페이스를 쿼리 `ICommandWithParameters` 합니다. `GetParameterInfo`정보를 호출 합니다. 두 인터페이스를 모두 사용할 수 없는 경우에는 매개 변수가 없는 것으로 간주할 수 있습니다.

1. 각 매개 변수에 대해를 호출 `AddParameterEntry` 하 여 매개 변수를 추가 하 고 설정 합니다.

1. 행 집합을 연 다음 bind 매개 변수를로 설정 **`false`** 합니다.

1. `GetColumnInfo`을 호출 하 여 출력 열을 검색 합니다. `AddBindEntry`를 사용 하 여 출력 열을 바인딩에 추가 합니다.

1. `GetNextResult`을 호출 하 여 더 많은 행 집합을 사용할 수 있는지 확인 합니다. 2-5 단계를 반복 합니다.

수동 접근자에 대 한 예제는 `CDBListView::CallProcedure` [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 샘플에서을 참조 하세요.

## <a name="see-also"></a>참고 항목

[접근자 사용](../../data/oledb/using-accessors.md)
