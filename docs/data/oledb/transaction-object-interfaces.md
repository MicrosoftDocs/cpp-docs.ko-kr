---
description: '자세한 정보: 트랜잭션 개체 인터페이스'
title: 트랜잭션 개체 인터페이스
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: bc8eec6ca5a962e825eafa12255d8a47a8a463f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97272645"
---
# <a name="transaction-object-interfaces"></a>트랜잭션 개체 인터페이스

트랜잭션 개체는 데이터 원본에 대 한 원자 단위 작업을 정의 하 고 이러한 작업 단위가 서로 어떻게 관련 되는지를 결정 합니다. 이 개체는 OLE DB 공급자 템플릿에서 직접 지원 되지 않습니다. 즉, 고유한 개체를 만들어야 합니다.

다음 표에서는 트랜잭션 개체에 대 한 OLE DB에서 정의 된 필수 및 선택적 인터페이스를 보여 줍니다.

|인터페이스|필수 여부|OLE DB 템플릿에서 구현 됩니까?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|필수|아니요|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|필수|아니요|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|선택 사항|아니요|

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
