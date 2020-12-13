---
description: '자세히 알아보기: 시각화 관리자'
title: 시각화 관리자
ms.date: 11/19/2018
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
ms.openlocfilehash: b99331503e4e7e69cc5d8a19fde7641c1b1daeeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143210"
---
# <a name="visualization-manager"></a>시각화 관리자

비주얼 관리자는 전체 응용 프로그램의 모양을 제어 하는 개체입니다. 응용 프로그램에 대 한 모든 그리기 코드를 입력할 수 있는 단일 클래스 역할을 합니다. MFC 라이브러리에는 몇 가지 시각적 관리자가 포함 되어 있습니다. 응용 프로그램에 대 한 사용자 지정 보기를 만들려는 경우 고유한 시각적 관리자를 만들 수도 있습니다. 다음 이미지는 여러 시각적 관리자를 사용 하도록 설정한 경우 동일한 응용 프로그램을 보여 줍니다.

![CMFCVisualManagerWindows에서 렌더링된 MyApp](../mfc/media/vmwindows.png "CMFCVisualManagerWindows에서 렌더링된 MyApp") <br/>
CMFCVisualManagerWindows visual manager를 사용 하는 MyApp

![CMFCVisualManagerVS2005에서 렌더링된 MyApp](../mfc/media/vmvs2005.png "CMFCVisualManagerVS2005에서 렌더링된 MyApp") <br/>
CMFCVisualManagerVS2005 visual manager를 사용 하는 MyApp

![CMFCVisualManagerOfficeXP에서 렌더링된 MyApp](../mfc/media/vmofficexp.png "CMFCVisualManagerOfficeXP에서 렌더링된 MyApp") <br/>
CMFCVisualManagerOfficeXP visual manager를 사용 하는 MyApp

![CMFCVisualManagerOffice2003에서 렌더링된 MyApp](../mfc/media/vmoffice2003.png "CMFCVisualManagerOffice2003에서 렌더링된 MyApp") <br/>
CMFCVisualManagerOffice2003 visual manager를 사용 하는 MyApp

![CMFCVisualManagerOffice2007에서 렌더링된 MyApp](../mfc/media/msoffice2007.png "CMFCVisualManagerOffice2007에서 렌더링된 MyApp") <br/>
CMFCVisualManagerOffice2007 visual manager를 사용 하는 MyApp

기본적으로 visual manager는 몇 가지 GUI 요소에 대 한 그리기 코드를 유지 관리 합니다. 사용자 지정 UI 요소를 제공 하려면 시각적 관리자의 관련 그리기 메서드를 재정의 해야 합니다. 이러한 방법의 목록은 [Cmfcvisualmanager 클래스](../mfc/reference/cmfcvisualmanager-class.md)를 참조 하세요. 사용자 지정 모양을 제공 하기 위해 재정의할 수 있는 메서드는 모두로 시작 하는 메서드입니다 `OnDraw` .

응용 프로그램에는 하나의 개체만 있을 수 있습니다 `CMFCVisualManager` . 응용 프로그램의 시각적 관리자에 대 한 포인터를 가져오려면 정적 함수 [Cmfcvisualmanager:: GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance)를 호출 합니다. 모든 시각적 관리자는에서 상속 하므로 `CMFCVisualManager` `CMFCVisualManager::GetInstance` 사용자 지정 시각적 개체 관리자를 만드는 경우에도 메서드는 적절 한 시각적 관리자에 대 한 포인터를 가져옵니다.

사용자 지정 시각적 개체 관리자를 만들려는 경우 이미 존재 하는 비주얼 관리자에서 파생 해야 합니다. 에서 파생 되는 기본 클래스는 `CMFCVisualManager` 입니다. 그러나 응용 프로그램에 사용할 수 있는 것과 비슷한 경우 다른 시각적 관리자를 사용할 수 있습니다. 예를 들어, visual manager를 사용 하려고 `CMFCVisualManagerOffice2007` 하지만 구분 기호 모양을 변경 하려는 경우에서 사용자 지정 클래스를 파생할 수 있습니다 `CMFCVisualManagerOffice2007` . 이 시나리오에서는 그리기 구분 기호에 대 한 메서드만 덮어써야 합니다.

응용 프로그램에 특정 비주얼 관리자를 사용 하는 방법에는 두 가지가 있습니다. 한 가지 방법은 [Cmfcvisualmanager:: SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) 메서드를 호출 하 고 적절 한 visual manager를 매개 변수로 전달 하는 것입니다. 다음 코드 예제에서는이 메서드를 사용 하 여 visual manager를 사용 하는 방법을 보여 줍니다 `CMFCVisualManagerVS2005` .

```cpp
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```

응용 프로그램에서 visual manager를 사용 하는 다른 방법은 수동으로 만드는 것입니다. 그러면 응용 프로그램에서 모든 렌더링에 대해이 새 시각적 관리자를 사용 합니다. 그러나 응용 프로그램 마다 개체가 하나만 있을 수 있기 때문에 `CMFCVisualManager` 새 개체를 만들기 전에 현재 visual manager를 삭제 해야 합니다. 다음 예제에서 `CMyVisualManager` 는에서 파생 된 사용자 지정 시각적 관리자입니다 `CMFCVisualManager` . 다음 메서드는 인덱스에 따라 응용 프로그램을 표시 하는 데 사용 되는 시각적 관리자를 변경 합니다.

```cpp
void CMyApp::SetSkin (int index)
{
    if (CMFCVisualManager::GetInstance() != NULL)
    {
        delete CMFCVisualManager::GetInstance();
    }

    switch (index)
    {
    case DEFAULT_STYLE:
        // The following statement creates a new CMFCVisualManager
        CMFCVisualManager::GetInstance();
        break;

    case CUSTOM_STYLE:
        new CMyVisualManager;
        break;

    default:
        CMFCVisualManager::GetInstance();
        break;
    }

    CMFCVisualManager::GetInstance()->RedrawAll();
}
```

## <a name="see-also"></a>참고 항목

[사용자 인터페이스 요소](../mfc/user-interface-elements-mfc.md)<br/>
[CMFCVisualManager 클래스](../mfc/reference/cmfcvisualmanager-class.md)
