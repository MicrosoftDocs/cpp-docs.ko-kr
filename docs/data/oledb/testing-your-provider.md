---
description: '자세한 정보: 공급자 테스트'
title: 공급자 테스트
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: de9ba1b6cb66df8041cc6a94f357d52fc2194553
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272658"
---
# <a name="testing-your-provider"></a>공급자 테스트

공급자를 해제 하기 전에 다음 테스트를 표시 된 순서 대로 수행 해야 합니다. 이러한 테스트는 공급자가 대부분의 잠재적 사용자에 대해 제대로 작동 하는 것을 보여 줍니다.

1. OLE DB 소비자 템플릿으로 작성 된 [소비자](../../data/oledb/creating-an-ole-db-consumer.md) 응용 프로그램을 사용 하 여 공급자를 테스트 합니다. 테스트 소비자는 공급자의 모든 기능 영역 (추가 하거나 수정한 모든 코드)을 포함 해야 합니다.

1. ADO를 사용 하 여 작성 된 소비자 응용 프로그램을 사용 하 여 공급자를 테스트 합니다. 대부분의 개발자 (특히 Microsoft Visual Basic 및 Microsoft c # 개발자)는 소비자 응용 프로그램에 ADO 또는 ADO.NET를 사용 합니다. 테스트 소비자는 공급자의 모든 기능 영역을 포함 해야 합니다. ADO 소비자 응용 프로그램의 예제는 [Microsoft Visual Basic의 Ado 코드 예제](/previous-versions/ms807514(v=msdn.10))를 참조 하세요.

1. OLE DB 규칙 테스트 (ADO 규칙 테스트 포함)를 실행 하 여 공급자가 OLE DB 공급자에 대해 수준 0 표준을 충족 하는지 표시 합니다. 수준 0에 대 한 설명은 [OLE DB 프로그래머 가이드](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)에서 **OLE DB 수준 0 규칙 테스트** 를 검색 합니다. 이러한 테스트 및 관련 설명서는 데이터 액세스 SDK에 Visual C++ 포함 되어 있습니다. 이러한 테스트는 다른 [서비스 공급자](../../data/oledb/ole-db-resource-pooling-and-services.md) 가 집계할 때 공급자가 제대로 실행 되 고 있는지를 표시 하는 데도 도움이 되며 특히 속성을 수정 하거나 추가 하는 경우 유용 합니다. 규칙 테스트에 대 한 자세한 내용은 Visual Studio Cd 중 하나에 있는 Data Access SDK의 추가 정보 파일을 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 사용](../../data/oledb/working-with-ole-db-provider-templates.md)
