---
description: '자세한 정보: OLE DB 공급자 템플릿 (c + +)'
title: OLE DB 공급자 템플릿(C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 8706fcd9467e6d184633917d7c83ac81ad137b9d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286919"
---
# <a name="ole-db-provider-templates-c"></a>OLE DB 공급자 템플릿(C++)

OLE DB은 Microsoft 유니버설 데이터 액세스 전략의 중요 한 부분입니다. OLE DB 디자인을 사용 하면 모든 데이터 원본에서 고성능 데이터에 액세스할 수 있습니다. 테이블 형식 데이터는 데이터베이스의 출처에 관계 없이 OLE DB를 통해 볼 수 있습니다. 유연성이 있으면 엄청난 양의 전력이 제공 됩니다.

[OLE DB 소비자 및 공급자](../../data/oledb/ole-db-consumers-and-providers.md)에 설명 된 대로 OLE DB는 소비자와 공급자의 개념을 사용 합니다. 소비자는 데이터에 대 한 요청을 만듭니다. 공급자는 소비자에 게 데이터를 테이블 형식으로 반환 합니다. 프로그래밍 관점에서이 모델의 가장 중요 한 의미는 공급자가 소비자가 수행할 수 있는 호출을 구현 해야 한다는 것입니다.

## <a name="what-is-a-provider"></a>공급자 란?

OLE DB 공급자는 소비자 개체의 인터페이스 호출을 제공 하 고 지 속성 원본 (데이터 저장소 라고 함)에서 소비자에 게 테이블 형식으로 데이터를 전송 하는 COM 개체 집합입니다.

공급자는 단순 하거나 복잡할 수 있습니다. 공급자는 더 많은 인터페이스를 구현 하 여 최소한의 기능 또는 전체 프로덕션 품질 공급자를 지원할 수 있습니다. 공급자는 테이블을 반환 하 고, 클라이언트가 해당 테이블의 형식을 확인 하 고, 해당 데이터에 대 한 작업을 수행할 수 있습니다.

각 공급자는 클라이언트의 요청을 처리 하는 표준 COM 개체 집합을 구현 합니다. 즉, 모든 OLE DB 소비자는 언어 (예: c + + 및 기본)에 관계 없이 모든 공급자의 데이터에 액세스할 수 있습니다.

각 COM 개체에는 몇 가지 인터페이스가 포함 되어 있으며, 그 중 일부는 선택적 요소입니다. 공급자는 필수 인터페이스를 구현 하 여 모든 클라이언트에서 사용할 수 있는 최소 수준의 기능 (준수)을 보장 합니다. 공급자는 선택적 인터페이스를 구현 하 여 추가 기능을 제공할 수 있습니다. [OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md) 는 이러한 인터페이스에 대해 자세히 설명 합니다. 클라이언트는 항상를 호출 `QueryInterface` 하 여 공급자가 지정 된 인터페이스를 지원 하는지 확인 해야 합니다.

## <a name="ole-db-specification-level-support"></a>OLE DB 사양 수준 지원

OLE DB 공급자 템플릿은 OLE DB 버전 2.7 사양을 지원 합니다. OLE DB 공급자 템플릿을 사용 하 여 수준 0 호환 공급자를 구현할 수 있습니다. 예를 들어 예제에서는 `Provider` 템플릿을 사용 하 여 파일 시스템을 쿼리 하기 위해 DOS DIR 명령을 실행 하는 비 SQL (MS-DOS) 명령 서버를 구현 합니다. `Provider`이 샘플은 테이블 형식 데이터를 반환 하는 표준 OLE DB 메커니즘인 행 집합의 디렉터리 정보를 반환 합니다.

OLE DB 템플릿에서 지원 되는 가장 간단한 유형의 공급자는 명령이 없는 읽기 전용 공급자입니다. 책갈피 및 읽기/쓰기 기능과 마찬가지로 명령이 있는 공급자도 지원 됩니다. 추가 코드를 작성 하 여 읽기/쓰기 공급자를 구현할 수 있습니다. 동적 행 집합 및 트랜잭션은 현재 버전에서 지원 되지 않지만 원하는 경우 추가할 수 있습니다.

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>OLE DB 공급자를 만들어야 하는 경우는 언제 인가요?

사용자 고유의 공급자를 반드시 만들 필요는 없습니다. Microsoft는 Visual C++의 **데이터 연결 속성** 대화 상자에서 여러 미리 패키지 된 표준 공급자를 제공 합니다. OLE DB 공급자를 만드는 주된 이유는 범용 데이터 액세스 전략을 활용 하는 것입니다. 이러한 작업을 수행 하는 몇 가지 이점은 다음과 같습니다.

- C + +, Basic 및 Visual Basic Scripting Edition 같은 언어를 통해 데이터에 액세스 합니다. 이를 통해 조직의 여러 프로그래머가 사용 하는 언어에 관계 없이 동일한 방식으로 동일한 데이터에 액세스할 수 있습니다.

- SQL Server, Excel, Access 등의 다른 데이터 원본에 대 한 데이터를 엽니다. 이는 서로 다른 형식으로 데이터를 전송 하려는 경우에 유용할 수 있습니다.

- 데이터 원본 간 (이기종) 작업에 참여 합니다. 이 방법은 데이터 웨어하우징을 효과적으로 사용할 수 있습니다. OLE DB 공급자를 사용 하면 데이터를 네이티브 형식으로 유지 하면서도 간단한 작업으로 데이터를 액세스할 수 있습니다.

- 쿼리 처리와 같은 추가 기능을 데이터에 추가 합니다.

- 데이터의 조작 방식을 제어 하 여 데이터 액세스의 성능을 향상 시킵니다.

- 견고성 강화. 한 명의 프로그래머만 액세스할 수 있는 독점적인 데이터 형식이 있는 경우에는 위험에 노출 됩니다. OLE DB 공급자를 사용 하 여 모든 프로그래머에 게 해당 소유 형식을 열 수 있습니다.

## <a name="read-only-and-updatable-providers"></a>Read-Only 및 업데이트 가능 공급자

공급자는 복잡성과 기능에 따라 크게 다를 수 있습니다. 공급자를 읽기 전용 공급자 및 업데이트할 수 있는 공급자로 분류 하는 것이 유용 합니다.

- Visual C++ 6.0는 읽기 전용 공급자만 지원 합니다. [OLE DB 공급자를 만드는](../../data/oledb/creating-an-ole-db-provider.md) 방법에 대 한 자세한 내용은 읽기 전용 공급자를 만드는 방법을 설명 합니다.
- Visual C++은 데이터 저장소를 업데이트 (쓰기) 할 수 있는 업데이트 가능 공급자를 지원 합니다. 업데이트 가능한 공급자에 대 한 자세한 내용은 [업데이트 가능 공급자 만들기](../../data/oledb/creating-an-updatable-provider.md)를 참조 하세요. [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플은 업데이트 가능한 공급자의 예입니다.

자세한 내용은 다음을 참조하세요.

- [OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)

- [OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)

- [OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>참고 항목

[데이터 액세스](../data-access-in-cpp.md)<br/>
[OLE DB SDK 설명서](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[OLE DB 프로그래머 참조](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
