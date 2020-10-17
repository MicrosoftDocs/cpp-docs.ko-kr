---
title: CWindowImpl를 사용 하 여 창 구현
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], subclassing
- windows [C++], superclassing
- windows [C++], ATL
- subclassing ATL window classes
- superclassing, ATL
ms.assetid: 3fc40550-f1d6-4702-8b7c-4cf682b6a855
ms.openlocfilehash: 7ce1a2ec08e49e047aee5248bda0094d9e392614
ms.sourcegitcommit: ced5ff1431ffbd25b20d106901955532723bd188
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2020
ms.locfileid: "92135517"
---
# <a name="implementing-a-window-with-cwindowimpl"></a>CWindowImpl를 사용 하 여 창 구현

창을 구현 하려면에서 클래스를 파생 시킵니다 `CWindowImpl` . 파생 클래스에서 메시지 맵과 메시지 처리기 함수를 선언 합니다. 이제 클래스를 세 가지 다른 방법으로 사용할 수 있습니다.

- [새 Windows 클래스를 기반으로 창 만들기](#_atl_creating_a_window_based_on_a_new_windows_class)

- [기존 Windows 클래스의 슈퍼 클래스](#_atl_superclassing_an_existing_windows_class)

- [기존 창 서브 클래스](#_atl_subclassing_an_existing_window)

## <a name="creating-a-window-based-on-a-new-windows-class"></a><a name="_atl_creating_a_window_based_on_a_new_windows_class"></a> 새 Windows 클래스를 기반으로 창 만들기

`CWindowImpl` Windows 클래스 정보를 선언 하는 [DECLARE_WND_CLASS](reference/window-class-macros.md#declare_wnd_class) 매크로를 포함 합니다. 이 매크로는 `GetWndClassInfo` [CWndClassInfo](../atl/reference/cwndclassinfo-class.md) 를 사용 하 여 새 Windows 클래스의 정보를 정의 하는 함수를 구현 합니다. `CWindowImpl::Create`가 호출 되 면이 Windows 클래스가 등록 되 고 새 창이 만들어집니다.

> [!NOTE]
> `CWindowImpl` 매크로에 NULL을 전달 합니다 `DECLARE_WND_CLASS` .이는 ATL에서 Windows 클래스 이름을 생성 하는 것을 의미 합니다. 사용자 고유의 이름을 지정 하려면 파생 클래스에서 DECLARE_WND_CLASS에 대 한 문자열을 전달 `CWindowImpl` 합니다.

## <a name="example-implement-a-window"></a>예: 창 구현

다음은 새 Windows 클래스를 기반으로 창을 구현 하는 클래스의 예입니다.

[!code-cpp[NVC_ATL_Windowing#64](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_1.h)]

창을 만들려면의 인스턴스를 만든 `CMyWindow` 다음 메서드를 호출 `Create` 합니다.

> [!NOTE]
> 기본 Windows 클래스 정보를 재정의 하려면 `GetWndClassInfo` `CWndClassInfo` 멤버를 적절 한 값으로 설정 하 여 파생 클래스에서 메서드를 구현 합니다.

## <a name="superclassing-an-existing-windows-class"></a><a name="_atl_superclassing_an_existing_windows_class"></a> 기존 Windows 클래스 Superclassing

[DECLARE_WND_SUPERCLASS](reference/window-class-macros.md#declare_wnd_superclass) 매크로를 사용 하 여 기존 Windows 클래스를 슈퍼 클래스 하는 창을 만들 수 있습니다. 파생 클래스에서이 매크로를 지정 `CWindowImpl` 합니다. 다른 ATL 창과 마찬가지로 메시지 맵에서 메시지를 처리 합니다.

DECLARE_WND_SUPERCLASS 사용 하는 경우 새 Windows 클래스가 등록 됩니다. 이 새 클래스는 지정 하는 기존 클래스와 동일 하지만 창 프로시저를로 대체 합니다 `CWindowImpl::WindowProc` (또는이 메서드를 재정의 하는 함수로 대체 됨).

## <a name="example-superclass-the-edit-class"></a>예: Edit 클래스의 슈퍼 클래스

다음은 표준 Edit 클래스의 슈퍼 클래스 예제입니다.

[!code-cpp[NVC_ATL_Windowing#65](../atl/codesnippet/cpp/implementing-a-window-with-cwindowimpl_2.h)]

Superclassed 편집 창을 만들려면의 인스턴스를 만든 `CMyEdit` 다음 메서드를 호출 `Create` 합니다.

## <a name="subclassing-an-existing-window"></a><a name="_atl_subclassing_an_existing_window"></a> 기존 창 서브클래싱

기존 창을 서브 클래스로 만들려면에서 클래스를 파생 하 `CWindowImpl` 고 두 가지 이전 경우와 같이 메시지 맵을 선언 합니다. 그러나 기존 창을 이미 서브클래싱하 므로 Windows 클래스 정보를 지정 하지 않아도 됩니다.

를 호출 하는 대신 `Create` 을 호출 `SubclassWindow` 하 고 하위 클래스를 만들려는 기존 창에 대 한 핸들을 전달 합니다. 창이 서브클래싱된 후에는 `CWindowImpl::WindowProc` (또는이 메서드를 재정의 하는 함수)를 사용 하 여 메시지를 메시지 맵으로 보냅니다. 개체에서 서브클래싱된 창을 분리 하려면를 호출 `UnsubclassWindow` 합니다. 그러면 창의 원래 창 프로시저가 복원 됩니다.

## <a name="see-also"></a>참고 항목

[창 구현](../atl/implementing-a-window.md)
