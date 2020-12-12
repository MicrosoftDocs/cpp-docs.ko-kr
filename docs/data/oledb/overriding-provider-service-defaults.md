---
description: '자세한 정보: 공급자 서비스 기본값 재정의'
title: 공급자 서비스 기본값 재정의
ms.date: 10/29/2018
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
ms.openlocfilehash: eca6045c347ee8dc9295540d17bfc8feb225a73b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316923"
---
# <a name="overriding-provider-service-defaults"></a>공급자 서비스 기본값 재정의

OLEDB_SERVICES에 대 한 공급자의 레지스트리 값은 데이터 원본 개체의 [DBPROP_INIT_OLEDBSERVICES](/previous-versions/windows/desktop/ms716898(v=vs.85)) 초기화 속성에 대 한 기본값으로 반환 됩니다.

레지스트리 항목이 있는 한 공급자의 개체는 집계 됩니다. 사용자는 초기화 전에 DBPROP_INIT_OLEDBSERVICES 속성을 설정 하 여 사용 가능한 서비스에 대 한 공급자의 기본 설정을 재정의할 수 있습니다. 특정 서비스를 사용 하거나 사용 하지 않도록 설정 하기 위해 사용자는 DBPROP_INIT_OLEDBSERVICES 속성의 현재 값을 가져오거나, 특정 속성을 사용 하거나 사용 하지 않도록 비트를 설정 또는 해제 하 고, 속성을 다시 설정 합니다. DBPROP_INIT_OLEDBSERVICES는 OLE DB 또는 ADO 또는에 전달 된 연결 문자열에서 직접 설정할 수 있습니다 `IDataInitialize::GetDatasource` . 개별 서비스를 사용 하거나 사용 하지 않도록 설정 하는 해당 값은 다음 표에 나와 있습니다.

|기본 서비스 사용|DBPROP_INIT_OLEDBSERVICES 속성 값|연결 문자열의 값|
|------------------------------|------------------------------------------------|--------------------------------|
|모든 서비스 (기본값)|DBPROPVAL_OS_ENABLEALL|"OLE DB Services =-1;"|
|풀링 및 자동 인 리스트 먼 트를 제외한 모든|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"OLE DB Services =-4;"|
|클라이언트 커서를 제외한 모든 커서|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-5;"|
|풀링, AutoEnlistment 및 클라이언트 커서를 제외한 모든|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"OLE DB Services =-7;"|
|서비스 없음|`~DBPROPVAL_OS_ENABLEALL`|"OLE DB Services = 0;"|

공급자에 대 한 레지스트리 항목이 존재 하지 않는 경우 구성 요소 관리자는 공급자의 개체를 수집 하지 않습니다. 사용자가 명시적으로 요청한 경우에도 서비스는 설정 되지 않습니다.

## <a name="see-also"></a>참고 항목

[리소스 풀링](/previous-versions/windows/desktop/ms713655(v=vs.85))<br/>
[소비자가 리소스 풀링을 사용 하는 방법](/previous-versions/windows/desktop/ms715907(v=vs.85))<br/>
[공급자가 리소스 풀링을 효과적으로 사용 하는 방법](/previous-versions/windows/desktop/ms714906(v=vs.85))<br/>
[OLE DB 서비스 사용 및 사용 안 함](../../data/oledb/enabling-and-disabling-ole-db-services.md)<br/>
