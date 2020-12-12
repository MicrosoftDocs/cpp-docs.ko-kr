---
description: OLE DB 아키텍처 디자인 문제에 대해 자세히 알아보세요.
title: OLE DB 아키텍처 설계 문제
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: 2e6bd90b5d3c67fbdfb8cdfbb9c32af88ed106e6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286984"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB 아키텍처 설계 문제

> [!NOTE]
> Visual Studio 2019 이상에서는 ATL OLE DB 소비자 마법사를 사용할 수 없습니다. 수동으로 기능을 추가할 수는 있습니다. 자세한 내용은 [마법사를 사용하지 않고 소비자 만들기](creating-a-consumer-without-using-a-wizard.md)를 참조하세요.

OLE DB 애플리케이션을 시작하기 전에 다음 문제를 고려합니다.

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>OLE DB 애플리케이션을 작성하는 데 사용할 프로그래밍 구현

Microsoft에서는 OLE DB 템플릿 라이브러리, OLE DB 특성, OLE DB SDK의 원시 OLE DB 인터페이스 등 이 작업을 수행하는 여러 라이브러리를 제공합니다. 프로그램 작성을 도와주는 마법사도 있습니다. 이러한 구현에 대해서는 [OLE DB 템플릿, 특성 및 기타 구현](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)에서 설명합니다.

## <a name="do-you-need-to-write-your-own-provider"></a>고유한 공급자를 작성해야 하는지 여부

대부분의 개발자는 고유한 공급자를 작성할 필요가 없습니다. Microsoft에서 여러 공급자를 제공합니다. 데이터 연결을 만들 때마다(예: **ATL OLE DB 소비자 마법사** 를 사용하여 프로젝트에 소비자를 추가하는 경우) **데이터 연결 속성** 대화 상자에 시스템에 등록된 사용 가능한 모든 공급자가 나열됩니다. 공급자 중 하나가 고유한 데이터 저장소 및 데이터 액세스 애플리케이션에 적합한 경우 해당 공급자를 사용하는 것이 가장 편리합니다. 그러나 데이터 저장소가 이러한 범주 중 하나에 맞지 않는 경우 고유한 공급자를 만들어야 합니다. 공급자를 만드는 방법에 대한 자세한 내용은 [OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)을 참조하세요.

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>소비자에 필요한 지원 수준

기본적인 소비자도 있고, 복잡한 소비자도 있습니다. OLE DB 개체의 기능은 속성으로 지정됩니다. **ATL OLE DB 소비자 마법사** 를 사용하여 소비자를 만들거나 **데이터베이스 공급자 마법사** 를 사용하여 공급자를 만드는 경우, 마법사에서 적절한 개체 속성을 설정하여 표준 기능 집합을 제공합니다. 그러나 마법사 생성 소비자 또는 공급자 클래스에서 필요한 일부 기능을 지원하지 않는 경우 [OLE DB 템플릿 라이브러리](../../data/oledb/ole-db-templates.md)에서 해당 클래스의 인터페이스를 참조해야 합니다. 이러한 인터페이스는 원시 OLE DB 인터페이스를 래핑하여, 사용하기 편리하도록 추가 구현을 제공합니다.

예를 들어 행 집합의 데이터를 업데이트하려고 하는데 마법사를 사용하여 소비자를 만들 때 이 옵션을 지정하지 않은 경우, 명령 개체의 `DBPROP_IRowsetChange` 및 `DBPROP_UPDATABILITY` 속성을 설정하여 팩트 후에 기능을 지정할 수 있습니다. 그런 다음, 행 집합을 만들면 `IRowsetChange` 인터페이스가 표시됩니다.

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>다른 데이터 액세스 기술(ADO, ODBC 또는 DAO)을 사용하는 이전 코드가 있는지 여부

가능한 기술 조합(예: ADO 구성 요소와 OLE DB 구성 요소를 함께 사용, ODBC 코드를 OLE DB로 마이그레이션)을 고려할 때 모든 상황을 설명하는 것은 Visual C++ 설명서의 범위를 벗어납니다. 그러나 다음 Microsoft 웹 사이트에서 다양한 시나리오를 다루는 여러 문서를 확인할 수 있습니다.

- [Microsoft 도움말 및 지원](https://support.microsoft.com/)

- [Microsoft 데이터 액세스 기술 문서 개요](/previous-versions/ms810811(v=msdn.10))

## <a name="see-also"></a>참고 항목

[OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 프로그래밍 개요](../../data/oledb/ole-db-programming-overview.md)
