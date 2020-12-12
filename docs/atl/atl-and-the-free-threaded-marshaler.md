---
description: ATL 및 자유 스레드된 마샬러에 대해 자세히 알아보세요.
title: ATL 및 자유 스레드된 마샬러
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, free threaded marshaler
- free threaded marshaler
- threading [C++], marshaler in ATL
- threading [ATL], free threaded marshaler
- FTM in ATL
ms.assetid: 2db88a13-2217-4ebc-aa7e-432d5da902eb
ms.openlocfilehash: 01fb54386b5f48c8e49cc805e047c0faf8b0c39b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166072"
---
# <a name="atl-and-the-free-threaded-marshaler"></a>ATL 및 자유 스레드된 마샬러

ATL 단순 개체 마법사의 특성 페이지는 클래스가 자유 스레드 마샬러 (FTM)를 집계할 수 있도록 하는 옵션을 제공 합니다.

마법사는에서 자유 스레드 마샬러의 인스턴스를 만들고이 인스턴스를 해제 하는 코드를 생성 `FinalConstruct` `FinalRelease` 합니다. `QueryInterface` [IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal) 에 대 한 요청이 자유 스레드 마샬러에 의해 처리 되도록 COM_INTERFACE_ENTRY_AGGREGATE 매크로가 자동으로 COM 맵에 추가 됩니다.

자유 스레드된 마샬러를 사용 하면 동일한 프로세스의 모든 스레드에서 개체의 인터페이스에 직접 액세스 하 여 아파트 간 호출 속도를 향상 시킬 수 있습니다. 이 옵션은 두 스레딩 모델을 모두 사용 하는 클래스를 위한 것입니다.

이 옵션을 사용 하는 경우 클래스는 데이터의 스레드로부터의 안전성에 대 한 책임을 져야 합니다. 또한 자유 스레드 마샬러를 집계 하 고 다른 개체에서 얻은 인터페이스 포인터를 사용 해야 하는 개체는 인터페이스가 올바르게 마샬링되는 추가 단계를 수행 해야 합니다. 일반적으로이 작업에는 인터페이스 포인터를 GIT (전역 인터페이스 테이블)에 저장 하 고 사용할 때마다 GIT에서 포인터를 가져오는 작업이 포함 됩니다. ATL은 GIT에 저장 된 인터페이스 포인터를 사용 하는 데 도움이 되는 [CComGITPtr](../atl/reference/ccomgitptr-class.md) 클래스를 제공 합니다.

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)<br/>
[CoCreateFreeThreadedMarshaler](/windows/win32/api/combaseapi/nf-combaseapi-cocreatefreethreadedmarshaler)<br/>
[IMarshal](/windows/win32/api/objidlbase/nn-objidlbase-imarshal)<br/>
[전역 인터페이스 테이블을 사용 하는 경우](/windows/win32/com/when-to-use-the-global-interface-table)<br/>
[In-process 서버 스레딩 문제](/windows/win32/com/in-process-server-threading-issues)
