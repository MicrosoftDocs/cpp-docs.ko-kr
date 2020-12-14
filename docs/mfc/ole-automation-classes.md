---
description: '자세한 정보: OLE 자동화 클래스'
title: OLE 자동화 클래스
ms.date: 11/04/2016
helpviewer_keywords:
- Automation, classes
- Automation classes [MFC], OLE classes
- OLE Automation [MFC], classes
- Automation classes [MFC]
- OLE Automation [MFC]
ms.assetid: 96e5372b-ff8a-4da1-933b-4d9bbf4dceb3
ms.openlocfilehash: 588c684d17eb358183097cd4ed62432f334e3f0f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275570"
---
# <a name="ole-automation-classes"></a>OLE 자동화 클래스

이러한 클래스는 자동화 클라이언트 (다른 응용 프로그램을 제어 하는 응용 프로그램)를 지원 합니다. Automation 서버 (다른 응용 프로그램에서 제어할 수 있는 응용 프로그램)는 [디스패치 맵을](reference/dispatch-maps.md)통해 지원 됩니다.

[COleDispatchDriver](reference/coledispatchdriver-class.md)<br/>
자동화 클라이언트에서 자동화 서버를 호출 하는 데 사용 됩니다. 클래스를 추가 하는 경우이 클래스는 형식 라이브러리를 제공 하는 자동화 서버에 대해 형식이 안전한 클래스를 만드는 데 사용 됩니다.

[COleDispatchException](reference/coledispatchexception-class.md)<br/>
OLE 자동화 중 오류로 인해 발생 하는 예외입니다. 자동화 예외는 자동화 서버에 의해 throw되고 자동화 클라이언트에 의해 catch됩니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
