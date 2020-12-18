---
description: '자세한 정보: 연습: 명령줄에서 C++/CLI 프로그램 컴파일'
title: '연습: 명령줄에서 C++/CLI 프로그램 컴파일'
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 075ac90f08f62fb75c9a220b398f34841eafa60d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199001"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>연습: 명령줄에서 C++/CLI 프로그램 컴파일

CLR(공용 언어 런타임)을 대상으로 하는 Visual C++ 프로그램을 만들어 .NET Framework를 사용하여 명령줄에서 빌드할 수 있습니다. Visual C++은 .NET 프로그래밍 모델을 대상으로 하는 추가 형식 및 연산자가 있는 C++/CLI 프로그래밍 언어를 지원합니다. C++/CLI 언어에 대한 일반 정보는 [C++/CLI를 사용한 .NET 프로그래밍(Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)을 참조하세요.

이 연습에서는 텍스트 편집기를 사용하여 기본적인 C++/CLI 프로그램을 만든 다음 명령줄에서 컴파일합니다. 여기에 나와 있는 내용을 입력하는 대신 C++/CLI 프로그램을 직접 사용할 수도 있고 다른 도움말 문서의 C++/CLI 코드 샘플을 사용할 수도 있습니다. 이 기술은 UI 요소가 없는 소형 모듈을 빌드하고 테스트하는 데 유용합니다.

## <a name="prerequisites"></a>사전 요구 사항

C++ 언어의 기본적인 사항을 알고 있어야 합니다.

## <a name="compiling-a-ccli-program"></a>C++/CLI 프로그램 컴파일

다음 단계는 .NET Framework 클래스를 사용하는 C++/CLI 콘솔 애플리케이션을 컴파일하는 방법을 보여줍니다.

C++/CLI에 대해 컴파일을 사용하도록 설정하려면 [/clr](reference/clr-common-language-runtime-compilation.md) 컴파일러 옵션을 사용해야 합니다. MSVC 컴파일러는 MSIL 코드를 포함하거나 MSIL 코드와 네이티브 코드가 혼합된 .exe 파일을 생성하여 필수 .NET Framework 라이브러리에 연결합니다.

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>명령줄에서 C++/CLI 애플리케이션을 컴파일하려면

1. **개발자 명령 프롬프트** 창을 엽니다. 특정 지침은 [개발자 명령 프롬프트 창을 열려면](building-on-the-command-line.md#developer_command_prompt)을 참조하세요.

   컴퓨터 운영 체제 및 구성에 따라 코드를 정상적으로 컴파일하려면 관리자 자격 증명이 필요할 수 있습니다. 관리자 권한으로 명령 프롬프트 창을 실행하려면 마우스 오른쪽 단추를 클릭하여 명령 프롬프트의 바로 가기 메뉴를 연 다음 **기타** > **관리자 권한으로 실행** 을 선택합니다.

1. 명령 프롬프트에서 `notepad basicclr.cpp`을 입력합니다.

   파일을 만들 것인지 묻는 메시지가 나타나면 **예** 를 선택합니다.

1. 메모장에 다음 줄을 입력합니다.

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. 메뉴 모음에서 **파일** > **저장** 을 차례로 선택합니다.

   <xref:System> 네임스페이스에서 .NET Framework 클래스(<xref:System.Console>)를 사용하는 Visual C++ 소스 파일을 만들었습니다.

1. 명령 프롬프트에서 `cl /clr basicclr.cpp`을 입력합니다. cl.exe 컴파일러는 이 소스 파일을 MSIL이 포함된 .obj 파일로 컴파일한 다음 링커를 실행하여 실행 프로그램인 basicclr.exe를 생성합니다.

1. basicclr.exe 프로그램을 실행하려면 명령 프롬프트에 `basicclr`을 입력합니다.

   프로그램이 다음 텍스트를 표시하고 종료됩니다.

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>참조

[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[프로젝트 및 빌드 시스템](projects-and-build-systems-cpp.md)<br/>
[MSVC 컴파일러 옵션](reference/compiler-options.md)
