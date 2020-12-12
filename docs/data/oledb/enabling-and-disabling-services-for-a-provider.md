---
description: '자세한 정보: 공급자에 대 한 서비스 활성화 및 비활성화'
title: 공급자 서비스 사용 및 사용 안 함
ms.date: 07/30/2019
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 3deac1bb-f660-407a-92ef-95e139e280c0
ms.openlocfilehash: ead2ce9b8f1e678af00bcc03140c2868986a1564
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287543"
---
# <a name="enabling-and-disabling-services-for-a-provider"></a>공급자 서비스 사용 및 사용 안 함

단일 공급자에 액세스 하는 모든 응용 프로그램에 대해 기본적으로 개별 OLE DB 서비스를 사용 하거나 사용 하지 않도록 설정할 수 있습니다. 이 작업을 수행 하려면 다음 표에 나와 있는 것 처럼 공급자의 CLSID 아래에 OLEDB_SERVICES 레지스트리 항목을 추가 하 고 사용 하거나 사용 하지 않도록 설정할 서비스를 지정 하는 DWORD 값을 사용 합니다.

|기본 서비스 사용|DWORD 값|
|------------------------------|-------------------|
|클라이언트 커서 및 풀링을 제외한 모든 서비스|0xfffffffa|
|클라이언트 커서를 제외한 모든 서비스|0xfffffffb|
|풀링 및 자동 인 리스트 먼 트를 제외한 모든 서비스|0xfffffffc|
|풀링을 제외한 모든 서비스|0xfffffffe|
|모든 서비스 (기본값)|0xffffffff|
|서비스 없음|0x00000000|
|집계가 없습니다. 모든 서비스를 사용할 수 없습니다.|OLEDB_Services 레지스트리 항목이 없습니다.|

## <a name="see-also"></a>참고 항목

[OLE DB 서비스 사용 및 사용 안 함](../../data/oledb/enabling-and-disabling-ole-db-services.md)
