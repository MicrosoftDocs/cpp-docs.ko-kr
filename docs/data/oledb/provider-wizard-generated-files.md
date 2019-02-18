---
title: 공급자 마법사가 생성하는 파일
ms.date: 10/18/2018
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: c93618ebe9d3140864c2c47867ea970777c208b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580936"
---
# <a name="provider-wizard-generated-files"></a>공급자 마법사가 생성하는 파일

**ATL OLE DB 공급자 마법사**는 다음과 같은 파일을 생성합니다. 다음 항목에서는 *사용자 지정* 약식 이름을 사용하지만 정확한 파일 이름은 공급자를 만들 때 입력한 이름에 따라 다릅니다.

|파일 이름|설명|
|---------------|-----------------|
|*사용자 지정*RS.cpp|명령 도우미 `Execute` 메서드와 공급자 열 맵이 있습니다.|
|*사용자 지정*DS.h|데이터 소스 개체를 구현합니다. 이 헤더 파일에는 데이터 소스 속성에 대한 속성 맵이 있습니다.|
|*사용자 지정*RS.h|명령 개체와 행 집합 개체를 구현합니다. 이 헤더 파일에는 행 집합과 명령 속성에 대한 속성 맵이 있습니다.|
|*사용자 지정*Sess.h|세션 개체를 구현합니다. 이 헤더 파일에는 세션 속성에 대한 속성 맵이 있습니다.|
|*사용자 지정*.rgs|**OLE DB 공급자 마법사**가 생성한 등록된 개체가 있습니다.|

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 만들기](../../data/oledb/creating-an-ole-db-provider.md)<br/>
