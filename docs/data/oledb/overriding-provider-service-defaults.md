---
title: 공급자 서비스 기본값 재정의
ms.date: 11/04/2016
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: 9bd202a1e913bf624332e7a6499557851b0285ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588069"
---
# <a name="overriding-provider-service-defaults"></a>공급자 서비스 기본값 재정의

OLEDB_SERVICES에 대 한 공급자의 레지스트리 값에 대 한 기본 값으로 반환 됩니다 합니다 [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898) 데이터 원본 개체의 초기화 속성입니다.

레지스트리 항목이 존재 공급자의 개체가 집계 되 고 사용자는 공급자의 기본 설정 하 여 사용된 하는 서비스에 대 한 설정을 재정의할 수는 `DBPROP_INIT_OLEDBSERVICES` 초기화 전에 속성입니다. 를 사용 하거나 특정 서비스를 사용 하지 않도록 설정 하려면 사용자 일반적으로 현재 값을 가져옵니다는 `DBPROP_INIT_OLEDBSERVICES` 속성 설정 또는 특정 속성 활성화 또는 비활성화에 대 한 비트를 지웁니다 및 속성을 다시 설정 합니다. `DBPROP_INIT_OLEDBSERVICES` OLE DB 또는 ADO에 전달 된 연결 문자열에서 직접 설정할 수 있습니다 또는 `IDataInitialize::GetDatasource`합니다. 개별 서비스 활성화/비활성화를 해당 값은 다음 표에 나열 됩니다.

|기본 서비스를 사용 하도록 설정|DBPROP_INIT_OLEDBSERVICES 속성 값|연결 문자열 값|
|------------------------------|------------------------------------------------|--------------------------------|
|모든 서비스 (기본값)|`DBPROPVAL_OS_ENABLEALL`|"OLE DB 서비스-1 ="|
|풀링 제외한 모든 지역 및 AutoEnlistment|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB 서비스-; 4 ="|
|클라이언트 커서 제외한 모든 지역|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB 서비스-; 5 ="|
|풀링, AutoEnlistment, 및 클라이언트 커서를 제외한 모든|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB 서비스-7; ="|
|서비스가 없습니다|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB 서비스 = 0;"|

공급자에 대 한 레지스트리 항목이 없으면 구성 요소 관리자는 공급자의 개체를 집계 되 고 사용자가 명시적으로 요청 서비스가 호출 됩니다.

## <a name="see-also"></a>참고 항목

[리소스 풀링](/previous-versions/windows/desktop/ms713655)<br/>
[리소스 풀링을 소비자를 사용 하는 방법](/previous-versions/windows/desktop/ms715907)<br/>
[공급자를 사용 방법을 효과적으로 리소스 풀링](/previous-versions/windows/desktop/ms714906)<br/>
[OLE DB 서비스 사용 및 사용 안 함](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>