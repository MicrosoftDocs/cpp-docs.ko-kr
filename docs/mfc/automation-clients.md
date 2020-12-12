---
description: '자세히 알아보기: Automation 클라이언트'
title: 자동화 클라이언트
ms.date: 11/04/2016
helpviewer_keywords:
- clients, Automation
- Automation clients
- type libraries, Automation clients
- clients
ms.assetid: 84e34a79-06f6-4752-a33b-ae0ede1d8ecf
ms.openlocfilehash: 38379feb0881b154418daa5c02980eeee2dd21e5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97273958"
---
# <a name="automation-clients"></a>자동화 클라이언트

자동화를 사용 하면 응용 프로그램에서 다른 응용 프로그램에 구현 된 개체를 조작 하거나 개체를 조작할 수 있도록 노출할 수 있습니다. 자동화 클라이언트는 다른 응용 프로그램에 속하는 노출 된 개체를 조작할 수 있는 응용 프로그램입니다. 개체를 노출 하는 응용 프로그램을 자동화 서버 라고 합니다. 클라이언트는 해당 개체의 속성 및 함수에 액세스 하 여 서버 응용 프로그램의 개체를 조작 합니다.

### <a name="types-of-automation-clients"></a>자동화 클라이언트 유형

자동화 클라이언트에는 다음과 같은 두 가지 유형이 있습니다.

- 동적으로 (런타임에) 서버 속성 및 작업에 대 한 정보를 가져오는 클라이언트

- 서버 속성 및 작업을 지정 하는 정적 정보 (컴파일 타임에 제공 됨)를 보유 하는 클라이언트입니다.

첫 번째 종류의 클라이언트는 OLE 시스템의 메커니즘을 쿼리하여 서버의 메서드 및 속성에 대 한 정보를 얻습니다 `IDispatch` . 동적 클라이언트에는를 사용 하는 것이 좋지만 `IDispatch` 정적 클라이언트에는를 사용 하는 것이 어렵고,이 경우에는 컴파일 시에 개체를 파악 해야 합니다. 정적 바인딩 클라이언트의 경우 Microsoft Foundation 클래스는 [Coledispatchdriver](reference/coledispatchdriver-class.md) 클래스를 제공 합니다.

정적 바인딩 클라이언트는 클라이언트 응용 프로그램과 정적으로 연결 된 프록시 클래스를 사용 합니다. 이 클래스는 서버 응용 프로그램의 속성 및 작업에 대 한 형식이 안전한 c + + 캡슐화를 제공 합니다.

클래스는 `COleDispatchDriver` 자동화의 클라이언트 쪽에 대 한 주 지원을 제공 합니다. **새 항목 추가** 대화 상자를 사용 하 여에서 파생 된 클래스를 만듭니다 `COleDispatchDriver` .

그런 다음 서버 응용 프로그램 개체의 속성 및 함수를 설명 하는 형식 라이브러리 파일을 지정 합니다. 항목 추가 대화 상자는이 파일을 읽고 `COleDispatchDriver` 형식이 안전한 방식으로 c + +에서 서버 응용 프로그램의 개체에 액세스 하기 위해 응용 프로그램이 호출할 수 있는 멤버 함수를 사용 하 여 파생 클래스를 만듭니다. 에서 상속 되는 추가 기능은 `COleDispatchDriver` 적절 한 자동화 서버를 호출 하는 프로세스를 간소화 합니다.

### <a name="handling-events-in-automation-clients"></a>자동화 클라이언트에서 이벤트 처리

자동화 클라이언트에서 이벤트를 처리 하려면 싱크 인터페이스를 추가 해야 합니다. MFC는 ActiveX 컨트롤에 대 한 싱크 인터페이스를 추가 하는 데 필요한 기능을 제공 하지만 다른 COM 서버는 지원 하지 않습니다.

## <a name="see-also"></a>참고 항목

[자동화 클라이언트: 형식 라이브러리 사용](automation-clients-using-type-libraries.md)<br/>
[Automation](automation.md)<br/>
[MFC 응용 프로그램 마법사](reference/mfc-application-wizard.md)
