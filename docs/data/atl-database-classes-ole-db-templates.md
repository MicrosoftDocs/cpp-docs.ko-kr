---
description: '자세한 정보: ATL 데이터베이스 클래스 (OLE DB 템플릿)'
title: ATL 데이터베이스 클래스(OLE DB 템플릿)
ms.date: 05/02/2019
helpviewer_keywords:
- OLE DB templates [C++], ATL database classes
- database classes [C++], OLE DB
- database classes [C++], ATL
ms.assetid: 219766aa-e18a-405f-9e36-d7a0fdb31b2b
ms.openlocfilehash: a9cc532a0b49f591cd08c70c398f8a37c08071ee
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97213223"
---
# <a name="atl-database-classes-ole-db-templates"></a>ATL 데이터베이스 클래스(OLE DB 템플릿)

Microsoft는 다양 한 정보 소스 및 형식의 데이터에 대 한 일관 된 액세스를 제공 하는 일련의 COM 인터페이스를 제공 하는 여러 OLE DB 구현을 제공 합니다.

OLE DB 템플릿은 일반적으로 사용 되는 많은 OLE DB 인터페이스를 구현 하는 클래스를 제공 하 여 OLE DB 데이터베이스 기술을 더 쉽게 사용할 수 있게 해 주는 ATL의 c + + 템플릿입니다.

이 템플릿 라이브러리는 다음 두 부분으로 구성 됩니다.

- [OLE DB 소비자 템플릿](../data/oledb/ole-db-consumer-templates-cpp.md) 소비자 (OLE DB 클라이언트) 응용 프로그램을 구현 하는 데 사용 됩니다.

- [OLE DB 공급자 템플릿](../data/oledb/ole-db-provider-templates-cpp.md) OLE DB 서버 (공급자) 응용 프로그램을 구현 하는 데 사용 됩니다.

또한 [OLE DB 소비자 특성](../windows/attributes/ole-db-consumer-attributes.md) 은 OLE DB 소비자를 만드는 편리한 방법을 제공 합니다. OLE DB 특성은 OLE DB 소비자 템플릿을 기반으로 하는 코드를 삽입 하 여 작업 OLE DB 소비자를 만듭니다.

MFC 라이브러리에는 컨트롤에 데이터베이스 레코드를 표시 하는 [Coledbrecordview](../mfc/reference/coledbrecordview-class.md)클래스가 하나 있습니다. 뷰는 개체에 직접 연결 된 폼 뷰입니다 `CRowset` `CRowset` . 대화 상자 템플릿의 컨트롤에 개체의 필드를 표시 합니다.

자세한 내용은 [OLE DB 프로그래밍](../data/oledb/ole-db-programming.md) 및 [OLE DB 프로그래머 가이드](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 만들기](../data/oledb/creating-an-ole-db-consumer.md)<br/>
[OLE DB 공급자 만들기](../data/oledb/creating-an-ole-db-provider.md)<br/>
[OLE DB 소비자 템플릿 참조](../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[OLE DB 공급자 템플릿 참조](../data/oledb/ole-db-provider-templates-reference.md)<br/>
[OLE DB 템플릿 샘플](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB)
