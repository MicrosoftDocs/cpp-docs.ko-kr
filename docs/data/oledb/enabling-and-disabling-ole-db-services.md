---
description: '자세한 정보: OLE DB 서비스 사용 및 사용 안 함'
title: OLE DB 서비스 사용 및 사용 안 함
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: a2a3e51b69a0051b6a231d14c18f3b1f416fb547
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317664"
---
# <a name="enabling-and-disabling-ole-db-services"></a>OLE DB 서비스 사용 및 사용 안 함

OLE DB 서비스 구성 요소 관리자는 소비자가 지정한 속성을 공급자가 지 원하는 속성과 비교 하 여 소비자가 요청한 확장 된 기능을 충족 하는 데 개별 서비스 구성 요소를 사용할 수 있는지 여부를 확인 합니다. 예를 들어 응용 프로그램이 스크롤 가능 커서를 요청 하 고 공급자가 앞 으로만 이동 가능한 커서를 지 원하는 경우 서비스 구성 요소 관리자는 클라이언트 커서 엔진 서비스 구성 요소를 사용 하 여 스크롤 가능한 기능을 제공 합니다. 응용 프로그램이 기본적으로 공급자의 행 집합에서 지원 되는 확장 기능에 의존 하 고 응용 프로그램에서 해당 기능을 요청 하는 속성을 명시적으로 설정 하지 않은 경우 클라이언트 커서 엔진에서 반환 된 행 집합에 해당 기능이 표시 되지 않을 수 있습니다. 상호 운용성을 위해 응용 프로그램은 필요한 경우 확장 기능을 명시적으로 요청 하는 속성을 항상 설정 해야 합니다.

일부 경우에는 개별 OLE DB 서비스가 공급자의 특성을 가정 하는 기존 응용 프로그램에서 잘 작동 하지 않도록 설정 해야 할 수 있습니다. OLE DB 서비스는 개별 서비스를 사용 하지 않도록 설정 하거나 단일 공급자를 사용 하는 모든 응용 프로그램에 대 한 연결을 설정 하거나 모든 서비스를 사용 하지 않도록 설정 하는 기능을 제공 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 리소스 풀링 및 서비스](../../data/oledb/ole-db-resource-pooling-and-services.md)
