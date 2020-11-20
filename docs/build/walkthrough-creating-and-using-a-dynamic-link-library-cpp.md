---
title: '연습: 자체 동적 연결 라이브러리 만들기 및 사용(C++)'
description: C++를 사용하여 Visual Studio에서 Windows DLL(동적 연결 라이브러리)을 만듭니다.
ms.custom:
- walkthrough
- contperfq2
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.openlocfilehash: ca9aebd7103d36918940e52638b3c2cb52612c25
ms.sourcegitcommit: 43a6ff739516dff62fee521d401eb4b1201cea8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94870690"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>연습: 자체 동적 연결 라이브러리 만들기 및 사용(C++)

이 단계별 연습에서는 Visual Studio IDE를 사용하여 Microsoft C++(MSVC)로 작성된 자체 DLL(동적 연결 라이브러리)을 만드는 방법을 보여 줍니다. 그런 다음 다른 C++ 앱에서 DLL을 사용하는 방법을 보여줍니다. DLL(UNIX 기반 운영 체제에서는 ‘공유 라이브러리’라고도 함)은 Windows 구성 요소의 가장 유용한 종류 중 하나입니다.  DLL을 코드 및 리소스를 공유하는 방법으로 사용하여 앱의 크기를 줄일 수 있습니다. DLL을 사용하면 애플리케이션을 더 쉽게 서비스하고 확장할 수 있습니다.

이 연습에서는 어떤 수학 함수를 구현하는 DLL을 만듭니다. 그런 다음 DLL의 함수를 사용하는 콘솔 앱을 만듭니다. 또한 Windows DLL에서 사용되는 몇 가지 프로그래밍 기법 및 규칙을 소개합니다.

이 연습에서는 다음 작업 방법을 배웁니다.

- Visual Studio에서 DLL 프로젝트를 만듭니다.

- 내보낸 함수 및 변수를 DLL에 추가합니다.

- Visual Studio에서 콘솔 앱 프로젝트를 만듭니다.

- 콘솔 앱에서 DLL에서 가져온 함수 및 변수를 사용합니다.

- 완성된 앱을 실행합니다.

정적으로 연결된 라이브러리와 마찬가지로, DLL은 이름별로 변수, 함수 및 리소스를 _내보냅니다_. 클라이언트 앱은 해당 변수, 함수 및 리소스를 사용하기 위해 이름을 _가져옵니다_. 정적으로 연결된 라이브러리와 달리, Windows는 링크 타임에 앱의 가져오기를 DLL의 내보내기와 연결하는 것이 아니라 로드 시간 또는 런타임에 앱의 가져오기를 DLL의 내보내기에 연결합니다. Windows에서는 이렇게 연결하려면 표준 C++ 컴파일 모델에 속하지 않는 추가 정보가 필요합니다. MSVC 컴파일러는 C++에 대한 몇 가지 Microsoft 전용 확장을 구현하여 이 추가 정보를 제공합니다. 이 연습에서는 내용을 전개해가면서 해당 확장을 설명합니다.

이 연습에서는 두 개의 Visual Studio 솔루션을 만듭니다. 하나는 DLL을 빌드하는 솔루션이고, 다른 하나는 클라이언트 앱을 빌드하는 솔루션입니다. DLL은 C 호출 규칙을 사용합니다. 플랫폼, 호출 규칙 및 연결 규칙이 일치하는 경우 다른 프로그래밍 언어로 작성된 앱에서 호출할 수 있습니다. 클라이언트 앱은 Windows가 로드 시간에 앱을 DLL에 연결하는 ‘암시적 연결’을  사용합니다. 이 연결을 통해 앱은 DLL에서 제공한 함수를 정적으로 연결된 라이브러리의 함수처럼 호출할 수 있습니다.

