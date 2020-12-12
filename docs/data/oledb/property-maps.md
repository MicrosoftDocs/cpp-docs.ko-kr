---
description: '자세히 알아보기: 속성 맵'
title: 속성 맵
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 30b277451d871de45902661f7b7e56cbc7409c97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316910"
---
# <a name="property-maps"></a>속성 맵

Session, rowset 및 optional command 개체를 사용 하 여 각 공급자는 하나 이상의 속성을 지원 합니다. 이러한 속성은 **OLE DB 공급자 마법사** 에서 만든 헤더 파일에 저장 된 속성 맵에 정의 됩니다. 각 헤더 파일에는 해당 파일에 정의 된 개체에 대해 정의 된 OLE DB 속성 그룹의 속성에 대 한 맵이 포함 되어 있습니다. 데이터 원본 개체를 포함 하는 헤더 파일에도 [DataSource 속성](/previous-versions/windows/desktop/ms724188(v=vs.85))에 대 한 속성 맵이 포함 됩니다. `Session.h`[세션 속성](/previous-versions/windows/desktop/ms714221(v=vs.85))에 대 한 속성 맵을 포함 합니다. 행 집합 및 명령 개체는 *projectname* RS. h 라는 단일 헤더 파일에 있습니다. 이러한 속성은 [행 집합 속성](/previous-versions/windows/desktop/ms711252(v=vs.85)) 그룹의 멤버입니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
