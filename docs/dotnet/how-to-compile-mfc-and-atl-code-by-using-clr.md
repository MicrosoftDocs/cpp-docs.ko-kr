---
description: '자세히 알아보기: 방법:/clr을 사용 하 여 MFC 및 ATL 코드 컴파일'
title: 방법:-clr을 사용 하 여 MFC 및 ATL 코드 컴파일
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], interoperability
- ATL [C++], interoperability
- mixed assemblies [C++], MFC code
- mixed assemblies [C++], ATL code
- /clr compiler option [C++], compiling ATL and MFC code
- interoperability [C++], /clr compiler option
- regular MFC DLLs [C++], /clr compiler option
- interop [C++], /clr compiler option
- extension DLLs [C++], /clr compiler option
ms.assetid: 12464bec-33a4-482c-880a-c078de7f6ea5
ms.openlocfilehash: 67a861dac3b4c4b454f4fbde4a500c3677ce0e25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97304495"
---
# <a name="how-to-compile-mfc-and-atl-code-by-using-clr"></a>방법: /clr을 사용하여 MFC 및 ATL 코드 컴파일

이 항목에서는 공용 언어 런타임을 대상으로 하는 기존 MFC 및 ATL 프로그램을 컴파일하는 방법에 대해 설명 합니다.

### <a name="to-compile-an-mfc-executable-or-regular-mfc-dll-by-using-clr"></a>/Clr을 사용 하 여 MFC 실행 파일 또는 일반 MFC DLL을 컴파일하려면

1. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다.

1. **프로젝트 속성** 대화 상자에서 **구성 속성** 옆에 있는 노드를 확장 하 고 **일반** 을 선택 합니다. 오른쪽 창의 **프로젝트 기본값** 에서 **공용 언어 런타임 지원** 을 **공용 언어 런타임 지원 (/clr)** 으로 설정 합니다.

   동일한 창에서 **Mfc 사용** 이 **공유 DLL에서 mfc를 사용** 하도록 설정 되어 있는지 확인 합니다.

1. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. **디버그 정보 형식이** **프로그램 데이터베이스/zi** ( **/zi** 아님)로 설정 되어 있는지 확인 합니다.

1. **코드 생성** 노드를 선택 합니다. **최소 다시 빌드 사용** 을 **아니요 (/gm-)** 로 설정 합니다. 또한 기본 **런타임 검사** 를 **기본** 으로 설정 합니다.

1. **구성 속성** 에서 **C/c + +** , **코드 생성** 을 차례로 선택 합니다. **런타임 라이브러리가** **다중 스레드 디버그 dll (/Mdd)** 또는 **다중 스레드 DLL (/md)** 로 설정 되어 있는지 확인 합니다.

1. Stdafx.h에서 다음 줄을 추가 합니다.

    ```
    #using <System.Windows.Forms.dll>
    ```

### <a name="to-compile-an-mfc-extension-dll-by-using-clr"></a>/Clr을 사용 하 여 MFC 확장명 DLL을 컴파일하려면

1. "/Clr을 사용 하 여 MFC 실행 파일 또는 일반 MFC DLL을 컴파일하려면"의 단계를 따르세요.

1. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **미리 컴파일된 헤더** 를 선택 합니다. 미리 컴파일된 헤더를 **사용 하지 않도록** **미리 컴파일된 헤더 만들기/사용** 을 설정 합니다.

   또는 **솔루션 탐색기** 에서 stdafx.h를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. 공용 언어 런타임 **지원을 사용 하 여 컴파일** 을 **공용 언어 런타임 지원을 사용 하지 않도록** 설정 합니다.

1. DllMain을 포함 하는 파일 및 호출 하는 모든 항목에 대해 **솔루션 탐색기** 에서 파일을 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. 오른쪽 창의 **프로젝트 기본값** 에서 공용 언어 **런타임 지원을 사용 하 여 컴파일** 을 **공용 언어 런타임 지원** 으로 설정 합니다.

### <a name="to-compile-an-atl-executable-by-using-clr"></a>/Clr을 사용 하 여 ATL 실행 파일을 컴파일하려면

1. **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다.

1. **프로젝트 속성** 대화 상자에서 **구성 속성** 옆에 있는 노드를 확장 하 고 **일반** 을 선택 합니다. 오른쪽 창의 **프로젝트 기본값** 에서 **공용 언어 런타임 지원** 을 **공용 언어 런타임 지원 (/clr)** 으로 설정 합니다.

1. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. **디버그 정보 형식이** **프로그램 데이터베이스/zi** ( **/zi** 아님)로 설정 되어 있는지 확인 합니다.

1. **코드 생성** 노드를 선택 합니다. **최소 다시 빌드 사용** 을 **아니요 (/gm-)** 로 설정 합니다. 또한 기본 **런타임 검사** 를 **기본** 으로 설정 합니다.

1. **구성 속성** 에서 **C/c + +** , **코드 생성** 을 차례로 선택 합니다. **런타임 라이브러리가** **다중 스레드 디버그 dll (/Mdd)** 또는 **다중 스레드 DLL (/md)** 로 설정 되어 있는지 확인 합니다.

1. 모든 MIDL 생성 파일 (C 파일)에 대해 **솔루션 탐색기** 에서 파일을 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. 공용 언어 런타임 **지원을 사용 하 여 컴파일** 을 **공용 언어 런타임 지원을 사용 하지 않도록** 설정 합니다.

### <a name="to-compile-an-atl-dll-by-using-clr"></a>/Clr을 사용 하 여 ATL DLL을 컴파일하려면

1. "/Clr을 사용 하 여 ATL 실행 파일을 컴파일하려면" 섹션의 단계를 따르세요.

1. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **미리 컴파일된 헤더** 를 선택 합니다. 미리 컴파일된 헤더를 **사용 하지 않도록** **미리 컴파일된 헤더 만들기/사용** 을 설정 합니다.

   또는 **솔루션 탐색기** 에서 stdafx.h를 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. 공용 언어 런타임 **지원을 사용 하 여 컴파일** 을 **공용 언어 런타임 지원을 사용 하지 않도록** 설정 합니다.

1. DllMain을 포함 하는 파일 및 호출 하는 모든 항목에 대해 **솔루션 탐색기** 에서 파일을 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 클릭 합니다. **구성 속성** 에서 **C/c + +** 옆의 노드를 확장 하 고 **일반** 을 선택 합니다. 오른쪽 창의 **프로젝트 기본값** 에서 공용 언어 **런타임 지원을 사용 하 여 컴파일** 을 **공용 언어 런타임 지원** 으로 설정 합니다.

## <a name="see-also"></a>참고 항목

[혼합형 (네이티브 및 관리) 어셈블리](../dotnet/mixed-native-and-managed-assemblies.md)
