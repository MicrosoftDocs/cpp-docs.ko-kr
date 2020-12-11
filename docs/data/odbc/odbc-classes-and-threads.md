---
description: '자세한 정보: ODBC 클래스 및 스레드'
title: ODBC 클래스와 스레드
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
ms.openlocfilehash: bff5ef5a53543b2e0ffa7888f469ed4ce1e54a37
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97161080"
---
# <a name="odbc-classes-and-threads"></a>ODBC 클래스와 스레드

MFC 4.2부터 MFC ODBC 클래스에 대 한 다중 스레딩 지원이 있습니다. 그러나 MFC는 DAO 클래스에 대 한 다중 스레딩 지원을 제공 하지 않습니다.

ODBC 클래스에 대 한 다중 스레딩 지원에는 몇 가지 제한 사항이 있습니다. 이러한 클래스는 ODBC API를 래핑 하므로 이러한 클래스는 작성 되는 구성 요소의 다중 스레딩 지원으로 제한 됩니다. 예를 들어 많은 ODBC 드라이버는 스레드로부터 안전 하지 않습니다. 따라서 이러한 드라이버 중 하나에서 MFC ODBC 클래스를 사용 하는 경우이 클래스는 스레드로부터 안전 하지 않습니다. 특정 드라이버가 스레드로부터 안전한 지 여부를 확인 해야 합니다.

다중 스레드 응용 프로그램을 만들 때 여러 스레드를 사용 하 여 동일한 개체를 조작 하는 데 매우 주의 해야 합니다. 예를 들어 두 스레드에 동일한 개체를 사용 하면 `CRecordset` 데이터를 검색할 때 문제가 발생할 수 있습니다. 한 스레드의 인출 작업이 다른 스레드에서 인출 된 데이터를 덮어쓸 수 있습니다. 별도의 스레드에서 MFC ODBC 클래스를 보다 일반적으로 사용 하는 것은 `CDatabase` 각 스레드에서 별도의 개체를 사용 하 여 동일한 ODBC 연결을 사용 하기 위해 여러 스레드에서 열린 개체를 공유 하는 것입니다 `CRecordset` . 열려 있지 않은 `CDatabase` 개체를 다른 스레드의 개체에 전달 하면 안 `CRecordset` 됩니다.

> [!NOTE]
> 여러 스레드가 동일한 개체를 조작 해야 하는 경우에는 중요 한 섹션과 같은 적절 한 동기화 메커니즘을 구현 해야 합니다. 와 같은 특정 작업 `Open` 은 보호 되지 않습니다. 이러한 작업은 별도의 스레드에서 동시에 호출 되지 않아야 합니다.

다중 스레드 응용 프로그램을 만드는 방법에 대 한 자세한 내용은 [다중 스레딩 항목](../../parallel/multithreading-support-for-older-code-visual-cpp.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[ODBC (Open Database Connectivity)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[데이터 액세스 프로그래밍 (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)
