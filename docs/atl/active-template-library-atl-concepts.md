---
description: '자세한 정보: ATL (액티브 템플릿 라이브러리) 개념'
title: ATL(액티브 템플릿 라이브러리) 개념
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: 5437f381ea145d5474dcdba25673d4e41c60c54b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166319"
---
# <a name="active-template-library-atl-concepts"></a>ATL(액티브 템플릿 라이브러리) 개념

ATL(액티브 템플릿 라이브러리)은 작고 신속한 COM(구성 요소 개체 모델) 개체를 만들 수 있는 템플릿 기반 C++ 클래스의 세트입니다. 스톡 구현, 이중 인터페이스, 표준 COM 열거자 인터페이스, 연결점, 분할 인터페이스, ActiveX 컨트롤 등, 주요 COM 기능을 특별히 지원합니다.

ATL 프로그래밍 작업이 많은 경우 단순한 COM 프로그래밍을 위해 설계된 COM 및 .NET의 특성을 자세히 알아볼 필요가 있습니다. 자세한 내용은 [특성 사용 프로그래밍](../windows/attributes/cpp-attributes-com-net.md)을 참조하세요. (COM 및 .NET 특성을 C++ 표준의 \[\[attribute]] 기능과 혼동하면 안 됨)

## <a name="in-this-section"></a>섹션 내용

[COM 및 ATL 소개](introduction-to-com-and-atl.md)<br/>
COM(구성 요소 개체 모델)의 배경이 되는 주요 개념을 소개합니다. 이 문서에서는 ATL이란 무엇이며 언제 사용하는지에 대해서도 간략히 설명합니다.

[ATL COM 개체의 기본 사항](fundamentals-of-atl-com-objects.md)<br/>
다양한 ATL 클래스 간의 관계와, 클래스가 구현되는 방식에 대해 설명합니다.

[이중 인터페이스 및 ATL](dual-interfaces-and-atl.md)<br/>
ATL의 관점에서 이중 인터페이스를 설명합니다.

[ATL 컬렉션 및 열거자](atl-collections-and-enumerators.md)<br/>
ATL에서의 컬렉션 및 열거자 구현과 만들기에 대해 설명합니다.

[복합 컨트롤 기본 사항](atl-composite-control-fundamentals.md)<br/>
복합 컨트롤을 만들기 위한 단계별 지침을 제공합니다. 복합 컨트롤은 다른 ActiveX 컨트롤 또는 Windows 컨트롤을 포함할 수 있는 ActiveX 컨트롤의 형식입니다.

[ATL 컨트롤 포함 FAQ](atl-control-containment-faq.md)<br/>
ATL 컨트롤을 통한 호스팅과 관련한 기본 사항을 설명합니다.

[ATL COM 속성 페이지](atl-com-property-pages.md)<br/>
COM 속성 페이지의 지정 및 구현 방법을 보여 줍니다.

[DHTML 컨트롤에 대 한 ATL 지원](atl-support-for-dhtml-controls.md)<br/>
DHTML 컨트롤을 만들기 위한 단계별 지침을 제공합니다.

[ATL 연결 지점의](atl-connection-points.md)<br/>
연결점이란 무엇이며 ATL을 구현하는 방법에 대해 설명합니다.

[이벤트 처리 및 ATL](event-handling-and-atl.md)<br/>
ATL의 [IDispEventImpl](reference/idispeventimpl-class.md) 및 [IDispEventSimpleImpl](reference/idispeventsimpleimpl-class.md) 클래스를 사용하여 COM 이벤트를 처리하기 위해 필요한 단계를 설명합니다.

[ATL 및 자유 스레드된 마샬러](atl-and-the-free-threaded-marshaler.md)<br/>
클래스가 FTM(자유 스레드된 마샬러)를 집계할 수 있게 하는 ATL 단순 개체 마법사 옵션에 대한 세부 정보를 제공합니다.

[프로젝트의 스레딩 모델 지정](specifying-the-threading-model-for-a-project-atl.md)<br/>
프로젝트에서 스레딩과 관련한 런타임 성능을 제어할 수 있는 매크로에 대해 설명합니다.

[ATL 모듈 클래스](atl-module-classes.md)<br/>
ATL 7.0의 새 모듈 클래스에 대해 설명합니다. 모듈 클래스는 ATL에 필요한 기본 기능을 구현합니다.

[ATL 서비스](atl-services.md)<br/>
서비스를 구현할 때 발생하는 일련의 이벤트에 대해 설명합니다. 또한 서비스 개발과 관련한 일부 개념에 대해서도 설명합니다.

[ATL 창 클래스](atl-window-classes.md)<br/>
ATL에서 슈퍼클래스 및 서브클래스 창을 만드는 방법을 설명합니다. ATL 창 클래스는 COM 클래스가 아닙니다.

[ATL 컬렉션 클래스](atl-collection-classes.md)<br/>
ATL에서 배열과 맵을 사용하는 방법을 설명합니다.

[ATL 레지스트리 구성 요소(등록자)](atl-registry-component-registrar.md)<br/>
ATL 스크립팅 구문과 대체 가능 매개 변수를 설명합니다. 등록자에 대한 정적 링크를 설정하는 방법도 설명합니다.

[ATL 및 C Run-Time 코드를 사용한 프로그래밍](programming-with-atl-and-c-run-time-code.md)<br/>
정적 또는 동적 CRT(C 런타임) 라이브러리 연결의 장점에 대해 설명합니다.

[CComBSTR을 사용한 프로그래밍](programming-with-ccombstr-atl.md)<br/>
`CComBSTR`을 사용하여 프로그래밍할 때 주의가 필요한 몇 가지 상황에 대해 설명합니다.

[인코딩 참조](atl-encoding-reference.md)<br/>
atlenc.h에서 uuencode, 16진수, UTF8 같은 광범위한 공통 인터넷 표준 인코딩을 지원하는 함수와 매크로를 제공합니다.

[유틸리티 참조](atl-utilities-reference.md)<br/>
[CPathT](reference/cpatht-class.md) 및 [CUrl](reference/curl-class.md) 형식으로 경로 및 URL을 조작하는 코드를 제공합니다. 스레드 풀 [CThreadPool](reference/cthreadpool-class.md)을 자체 애플리케이션에 사용할 수 있습니다. 이 코드는 atlpath.h 및 atlutil.h에서 찾을 수 있습니다.

## <a name="related-sections"></a>관련 단원

[ATL 자습서](active-template-library-atl-tutorial.md)<br/>
컨트롤을 만드는 과정을 안내하고 프로세스의 몇 가지 ATL 기본 사항을 보여 줍니다.

[ATL 샘플](../overview/visual-cpp-samples.md)<br/>
ATL 샘플 프로그램의 설명과 링크를 제공합니다.

[ATL 프로젝트 만들기](reference/creating-an-atl-project.md)<br/>
ATL 프로젝트 마법사에 대한 정보를 포함합니다.

[ATL 컨트롤 마법사](reference/atl-control-wizard.md)<br/>
클래스를 추가하는 방법을 설명합니다.

[특성을 사용하는 프로그래밍](../windows/attributes/cpp-attributes-com-net.md)<br/>
특성을 사용한 COM 프로그래밍 간소화에 대한 개요와, 더 상세한 항목에 대한 링크 목록을 제공합니다.

[ATL 클래스 개요](atl-class-overview.md)<br/>
참조 정보와 ATL 클래스에 대한 링크를 제공합니다.
