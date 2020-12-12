---
description: '자세한 정보: 유니버설 Windows 앱 (c + +)'
title: 유니버설 Windows 앱(C++)
ms.date: 03/30/2018
ms.assetid: 357121cc-d390-4bae-b34a-39614861a9f4
ms.topic: overview
ms.openlocfilehash: ef107311ce2e8ec1b7c33bad42edfd3fbee358eb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288147"
---
# <a name="universal-windows-apps-c"></a>유니버설 Windows 앱(C++)

UWP (유니버설 Windows 플랫폼)는 Windows 용 최신 프로그래밍 인터페이스입니다. UWP를 사용 하면 응용 프로그램 또는 구성 요소를 한 번 작성 하 고 Windows 10 장치에 배포할 수 있습니다. C + +에서 구성 요소를 작성 하 고 다른 UWP 호환 언어로 작성 된 응용 프로그램은 사용할 수 있습니다.

대부분의 UWP 설명서는 [유니버설 Windows 플랫폼 설명서](/windows/uwp/)의 Windows 콘텐츠 트리에 있습니다. 여기에서 자습서 및 참조 설명서를 찾을 수 있습니다.

새 UWP 앱 및 구성 요소의 경우 Windows 런타임 Api에 대해 새로운 표준 c [+ + 17 언어 프로젝션을 사용 하](/windows/uwp/cpp-and-winrt-apis/)는 것이 좋습니다. C++/WinRT는 버전 1803부터 Windows 10 SDK에서 제공됩니다. C++/WinRT는 전적으로 헤더 파일에 구현되며 최신 Windows API에 대한 최고 수준의 액세스를 제공하도록 설계되었습니다. C + +/CX 구현과 달리, c + +/WinRT는 비표준 구문이 나 Microsoft 언어 확장을 사용 하지 않으며, c + + 컴파일러를 최대한 활용 하 여 최적화 된 출력을 만듭니다. 자세한 내용은 [c + +/WinRT 소개](/windows/uwp/cpp-and-winrt-apis/intro-to-using-cpp-with-winrt)를 참조 하세요.

데스크톱 브리지 앱 변환기를 사용 하 여 Microsoft Store를 통해 배포 하기 위해 기존 데스크톱 응용 프로그램을 패키지할 수 있습니다. 자세한 내용은 Centennial 프로젝트 및 [데스크톱 브리지](/windows/uwp/porting/desktop-to-uwp-root) [에서 Visual C++ 런타임 사용](https://devblogs.microsoft.com/cppblog/using-visual-c-runtime-in-centennial-project/) 을 참조 하세요.

## <a name="uwp-apps-that-use-ccx"></a>C + +/CX를 사용 하는 UWP 앱

[C + +/CX 언어 참조](visual-c-language-reference-c-cx.md)\
Windows 런타임 Api의 c + + 사용을 간소화 하 고 예외를 기반으로 하는 오류 처리를 사용 하는 확장 집합을 설명 합니다.

[앱 및 라이브러리 빌드 (c + +/CX)](building-apps-and-libraries-c-cx.md)\
C++/CX 앱이나 구성 요소에서 액세스할 수 있는 DLL 및 정적 라이브러리를 만드는 방법을 설명합니다.

[자습서: c + +/CX에서 UWP "Hello, 세계" 앱 만들기](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)\
C + +/CX에서 UWP 앱 개발의 기본 개념을 소개 하는 연습입니다.

[C + +/CX에서 Windows 런타임 구성 요소 만들기](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)\
다른 UWP 앱 및 구성 요소에서 사용할 수 있는 Dll을 만드는 방법을 설명 합니다.

[UWP 게임 프로그래밍](/windows/uwp/gaming/)\
DirectX 및 c + +/CX를 사용 하 여 게임을 만드는 방법을 설명 합니다.

## <a name="uwp-apps-that-use-the-windows-runtime-c-template-library-wrl"></a>Windows 런타임 c + + 템플릿 라이브러리 (WRL)를 사용 하는 UWP 앱

Windows 런타임 c + + 템플릿 라이브러리는 ISO c + + 코드가 예외 없는 환경에서 Windows 런타임에 액세스할 수 있는 하위 수준 COM 인터페이스를 제공 합니다. 대부분의 경우 UWP 앱 개발을 위해 Windows 런타임 c + + 템플릿 라이브러리 대신 c + +/WinRT 또는 c + +/CX를 사용 하는 것이 좋습니다. Windows 런타임 c + + 템플릿 라이브러리에 대 한 자세한 내용은 [Windows 런타임 c + + 템플릿 라이브러리 (WRL)](wrl/windows-runtime-cpp-template-library-wrl.md)를 참조 하십시오.

## <a name="see-also"></a>참고 항목

[Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md)<br/>
[C + +의 Windows 프로그래밍 개요](../windows/overview-of-windows-programming-in-cpp.md)<br/>
