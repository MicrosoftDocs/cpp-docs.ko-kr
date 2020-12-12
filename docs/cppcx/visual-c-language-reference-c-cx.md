---
description: '자세한 정보: c + +/CX 언어 참조'
title: C + +/CX 언어 참조
ms.date: 09/15/2017
ms.assetid: 3f6abf92-4e5e-4ed8-8e11-f9252380d30a
ms.openlocfilehash: ac72abeb84c656ce0ab9569ad5c944ea61b7d646
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97288037"
---
# <a name="ccx-language-reference"></a>C + +/CX 언어 참조

C + +/CX는 최신 c + +와 가능한 가까운 방식으로 Windows 앱 및 Windows 런타임 구성 요소를 만들 수 있도록 하는 c + + 언어에 대 한 확장 집합입니다. C + +/CX를 사용 하 여 Visual c #, Visual Basic, JavaScript 및 Windows 런타임를 지 원하는 다른 언어와 쉽게 상호 작용 하는 네이티브 코드로 Windows 앱 및 구성 요소를 작성할 수 있습니다. 드물지만 원시 COM 인터페이스 또는 비 예외 코드에 직접 액세스 해야 하는 경우에는 [Windows 런타임 c + + 템플릿 라이브러리 (WRL)](./wrl/windows-runtime-cpp-template-library-wrl.md)를 사용할 수 있습니다.

> [!NOTE]
> **[/Winrt는 C++/cx의 권장 되는 대안입니다. C++](/windows/uwp/cpp-and-winrt-apis/index)** 최신 Windows 10 SDK 버전 1803부터 사용할 수 있는 Windows 런타임 Api에 대 한 새로운 표준 c + + 17 언어 프로젝션입니다. C + +/WinRT는 헤더 파일에 완전히 구현 되며 최신 Windows API에 대 한 최고 수준의 액세스를 제공 하도록 설계 되었습니다.
>
> C + +/WinRT를 사용 하면 표준 규격 c + + 17 컴파일러를 사용 하 여 Windows 런타임 Api를 사용 하 고 제작할 수 있습니다. 일반적으로 c + +/WinRT는 Windows 런타임에 대 한 다른 언어 옵션 보다 더 작은 이진 파일을 생성 합니다. C++/CX와 WRL도 계속 지원되지만, 새 애플리케이션에서는 C++/WinRT를 사용하는 것이 좋습니다. 자세한 내용은 [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index) 참조하세요.

C + +/CX를 사용 하 여 다음을 만들 수 있습니다.

- XAML을 사용 하 여 사용자 인터페이스를 정의 하 고 네이티브 스택을 사용 하는 UWP (c + + 유니버설 Windows 플랫폼) 앱입니다. 자세한 내용은 [c + + (UWP)에서 "hello 세계" 앱 만들기](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)를 참조 하세요.

- JavaScript 기반 Windows 앱에서 사용할 수 있는 c + + Windows 런타임 구성 요소입니다. 자세한 내용은 [Creating Windows Runtime Components in C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)을 참조하세요.

- Windows DirectX 게임 및 그래픽 위주 앱. 자세한 내용은 [DirectX를 사용 하 여 간단한 UWP 게임 만들기](/windows/uwp/gaming/tutorial--create-your-first-uwp-directx-game)를 참조 하세요.

## <a name="related-articles"></a>관련 문서

| 링크 | 설명 |
|--|--|
| [빠른 참조](../cppcx/quick-reference-c-cx.md) | C + +/CX에 대 한 키워드 및 연산자 표 |
| [유형 시스템](../cppcx/type-system-c-cx.md) | 기본적인 c + +/CX 형식 및 프로그래밍 구문에 대해 설명 하 고, c + +/CX를 활용 하 여 Windows 런타임 형식을 사용 하 고 만드는 방법을 설명 합니다 |
| [앱 및 라이브러리 빌드](../cppcx/building-apps-and-libraries-c-cx.md) | IDE를 사용 하 여 앱을 빌드하고 정적 라이브러리 및 Dll에 연결 하는 방법을 설명 합니다. |
| [다른 언어와의 상호 운용](../cppcx/interoperating-with-other-languages-c-cx.md) | C + +/CX를 사용 하 여 작성 된 구성 요소를 JavaScript, 관리 되는 언어 또는 Windows 런타임 c + + 템플릿 라이브러리로 작성 된 구성 요소와 함께 사용할 수 있는 방법에 대해 설명 합니다. |
| [스레딩 및 마샬링](../cppcx/threading-and-marshaling-c-cx.md) | 사용자가 만든 구성 요소의 스레딩 및 마샬링 동작을 지정하는 방법을 설명합니다. |
| [네임 스페이스 참조](../cppcx/namespaces-reference-c-cx.md) | 기본 네임스페이스, Platform 네임스페이스, Platform::Collections 및 관련 네임스페이스에 대한 참조 설명서입니다. |
| [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) | Windows 런타임 앱에서 사용할 수 없는 CRT 함수를 나열합니다. |
| [Windows 10 앱 시작](/windows/uwp/get-started/) | Windows 10 앱에 대한 개략적인 지침 및 자세한 정보에 대한 링크를 제공합니다. |
| [C + +/CX 파트 0/ \[ n \] : 소개](https://devblogs.microsoft.com/cppblog/ccx-part-0-of-n-an-introduction/)<br /><br />[C + +/CX 파트 1/ \[ n \] : 간단한 클래스](https://devblogs.microsoft.com/cppblog/ccx-part-1-of-n-a-simple-class/)<br /><br />[C + +/CX 파트 2/ \[ n \] : 모자를 착용 하는 형식](https://devblogs.microsoft.com/cppblog/ccx-part-2-of-n-types-that-wear-hats/)<br /><br />[C + +/CX 파트 3/ \[ n \] : 생성 중](https://devblogs.microsoft.com/cppblog/ccx-part-3-of-n-under-construction/)<br /><br />[C + +/CX 파트 4/ \[ n \] : 정적 멤버 함수](https://devblogs.microsoft.com/cppblog/ccx-part-4-of-n-static-member-functions/)| C + +/CX의 소개 블로그 시리즈 |
