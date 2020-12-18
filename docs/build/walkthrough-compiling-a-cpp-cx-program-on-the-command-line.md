---
description: '자세한 정보: 연습: 명령줄에서 C++/CX 프로그램 컴파일'
title: '연습: 명령줄에서 C++/CX 프로그램 컴파일'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: 10bee181f347864fdef1703f88ca002a6c7c40b9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97198949"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>연습: 명령줄에서 C++/CX 프로그램 컴파일

> [!NOTE]
> 새 UWP 앱 및 구성 요소의 경우 Windows 런타임 API에 대한 표준 C++ 17 언어 프로젝션인 [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)를 사용하는 것이 좋습니다. C++/WinRT는 버전 1803부터 Windows 10 SDK에서 제공됩니다. C++/WinRT는 전적으로 헤더 파일에 구현되며 최신 Windows API에 대한 최고 수준의 액세스를 제공하도록 설계되었습니다.

Microsoft C++ 컴파일러(MSVC)는 Windows 런타임 프로그래밍 모델을 대상으로 하는 추가 형식 및 연산자가 있는 C++ 구성 요소 확장(C++/CX)을 지원합니다. C++/CX를 사용하여 UWP(유니버설 Windows 플랫폼) 및 Windows 데스크톱용 앱을 빌드할 수 있습니다. 자세한 내용은 [C++/CX 둘러보기](/archive/msdn-magazine/2013/april/component-extensions-a-tour-of-c-cx) 및 [런타임 플랫폼용 구성 요소 확장](../extensions/component-extensions-for-runtime-platforms.md)을 참조하세요.

이 연습에서는 텍스트 편집기를 사용하여 기본적인 C++/CX 프로그램을 만든 다음 명령줄에서 컴파일합니다. 여기에 나와 있는 내용을 입력하는 대신 C++/CX 프로그램을 직접 사용할 수도 있고 다른 도움말 문서의 C++/CX 코드 샘플을 사용할 수도 있습니다. 이 기술은 UI 요소가 없는 소형 모듈을 빌드하고 테스트하는 데 유용합니다.

> [!NOTE]
> 또한 Visual Studio IDE를 사용하여 C++/CX 프로그램을 컴파일할 수 있습니다. IDE는 명령줄에서는 제공되지 않는 디자인, 디버그, 에뮬레이션 및 배포 지원을 포함하므로 IDE를 사용하여 UWP(유니버설 Windows 플랫폼) 앱을 빌드하는 것이 좋습니다. 자세한 내용은 [C++에서 UWP 앱 만들기](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)를 참조하세요.

## <a name="prerequisites"></a>사전 요구 사항

C++ 언어의 기본적인 사항을 알고 있어야 합니다.

## <a name="compiling-a-ccx-program"></a>C++/CX 프로그램 컴파일

C++/CX를 컴파일할 수 있도록 설정하려면 [/ZW](reference/zw-windows-runtime-compilation.md) 컴파일러 옵션을 사용해야 합니다. MSVC 컴파일러는 Windows 런타임을 대상으로 하는 .exe 파일을 생성하고 필수 라이브러리에 연결합니다.

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>명령줄에서 C++/CX 애플리케이션을 컴파일하려면

1. **개발자 명령 프롬프트** 창을 엽니다. (**시작** 창에서 **앱** 을 엽니다. 사용 중인 Visual Studio 버전에서 **Visual Studio Tools** 폴더를 연 다음 **개발자 명령 프롬프트** 바로 가기를 선택합니다.) 개발자 명령 프롬프트 창을 여는 방법에 대한 자세한 내용은 [명령줄에서 MSVC 도구 집합 사용](building-on-the-command-line.md)을 참조하세요.

   컴퓨터 운영 체제 및 구성에 따라 코드를 정상적으로 컴파일하려면 관리자 자격 증명이 필요할 수 있습니다. 관리자로 명령 프롬프트 창을 실행하려면 **개발자 명령 프롬프트** 의 바로 가기 메뉴를 연 다음 **관리자 권한으로 실행** 을 선택합니다.

1. 명령 프롬프트에 **notepad basiccx.cpp** 를 입력합니다.

   파일을 만들지 묻는 메시지가 나타나면 **예** 를 선택합니다.

1. 메모장에 다음 줄을 입력합니다.

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. 메뉴 모음에서 **파일** > **저장** 을 선택합니다.

   Windows 런타임 [Platform namespace](../cppcx/platform-namespace-c-cx.md) 네임스페이스를 사용하는 C++ 소스 파일을 만들었습니다.

1. 명령 프롬프트에 **cl /EHsc /ZW basiccx.cpp /link /SUBSYSTEM:CONSOLE** 을 입력합니다. cl.exe 컴파일러는 이 소스 파일을 .obj 파일로 컴파일한 다음 링커를 실행하여 실행 프로그램인 basiccx.exe를 생성합니다. ([/EHsc](reference/eh-exception-handling-model.md) 컴파일러 옵션은 C++ 예외 처리 모델을 지정하고 [/link](reference/link-pass-options-to-linker.md) 플래그는 콘솔 애플리케이션을 지정합니다.)

1. basiccx.exe 프로그램을 실행하려면 명령 프롬프트에 **basiccx** 를 입력합니다.

   프로그램이 다음 텍스트를 표시하고 종료됩니다.

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>참조

[프로젝트 및 빌드 시스템](projects-and-build-systems-cpp.md)<br/>
[MSVC 컴파일러 옵션](reference/compiler-options.md)
