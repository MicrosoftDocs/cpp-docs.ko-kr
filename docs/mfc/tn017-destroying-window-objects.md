---
description: '자세히 알아보기: TN017: 창 개체 소멸'
title: 'TN017: 창 개체 제거'
ms.date: 11/04/2016
f1_keywords:
- vc.objects
helpviewer_keywords:
- destroying windows
- TN017
- PostNcDestroy method [MFC]
ms.assetid: 5bf208a5-5683-439b-92a1-547c5ded26cd
ms.openlocfilehash: 86ce1255055db98a247ac8997aa7d146eb135583
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215913"
---
# <a name="tn017-destroying-window-objects"></a>TN017: 창 개체 제거

이 참고에서는 [CWnd::P ostncdestroy](../mfc/reference/cwnd-class.md#postncdestroy) 메서드를 사용 하는 방법을 설명 합니다. 파생 개체의 사용자 지정 할당을 수행 하려는 경우이 메서드를 사용 `CWnd` 합니다. 이 참고는 또한 [CWnd::D estroyWindow](../mfc/reference/cwnd-class.md#destroywindow) 를 사용 하 여 연산자 대신 c + + Windows 개체를 삭제 해야 하는 이유를 설명 합니다 **`delete`** .

이 항목의 지침을 따르면 정리 문제가 거의 발생 하지 않습니다. 이러한 문제는 c + + 메모리를 삭제 하거나 해제 하는 것과 같은 문제가 발생할 수 있습니다. s와 같은 시스템 리소스를 확보 `HWND` 하거나 개체를 너무 많이 해제 하는 등의 문제가 발생할 수 있습니다.

## <a name="the-problem"></a>문제

각 windows 개체 (에서 파생 된 클래스의 개체 `CWnd` )는 c + + 개체와를 모두 나타냅니다 `HWND` . C + + 개체는 응용 프로그램의 힙에 할당 되 고는 `HWND` 창 관리자에 의해 시스템 리소스에 할당 됩니다. 여러 가지 방법으로 창 개체를 삭제할 수 있으므로 시스템 리소스 또는 메모리 누수를 방지 하는 규칙 집합을 제공 해야 합니다. 이러한 규칙은 개체와 Windows 핸들이 두 번 이상 제거 되는 것을 방지 해야 합니다.

## <a name="destroying-windows"></a>Windows 소멸

다음은 Windows 개체를 제거 하는 데 허용 되는 두 가지 방법입니다.

- `CWnd::DestroyWindow`또는 WINDOWS API를 호출 `DestroyWindow` 합니다.

- 연산자를 사용 하 여 명시적으로 삭제 **`delete`** 합니다.

첫 번째 경우는 가장 일반적인 경우입니다. 이 경우 코드에서 직접 호출 하지 않는 경우에도 적용 됩니다 `DestroyWindow` . 사용자가 프레임 창을 직접 닫으면이 작업은 WM_CLOSE 메시지를 생성 하 고,이 메시지에 대 한 기본 응답은 부모 창이 소멸 될 때를 호출 하는 것입니다 .이 메시지에 대 한 기본 응답은 `DestroyWindow.` `DestroyWindow` 모든 자식에 대 한 Windows 호출

두 번째 경우는 **`delete`** Windows 개체에 대해 연산자를 사용 하는 것이 드물게 발생 합니다. 다음은를 사용 하는 **`delete`** 것이 올바른 선택 인 경우입니다.

## <a name="auto-cleanup-with-cwndpostncdestroy"></a>CWnd::P ostNcDestroy를 사용 하 여 자동 정리

시스템이 Windows 창을 소멸 시킬 때 창으로 전송 된 마지막 Windows 메시지는 WM_NCDESTROY 됩니다. `CWnd`해당 메시지의 기본 처리기는 [CWnd:: OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)입니다. `OnNcDestroy` 는 `HWND` c + + 개체에서를 분리 하 고 가상 함수를 호출 `PostNcDestroy` 합니다. 일부 클래스는이 함수를 재정의 하 여 c + + 개체를 삭제 합니다.

의 기본 구현은 `CWnd::PostNcDestroy` 아무 작업도 수행 하지 않습니다 .이는 스택 프레임에 할당 되거나 다른 개체에 포함 된 창 개체에 적합 합니다. 이는 다른 개체 없이 힙에 할당 되도록 설계 된 창 개체에는 적합 하지 않습니다. 즉, 다른 c + + 개체에 포함 되지 않은 창 개체에는 적합 하지 않습니다.

힙에서 단독으로 할당 되도록 디자인 된 클래스는 `PostNcDestroy` **삭제** 를 수행 하는 메서드를 재정의 합니다. 이 문은 c + + 개체와 연결 된 모든 메모리를 해제 합니다. `CWnd` `DestroyWindow` *M_hWnd* 가 null이 아닌 경우 기본 소멸자가를 호출 하더라도 정리 단계 중에 핸들이 분리 되 고 null 인 경우에는 무한 재귀가 발생 하지 않습니다.

> [!NOTE]
> 일반적으로 시스템은 `CWnd::PostNcDestroy` Windows WM_NCDESTROY 메시지를 처리 한 후를 호출 하 고 `HWND` , 및 c + + 창 개체는 더 이상 연결 되지 않습니다. 또한 시스템은 `CWnd::PostNcDestroy` 오류가 발생 하는 경우 [CWnd:: Create](../mfc/reference/cwnd-class.md#create) 호출의 구현에서를 호출 합니다. 자동 정리 규칙은이 항목의 뒷부분에 설명 되어 있습니다.

## <a name="auto-cleanup-classes"></a>자동 정리 클래스

다음 클래스는 자동 정리를 위해 설계 되지 않았습니다. 일반적으로 다른 c + + 개체에 포함 되거나 스택에 포함 됩니다.

- 모든 표준 Windows 컨트롤 ( `CStatic` , `CEdit` , `CListBox` 등).

- 에서 직접 파생 된 모든 자식 창 `CWnd` (예: 사용자 지정 컨트롤)

- 분할자 창 ( `CSplitterWnd` ).

- 기본 컨트롤 막대 (에서 파생 된 클래스 `CControlBar` 는 컨트롤 막대 개체에 자동 삭제를 사용 하도록 설정 하는 [기술 참고 31](../mfc/tn031-control-bars.md) 참조)

- `CDialog`스택 프레임의 모달 대화 상자에 대해 디자인 된 대화 상자 ()입니다.

- 을 제외한 모든 표준 대화 상자 `CFindReplaceDialog` 입니다.

- 클래스 마법사에서 만든 기본 대화 상자입니다.

다음 클래스는 자동 정리를 위해 설계 되었습니다. 일반적으로 힙에 의해 자체적으로 할당 됩니다.

- 주 프레임 창 (에서 직접 또는 간접적으로 파생 `CFrameWnd` ).

- 보기 창 (에서 직접 또는 간접적으로 파생 `CView` )

이러한 규칙을 중단 하려면 `PostNcDestroy` 파생 클래스에서 메서드를 재정의 해야 합니다. 자동 정리를 클래스에 추가 하려면 기본 클래스를 호출한 다음 **삭제** 를 수행 합니다. 클래스에서 자동 정리를 제거 하려면 `CWnd::PostNcDestroy` `PostNcDestroy` 직접 기본 클래스의 메서드 대신을 직접 호출 합니다.

자동 정리 동작을 변경 하는 가장 일반적인 용도는 힙에 할당 될 수 있는 모덜리스 대화 상자를 만드는 것입니다.

## <a name="when-to-call-delete"></a>삭제를 호출 하는 경우

`DestroyWindow`Windows 개체 (c + + 메서드 또는 전역 API)를 삭제 하려면를 호출 하는 것이 좋습니다 `DestroyWindow` .

`DestroyWindow`MDI 자식 창을 제거 하려면 전역 API를 호출 하지 마세요. 가상 메서드를 대신 사용 해야 합니다 `CWnd::DestroyWindow` .

자동 정리를 수행 하지 않는 c + + 창 개체의 경우,이 연산자를 사용 하면 **`delete`** `DestroyWindow` `CWnd::~CWnd` VTBL이 올바르게 파생 된 클래스를 가리키지 않는 경우 소멸자에서를 호출 하려고 하면 메모리 누수가 발생할 수 있습니다. 이는 시스템에서 호출할 적절 한 소멸 메서드를 찾을 수 없기 때문에 발생 합니다. `DestroyWindow`대신를 사용 하면 **`delete`** 이러한 문제가 방지 됩니다. 이는 미묘한 오류가 될 수 있으므로 디버그 모드에서 컴파일하면 위험에 노출 되는 경우 다음과 같은 경고가 생성 됩니다.

```
Warning: calling DestroyWindow in CWnd::~CWnd
    OnDestroy or PostNcDestroy in derived class will not be called
```

자동 정리를 수행 하는 c + + Windows 개체의 경우를 호출 해야 합니다 `DestroyWindow` . 연산자를 직접 사용 하는 경우 **`delete`** MFC 진단 메모리 할당자는 메모리를 두 번 해제 했음을 알립니다. 두 항목은의 자동 정리 구현에서 **이를 삭제** 하기 위한 첫 번째 명시적 호출 및 간접 호출입니다 `PostNcDestroy` .

`DestroyWindow`자동 정리 개체가 아닌 개체에 대해를 호출한 후에는 c + + 개체는 계속 해 서 발생 하지만 *m_hWnd* NULL이 됩니다. `DestroyWindow`자동 정리 개체에서를 호출한 후 c + + 개체는의 자동 정리 구현에서 c + + delete 연산자에 의해 해제 됩니다 `PostNcDestroy` .

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
