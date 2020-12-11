---
description: '자세히 알아보기: 웹 페이지에 컨트롤 배치 (ATL 자습서, 7 부)'
title: 웹 페이지에 컨트롤 배치(ATL 자습서, 7부)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: 738d847a6436a2afab2e336502ec3255d1a1e589
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97159181"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>웹 페이지에 컨트롤 배치(ATL 자습서, 7부)

이제 컨트롤이 끝났습니다. 실제 상황에서 컨트롤이 작동 하는 것을 확인 하려면 웹 페이지에 배치 합니다. 컨트롤을 정의할 때 컨트롤을 포함 하는 HTML 파일이 생성 되었습니다. **솔루션 탐색기** 에서 PolyCtl.htm 파일을 열면 웹 페이지에서 컨트롤을 볼 수 있습니다.

이 단계에서는 컨트롤에 기능을 추가 하 고 이벤트에 응답 하는 웹 페이지를 스크립팅 합니다. 또한 컨트롤을 수정 하 여 Internet Explorer에서 컨트롤이 스크립팅에 안전 하다는 것을 알 수 있습니다.

## <a name="adding-new-functionality"></a>새 기능 추가

### <a name="to-add-control-features"></a>컨트롤 기능을 추가 하려면

1. Polyctl.htm를 열고 다음 코드를 바꿉니다.

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    다음과 같이 바꿉니다.

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

이제 셰이프는 클릭 한 위치에 따라 면을 추가 하거나 제거 합니다.

## <a name="scripting-the-web-page"></a>웹 페이지 스크립팅

컨트롤은 아직 작업을 수행 하지 않으므로 전송 하는 이벤트에 응답 하도록 웹 페이지를 변경 합니다.

### <a name="to-script-the-web-page"></a>웹 페이지를 스크립팅하려면

1. PolyCtl.htm를 열고 HTML 보기를 선택 합니다. HTML 코드에 다음 줄을 추가 합니다. 이후에 추가 해야 `</OBJECT>` `</BODY>` 합니다.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. HTM 파일을 저장 합니다.

컨트롤에서 변의 속성을 가져오는 일부 VBScript 코드를 추가 했습니다. 컨트롤 내부를 클릭 하면 변의 수가 하나씩 늘어납니다. 컨트롤 바깥쪽을 클릭 하면 변의 수가 하나씩 줄어듭니다.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>컨트롤이 스크립팅에 안전 함을 나타냅니다.

Internet Explorer의 컨트롤을 사용 하 여 웹 페이지를 볼 수 있습니다. 다른 브라우저는 보안 약점 때문에 ActiveX 컨트롤을 더 이상 지원 하지 않습니다.

> [!NOTE]
> 컨트롤이 표시 되지 않는 경우 일부 브라우저에서 ActiveX 컨트롤을 실행 하기 위한 설정 조정이 필요 함을 알 수 있습니다. ActiveX 컨트롤을 사용 하도록 설정 하는 방법에 대 한 브라우저 설명서를 참조 하세요.

현재 Internet Explorer 보안 설정에 따라 보안 경고 대화 상자가 표시 될 수 있습니다. 컨트롤은 스크립트에 안전 하지 않을 수 있으며 잠재적으로 손상 될 수 있습니다. 예를 들어 파일을 표시 하지만 파일을 삭제 한 메서드가 있는 컨트롤이 있는 경우 `Delete` 페이지에서 보기만 하면 안전 합니다. 그러나 누군가가 메서드를 호출할 수 있기 때문에 스크립트는 안전 하지 않습니다 `Delete` .

> [!IMPORTANT]
> 이 자습서에서는 Internet Explorer의 보안 설정을 변경 하 여 안전한 것으로 표시 되지 않은 ActiveX 컨트롤을 실행할 수 있습니다. 제어판에서 **인터넷 속성** 을 클릭 하 고 **보안** 을 클릭 하 여 적절 한 설정을 변경 합니다. 자습서를 완료 한 후에는 보안 설정을 다시 원래 상태로 변경 합니다.

이 특정 컨트롤에 대 한 보안 경고 대화 상자를 표시 하지 않아도 되도록 Internet Explorer에 프로그래밍 방식으로 경고할 수 있습니다. 인터페이스를 사용 하 여이 작업을 수행할 수 있습니다 `IObjectSafety` . ATL은 [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md)클래스에서이 인터페이스의 구현을 제공 합니다. 컨트롤에 인터페이스를 추가 하려면 `IObjectSafetyImpl` 상속 된 클래스 목록에를 추가 하 고 COM 맵에 항목을 추가 합니다.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>컨트롤에 IObjectSafetyImpl를 추가 하려면

1. Polyctl.htm에서 상속 된 클래스 목록의 끝에 다음 줄을 추가 하 고 앞 줄에 쉼표를 추가 합니다.

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Polyctl.htm의 COM 맵에 다음 줄을 추가 합니다.

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>컨트롤 빌드 및 테스트

컨트롤을 빌드합니다. 빌드가 완료 되 면 브라우저 보기에서 PolyCtl.htm를 다시 엽니다. 이번에는 **보안 경고** 대화 상자 없이 웹 페이지를 직접 표시 해야 합니다. 다각형 내부를 클릭 하면 변의 수가 1 씩 늘어납니다. 다각형 바깥쪽을 클릭 하 여 변의 수를 줄입니다.

[6 단계로 돌아가기](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>다음 단계

이 단계에서는 ATL 자습서를 마칩니다. ATL에 대 한 자세한 내용은 [atl 시작 페이지](../atl/active-template-library-atl-concepts.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[자습서](../atl/active-template-library-atl-tutorial.md)
