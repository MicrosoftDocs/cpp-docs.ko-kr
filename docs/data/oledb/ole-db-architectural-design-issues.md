---
title: OLE DB 아키텍처 설계 문제 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2b0a5c568a774d0aed05d702454664e653989401
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43676838"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 아키텍처 설계 문제
OLE DB 응용 프로그램을 시작 하기 전에 다음과 같은 문제를 고려해 야 합니다.  
  
 **OLE DB 응용 프로그램을 작성 하는 프로그래밍 구현을 사용할 것인가?**  
 Microsoft는이 위해 몇 가지 라이브러리를 제공 합니다: OLE DB 템플릿 라이브러리를, OLE DB 특성 및 OLE DB SDK에서 원시 OLE DB 인터페이스입니다. 또한 마법사가 프로그램을 작성 하는 데 도움이 되도록 합니다. 이러한 구현에 설명 되어 있습니다 [OLE DB 템플릿, 특성 및 기타 구현](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)합니다.  
  
 **고유한 공급자를 작성 해야 하나요?**  
 대부분의 개발자는 고유한 공급자를 작성할 필요가 없습니다. Microsoft는 여러 공급자를 제공합니다. (예를 들어 소비자 ATL OLE DB 소비자 마법사를 사용 하 여 프로젝트를 추가할 때), 데이터 연결을 만들 때마다 합니다 **데이터 연결 속성** 대화 상자에 시스템에 등록 된 모든 사용 가능한 공급자를 나열 합니다. 사용자 고유의 데이터 저장소 및 데이터 액세스 응용 프로그램에 대 한 적절 한 경우 이러한 공급자 중 하나는 가장 쉬운 방법은 다음 중 하나를 사용 합니다. 그러나 데이터 저장소에 이러한 범주 중 하나를 맞지 경우 고유한 공급자를 만들려고 합니다. 공급자를 만드는 방법에 대 한 자세한 내용은 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)합니다.  
  
 **소비자에 대 한 어떤 수준의 지원이 필요 한가요?**  
 일부 소비자는 매우 기본적인; 수 합니다. 하지만 다른 매우 복잡할 수 있습니다. OLE DB 개체의 기능 속성으로 지정 됩니다. ATL OLE DB 소비자 마법사를 사용 하 여 소비자를 만들거나 데이터베이스 공급자 마법사 공급자를 만들 때 표준 집합 기능을 제공 하 여 적절 한 개체 속성을 설정 합니다. 그러나 마법사 생성 소비자 또는 공급자 클래스를 지원 하지 않아도 되 작업을 수행 하 고 모든 경우에서 해당 클래스에 대 한 인터페이스를 참조 하는 [OLE DB 템플릿 라이브러리](../../data/oledb/ole-db-templates.md)합니다. 이러한 인터페이스를 사용 하 여 쉽게를 추가로 구현 제공 원시 OLE DB 인터페이스를 래핑합니다.  
  
 예를 들어, 행 집합의 데이터를 업데이트 하려고 하지만 경우 마법사를 사용 하 여 소비자를 만든 경우이 값을 지정 하지 않았습니다 수 기능을 사후 설정 하 여 지정 된 `DBPROP_IRowsetChange` 및 `DBPROP_UPDATABILITY` 명령 개체의 속성입니다. 그런 다음 행 집합 만들어질 때에 `IRowsetChange` 인터페이스입니다.  
  
 **다른 데이터 액세스 기술 (예: ADO, ODBC 또는 DAO)를 사용 하 여 이전 코드 있습니까?**  
 기술 (예: ADO 구성 요소를 사용 하 여 OLE DB 구성 요소를 사용 하 여 및 ODBC 코드 OLE DB로 마이그레이션)의 가능한 조합 지정, Visual c + + 설명서의 범위를 벗어납니다 모든 상황을 포함 합니다. 그러나 다양 한 시나리오를 다루는 여러 문서 다음 Microsoft 웹 사이트에서 사용할 수 있습니다.  
  
-   [Microsoft 도움말 및 지원](https://support.microsoft.com/)  
  
-   [Microsoft 데이터 액세스 기술 문서 개요](https://msdn.microsoft.com/en-us/library/ms810811.aspx)  
  
## <a name="see-also"></a>참고 항목  
 [OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)   
 [OLE DB 프로그래밍 개요](../../data/oledb/ole-db-programming-overview.md)