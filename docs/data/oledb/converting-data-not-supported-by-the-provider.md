---
description: '자세한 정보: 공급자가 지원 하지 않는 데이터 변환'
title: 공급자가 지원하지 않는 데이터 변환
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB provider templates, unsupported data types
ms.assetid: f495e50f-530a-4fab-ab54-e0c359785845
ms.openlocfilehash: 9fb449247ff40118e89dbebee5f43a1208a1f181
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323368"
---
# <a name="converting-data-not-supported-by-the-provider"></a>공급자가 지원하지 않는 데이터 변환

소비자가 공급자가 지원 하지 않는 데이터 형식을 요청 하는 경우 호출에 대 한 OLE DB 공급자 템플릿 코드 `IRowsetImpl::GetData` Msdadc.dll 데이터 형식을 변환 합니다.

데이터를 변환 해야 하는 것과 같은 인터페이스를 구현 하는 경우 `IRowsetChange` Msdaenum.dll를 호출 하 여 변환을 수행할 수 있습니다. `GetData`Atldb.h에 정의 된를 예로 사용 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 사용](../../data/oledb/working-with-ole-db-provider-templates.md)
