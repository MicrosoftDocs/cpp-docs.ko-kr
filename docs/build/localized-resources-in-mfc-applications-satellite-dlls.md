---
description: '자세한 정보: MFC 애플리케이션의 지역화된 리소스: 위성 DLL'
title: 'MFC 애플리케이션의 지역화된 리소스: 위성 DLL'
ms.date: 11/04/2016
helpviewer_keywords:
- multiple language support [C++]
- localization [C++], MFC resources
- localized resources [C++]
- MFC DLLs [C++], localizing
- DLLs [C++], localizing MFC
- resources [MFC], localizing
- resource-only DLLs [C++]
- resource-only DLLs [C++], MFC applications
- satellite DLLs [C++]
ms.assetid: 3a1100ae-a9c8-47b5-adbd-cbedef5992ef
ms.openlocfilehash: 4af771999c97af40ffe50399c77e91aec1af992a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176472"
---
# <a name="localized-resources-in-mfc-applications-satellite-dlls"></a>MFC 애플리케이션의 지역화된 리소스: 위성 DLL

MFC 버전 7.0 이상에서는 여러 언어로 지역화된 애플리케이션을 만드는 데 도움이 되는 위성 DLL에 대한 향상된 지원 기능을 제공합니다. 위성 DLL은 특정 언어로 지역화된 애플리케이션 리소스를 포함하는 [리소스 전용 DLL](creating-a-resource-only-dll.md)입니다. 애플리케이션 실행이 시작되면 MFC는 환경에 가장 적합한 지역화된 리소스를 자동으로 로드합니다. 예를 들어 영어 리소스를 사용하는 애플리케이션에 두 개의 위성 DLL이 있고, 각각 리소스의 프랑스어 번역과 독일어 번역이 포함되어 있을 수 있습니다. 이 애플리케이션을 영어 시스템에서 실행하면 영어 리소스가 사용됩니다. 프랑스어 시스템에서 실행하면 프랑스어 리소스, 독일어 시스템에서 실행하면 독일어 리소스가 사용됩니다.

MFC 애플리케이션에서 지역화된 리소스를 지원하기 위해 MFC는 특정 언어로 지역화된 리소스를 포함하는 위성 DLL을 로드하려고 합니다. 위성 DLL은 *ApplicationNameXXX* 로 이름이 지정됩니다. 여기서 *ApplicationName* 은 MFC를 사용하는 .exe 또는 .dll의 이름이고, *XXX* 는 리소스의 언어를 나타내는 세 문자 코드입니다(예: ‘ENU’ 또는 ‘DEU’).

MFC는 다음 각 언어의 리소스 DLL을 순서대로 로드하려고 하고 해당 DLL을 찾으면 중지합니다.

1. GetUserDefaultUILanguage() Win32 API에서 반환되는 현재 사용자의 기본 UI 언어

1. 특정 하위 언어를 제외한 현재 사용자의 기본 UI 언어(즉, ENC[캐나다 영어]는 ENU[미국 영어]가 됨)

1. GetSystemDefaultUILanguage() API에서 반환되는 시스템의 기본 UI 언어. 다른 플랫폼에서는 OS 자체의 언어입니다.

1. 특정 하위 언어를 제외한 시스템의 기본 UI 언어

1. 3자 코드 LOC를 사용하는 가짜 언어

MFC가 위성 DLL을 찾지 못하면 애플리케이션 자체에 포함된 모든 리소스를 사용합니다.

예를 들어 애플리케이션 LangExample.exe가 MFC를 사용하고 여러 사용자 인터페이스 시스템에서 실행되고 있다고 가정합니다. 시스템 UI 언어는 ENU[미국 영어]이고 현재 사용자의 UI 언어는 FRC[캐나다 프랑스어]로 설정되어 있습니다. MFC는 다음과 같은 순서로 DLL을 찾습니다.

1. LangExampleFRC.dll(사용자 UI 언어)

1. LangExampleFRA.dll(하위 언어를 제외한 사용자 UI 언어, 이 예제에서는 프랑스어(프랑스))

1. LangExampleENU.dll(시스템의 UI 언어)

1. LangExampleLOC.dll

관련 DLL이 모두 없으면 MFC는 LangExample.exe의 리소스를 사용합니다.

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)<br/>
[TN057: MFC 구성 요소의 지역화](../mfc/tn057-localization-of-mfc-components.md)
