---
description: '자세히 알아보기: 포함 된 창 사용'
title: 포함 된 창 사용
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 11beb998365a10a8126e37ecbf7388ec6177e659
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97138218"
---
# <a name="using-contained-windows"></a>포함 된 창 사용

ATL은 [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)를 사용 하 여 포함 된 창을 구현 합니다. 포함 된 창은 해당 메시지를 자체 클래스에서 처리 하는 대신 컨테이너 개체에 위임 하는 창을 나타냅니다.

> [!NOTE]
> 포함 된 창을 사용 하기 위해에서 클래스를 파생 하지 않아도 `CContainedWindowT` 됩니다.

포함 된 창이 있는 경우 기존 Windows 클래스의 슈퍼 클래스를 사용 하거나 기존 창의 서브 클래스를 만들 수 있습니다. 기존 Windows 클래스의 슈퍼 클래스를 만들려면 먼저 개체에 대 한 생성자에서 기존 클래스 이름을 지정 `CContainedWindowT` 합니다. 그런 다음 `CContainedWindowT::Create` 를 호출 합니다. 기존 창을 서브 클래스 하려면 Windows 클래스 이름을 지정 하지 않아도 됩니다 (생성자에 NULL 전달). `CContainedWindowT::SubclassWindow`서브클래싱된 창의 핸들을 사용 하 여 메서드를 호출 하기만 하면 됩니다.

일반적으로 포함 된 창을 컨테이너 클래스의 데이터 멤버로 사용 합니다. 컨테이너가 창이 될 필요는 없습니다. 그러나 [Cmessagemap](../atl/reference/cmessagemap-class.md)파생 되어야 합니다.

포함 된 창은 대체 메시지 맵을 사용 하 여 해당 메시지를 처리할 수 있습니다. 둘 이상의 포함 된 창이 있는 경우 각각 별도의 포함 된 창에 해당 하는 여러 대체 메시지 맵을 선언 해야 합니다.

## <a name="example"></a>예제

다음은 두 개의 포함 된 창이 있는 컨테이너 클래스의 예제입니다.

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

포함 된 창에 대 한 자세한 내용은 [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) 샘플을 참조 하세요.

## <a name="see-also"></a>참고 항목

[창 클래스](../atl/atl-window-classes.md)
