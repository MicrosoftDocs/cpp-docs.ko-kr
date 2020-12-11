---
description: '자세히 알아보기: 창 특성 이해'
title: ATL 창 특성
ms.date: 11/04/2016
helpviewer_keywords:
- window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
ms.openlocfilehash: a42ef66afe09e0e528f05419799dce48c43b1bbf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157297"
---
# <a name="understanding-window-traits"></a>창 특성 이해

창 특성 클래스는 ATL 창 개체를 만드는 데 사용 되는 스타일을 표준화 하기 위한 간단한 방법을 제공 합니다. 창 특성은 클래스 수준에서 기본 창 스타일을 제공 하는 방법으로 [CWindowImpl](../atl/reference/cwindowimpl-class.md) 및 기타 ATL 창 클래스에서 템플릿 매개 변수로 허용 됩니다.

창 인스턴스의 작성자가 [Create](../atl/reference/cwindowimpl-class.md#create)호출에서 스타일을 명시적으로 제공 하지 않는 경우 특성 클래스를 사용 하 여 창이 올바른 스타일로 생성 되었는지 확인할 수 있습니다. 인스턴스 단위로 다른 스타일을 설정 하도록 허용 하는 동시에 해당 창 클래스의 모든 인스턴스에 대해 특정 스타일이 설정 되었는지 확인할 수 있습니다.

## <a name="atl-window-traits-templates"></a>ATL 창 특성 템플릿

ATL은 템플릿 매개 변수를 사용 하 여 컴파일 타임에 기본 스타일을 설정 하는 데 사용할 수 있는 두 가지 창 특성 템플릿을 제공 합니다.

|클래스|설명|
|-----------|-----------------|
|[CWinTraits](../atl/reference/cwintraits-class.md)|호출에 다른 스타일이 지정 되지 않은 경우에만 사용 되는 기본 창 스타일을 제공 하려는 경우이 템플릿을 사용 `Create` 합니다. 런타임에 제공 되는 스타일은 컴파일 타임에 설정 된 스타일 보다 우선적으로 적용 됩니다.|
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|항상 창 클래스에 대해 설정 해야 하는 스타일을 지정 하려면이 클래스를 사용 합니다. 런타임에 제공 되는 스타일은 비트 OR 연산자를 사용 하 여 컴파일 타임에 설정 된 스타일과 결합 됩니다.|

이러한 템플릿 외에도 ATL은 `CWinTraits` 일반적으로 사용 되는 창 스타일 조합에 대해 미리 정의 된 여러 가지 특수화 된 특수화를 제공 합니다. 자세한 내용은 [CWinTraits](../atl/reference/cwintraits-class.md) 참조 설명서를 참조 하세요.

## <a name="custom-window-traits"></a>사용자 지정 창 특성

ATL에서 제공 하는 템플릿 중 하나를 특수화 하는 것 만으로는 충분 하지 않으며 고유한 특성 클래스를 만들어야 하는 경우에는 및의 두 정적 함수를 구현 하는 클래스를 만들어야 합니다. `GetWndStyle` `GetWndStyleEx`

[!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]

이러한 각 함수에는 런타임에 새 스타일 값을 생성 하는 데 사용할 수 있는 일부 스타일 값이 전달 됩니다. 창 특성 클래스가 ATL 창 클래스에 대 한 템플릿 인수로 사용 되는 경우 이러한 정적 함수에 전달 된 스타일 값은 [만들](../atl/reference/cwindowimpl-class.md#create)스타일 인수로 전달 된 것입니다.

## <a name="see-also"></a>참고 항목

[창 클래스](../atl/atl-window-classes.md)
