---
description: '자세히 알아보기: 컨트롤에 속성 추가 (ATL 자습서, 3 부)'
title: 컨트롤에 속성 추가(ATL 자습서, 3부)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: f775fe34-103b-4f07-9999-400e987ee030
ms.openlocfilehash: 22a44b6878afd6d51fb396d8f02a60e93436cf05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166332"
---
# <a name="adding-a-property-to-the-control-atl-tutorial-part-3"></a>컨트롤에 속성 추가(ATL 자습서, 3부)

`IPolyCtl` 는 컨트롤의 사용자 지정 메서드 및 속성을 포함 하는 인터페이스 이며 여기에 속성을 추가 합니다.

### <a name="to-add-the-property-definitions-to-your-project"></a>프로젝트에 속성 정의를 추가 하려면

1. **클래스 뷰** 에서 분기를 확장 `Polygon` 합니다.

1. 를 마우스 오른쪽 단추로 클릭 `IPolyCtl` 합니다.

1. 바로 가기 메뉴에서 **추가** 를 클릭 한 다음 **속성 추가** 를 클릭 합니다. **속성 추가** 마법사가 나타납니다.

1. `Sides` **속성 이름** 으로를 입력 합니다.

1. **속성 유형** 드롭다운 목록에서을 선택 **`short`** 합니다.

1. **확인** 을 클릭 하 여 속성 추가를 마칩니다.

1. **솔루션 탐색기** 에서 Polygon을 열고 인터페이스 끝에서 다음 줄을 바꿉니다 `IPolyCtl : IDispatch` .

    ```cpp
    short get_Sides();
    void set_Sides(short value);
    ```

    다음과 같이 바꿉니다.

    ```cpp
    [propget, id(1), helpstring("property Sides")] HRESULT Sides([out, retval] short *pVal);
    [propput, id(1), helpstring("property Sides")] HRESULT Sides([in] short newVal);
    ```

1. **솔루션 탐색기** 에서 polyctl.htm를 열고의 정의 뒤에 다음 줄을 추가 `m_clrFillColor` 합니다.

    [!code-cpp[NVC_ATL_Windowing#44](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_1.h)]

이제 속성 및 속성을 저장 하는 변수를 설정 하 고 검색 하는 기본 함수가 있지만 함수를 적절 하 게 구현 해야 합니다.

### <a name="to-update-the-get-and-put-methods"></a>Get 및 put 메서드를 업데이트 하려면

1. 의 기본값을 설정 `m_nSides` 합니다. Polyctl.htm의 생성자에 줄을 추가 하 여 기본 모양을 삼각형으로 만듭니다.

    [!code-cpp[NVC_ATL_Windowing#45](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_2.h)]

1. `Get`및 메서드를 구현 `Put` 합니다. `get_Sides`및 `put_Sides` 함수 선언이 polyctl.htm에 추가 되었습니다. 이제 다음을 사용 하 여 및에 대 한 코드를 `get_Sides` `put_Sides` polyctl.htm에 추가 합니다.

    [!code-cpp[NVC_ATL_Windowing#46](../atl/codesnippet/cpp/adding-a-property-to-the-control-atl-tutorial-part-3_3.cpp)]

`get_Sides`메서드는 `Sides` 포인터를 통해 속성의 현재 값을 반환 합니다 `pVal` . `put_Sides`메서드에서 코드는 사용자가 `Sides` 속성을 허용 가능한 값으로 설정 하 고 있는지 확인 합니다. 최소값은 3이 고, 점의 배열이 각 면에 사용 되므로 100는 최대값에 대 한 적절 한 제한입니다.

이제 라는 속성이 있습니다 `Sides` . 다음 단계에서는 그리기 코드를 사용 하도록 변경 합니다.

[2 단계로 돌아가기](../atl/adding-a-control-atl-tutorial-part-2.md) &#124; [4 단계](../atl/changing-the-drawing-code-atl-tutorial-part-4.md)

## <a name="see-also"></a>참고 항목

[자습서](../atl/active-template-library-atl-tutorial.md)
