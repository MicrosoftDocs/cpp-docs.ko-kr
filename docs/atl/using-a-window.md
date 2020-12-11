---
description: '자세히 알아보기: 창 사용'
title: 창 사용 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- CWindow class, about CWindow class
- windows [C++], ATL
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
ms.openlocfilehash: fb9f1e03a27ad8b637da30eacbd100daf920cdb4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157282"
---
# <a name="using-a-window"></a>창 사용

클래스 [CWindow](../atl/reference/cwindow-class.md) 를 사용 하면 창을 사용할 수 있습니다. 창을 개체에 연결한 후에 `CWindow` `CWindow` 는 메서드를 호출 하 여 창을 조작할 수 있습니다. `CWindow` 개체를 HWND로 변환 하는 HWND 연산자도 포함 됩니다 `CWindow` . 따라서 `CWindow` 창에 대 한 핸들이 필요한 함수에 개체를 전달할 수 있습니다. `CWindow`임시 개체를 만들지 않고도 메서드 호출 및 Win32 함수 호출을 쉽게 혼합할 수 있습니다.

에는 `CWindow` 두 개의 데이터 멤버 (창 핸들과 기본 차원)만 있으므로 코드에서 오버 헤드를 적용 하지 않습니다. 또한 대부분의 `CWindow` 메서드는 해당 Win32 API 함수를 간단 하 게 래핑합니다. 를 사용 하면 `CWindow` HWND 멤버가 자동으로 Win32 함수에 전달 됩니다.

를 직접 사용 하는 것 외에 `CWindow` 도이 클래스에서 파생 하 여 클래스에 데이터 또는 코드를 추가할 수 있습니다. ATL 자체 `CWindow` 는 [CWindowImpl](../atl/implementing-a-window.md), [Cdialogimpl](../atl/implementing-a-dialog-box.md), [CContainedWindowT](../atl/using-contained-windows.md)의 세 가지 클래스를 파생 합니다.

## <a name="see-also"></a>참고 항목

[창 클래스](../atl/atl-window-classes.md)
