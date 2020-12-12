---
description: '자세한 정보: 명령 및 테이블'
title: 명령 및 테이블
ms.date: 11/19/2018
helpviewer_keywords:
- OLE DB consumer templates, table support
- CCommand class, OLE DB consumer templates
- commands [C++], OLE DB Consumer Templates
- CTable class
- CAccessorRowset class, command and table classes
- rowsets, accessing
- tables [C++], OLE DB Consumer Templates
- OLE DB consumer templates, command support
ms.assetid: 4bd3787b-6d26-40a9-be0c-083080537c12
ms.openlocfilehash: 767077af7b44b4727272fefc1c2af2f717baddd8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323342"
---
# <a name="commands-and-tables"></a>명령 및 테이블

명령 및 테이블을 사용 하 여 행 집합에 액세스할 수 있습니다. 즉, 행 집합을 열고, 명령을 실행 하 고, 열을 바인딩합니다. [CCommand](../../data/oledb/ccommand-class.md) 및 [CTable](../../data/oledb/ctable-class.md) 클래스는 각각 명령 및 테이블 개체를 인스턴스화합니다. 이러한 클래스는 다음 그림에 표시 된 것 처럼 [CAccessorRowset](../../data/oledb/caccessorrowset-class.md) 에서 파생 됩니다.

![CCommand 및 CTable](../../data/oledb/media/vccommandstables.gif "CCommand 및 CTable")<br/>
명령 및 테이블 클래스

위의 표에서는 접근자 형식 `TAccessor` 에 나열 된 모든 접근자 형식일 수 [](../../data/oledb/accessors-and-rowsets.md)있습니다. `TRowset`[행 집합](../../data/oledb/accessors-and-rowsets.md)형식에 나열 된 모든 행 집합 형식일 수 있습니다. `TMultiple` 결과 유형 (단일 또는 여러 결과 집합)을 지정 합니다.

[ATL OLE DB 소비자 마법사](../../atl/reference/atl-ole-db-consumer-wizard.md) 를 사용 하 여 명령 또는 테이블 개체를 사용할지 여부를 지정할 수 있습니다.

- 명령이 없는 데이터 원본의 경우 클래스를 사용할 수 있습니다 `CTable` . 일반적으로 매개 변수를 지정 하지 않고 여러 결과가 필요 하지 않은 간단한 행 집합에 사용 합니다. 이 간단한 클래스는 지정 된 테이블 이름을 사용 하 여 데이터 원본에서 테이블을 엽니다.

- 명령을 지 원하는 데이터 원본의 경우 클래스를 대신 사용할 수 있습니다 `CCommand` . 명령을 실행 하려면이 클래스에서 [Open](./ccommand-class.md#open) 을 호출 합니다. 대신를 호출 `Prepare` 하 여 두 번 이상 실행 하려는 명령을 준비할 수 있습니다.

   `CCommand` 에는 세 가지 템플릿 인수인 접근자 형식, 행 집합 형식 및 결과 형식 (기본적으로 `CNoMultipleResults` 또는)이 있습니다 `CMultipleResults` . 을 지정 하 `CMultipleResults` 는 경우 `CCommand` 클래스는 인터페이스를 지원 `IMultipleResults` 하 고 여러 행 집합을 처리 합니다. [DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) 샘플에서는 여러 결과를 처리 하는 방법을 보여 줍니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)
