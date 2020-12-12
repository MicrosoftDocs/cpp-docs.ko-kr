---
description: '자세한 정보: 소비자 및 공급자 OLE DB'
title: OLE DB 소비자 및 공급자
ms.date: 10/22/2018
helpviewer_keywords:
- OLE DB providers, OLE DB data architecture
- OLE DB providers
- OLE DB consumers, OLE DB data architecture
- OLE DB consumers
- OLE DB, data model
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
ms.openlocfilehash: dedcbe7837cf7fad5bc9db8832e34edd3859a02b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97317144"
---
# <a name="ole-db-consumers-and-providers"></a>OLE DB 소비자 및 공급자

OLE DB 아키텍처는 소비자와 공급자의 모델을 사용 합니다. 소비자는 데이터에 대 한 요청을 만듭니다. 공급자는 데이터를 테이블 형식으로 배치 하 고 소비자에 게 반환 하 여 이러한 요청에 응답 합니다. 소비자가 만들 수 있는 모든 호출은 공급자에서 구현 되어야 합니다.

기술적으로 정의 된 소비자는 OLE DB 인터페이스를 통해 데이터에 액세스 하는 시스템 또는 응용 프로그램 코드 (반드시 OLE DB 구성 요소는 아님)입니다. 인터페이스는 공급자에서 구현 됩니다. 따라서 공급자는 데이터에 대 한 액세스를 캡슐화 하 고 다른 개체 (즉, 소비자)에 노출 하는 OLE DB 인터페이스를 구현 하는 소프트웨어 구성 요소입니다.

역할의 경우 소비자는 OLE DB 인터페이스에서 메서드를 호출 합니다. OLE DB 공급자는 필요한 OLE DB 인터페이스를 구현 합니다.

이러한 역할은 특히 n 계층 상황에서 항상 적합 한 것은 아니므로 클라이언트와 서버 라는 용어를 사용 하지 않도록 OLE DB. 소비자는 다른 구성 요소를 제공 하는 계층의 구성 요소 일 수 있기 때문에 클라이언트 구성 요소를 호출 하는 것은 혼란 스 러 울 것입니다. 또한 공급자는 서버 보다 데이터베이스 드라이버와 같은 역할을 하기도 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 프로그래밍](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB 프로그래밍 개요](../../data/oledb/ole-db-programming-overview.md)