이 연습에서는 일부 일반적인 상황은 다루지 않습니다. 코드는 다른 프로그래밍 언어로 C++ DLL 사용을 표시하지 않습니다. [리소스 전용 DLL 만드는 방법](creating-a-resource-only-dll.md) 또는 [명시적 링크](linking-an-executable-to-a-dll.md#linking-explicitly)를 사용하여 로드 시간이 아닌 런타임에 DLL을 로드하는 방법을 보여 주지 않습니다. MSVC와 Visual Studio를 사용하여 모든 작업을 수행할 수 있으니 안심해도 됩니다.

DLL에 대한 자세한 내용의 링크는 [Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)를 참조하세요. 암시적 연결 및 명시적 연결에 대한 자세한 내용은 [사용할 연결 방법 결정](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)을 참조하세요. C 언어 연결 규칙을 사용하는 프로그래밍 언어로 사용할 C++ DLL을 만드는 방법에 대한 자세한 내용은 [C++ 함수를 C 언어 실행 파일에서 사용할 수 있도록 내보내기](exporting-cpp-functions-for-use-in-c-language-executables.md)를 참조하세요. .NET 언어로 사용할 DLL을 만드는 방법에 대한 자세한 내용은 [Visual Basic 애플리케이션에서 DLL 함수 호출](calling-dll-functions-from-visual-basic-applications.md)을 참조하세요.

## <a name="prerequisites"></a>사전 요구 사항

- Microsoft Windows 7 이상 버전을 실행하는 컴퓨터. 최상의 개발 환경을 위해서는 Windows 10이 권장됩니다.

::: moniker range=">=msvc-150"

- Visual Studio. Visual Studio를 다운로드 및 설치하는 방법에 대한 자세한 내용은 [Visual Studio 설치](/visualstudio/install/install-visual-studio)를 참조하세요. 설치 관리자를 실행할 때 **C++를 사용한 데스크톱 개발** 워크로드를 선택해야 합니다. Visual Studio를 설치할 때 이 워크로드를 설치하지 않은 경우 걱정하지 마세요. 설치 관리자를 다시 실행하고 바로 설치할 수 있습니다.

   ![C++를 사용한 데스크톱 개발](media/desktop-development-with-cpp.png "C++를 사용한 데스크톱 개발")

::: moniker-end

::: moniker range="msvc-140"

- Visual Studio. Visual Studio 2015를 다운로드 및 설치하는 방법에 대한 자세한 내용은 [Visual Studio 2015 설치](/visualstudio/install/install-visual-studio-2015?view=vs-2015&preserve-view=true)를 참조하세요. 기본적으로 설치되지 않으므로 **사용자 지정** C++ 설치를 사용하여 컴파일러 및 도구를 설치합니다.

::: moniker-end

- Visual Studio IDE 사용의 기본 사항에 대한 이해. 이전에 Windows 데스크톱 앱을 사용한 경우 내용을 따라갈 수 있습니다. 소개 내용을 살펴보려면 [Visual Studio IDE 기능 둘러보기](/visualstudio/ide/visual-studio-ide)를 참조하세요.

- 내용을 따라가기에 충분한 C++ 언어의 기본 사항에 대한 이해. 너무 복잡한 내용을 다루지는 않으므로 걱정하지 마세요.

::: moniker range="msvc-150"

> [!NOTE]
> 이 연습에서는 Visual Studio 2017 버전 15.9 이상을 사용하고 있다고 가정합니다. 일부 이전 버전의 Visual Studio 2017은 코드 템플릿에서 결함이 있거나 다른 사용자 인터페이스 대화 상자를 사용했습니다. 문제를 방지하려면 Visual Studio 설치 관리자를 사용하여 Visual Studio 2017을 버전 15.9 이상으로 업데이트합니다.

::: moniker-end

## <a name="create-the-dll-project"></a>DLL 프로젝트 만들기

이 작업 세트에서는 DLL용 프로젝트를 만들고 코드를 추가하고 빌드합니다. 시작하려면 Visual Studio IDE를 시작하고 필요한 경우 로그인합니다. 사용 중인 Visual Studio 버전에 따라 지침이 약간 다릅니다. 이 페이지의 왼쪽 위에 있는 컨트롤에서 올바른 버전을 선택했는지 확인합니다.

::: moniker range=">=msvc-160"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Visual Studio 2019에서 DLL 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

   ![새 DLL 프로젝트 만들기](media/create-new-dll-project-2019.png "MathLibrary 프로젝트 만들기")

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **라이브러리** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **DLL(동적 연결 라이브러리)** 을 선택하고 **다음** 을 선택합니다.

1. **새 프로젝트 구성** 페이지에서 **프로젝트 이름** 상자에 *MathLibrary* 를 입력하여 프로젝트의 이름을 지정합니다. 기본 **위치** 및 **솔루션 이름** 값은 그대로 둡니다. **솔루션** 을 **새 솔루션 만들기** 로 설정합니다. **동일한 디렉터리에 솔루션과 프로젝트 배치** 가 선택된 경우 선택을 해제합니다.

1. **만들기** 단추를 선택하여 프로젝트를 만듭니다.

솔루션이 만들어지면 Visual Studio의 **솔루션 탐색기** 창에서 생성된 프로젝트 및 소스 파일을 볼 수 있습니다.

![Math Library가 강조 표시된 Visual Studio 2019 솔루션 탐색기의 스크린샷.](media/mathlibrary-solution-explorer-162.png "Visual Studio에서 생성된 솔루션")

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Visual Studio 2017에서 DLL 프로젝트를 만들려면

1. 메뉴 모음에서 **파일**, >**새로 만들기**>, **프로젝트** 를 선택하여 **새 프로젝트** 대화 상자를 엽니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **설치된** > **Visual C++**  > **Windows 데스크톱** 을 선택합니다. 가운데 창에서 **DLL(동적 연결 라이브러리)** 을 선택합니다. **이름** 상자에 *MathLibrary* 를 입력하여 프로젝트 이름을 지정합니다. 기본 **위치** 및 **솔루션 이름** 값은 그대로 둡니다. **솔루션** 을 **새 솔루션 만들기** 로 설정합니다. 선택하지 않은 경우 **솔루션에 대한 디렉터리 만들기** 를 선택합니다.

   ![이름 텍스트 상자의 Math Library를 보여 주는 Visual Studio 2017 새 프로젝트 대화 상자의 스크린샷](media/mathlibrary-new-project-name-159.png "MathLibrary 프로젝트 이름 지정")

1. **확인** 단추를 선택하여 프로젝트를 만듭니다.

솔루션이 만들어지면 Visual Studio의 **솔루션 탐색기** 창에서 생성된 프로젝트 및 소스 파일을 볼 수 있습니다.

![Math Library가 강조 표시된 Visual Studio 2017 솔루션 탐색기 창의 스크린샷](media/mathlibrary-solution-explorer-159.png "Visual Studio에서 생성된 솔루션")

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>이전 버전의 Visual Studio 2015 이하에서 DLL 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창에서 **설치됨** > **템플릿** 을 확장하고 **Visual C++** 를 선택한 후 가운데 창에서 **Win32 콘솔 애플리케이션** 을 선택합니다. **이름** 편집 상자에 *MathLibrary* 를 입력하여 프로젝트 이름을 지정합니다. 기본 **위치** 및 **솔루션 이름** 값은 그대로 둡니다. **솔루션** 을 **새 솔루션 만들기** 로 설정합니다. 선택하지 않은 경우 **솔루션에 대한 디렉터리 만들기** 를 선택합니다.

   ![이름 텍스트 상자의 Math Library를 보여 주는 Visual Studio 2015 새 프로젝트 대화 상자의 스크린샷](media/mathlibrary-project-name.png "MathLibrary 프로젝트 이름 지정")

1. **확인** 단추를 선택하여 **새 프로젝트** 대화 상자를 닫고 **Win32 애플리케이션 마법사** 를 시작합니다.

   ![Win32 애플리케이션 마법사 개요](media/mathlibrary-project-wizard-1.png "Win32 애플리케이션 마법사 개요")

1. **다음** 단추를 선택합니다. **애플리케이션 설정** 페이지의 **애플리케이션 유형** 에서 **DLL** 을 선택합니다.

   ![Win32 애플리케이션 마법사에서 DLL 만들기](media/mathlibrary-project-wizard-2.png "Win32 애플리케이션 마법사에서 DLL 만들기")

1. **마침** 단추를 선택하여 프로젝트를 만듭니다.

마법사가 솔루션을 완료하면 Visual Studio의 **솔루션 탐색기** 창에서 생성된 프로젝트 및 소스 파일을 볼 수 있습니다.

![Math Library가 강조 표시된 Visual Studio 2015 솔루션 탐색기 창의 스크린샷](media/mathlibrary-solution-explorer-153.png "Visual Studio에서 생성된 솔루션")

::: moniker-end

지금은 이 DLL이 크게 하는 일이 없습니다. 다음으로, DLL이 내보내는 함수를 선언하는 헤더 파일을 만든 후 DLL에 함수 정의를 추가하여 더 유용하게 합니다.

### <a name="to-add-a-header-file-to-the-dll"></a>DLL에 헤더 파일을 추가하려면

1. 함수의 헤더 파일을 만들려면 메뉴 모음에서 **프로젝트** > **새 항목 추가** 를 선택합니다.

1. **새 항목 추가** 대화 상자의 왼쪽 창에서 **Visual C++** 를 선택합니다. 가운데 창에서 **헤더 파일 (.h)** 을 선택합니다. 헤더 파일 이름으로 *MathLibrary* 를 지정합니다.

   ![새 항목 추가 대화 상자에서 헤더 추가](media/mathlibrary-add-new-item-header-file.png "새 항목 추가 대화 상자에서 헤더 파일 추가")

1. **추가** 단추를 선택하여 빈 헤더 파일(새 편집기 창에 표시됨)을 생성합니다.

   ![편집기의 빈 MathLibrary.h 파일](media/edit-empty-mathlibrary-header.png "편집기의 빈 MathLibrary 파일")

1. 헤더 파일의 내용을 다음 코드로 바꿉니다.

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

이 헤더 파일은 두 개의 초기 값이 지정된 일반화된 피보나치 시퀀스를 생성하는 몇 가지 함수를 선언합니다. `fibonacci_init(1, 1)` 호출은 친숙한 피보나치 수열을 생성합니다.

파일 맨 위의 전처리기 문을 확인합니다. DLL 프로젝트용 새 프로젝트 템플릿은 정의된 전처리기 매크로에 **_PROJECTNAME_&#95;EXPORTS** 를 추가합니다. 이 예에서 Visual Studio는 MathLibrary DLL 프로젝트가 빌드될 때 **MATHLIBRARY&#95;EXPORTS** 를 정의합니다.

**MATHLIBRARY&#95;EXPORTS** 매크로가 정의되면 **MATHLIBRARY&#95;API** 매크로는 함수 선언에서 `__declspec(dllexport)` 한정자를 설정합니다. 이 한정자는 DLL에서 함수 또는 변수를 내보내도록 컴파일러 및 링커에 알려 다른 애플리케이션에서 사용할 수 있도록 합니다. **MATHLIBRARY&#95;EXPORTS** 가 정의되지 않은 경우(예: 헤더 파일이 클라이언트 애플리케이션에 의해 포함되는 경우) **MATHLIBRARY&#95;API** 는 선언에 `__declspec(dllimport)` 한정자를 적용합니다. 이 한정자는 애플리케이션에서 함수 또는 변수의 가져오기를 최적화합니다. 자세한 내용은 [dllexport, dllimport](../cpp/dllexport-dllimport.md)를 참조하세요.

### <a name="to-add-an-implementation-to-the-dll"></a>DLL에 구현을 추가하려면

::: moniker range=">=msvc-160"

1. **솔루션 탐색기** 에서 **소스 파일** 노드를 마우스 오른쪽 단추로 클릭하고 **추가** > **새 항목** 을 선택합니다. 이전 단계에서 새 헤더 파일을 추가한 것과 동일한 방식으로 *MathLibrary* 라는 새 .cpp 파일을 만듭니다.

1. 편집기 창에서 **MathLibrary.cpp** 가 이미 열려 있는 경우 해당 탭을 선택합니다. 그러지 않으면 **솔루션 탐색기** 에서 **MathLibrary** 프로젝트의 **소스 파일** 폴더에 있는 **MathLibrary.cpp** 를 두 번 클릭하여 엽니다.

1. 편집기에서 MathLibrary.cpp 파일의 내용을 다음 코드로 바꿉니다.

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

::: moniker-end

::: moniker range="<=msvc-150"

1. 편집기 창에서 **MathLibrary.cpp** 가 이미 열려 있는 경우 해당 탭을 선택합니다. 그러지 않으면 **솔루션 탐색기** 에서 **MathLibrary** 프로젝트의 **소스 파일** 폴더에 있는 **MathLibrary.cpp** 를 두 번 클릭하여 엽니다.

1. 편집기에서 MathLibrary.cpp 파일의 내용을 다음 코드로 바꿉니다.

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

::: moniker-end

지금까지 수행한 모든 사항이 작동하는지 확인하려면 동적 연결 라이브러리를 컴파일합니다. 컴파일하려면 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택합니다. DLL 및 관련 컴파일러 출력은 솔루션 폴더 바로 아래에 *Debug* 라는 폴더에 배치됩니다. 릴리스 빌드를 만드는 경우 출력은 *Release* 라는 폴더에 배치됩니다. 출력은 다음과 비슷합니다.

::: moniker range=">=msvc-160"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="msvc-150"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="msvc-140"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

축하합니다. Visual Studio를 사용하여 DLL을 만들었습니다! 다음으로, DLL에서 내보낸 함수를 사용하는 클라이언트 앱을 만듭니다.

## <a name="create-a-client-app-that-uses-the-dll"></a>DLL을 사용하는 클라이언트 앱 만들기

DLL을 만들 때 클라이언트 앱에서 사용할 수 있는 방법을 생각해 봅니다. 함수를 호출하거나 DLL에서 내보낸 데이터에 액세스하려면 클라이언트 소스 코드에는 컴파일 타임에 사용할 수 있는 선언이 있어야 합니다. 연결 시간에 링커에는 함수 호출 또는 데이터 액세스를 확인하는 정보가 필요합니다. DLL은 실제 코드 대신 함수 및 데이터를 찾는 방법에 대한 정보가 들어 있는 파일인 ‘라이브러리 가져오기’에서 이 정보를 제공합니다.  또한 런타임에 운영 체제가 찾을 수 있는 위치에서 클라이언트가 DLL을 사용할 수 있어야 합니다.

클라이언트 앱 프로젝트는 자체 또는 타사와 관계없이 DLL을 사용하기 위한 여러 가지 정보가 필요합니다. DLL 내보내기, 링커용 라이브러리 가져오기 및 DLL 자체를 선언하는 헤더를 찾아야 합니다. 한 가지 솔루션은 해당 파일을 모두 클라이언트 프로젝트에 복사하는 것입니다. 클라이언트가 개발 중일 때 변경될 가능성이 없는 타사 DLL의 경우 이 매서드가 DLL을 사용하는 최상의 방법이 될 수 있습니다. 그러나 DLL을 빌드하기도 할 경우에는 중복을 피하는 것이 좋습니다. 개발 중인 DLL 파일의 로컬 복사본을 만드는 경우 실수로 한 복사본의 헤더 파일은 변경하고 다른 복사본의 헤더 파일은 변경하지 않거나 오래된 라이브러리를 사용할 수 있습니다.

동기화되지 않은 코드를 방지하려면 클라이언트 프로젝트에 포함 경로를 설정하여 DLL 프로젝트에서 직접 DLL 헤더 파일을 포함하는 것이 좋습니다. 또한 클라이언트 프로젝트에 라이브러리 경로를 설정하여 DLL 프로젝트의 DLL 가져오기 라이브러리를 포함합니다. 마지막으로 DLL 프로젝트의 빌드된 DLL을 클라이언트 빌드 출력 디렉터리에 복사합니다. 이 단계에서는 클라이언트 앱이 사용자가 빌드한 것과 같은 DLL 코드를 사용할 수 있습니다.

::: moniker range=">=msvc-160"

### <a name="to-create-a-client-app-in-visual-studio"></a>Visual Studio에서 클라이언트 앱을 만들려면

1. 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서 **언어** 를 **C++** 로 설정하고 **플랫폼** 을 **Windows** 로 설정하고 **프로젝트 형식** 을 **콘솔** 로 설정합니다.

1. 필터링된 프로젝트 형식 목록에서 **콘솔 앱** 을 선택한 후 **다음** 을 선택합니다.

1. **새 프로젝트 구성** 페이지에서 **프로젝트 이름** 상자에 *MathClient* 를 입력하여 프로젝트의 이름을 지정합니다. 기본 **위치** 및 **솔루션 이름** 값은 그대로 둡니다. **솔루션** 을 **새 솔루션 만들기** 로 설정합니다. **동일한 디렉터리에 솔루션과 프로젝트 배치** 가 선택된 경우 선택을 해제합니다.

   ![콘솔 앱 옵션이 강조 표시된 새 프로젝트 만들기 대화 상자의 스크린샷](media/mathclient-project-name-2019.png "클라이언트 프로젝트 이름 지정")

1. **만들기** 단추를 선택하여 클라이언트 프로젝트를 만듭니다.

최소한의 콘솔 애플리케이션 프로젝트가 만들어집니다. 기본 소스 파일의 이름은 앞에서 입력한 프로젝트 이름과 같습니다. 이 예에서는 이름이 **MathClient.cpp** 입니다. 이 프로젝트를 빌드할 수 있지만, 아직 DLL이 사용되지는 않습니다.

::: moniker-end

::: moniker range="msvc-150"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Visual Studio 2017에서 클라이언트 앱을 만들려면

1. 만든 DLL을 사용하는 C++ 앱을 만들려면 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창의 **설치됨** > **Visual C++** 에서 **Windows 데스크톱** 을 선택합니다. 가운데 창에서 **Windows 콘솔 애플리케이션** 을 선택합니다. **이름** 편집 상자에 프로젝트 이름 *MathClient* 를 지정합니다.  기본 **위치** 및 **솔루션 이름** 값은 그대로 둡니다. **솔루션** 을 **새 솔루션 만들기** 로 설정합니다. 선택하지 않은 경우 **솔루션에 대한 디렉터리 만들기** 를 선택합니다.

   ![설치됨 > Visual C++ > Windows 데스크톱이 선택되고 Windows 콘솔 애플리케이션이 강조 표시되었으며 이름 텍스트 상자에 Math Client가 입력된 새 프로젝트 대화 상자의 스크린샷](media/mathclient-new-project-name-159.png "클라이언트 프로젝트 이름 지정")

1. **확인** 을 선택하여 클라이언트 앱 프로젝트를 만듭니다.

최소한의 콘솔 애플리케이션 프로젝트가 만들어집니다. 기본 소스 파일의 이름은 앞에서 입력한 프로젝트 이름과 같습니다. 이 예에서는 이름이 **MathClient.cpp** 입니다. 이 프로젝트를 빌드할 수 있지만, 아직 DLL이 사용되지는 않습니다.

::: moniker-end

::: moniker range="msvc-140"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>Visual Studio 2015에서 클라이언트 앱을 만들려면

1. 만든 DLL을 사용하는 C++ 앱을 만들려면 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택합니다.

1. **새 프로젝트** 대화 상자의 왼쪽 창의 **설치됨** > **템플릿** > **Visual C++** 에서 **Win32** 를 선택합니다. 가운데 창에서 **Win32 콘솔 애플리케이션** 을 선택합니다. **이름** 편집 상자에 프로젝트 이름 *MathClient* 를 지정합니다. 기본 **위치** 및 **솔루션 이름** 값은 그대로 둡니다. **솔루션** 을 **새 솔루션 만들기** 로 설정합니다. 선택하지 않은 경우 **솔루션에 대한 디렉터리 만들기** 를 선택합니다.

   ![설치됨 > 템플릿 > Visual C++ > Win32가 선택되고 Win32 콘솔 애플리케이션 Visual C++가 강조 표시되었으며 이름 텍스트 상자에 Math Client가 입력된 새 프로젝트 대화 상자의 스크린샷](media/mathclient-project-name.png "클라이언트 프로젝트 이름 지정")

1. **확인** 단추를 선택하여 **새 프로젝트** 대화 상자를 닫고 **Win32 애플리케이션 마법사** 를 시작합니다. **Win32 애플리케이션 마법사** 대화 상자의 **개요** 페이지에서 **다음** 단추를 선택합니다.

1. **애플리케이션 설정** 페이지의 **애플리케이션 유형** 에서 **콘솔 애플리케이션** 이 아직 선택되어 있지 않으면 선택합니다.

1. **마침** 단추를 선택하여 프로젝트를 만듭니다.

마법사가 완료되면 최소한의 콘솔 애플리케이션 프로젝트가 만들어집니다. 기본 소스 파일의 이름은 앞에서 입력한 프로젝트 이름과 같습니다. 이 예에서는 이름이 **MathClient.cpp** 입니다. 이 프로젝트를 빌드할 수 있지만, 아직 DLL이 사용되지는 않습니다.

::: moniker-end

다음으로, 소스 코드에서 MathLibrary 함수를 호출하려면 프로젝트가 *MathLibrary.h* 파일을 포함해야 합니다. 이 헤더 파일을 클라이언트 앱 프로젝트에 복사한 후 프로젝트에 기존 항목으로 추가할 수 있습니다. 이 방법은 타사 라이브러리에 적합할 수 있습니다. 그러나 DLL 및 클라이언트에 대한 코드에서 동시에 작업하는 경우 헤더 파일이 동기화되지 않을 수 있습니다. 이 문제를 방지하려면 원래 헤더 경로를 포함하도록 프로젝트의 **추가 포함 디렉터리** 경로를 설정합니다.

### <a name="to-add-the-dll-header-to-your-include-path"></a>포함 경로에 DLL 헤더를 추가하려면

1. **솔루션 탐색기** 에서 **MathClient** 노드를 마우스 오른쪽 단추로 클릭하여 **속성 페이지** 대화 상자를 엽니다.

1. **구성** 드롭다운 상자에서 **모든 구성** 이 아직 선택되어 있지 않으면 선택합니다.

1. 왼쪽 창에서 **구성 속성** > **C/C++**  > **일반** 을 선택합니다.

1. 속성 창에서 **추가 포함 디렉터리** 편집 상자 옆에 있는 드롭다운 컨트롤을 선택한 후 **편집** 을 선택합니다.

   ![추가 포함 디렉터리 속성 편집](media/mathclient-additional-include-directories-property.png "추가 포함 디렉터리 속성 편집")

1. **추가 포함 디렉터리** 대화 상자의 위쪽 창을 두 번 클릭하여 편집 컨트롤을 사용하도록 설정합니다. 또는 폴더 아이콘을 선택하여 새 항목을 만듭니다.

1. 편집 컨트롤에서 **MathLibrary.h** 헤더 파일 위치 경로를 지정합니다. 줄임표( **...** ) 컨트롤을 선택하여 올바른 폴더로 이동할 수 있습니다.

   클라이언트 소스 파일에서 DLL 헤더 파일이 포함된 폴더까지 상대 경로를 입력할 수도 있습니다. 클라이언트 프로젝트를 DLL과 별도의 솔루션에 배치하는 지침을 따른 경우 상대 경로는 다음과 같습니다.

   `..\..\MathLibrary\MathLibrary`

   DLL 및 클라이언트 프로젝트가 동일한 솔루션에 있는 경우 상대 경로는 다음과 같습니다.

   `..\MathLibrary`

   DLL 및 클라이언트 프로젝트가 다른 폴더에 있으면 상대 경로를 조정하여 일치시킵니다. 또는 줄임표 컨트롤을 사용하여 폴더를 찾습니다.

   ![추가 포함 디렉터리 속성에 헤더 위치 추가하기](media/mathclient-additional-include-directories.png "추가 포함 디렉터리 속성에 헤더 위치 추가하기")

1. **추가 포함 디렉터리** 대화 상자에서 헤더 파일에 대한 경로를 입력한 후 **확인** 단추를 선택합니다. **속성 페이지** 대화 상자에서 **확인** 단추를 선택하여 변경 내용을 저장합니다.

이제 **MathLibrary.h** 파일을 포함하고 해당 파일이 클라이언트 애플리케이션에서 선언하는 함수를 사용할 수 있습니다. 다음 코드를 사용하여 **MathClient.cpp** 의 내용을 바꿉니다.

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

이 코드를 컴파일할 수는 있지만 연결할 수는 없습니다. 지금 클라이언트 앱을 빌드하는 경우 오류 목록에 몇 가지 LNK2019 오류가 표시됩니다. 프로젝트에 일부 정보가 누락되었기 때문입니다. 프로젝트가 *MathLibrary.lib* 라이브러리에 대한 종속성을 가지는지 아직 지정하지 않았습니다. 또한 *MathLibrary.lib* 파일을 찾는 방법을 링커에 지시하지 않았습니다.

이 문제를 해결하기 위해 라이브러리 파일을 클라이언트 앱 프로젝트에 직접 복사할 수 있습니다. 링커가 자동으로 검색하여 사용합니다. 하지만 라이브러리와 클라이언트 앱 둘 다 개발 중인 경우 한 복사본의 변경 사항이 다른 복사본에는 표시되지 않을 수 있습니다. 이 문제를 방지하려면 **추가 종속성** 속성을 설정하여 프로젝트가 *MathLibrary.lib* 에 종속되어 있음을 빌드 시스템에 지시할 수 있습니다. 그리고 연결할 때 원래 라이브러리 경로를 포함하도록 프로젝트의 **추가 라이브러리 디렉터리** 경로를 설정할 수 있습니다.

### <a name="to-add-the-dll-import-library-to-your-project"></a>프로젝트에 DLL 가져오기 라이브러리를 추가하려면

1. **솔루션 탐색기** 에서 **MathClient** 노드를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택하여 **속성 페이지** 대화 상자를 엽니다.

1. **구성** 드롭다운 상자에서 **모든 구성** 이 아직 선택되어 있지 않으면 선택합니다. 이를 통해 디버그 및 릴리스 빌드 모두에 속성 변경이 적용됩니다.

1. 왼쪽 창에서 **구성 속성** > **링커** > **입력** 을 선택합니다. 속성 창에서 **추가 종속성** 편집 상자 옆에 있는 드롭다운 컨트롤을 선택한 후 **편집** 을 선택합니다.

   ![추가 종속성 속성 편집](media/mathclient-additional-dependencies-property.png "추가 종속성 속성 편집")

1. **추가 종속성** 대화 상자에서 맨 위 편집 컨트롤의 목록에 *MathLibrary.lib* 를 추가합니다.

   ![라이브러리 종속성 추가](media/mathclient-additional-dependencies.png "라이브러리 종속성 추가")

1. **확인** 을 선택하여 **속성 페이지** 대화 상자로 돌아갑니다.

1. 왼쪽 창에서 **구성 속성** > **링커** > **일반** 을 선택합니다. 속성 창에서 **추가 라이브러리 디렉터리** 편집 상자 옆에 있는 드롭다운 컨트롤을 선택한 후 **편집** 을 선택합니다.

   ![추가 라이브러리 디렉터리 속성 편집](media/mathclient-additional-library-directories-property.png "추가 라이브러리 디렉터리 속성 편집")

1. **추가 라이브러리 디렉터리** 대화 상자의 위쪽 창을 두 번 클릭하여 편집 컨트롤을 사용하도록 설정합니다. 편집 컨트롤에서 **MathLibrary.lib** 파일 위치 경로를 지정합니다. 기본적으로 DLL 솔루션 폴더 바로 아래에 *Debug* 라는 폴더에 있습니다. 릴리스 빌드를 만드는 경우 파일은 *Release* 라는 폴더에 배치됩니다. 사용자가 만드는 빌드 종류와 관계없이 링커가 DLL을 찾을 수 있도록 `$(IntDir)` 매크로를 사용할 수 있습니다. 클라이언트 프로젝트를 DLL 프로젝트와는 별개의 솔루션에 배치하는 지침을 따른 경우 상대 경로는 다음과 같습니다.

   `..\..\MathLibrary\$(IntDir)`

   DLL 및 클라이언트 프로젝트가 다른 위치에 있으면 상대 경로를 조정하여 일치시킵니다.

   ![라이브러리 디렉터리 추가](media/mathclient-additional-library-directories.png "라이브러리 디렉터리 추가")

1. **추가 라이브러리 디렉터리** 대화 상자에서 라이브러리 파일 경로를 입력한 후에는 **확인** 단추를 선택하여 **속성 페이지** 대화 상자로 돌아갑니다. **확인** 을 선택하여 속성 변경 내용을 저장합니다.

이제 클라이언트 앱을 컴파일하고 연결할 수 있지만, 아직 실행하는 데 필요한 모든 사항이 갖춰지지는 않았습니다. 운영 체제가 앱을 로드할 때 MathLibrary DLL을 찾습니다. 특정 시스템 디렉터리, 환경 경로 또는 로컬 앱 디렉터리에서 DLL을 찾을 수 없는 경우 로드에 실패합니다. 운영 체제에 따라 다음과 같은 오류 메시지가 표시됩니다.

![MathLibrary DLL을 찾을 수 없음 오류](media/mathclient-system-error-mathlibrary-dll-not-found.png "MathLibrary DLL을 찾을 수 없음 오류")

이 문제를 방지하는 한 가지 방법은 빌드 프로세스의 일부로 클라이언트 실행 파일을 포함하는 디렉터리에 DLL을 복사하는 것입니다. 프로젝트에 **빌드 후 이벤트** 를 추가하여 DLL을 빌드 출력 디렉터리에 복사하는 명령을 추가하면 됩니다. 여기에 지정된 명령은 DLL이 없거나 변경된 경우에만 해당 DLL을 복사합니다. 빌드 구성에 따라 매크로를 사용하여 디버그 또는 릴리스 위치에 복사합니다.

### <a name="to-copy-the-dll-in-a-post-build-event"></a>빌드 후 이벤트에 DLL을 복사하려면

1. **솔루션 탐색기** 에서 **MathClient** 노드를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택하여 **속성 페이지** 대화 상자를 엽니다.

1. **구성** 드롭다운 상자에서 **모든 구성** 이 아직 선택되어 있지 않으면 선택합니다.

1. 왼쪽 창에서 **구성 속성** > **빌드 이벤트** > **빌드 후 이벤트** 를 선택합니다.

1. 속성 창의 **명령줄** 필드에서 편집 컨트롤을 선택합니다. 클라이언트 프로젝트를 DLL 프로젝트와는 별개의 솔루션에 배치하는 지침을 따른 경우 다음 명령을 입력합니다.

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   DLL 및 클라이언트 프로젝트가 다른 디렉터리에 있으면 상대 경로를 DLL에 일치하도록 조정합니다.

   ![빌드 후 명령 추가](media/mathclient-post-build-command-line.png "빌드 후 명령 추가")

1. **확인** 단추를 선택하여 프로젝트 속성의 변경 사항을 저장합니다.

이제 클라이언트 앱을 빌드 및 실행하는 데 필요한 모든 사항이 갖춰졌습니다. 메뉴 모음에서 **빌드** > **솔루션 빌드** 를 선택하여 애플리케이션을 빌드합니다. Visual Studio의 **출력** 창에는 Visual Studio 버전에 따라 다음 예제와 같은 항목이 있어야 합니다.

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

축하합니다. DLL의 함수를 호출하는 애플리케이션을 만들었습니다. 이제 애플리케이션을 실행하여 수행하는 작업을 확인합니다. 메뉴 모음에서 **디버그** > **디버깅하지 않고 시작** 을 선택합니다. Visual Studio에서 프로그램을 실행하기 위한 명령 창이 열립니다. 출력의 마지막 부분은 다음과 같습니다.

![디버깅하지 않고 클라이언트 앱 시작](media/mathclient-run-without-debugging.png "디버깅하지 않고 클라이언트 앱 시작")

아무 키나 눌러 명령 창을 닫습니다.

이제 DLL과 클라이언트 애플리케이션을 만들었으므로 실험할 수 있습니다. 클라이언트 앱의 코드에 중단점을 설정하고 디버거에서 앱을 실행합니다. 라이브러리 호출을 한 단계씩 코드 실행할 때 어떤 일이 발생하는지 확인합니다. 라이브러리에 DLL을 사용하는 다른 함수를 추가하거나, DLL을 사용하는 다른 클라이언트 앱을 작성합니다.

앱을 배포할 때 앱에 사용되는 DLL도 배포해야 합니다. 직접 빌드하거나 타사에서 포함하는 DLL을 사용할 수 있게 만드는 가장 간단한 방법은 앱과 같은 디렉터리에 배치하는 것입니다. ‘앱 로컬 배포’라고 합니다.  배포에 대한 자세한 내용은 [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md)를 참조하세요.

## <a name="see-also"></a>참조

[Visual Basic 애플리케이션에서 DLL 함수 호출](calling-dll-functions-from-visual-basic-applications.md)
