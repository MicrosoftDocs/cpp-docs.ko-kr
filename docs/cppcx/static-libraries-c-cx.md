---
title: 정적 라이브러리(C++/CX)
ms.date: 02/03/2017
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
ms.openlocfilehash: 756f8d2c1af2c6be414ad39b4a96fa6cc7ccfb02
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924709"
---
# <a name="static-libraries-ccx"></a>정적 라이브러리(C++/CX)

UWP (유니버설 Windows 플랫폼) 앱에서 사용 되는 정적 라이브러리는 STL 형식을 비롯 하 여 ISO 표준 c + + 코드를 포함할 수 있으며 Windows 런타임 앱 플랫폼에서 제외 되지 않은 Win32 Api에 대 한 호출도 포함할 수 있습니다. 정적 라이브러리는 Windows 런타임 구성 요소를 사용 하며 특정 제한 사항이 있는 Windows 런타임 구성 요소를 만들 수 있습니다.

## <a name="creating-static-libraries"></a>정적 라이브러리 만들기

새 프로젝트를 만드는 방법에 대 한 지침은 설치한 Visual Studio 버전에 따라 다릅니다. 기본 설정된 버전의 Visual Studio에 대한 설명서를 보려면 **버전** 선택기 컨트롤을 사용하세요. 이 페이지의 목차 맨 위에 있습니다.

::: moniker range="msvc-160"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2019"></a>Visual Studio 2019에서 UWP 정적 라이브러리를 만들려면

1. 메뉴 모음에서 **파일** >**새로 만들기** >**프로젝트** 를 선택하여 **새 프로젝트 만들기** 대화 상자를 엽니다.

1. 대화 상자 맨 위에서  **언어** 를 **c + +** 로 설정 하 고, **플랫폼** 을 **Windows** 로 설정 하 고, **프로젝트 형식** 을 **UWP** 로 설정 합니다.

1. 필터링 된 프로젝트 형식 목록에서 **정적 라이브러리 (유니버설 Windows-c + +/cx)** 를 선택한 후 **다음** 을 선택 합니다. 다음 페이지에서 프로젝트에 이름을 지정 하 고 원하는 경우 프로젝트 위치를 지정 합니다.

1. **만들기** 단추를 선택하여 프로젝트를 만듭니다.

::: moniker-end

::: moniker range="<=msvc-150"

### <a name="to-create-a-uwp-static-library-in-visual-studio-2017-or-visual-studio-2015"></a>Visual Studio 2017 또는 Visual Studio 2015에서 UWP 정적 라이브러리를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트** 를 선택합니다. **Visual C++**  >  **Windows 유니버설** 에서 **정적 라이브러리 (유니버설 Windows)** 를 선택 합니다.

1. **솔루션 탐색기** 에서 프로젝트의 바로 가기 메뉴를 열고 **속성** 을 선택합니다. **속성** 대화 상자의 **구성 속성**  >  **C/c + +** 페이지에서 **Windows 런타임 확장 사용** 을 **예 (/zw)** 로 설정 합니다.

::: moniker-end

새 정적 라이브러리를 컴파일할 때 UWP 앱에 대해 제외 된 Win32 API를 호출 하면 컴파일러에서 오류 C3861 "식별자를 찾을 수 없습니다."가 발생 합니다. Windows 런타임에 대해 지원 되는 대체 방법을 찾으려면 [UWP 앱에서 Windows api에](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)대 한 대체 항목을 참조 하세요.

UWP 앱 솔루션에 c + + 정적 라이브러리 프로젝트를 추가 하는 경우 UWP 지원 속성이 **예** 로 설정 되도록 라이브러리 프로젝트의 속성 설정을 업데이트 해야 할 수 있습니다. 이 설정이 없으면 코드가 빌드되고 연결 되지만 Microsoft Store에 대 한 앱을 확인 하려고 하면 오류가 발생 합니다. 정적 lib는 해당 lib를 사용하는 프로젝트와 동일한 컴파일러 설정을 사용하여 컴파일해야 합니다.

public `ref` 클래스, 공용 인터페이스 클래스 또는 공용 값 클래스를 만드는 정적 라이브러리를 사용하면 링커가 다음과 같은 경고를 발생시킵니다.

> **경고 LNK4264:** /zw를 사용 하 여 컴파일된 개체 파일을 정적 라이브러리에 보관 합니다. Windows 런타임 형식을 작성 하는 경우 Windows 런타임 메타 데이터를 포함 하는 정적 라이브러리와 연결 하지 않는 것이 좋습니다.

정적 라이브러리가 라이브러리 자체 외부에서 사용 되는 Windows 런타임 구성 요소를 생성 하지 않는 경우에만 경고를 안전 하 게 무시할 수 있습니다. 라이브러리에 정의된 구성 요소가 라이브러리에 사용되지 않는 경우 링커는 공용 메타 데이터에 형식 정보가 있는 경우에도 구현을 최적화할 수 있습니다. 즉, 정적 라이브러리의 공용 구성 요소는 컴파일되지만 런타임에 활성화되지 않습니다. 따라서 다른 구성 요소나 앱에서 사용 하기 위한 모든 Windows 런타임 구성 요소는 DLL (동적 연결 라이브러리)에서 구현 되어야 합니다.

## <a name="see-also"></a>참고 항목

[스레딩 및 마샬링](../cppcx/threading-and-marshaling-c-cx.md)
