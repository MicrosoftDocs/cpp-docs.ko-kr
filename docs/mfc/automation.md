---
description: '자세히 알아보기: 자동화'
title: 자동화
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers, about Automation servers
- clients, Automation
- programmatic control [MFC]
- properties [MFC], Automation
- MFC, COM support
- OLE Automation
- Automation
- servers [MFC], Automation
- Automation clients
- sample applications [MFC], Automation
- methods [MFC]
- passing parameters, Automation
- Automation method [MFC]
- Automation, passing parameters
- Automation property [MFC]
- MFC COM, Automation
- methods [MFC], Automation
ms.assetid: 329117f0-c1aa-4680-a901-bfb71277dfba
ms.openlocfilehash: 8a038a3590c3db9c90c8f99eaaa6f98d2c4e20cc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339841"
---
# <a name="automation"></a>자동화

자동화(이전의 OLE 자동화) 기술은 한 애플리케이션에서 다른 애플리케이션에 구현된 개체를 조작하거나 개체를 조작할 수 있도록 노출시키는 것을 가능하게 하는 기술입니다.

[자동화 서버](automation-servers.md) 는 COM 인터페이스를 통해 다른 애플리케이션( [자동화 클라이언트](automation-clients.md))에 기능을 노출하는 애플리케이션(COM 서버의 일종)입니다. 자동화 서버에서 기능을 노출시키면 자동화 클라이언트는 개체에 직접 액세스하여 해당 개체에서 제공하는 서비스를 사용하는 방법으로 특정 기능을 자동화할 수 있습니다.

자동화 서버 및 클라이언트는 항상 `IDispatch` 에서 파생되는 COM 인터페이스를 사용하며 자동화 형식이라고 하는 특정 데이터 형식을 사용 및 반환합니다. 자동화 인터페이스를 노출시킴으로써 다른 애플리케이션에서 액세스할 수 있는 메서드 및 속성을 제공하는 개체는 모두 자동화할 수 있습니다. 자동화는 OLE 및 COM 개체 모두에 대해 사용할 수 있습니다. 자동화된 개체는 전역 개체 또는 원격 개체(다른 컴퓨터에서 네트워크를 통해 액세스할 수 있는 개체)이므로 다음과 같은 두 가지 범주로 나눌 수 있습니다.

- 로컬 자동화

- 원격 자동화(네트워크에서 분산 DCOM 또는 DCOM 사용)

개체 노출은 애플리케이션에서 다른 애플리케이션에 유용한 기능을 제공할 때 편리한 기능입니다. 예를 들어, ActiveX 컨트롤은 자동화 서버의 일종이며 ActiveX 컨트롤을 사용하는 애플리케이션은 해당 컨트롤의 자동화 클라이언트입니다.

또 다른 예로, 워드 프로세서에서는 해당 프로그램의 맞춤법 검사 기능을 다른 프로그램에 노출시킬 수 있습니다. 개체 노출을 통해 공급업체는 다른 애플리케이션의 기존 기능을 사용하여 자사 애플리케이션의 기능을 향상시킬 수 있습니다. 이런 자동화 방법으로 다시 사용하거나 캡슐화가 가능한 개체 지향 프로그래밍의 몇 가지 원칙을 애플리케이션 수준에서 구현할 수 있습니다.

보다 중요한 것은 자동화 지원이 사용자 및 솔루션 공급자에게 제공된다는 것입니다. 자동화는 잘 정의된 공용 인터페이스를 통해 애플리케이션 기능을 노출시킴으로써 다양한 애플리케이션 고유의 매크로 언어 대신 Microsoft Visual Basic 같은 일반 프로그래밍 언어만으로 복잡한 솔루션을 빌드할 수 있게 합니다.

Microsoft Excel이나 Microsoft Visual C++ 같은 대부분의 상업용 애플리케이션에서는 사용자가 대부분의 애플리케이션 기능을 자동화할 수 있습니다. 예를 들어 Visual C++에서는 VBScript 매크로를 만들어 빌드, 코드 편집 또는 디버깅 작업을 자동화할 수 있습니다.

## <a name="passing-parameters-in-automation"></a><a name="_core_passing_parameters_in_automation"></a> 자동화에서의 매개 변수 전달

자동화 메서드를 만드는 어려움 중 하나는 공통적이고 "안전한" 메커니즘을 통해 자동화 서버와 자동화 클라이언트 간에 데이터를 전달하는 것입니다. 자동화에서는 **VARIANT** 형식을 사용하여 데이터를 전달하며, **VARIANT** 형식은 태그가 지정된 공용 구조체입니다. 이 형식은 해당 값에 대한 데이터 멤버(익명 C++ 공용 구조체)와 공용 구조체에 저장된 정보 형식을 나타내는 데이터 멤버를 가지고 있습니다. **VARIANT** 형식은 2바이트 및 4바이트 정수, 4바이트 및 8바이트 부동 소수점 수, 문자열, 부울 값 등의 여러 가지 표준 데이터 형식을 지원합니다. 또한 **HRESULT** (OLE 오류 코드), **CURRENCY** (고정 소수점 숫자 형식) 및 **DATE** (절대 날짜 및 시간) 형식을 지원 하 `IUnknown` 고 및 인터페이스에 대 한 포인터도 지원 합니다 `IDispatch` .

**VARIANT** 형식은 [COleVariant](reference/colevariant-class.md) 클래스에 캡슐화되어 있습니다. 지원되는 **CURRENCY** 및 **DATE** 클래스는 [COleCurrency](reference/colecurrency-class.md) 및 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md) 클래스에 캡슐화되어 있습니다.

## <a name="automation-samples"></a>자동화 샘플

- [AUTOCLIK](../overview/visual-cpp-samples.md) 자동화 기술을 익히고 원격 자동화를 이해하도록 도와 줍니다.

- [ACDUAL](../overview/visual-cpp-samples.md) 자동화 서버 애플리케이션에 이중 인터페이스를 추가합니다.

- [CALCDRIV](../overview/visual-cpp-samples.md) MFCCALC를 구동하는 자동화 클라이언트 애플리케이션입니다.

- [INPROC](../overview/visual-cpp-samples.md) In-Process 자동화 서버 애플리케이션의 예를 보여 줍니다.

- [IPDRIVE](../overview/visual-cpp-samples.md) INPROC를 구동하는 자동화 클라이언트 애플리케이션입니다.

- [MFCCALC](../overview/visual-cpp-samples.md) 자동화 클라이언트 애플리케이션의 예를 보여 줍니다.

## <a name="what-do-you-want-to-know-more-about"></a>자세히 알아야 할 내용

- [자동화 클라이언트](automation-clients.md)

- [자동화 서버](automation-servers.md)

- [OLE](ole-in-mfc.md)

- [액티드 기술](mfc-com.md)

## <a name="what-do-you-want-to-do"></a>뭘 하고 싶으세요

- [자동화 클래스 추가](automation-servers.md)

- [형식 라이브러리 사용](automation-clients-using-type-libraries.md)

- [자동화 서버 액세스](automation-servers.md)

- [C++로 자동화 클라이언트 작성](automation-clients.md)

## <a name="see-also"></a>참고 항목

[MFC COM](mfc-com.md)
