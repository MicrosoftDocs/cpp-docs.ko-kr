---
title: OLE DB 템플릿, 특성 및 기타 구현
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB, implementations
- OLE DB templates, about OLE DB templates
- OLE DB templates
ms.assetid: 0c780c1b-9bba-4788-8c33-8552d9f120ac
ms.openlocfilehash: 217db304c7d0b5723b7af383e07290f160cc9465
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500917"
---
# <a name="ole-db-templates-attributes-and-other-implementations"></a>OLE DB 템플릿, 특성 및 기타 구현

## <a name="atl-ole-db-templates"></a>ATL OLE DB 템플릿

ATL (액티브 템플릿 라이브러리)의 일부인 OLE DB 템플릿은 일반적으로 사용 되는 많은 OLE DB 인터페이스를 구현 하는 클래스를 제공 하 여 고성능 OLE DB 데이터베이스 기술을 더 쉽게 사용할 수 있도록 합니다. 이 템플릿 라이브러리와 함께 OLE DB 시작 응용 프로그램을 만들기 위한 마법사 지원이 제공 됩니다.

이 템플릿 라이브러리는 다음 두 부분으로 구성 됩니다.

- **OLE DB 소비자 템플릿** 소비자 (OLE DB 클라이언트) 응용 프로그램을 구현 하는 데 사용 됩니다.

- **OLE DB 공급자 템플릿** OLE DB 서버 (공급자) 응용 프로그램을 구현 하는 데 사용 됩니다.

OLE DB 템플릿을 사용하려면 C++ 템플릿, COM 및 OLE DB 인터페이스에 대해 잘 알고 있어야 합니다. OLE DB에 익숙하지 않은 경우 [OLE DB 프로그래머 참조](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)를 참조 하세요.

자세한 내용은 다음을 수행할 수 있습니다.

- [OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md) 또는 [OLE DB 공급자 템플릿에](../../data/oledb/ole-db-provider-templates-cpp.md)대 한 항목을 참조 하세요.

- [OLE DB 소비자](../../data/oledb/creating-an-ole-db-consumer.md) 또는 [OLE DB 공급자](../../data/oledb/creating-an-ole-db-provider.md)를 만듭니다.

- [OLE DB 소비자 클래스](../../data/oledb/ole-db-consumer-templates-reference.md) 목록 또는 [공급자 클래스 OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)를 참조 하세요.

- [OLE DB 템플릿 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)목록을 참조 하세요.

- [OLE DB 프로그래머 참조](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) (Windows SDK)를 참조 하세요.

## <a name="ole-db-attributes"></a>OLE DB 특성

[OLE DB 소비자 특성](../../windows/attributes/ole-db-consumer-attributes.md) 은 OLE DB 소비자를 만드는 편리한 방법을 제공 합니다. OLE DB 특성은 [OLE DB 소비자 템플릿을](../../data/oledb/ole-db-consumer-templates-reference.md) 기반으로 하는 코드를 삽입 하 여 작업 OLE DB 소비자 및 공급자를 만듭니다. 특성에서 지원 하지 않는 기능을 지정 해야 하는 경우 OLE DB 템플릿을 코드의 특성과 함께 사용할 수 있습니다.

## <a name="mfc-ole-db-classes"></a>MFC OLE DB 클래스

MFC 라이브러리에는 컨트롤에 데이터베이스 레코드를 표시 하는 [Coledbrecordview](../../mfc/reference/coledbrecordview-class.md)클래스가 하나 있습니다. 뷰는 개체에 직접 연결 된 폼 뷰입니다 `CRowset` `CRowset` . 대화 상자 템플릿의 컨트롤에 개체의 필드를 표시 합니다. 또한 첫 번째, 다음, 이전 또는 마지막 레코드로 이동 하는 기본 구현을 제공 하 고 현재 보기에서 레코드를 업데이트 하기 위한 인터페이스를 제공 합니다. 자세한 내용은 `COleDBRecordView`를 참조하세요.

## <a name="ole-db-sdk-interfaces"></a>OLE DB SDK 인터페이스

OLE DB 템플릿이 OLE DB 기능을 지원 하지 않는 경우 OLE DB 인터페이스 자체를 사용 해야 합니다. 자세한 내용은 Windows SDK [OLE DB 프로그래머 참조](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 프로그래밍 개요](../../data/oledb/ole-db-programming-overview.md)
