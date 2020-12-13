---
description: '자세한 내용: 그리기 코드 변경 (ATL 자습서, 4 부)'
title: 그리기 코드 변경(ATL 자습서, 4부)
ms.custom: get-started-article
ms.date: 09/26/2018
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 08ff14e8-aa49-4139-a110-5d071939cf1e
ms.openlocfilehash: 4d134930bf2c9bc886a3c59a68db5a52f7c6ca7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153384"
---
# <a name="changing-the-drawing-code-atl-tutorial-part-4"></a>그리기 코드 변경(ATL 자습서, 4부)

기본적으로 컨트롤의 그리기 코드는 사각형 및 텍스트 **polyctl.htm** 을 표시 합니다. 이 단계에서는 코드를 변경 하 여 더 흥미로운 항목을 표시 합니다. 관련 된 작업은 다음과 같습니다.

- 헤더 파일 수정

- 함수 수정 `OnDraw`

- 다각형 점수를 계산 하는 메서드 추가

- 채우기 색 초기화

## <a name="modifying-the-header-file"></a>헤더 파일 수정

먼저 수학 함수 및에 대 한 지원을 추가 하 `sin` `cos` 고, 다각형 점수를 계산 하 고, 위치를 저장 하는 배열을 만들어 사용 해야 합니다.

### <a name="to-modify-the-header-file"></a>헤더 파일을 수정 하려면

