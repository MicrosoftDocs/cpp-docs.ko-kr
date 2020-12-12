---
description: 리소스 풀링 및 서비스 OLE DB에 대해 자세히 알아보세요.
title: OLE DB 리소스 풀링 및 서비스
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 1a66a6a616ed67e70fb10fa1bf43dac634051325
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97286789"
---
# <a name="ole-db-resource-pooling-and-services"></a>OLE DB 리소스 풀링 및 서비스

OLE DB 풀링이 나 OLE DB 서비스에서 잘 작동 하려면 공급자가 모든 개체의 집계를 지원 해야 합니다. 이는 OLE DB 1.5 이상의 공급자에 대 한 요구 사항입니다. 서비스를 활용 하는 것이 중요 합니다. 집계를 지원 하지 않는 공급자는 풀링할 수 없으며 추가 서비스가 제공 되지 않습니다.

풀링된 경우 공급자는 자유 스레드 모델을 지원 해야 합니다. 리소스 풀은 DBPROP_THREADMODEL 속성에 따라 공급자의 스레드 모델을 결정 합니다.

데이터 소스가 초기화 된 상태에서 변경 될 수 있는 전역 연결 상태가 공급자에 있는 경우 새 DBPROP_RESETDATASOURCE 속성을 지원 해야 합니다. 이 속성은 연결이 다시 사용 되기 전에 호출 되며, 공급자에 게 다음에 사용 되기 전에 상태를 정리할 수 있는 기회를 제공 합니다. 공급자가 연결과 관련 된 일부 상태를 정리할 수 없는 경우 속성에 대 한 DBPROPSTATUS_NOTSETTABLE를 반환할 수 있으며 연결이 다시 사용 되지 않습니다.

원격 데이터베이스에 연결 하 고 연결이 끊어질 수 있는지 여부를 검색할 수 있는 공급자는 DBPROP_CONNECTIONSTATUS 속성을 지원 해야 합니다. 이 속성은 OLE DB 서비스에서 중단 된 연결을 검색 하 고 풀로 반환 되지 않는지 확인 하는 기능을 제공 합니다.

마지막으로, 자동 트랜잭션 인 리스트 먼 트는 풀링이 발생 하는 동일한 수준에서 구현 되지 않는 한 일반적으로 작동 하지 않습니다. 자동 트랜잭션 인 리스트 먼 트를 지 원하는 공급자는 DBPROP_INIT_OLEDBSERVICES 속성을 노출 하 고 DBPROPVAL_OS_TXNENLISTMENT 선택 취소 된 경우 인 리스트 먼 트를 해제 하 여이 인 리스트 먼 트 비활성화

## <a name="see-also"></a>참고 항목

[고급 공급자 기술](../../data/oledb/advanced-provider-techniques.md)
