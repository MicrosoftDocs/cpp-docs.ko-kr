---
description: OLE DB 개체 모델에 대해 자세히 알아보세요.
title: OLE DB 개체 모델
ms.date: 10/22/2018
helpviewer_keywords:
- rowsets, OLE DB object model
- OLE DB, object model
ms.assetid: 1a274a25-c310-4430-a1ec-bd2bd8120eff
ms.openlocfilehash: 8286c62e890d891f015a0d54ac761b4de6e58d85
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286971"
---
# <a name="ole-db-object-model"></a>OLE DB 개체 모델

OLE DB 개체 모델은 다음 개체 또는 구성 요소로 구성 됩니다. 처음 네 개의 개체나 구성 요소 (데이터 원본, 세션, 명령 및 행 집합)를 사용 하 여 데이터 원본에 연결 하 고 볼 수 있습니다. 접근자로 시작 하는 나머지는 데이터를 표시할 때 데이터 작업을 수행 하는 것과 관련이 있습니다.

## <a name="data-sources"></a>솔루션 탐색기

데이터 원본 개체를 사용 하 여 파일 또는 DBMS와 같은 데이터 원본에 연결할 수 있습니다. 데이터 원본 개체는 연결을 만들고 관리 하며 사용 권한 및 인증 정보 (예: 로그인 이름 및 암호)를 포함 합니다. 데이터 원본 개체는 하나 이상의 세션을 만들 수 있습니다.

## <a name="sessions"></a>세션

세션은 데이터 원본과의 특정 상호 작용을 관리 하 여 데이터를 쿼리하고 검색 합니다. 각 세션은 단일 트랜잭션입니다. 트랜잭션은 ACID 테스트에서 정의한 나눌 작업 단위입니다. ACID에 대 한 정의는 [트랜잭션](#vcconoledbcomponents_transactions)을 참조 하세요.

세션은 행 집합을 열고이를 만든 데이터 원본 개체를 반환 하는 것과 같은 중요 한 태스크를 수행 합니다. 또한 세션은 메타 데이터 또는 데이터 원본 자체에 대 한 정보 (예: 테이블 정보)를 반환할 수 있습니다.

세션은 하나 이상의 명령을 만들 수 있습니다.

## <a name="commands"></a>명령

명령은 SQL 문과 같은 텍스트 명령을 실행 합니다. 텍스트 명령이 SQL **SELECT** 문과 같은 행 집합을 지정 하는 경우이 명령은 행 집합을 만듭니다.

명령은 단순히 공급자의 기본 데이터 저장소에서 실행할 수 있도록 소비자에서 데이터 원본 개체로 전달 되는 문자열 (예: SQL 문) 인 텍스트 명령의 컨테이너입니다. 일반적으로 text 명령은 SQL **select** 문입니다 .이 경우 sql **select** 는 행 집합을 지정 하 고 명령은 행 집합을 자동으로 만듭니다.

## <a name="rowsets"></a>행 집합

행 집합은 데이터를 테이블 형식으로 표시 합니다. 인덱스는 행 집합의 특별 한 경우입니다. 세션 또는 명령에서 행 집합을 만들 수 있습니다.

### <a name="schema-rowsets"></a>스키마 행 집합

스키마에는 데이터베이스에 대 한 메타 데이터 (구조적 정보)가 있습니다. 스키마 행 집합은 스키마 정보를 포함 하는 행 집합입니다. DBMS에 대 한 일부 OLE DB 공급자는 스키마 행 집합 개체를 지원 합니다. 스키마 행 집합에 대 한 자세한 내용은 스키마 행 집합 및 [스키마 행 집합 클래스 및 Typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) [를 사용 하 여 메타 데이터 가져오기](../../data/oledb/obtaining-metadata-with-schema-rowsets.md) 를 참조 하세요.

### <a name="view-objects"></a>개체 보기

View 개체는 행 집합에서 행과 열의 하위 집합을 정의 합니다. 자체 데이터는 없습니다. 뷰 개체는 여러 행 집합의 데이터를 결합할 수 없습니다.

## <a name="accessors"></a>접근자

OLE DB만 접근자의 개념을 사용 합니다. 접근자는 소비자에 게 데이터가 저장 되는 방법을 설명 합니다. 이 클래스에는 행 집합 필드 (열)와 소비자에 선언 된 데이터 멤버 간의 바인딩 집합 (열 맵 이라고 함)이 있습니다.

## <a name="transactions"></a><a name="vcconoledbcomponents_transactions"></a> 트랜잭션

트랜잭션 개체는 최하위 수준 이외의 중첩 트랜잭션을 커밋하거나 중단 하는 데 사용 됩니다. 트랜잭션은 ACID 테스트에서 정의한 나눌 작업 단위입니다. ACID는 다음을 의미 합니다.

- 원자성은 더 작은 작업 단위로 나눌 수 없습니다.

- 동시성, 한 번에 둘 이상의 트랜잭션을 수행할 수 있습니다.

- 격리, 한 트랜잭션이 다른 트랜잭션에의 한 변경 내용에 대 한 정보를 제한 합니다.

- 내구성, 트랜잭션이 영구적으로 변경 될 수 있습니다.

## <a name="enumerators"></a>Enumerators

열거자는 사용 가능한 데이터 원본 및 기타 열거자를 검색 합니다. 특정 데이터 원본에 대해 사용자 지정 되지 않은 소비자는 열거자를 사용 하 여 사용할 데이터 원본을 검색 합니다.

Microsoft Data Access SDK에 제공 되는 루트 열거자는 레지스트리를 순회 하 여 데이터 원본 및 기타 열거자를 찾습니다. 다른 열거자는 공급자별 방식으로 레지스트리 또는 검색을 트래버스 합니다.

## <a name="errors"></a>오류

모든 OLE DB 개체의 인터페이스에서 오류를 생성할 수 있습니다. 오류에는 선택적 사용자 지정 오류 개체를 비롯 하 여 오류에 대 한 추가 정보가 있습니다. 이 정보는 HRESULT에 저장 됩니다.

## <a name="notifications"></a>알림

알림은 행 집합을 공유 하는 협동 소비자 그룹에서 사용 됩니다. 공유는 소비자가 동일한 트랜잭션 내에서 작업 하는 것으로 간주 됩니다. 알림을 통해 행 집합을 공유 하는 협동 소비자가 피어가 수행한 행 집합에 대 한 작업에 대 한 정보를 받을 수 있습니다.

## <a name="see-also"></a>참고 항목

[OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 프로그래밍 개요](../../data/oledb/ole-db-programming-overview.md)
