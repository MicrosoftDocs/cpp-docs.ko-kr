---
description: '자세한 정보: OLE DB 응용 프로그램의 리소스 풀링'
title: OLE DB 애플리케이션의 리소스 풀링
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], resource pooling
- resource pooling [OLE DB], services
- OLE DB, resource pooling
- OLE DB providers, resource pooling
ms.assetid: 2ead1bcf-bbd4-43ea-a307-bb694b992fc1
ms.openlocfilehash: 504217092f4e4a19a3db2898b97e6a35269db7ba
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316871"
---
# <a name="resource-pooling-in-your-ole-db-application"></a>OLE DB 애플리케이션의 리소스 풀링

응용 프로그램에서 풀링을 활용 하려면 또는을 통해 데이터 소스를 가져와 OLE DB services가 호출 되는지 확인 해야 합니다 `IDataInitialize` `IDBPromptInitialize` . 를 직접 사용 하 여 `CoCreateInstance` 공급자의 CLSID를 기준으로 공급자를 호출 하는 경우 OLE DB 서비스가 호출 되지 않습니다.

OLE DB 서비스는 또는에 대 한 참조가 있거나 `IDataInitialize` 사용 중인 연결이 있는 동안 연결 된 데이터 원본의 풀을 유지 관리 합니다 `IDBPromptInitialize` . 또한 풀은 COM + 1.0 서비스 또는 인터넷 정보 서비스 (IIS) 환경 내에서 자동으로 유지 관리 됩니다. 응용 프로그램에서 COM + 1.0 서비스 또는 IIS 환경의 외부 풀링을 활용 하는 경우 하나 이상의 연결에 대 한 참조를 유지 하거나 하나 이상의 연결을 유지 해야 합니다 `IDataInitialize` `IDBPromptInitialize` . 응용 프로그램에서 마지막 연결을 해제할 때 풀이 소멸 되지 않도록 하려면 응용 프로그램의 수명 동안 참조를 유지 하거나 연결을 유지 합니다.

OLE DB 서비스는가 호출 될 때 연결을 그릴 풀을 식별 `Initialize` 합니다. 풀에서 연결을 가져온 후에는 다른 풀로 이동할 수 없습니다. 따라서를 `UnInitialize` `QueryInterface` 호출 하기 전에 공급자 특정 인터페이스에 대 한 호출 또는 호출과 같은 초기화 정보를 변경 하는 응용 프로그램에서 작업을 수행 하지 않도록 `Initialize` 합니다. 또한 DBPROMPT_NOPROMPT 아닌 프롬프트 값으로 설정 된 연결은 풀링되지 않습니다. 그러나 프롬프트를 통해 설정 된 연결에서 검색 된 초기화 문자열을 사용 하 여 동일한 데이터 원본에 대 한 추가 풀링된 연결을 설정할 수 있습니다.

일부 공급자는 각 세션에 대해 별도의 연결을 설정 해야 합니다. 이러한 추가 연결은 분산 트랜잭션에 별도로 참여 해야 합니다 (있는 경우). OLE DB 서비스는 데이터 원본 마다 단일 세션을 캐시 하 고 재사용 하지만 응용 프로그램이 단일 데이터 원본에서 한 번에 둘 이상의 세션을 요청 하는 경우 공급자는 추가 연결을 설정 하 고 풀링되지 않은 추가 트랜잭션 인 리스트 먼 트를 수행할 수 있습니다. 단일 데이터 원본에서 여러 세션을 만드는 것 보다 풀링된 환경에서 각 세션에 대해 별도의 데이터 원본을 만드는 것이 더 효율적입니다.

마지막으로 ADO에서 자동으로 OLE DB 서비스를 사용 하기 때문에 ADO를 사용 하 여 연결을 설정할 수 있으며 풀링 및 참여가 자동으로 수행 됩니다.

## <a name="see-also"></a>참고 항목

[OLE DB 리소스 풀링 및 서비스](../../data/oledb/ole-db-resource-pooling-and-services.md)