1. Polyctl.htm의 맨 위에 줄을 추가 합니다. `#include <math.h>` 파일의 위쪽은 다음과 같습니다.

    [!code-cpp[NVC_ATL_Windowing#47](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_1.cpp)]

1. `IProvideClassInfo`Polyctl.htm에 다음 코드를 추가 하 여 컨트롤에 대 한 메서드 정보를 제공 하는 인터페이스를 구현 합니다. 클래스에서 `CPolyCtl` 줄을 바꿉니다.

    ```cpp
    public CComControl<CPolyCtl>
    ```

    다음과 같이 바꿉니다.

    ```cpp
    public CComControl<CPolyCtl>,
    public IProvideClassInfo2Impl<&CLSID_PolyCtl, &DIID__IPolyCtlEvents, &LIBID_PolygonLib>
    ```

    그리고에서 `BEGIN_COM_MAP(CPolyCtl)` 다음 줄을 추가 합니다.

    ```cpp
    COM_INTERFACE_ENTRY(IProvideClassInfo)
    COM_INTERFACE_ENTRY(IProvideClassInfo2)
    ```

1. 다각형 점이 계산 된 후에는 형식의 배열에 저장 `POINT` 되므로 polyctl.htm의 정의 문 뒤에 배열을 추가 `short m_nSides;` 합니다.

    [!code-cpp[NVC_ATL_Windowing#48](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_2.h)]

## <a name="modifying-the-ondraw-method"></a>OnDraw 메서드 수정

이제 Polyctl.htm에서 메서드를 수정 해야 합니다. `OnDraw` 추가 하는 코드는 다각형을 그릴 새 펜과 브러시를 만든 다음 `Ellipse` , 및 Win32 API 함수를 호출 하 여 `Polygon` 실제 그리기를 수행 합니다.

### <a name="to-modify-the-ondraw-function"></a>OnDraw 함수를 수정 하려면

1. `OnDraw`Polyctl.htm의 기존 메서드를 다음 코드로 바꿉니다.

    [!code-cpp[NVC_ATL_Windowing#49](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_3.cpp)]

## <a name="adding-a-method-to-calculate-the-polygon-points"></a>다각형 점수를 계산 하는 메서드 추가

`CalcPoints`다각형의 경계를 구성 하는 점의 좌표를 계산 하는 라는 메서드를 추가 합니다. 이러한 계산은 함수로 전달 되는 RECT 변수에 따라 결정 됩니다.

### <a name="to-add-the-calcpoints-method"></a>CalcPoints 메서드를 추가 하려면

1. 의 선언을 `CalcPoints` `IPolyCtl` polyctl.htm에서 클래스의 public 섹션에 추가 `CPolyCtl` 합니다.

    [!code-cpp[NVC_ATL_Windowing#50](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_4.h)]

    클래스의 public 섹션에서 마지막 부분은 다음과 같이 표시 `CPolyCtl` 됩니다.

    [!code-cpp[NVC_ATL_Windowing#51](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_5.h)]

1. 이 `CalcPoints` 함수의 구현을 polyctl.htm의 끝에 추가 합니다.

    [!code-cpp[NVC_ATL_Windowing#52](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_6.cpp)]

## <a name="initializing-the-fill-color"></a>채우기 색 초기화

`m_clrFillColor`기본 색을 사용 하 여 초기화 합니다.

### <a name="to-initialize-the-fill-color"></a>채우기 색을 초기화 하려면

1. Polyctl.htm의 생성자에 다음 줄을 추가 하 여 녹색을 기본 색으로 사용 `CPolyCtl` 합니다.

    [!code-cpp[NVC_ATL_Windowing#53](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_7.h)]

이제 생성자는 다음과 같습니다.

[!code-cpp[NVC_ATL_Windowing#54](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_8.h)]

## <a name="building-and-testing-the-control"></a>컨트롤 빌드 및 테스트

컨트롤을 다시 빌드합니다. PolyCtl.htm 파일이 열려 있으면 해당 파일이 닫혀 있는지 확인 하 고 **빌드** 메뉴에서 **Polygon 빌드** 를 클릭 합니다. PolyCtl.htm 페이지에서 컨트롤을 다시 한 번 볼 수 있지만 이번에는 ActiveX 컨트롤 테스트 컨테이너를 사용 합니다.

### <a name="to-use-the-activex-control-test-container"></a>ActiveX 컨트롤 테스트 컨테이너를 사용 하려면

1. ActiveX 컨트롤 테스트 컨테이너를 빌드하고 시작 합니다. [TSTCON 샘플: ActiveX 컨트롤 테스트 컨테이너](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/MFC/ole/TstCon) 는 GitHub에서 찾을 수 있습니다.

    > [!NOTE]
    > 관련 된 오류의 경우 node.js `ATL::CW2AEX` 에서 줄을 `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT );` 로 바꾸고 줄을 `TRACE( "XActiveScriptSite::GetItemInfo( %s )\n", pszNameT.m_psz );` 로 바꿉니다 `TRACE( "Source Text: %s\n", COLE2CT( bstrSourceLineText ) );` `TRACE( "Source Text: %s\n", bstrSourceLineText );` .<br/>
    > 관련 된 오류의 경우 `HMONITOR` 프로젝트에서 stdafx.h를 열고 `TCProps` 다음을 바꿉니다.
    >
    > ```cpp
    > #ifndef WINVER
    > #define WINVER 0x0400
    > #endif
    > ```
    >
    > 다음과 같이 바꿉니다.
    >
    > ```cpp
    > #ifndef WINVER
    > #define WINVER 0x0500
    > #define _WIN32_WINNT 0x0500
    > #endif
    > ```

1. **테스트 컨테이너** 의 **편집** 메뉴에서 **새 컨트롤 삽입** 을 클릭 합니다.

1. 호출 되는 컨트롤을 찾은 `PolyCtl class` 다음 **확인** 을 클릭 합니다. 원 안에 녹색 삼각형이 표시 됩니다.

다음 절차에 따라 변의 수를 변경해 봅니다. **테스트 컨테이너** 내에서 이중 인터페이스에 대 한 속성을 수정 하려면 **Invoke 메서드** 를 사용 합니다.

### <a name="to-modify-a-controls-property-from-within-the-test-container"></a>테스트 컨테이너 내에서 컨트롤의 속성을 수정 하려면

1. **테스트 컨테이너** 에서 **컨트롤** 메뉴의 **메서드 호출** 을 클릭 합니다.

    **메서드 호출** 대화 상자가 표시 됩니다.

1. **메서드 이름** 드롭다운 목록 상자에서 **변의** 속성의 **PropPut** 버전을 선택 합니다.

1. `5` **매개 변수 값** 상자에를 입력 하 고 **값 설정** 을 클릭 한 다음 **호출** 을 클릭 합니다.

컨트롤은 변경 되지 않습니다. 변수를 설정 하 여 변의 수를 내부적으로 변경 했지만 `m_nSides` 이로 인해 컨트롤이 다시 그려지지는 않습니다. 다른 응용 프로그램으로 전환 하 고 다시 **테스트 컨테이너로** 전환 하는 경우 컨트롤이 다시 표시 되 고 올바른 수의 쪽이 있음을 알 수 있습니다.

이 문제를 해결 하려면 `FireViewChange` 변의 수를 설정한 후에 정의 된 함수에 대 한 호출을 추가 `IViewObjectExImpl` 합니다. 컨트롤이 자체 창에서 실행 되는 경우는 `FireViewChange` 메서드를 직접 호출 `InvalidateRect` 합니다. 컨트롤이 창 없는 창에서 실행 되는 경우 해당 `InvalidateRect` 메서드는 컨테이너의 사이트 인터페이스에서 호출 됩니다. 그러면 컨트롤이 자체적으로 다시 그려집니다.

### <a name="to-add-a-call-to-fireviewchange"></a>FireViewChange에 대 한 호출을 추가 하려면

1. 에 대 한 호출을 메서드에 추가 하 여 Polyctl.htm를 업데이트 합니다 `FireViewChange` `put_Sides` . 완료 되 면 `put_Sides` 메서드는 다음과 같습니다.

    [!code-cpp[NVC_ATL_Windowing#55](../atl/codesnippet/cpp/changing-the-drawing-code-atl-tutorial-part-4_9.cpp)]

를 추가한 후에 `FireViewChange` 는 ActiveX 컨트롤 테스트 컨테이너에서 다시 빌드하고 컨트롤을 다시 시도 합니다. 이번에는 변의 수를 변경 하 고 클릭 하면 `Invoke` 컨트롤이 즉시 변경 되는 것을 볼 수 있습니다.

다음 단계에서는 이벤트를 추가 합니다.

[3 단계로 돌아가서](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md) [5 단계를](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; 합니다.

## <a name="see-also"></a>참고 항목

[자습서](../atl/active-template-library-atl-tutorial.md)<br/>
[테스트 컨테이너로 속성 및 이벤트 테스트](../mfc/testing-properties-and-events-with-test-container.md)
