---
description: 'TN061: ON_NOTIFY 및 WM_NOTIFY 메시지에 대해 자세히 알아보세요.'
title: 'TN061: ON_NOTIFY 및 WM_NOTIFY 메시지'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: ecbbc03ad7328b163f89e5b1da095c8c179df097
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97214756"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: ON_NOTIFY 및 WM_NOTIFY 메시지

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 기술 정보는 새로운 WM_NOTIFY 메시지에 대 한 배경 정보를 제공 하 고 MFC 응용 프로그램에서 WM_NOTIFY 메시지를 처리 하는 권장 되는 가장 일반적인 방법에 대해 설명 합니다.

**Windows 3.x의 알림 메시지**

Windows 3.x에서 컨트롤은 마우스 클릭, 내용 및 선택 내용 변경, 부모에 게 메시지를 전송 하 여 배경 그리기 제어와 같은 이벤트의 부모에 게 알립니다. 간단한 알림은 알림 코드 (예: BN_CLICKED) 및 컨트롤 ID가 *wParam* 로 압축 되 고 컨트롤의 핸들이 *lParam* 에 압축 된 특수 WM_COMMAND 메시지로 전송 됩니다. *WParam* 및 *lParam* 이 가득 차서 추가 데이터를 전달할 수 있는 방법이 없습니다. 이러한 메시지는 단순한 알림만 될 수 있습니다. 예를 들어 BN_CLICKED 알림에서 단추를 클릭 했을 때 마우스 커서의 위치에 대 한 정보를 보낼 수 있는 방법이 없습니다.

Windows 3.x의 컨트롤에서 추가 데이터를 포함 하는 알림 메시지를 보내야 하는 경우 WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_CHARTOITEM, WM_VKEYTOITEM 등의 다양 한 특수 용도의 메시지를 사용 합니다. 이러한 메시지는 해당 메시지를 보낸 컨트롤에 다시 반영할 수 있습니다. 자세한 내용은 [TN062: Windows 컨트롤에 대 한 메시지 리플렉션](../mfc/tn062-message-reflection-for-windows-controls.md)을 참조 하세요.

**Win32의 알림 메시지**

Windows 3.1에 존재 하는 컨트롤의 경우 Win32 API는 Windows 3.x에서 사용 된 대부분의 알림 메시지를 사용 합니다. 그러나 Win32는 Windows 3.x에서 지원 되는 것에 많은 정교한 복합 컨트롤을 추가 하기도 합니다. 이러한 컨트롤은 알림 메시지와 함께 추가 데이터를 전송 해야 하는 경우가 많습니다.  <strong>\*</strong> 추가 데이터를 필요로 하는 각각의 새로운 알림에 대해 새 WM_ 메시지를 추가 하는 대신 Win32 API의 디자이너가 표준화 된 방법으로 모든 양의 추가 데이터를 전달할 수 있는 WM_NOTIFY 하나의 메시지만 추가 하도록 선택 했습니다.

WM_NOTIFY 메시지에는 *wParam* 로 메시지를 보내는 컨트롤의 ID와 *lParam* 의 구조체에 대 한 포인터가 포함 되어 있습니다. 이 구조체는 **NMHDR** 구조체 이거나 **NMHDR** 구조체를 첫 번째 멤버로 포함 하는 더 큰 구조체 중 하나입니다. **NMHDR** 멤버를 먼저 사용 하는 경우이 구조에 대 한 포인터를 **NMHDR** 에 대 한 포인터 또는 캐스팅 방법에 따라 더 큰 구조체에 대 한 포인터로 사용할 수 있습니다.

대부분의 경우 포인터는 더 큰 구조를 가리키고 사용할 때 캐스팅 해야 합니다. 이름이 **NM_** 로 시작 하 고 도구 설명 컨트롤의 TTN_SHOW 및 TTN_POP 알림이 있는 일반적인 알림과 같은 몇 가지 알림은 실제로 사용 되는 **NMHDR** 구조체입니다.

**NMHDR** 구조체 또는 초기 멤버에는 메시지를 보내는 컨트롤의 핸들 및 ID와 알림 코드 (예: TTN_SHOW)가 포함 됩니다. **NMHDR** 구조의 형식은 다음과 같습니다.

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

TTN_SHOW 메시지의 경우 **코드** 멤버가 TTN_SHOW로 설정 됩니다.

대부분의 알림은 첫 번째 멤버로 **NMHDR** 구조체를 포함 하는 더 큰 구조에 포인터를 전달 합니다. 예를 들어 목록 뷰 컨트롤의 키를 누를 때 전송 되는 목록 뷰 컨트롤의 LVN_KEYDOWN 알림 메시지에서 사용 하는 구조를 고려 합니다. 포인터는 아래와 같이 정의 된 **LV_KEYDOWN** 구조를 가리킵니다.

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

**NMHDR** 멤버는이 구조체의 첫 번째 구조 이므로 알림 메시지에 전달 된 포인터는 **NMHDR** 에 대 한 포인터 또는 **LV_KEYDOWN** 에 대 한 포인터로 캐스팅 될 수 있습니다.

**모든 새 Windows 컨트롤에 공통적인 알림**

일부 알림은 새로운 Windows 컨트롤에 공통적으로 있습니다. 이러한 알림은 **NMHDR** 구조체에 대 한 포인터를 전달 합니다.

|알림 코드|보낸 사람|
|-----------------------|------------------|
|NM_CLICK|사용자가 컨트롤에서 마우스 왼쪽 단추를 클릭 했습니다.|
|NM_DBLCLK|사용자가 컨트롤에서 마우스 왼쪽 단추를 두 번 클릭 했습니다.|
|NM_RCLICK|사용자가 컨트롤에서 마우스 오른쪽 단추를 클릭 했습니다.|
|NM_RDBLCLK|사용자가 컨트롤에서 마우스 오른쪽 단추를 두 번 클릭 했습니다.|
|NM_RETURN|컨트롤에 입력 포커스가 있는 동안 사용자가 ENTER 키를 눌렀습니다.|
|NM_SETFOCUS|컨트롤에 입력 포커스가 지정 되었습니다.|
|NM_KILLFOCUS|컨트롤의 입력 포커스가 손실 되었습니다.|
|NM_OUTOFMEMORY|사용 가능한 메모리가 부족 하 여 컨트롤에서 작업을 완료할 수 없습니다.|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY: MFC 응용 프로그램에서 WM_NOTIFY 메시지 처리

함수는 `CWnd::OnNotify` 알림 메시지를 처리 합니다. 기본 구현에서는 호출에 대 한 알림 처리기의 메시지 맵을 확인 합니다. 일반적으로는 재정의 하지 않습니다 `OnNotify` . 대신 처리기 함수를 제공 하 고 해당 처리기에 대 한 메시지 맵 항목을 소유자 창의 클래스의 메시지 맵에 추가 합니다.

클래스 마법사에서는 클래스 마법사 속성 시트를 통해 ON_NOTIFY 메시지 맵 항목을 만들고 기본 처리기 함수를 제공할 수 있습니다. 클래스 마법사를 사용 하 여이 작업을 쉽게 수행 하는 방법에 대 한 자세한 내용은 [함수에 메시지 매핑](../mfc/reference/mapping-messages-to-functions.md)을 참조 하세요.

ON_NOTIFY 메시지 매핑 매크로의 구문은 다음과 같습니다.

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

여기서 매개 변수는 다음과 같습니다.

*wNotifyCode*<br/>
LVN_KEYDOWN와 같이 처리할 알림 메시지에 대 한 코드입니다.

*id*<br/>
알림이 전송 되는 컨트롤의 자식 식별자입니다.

*memberFxn*<br/>
이 알림을 보낼 때 호출 되는 멤버 함수입니다.

다음 프로토타입을 사용 하 여 멤버 함수를 선언 해야 합니다.

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

여기서 매개 변수는 다음과 같습니다.

*pNotifyStruct*<br/>
위의 섹션에 설명 된 대로 알림 구조에 대 한 포인터입니다.

*result*<br/>
반환 하기 전에 설정 하는 결과 코드에 대 한 포인터입니다.

## <a name="example"></a>예제

멤버 함수에서 `OnKeydownList1` ID가 인의 LVN_KEYDOWN 메시지를 처리 하도록 지정 하려면 `CListCtrl` `IDC_LIST1` 클래스 마법사를 사용 하 여 다음을 메시지 맵에 추가 합니다.

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

위의 예제에서 클래스 마법사에서 제공 하는 함수는 다음과 같습니다.

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

클래스 마법사는 적절 한 형식의 포인터를 자동으로 제공 합니다. *Pnmhdr* 또는 *pLVKeyDow* 을 통해 알림 구조에 액세스할 수 있습니다.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE

컨트롤 집합에 대해 동일한 WM_NOTIFY 메시지를 처리 해야 하는 경우 ON_NOTIFY 아닌 ON_NOTIFY_RANGE를 사용할 수 있습니다. 예를 들어 특정 알림 메시지에 대해 동일한 작업을 수행 하려는 일련의 단추가 있을 수 있습니다.

ON_NOTIFY_RANGE 사용 하는 경우 범위의 시작 및 끝 자식 식별자를 지정 하 여 알림 메시지를 처리 하는 데 사용할 하위 식별자의 연속 범위를 지정 합니다.

클래스 마법사는 ON_NOTIFY_RANGE를 처리 하지 않습니다. 이를 사용 하려면 메시지 맵을 직접 편집 해야 합니다.

ON_NOTIFY_RANGE에 대 한 메시지 맵 항목과 함수 프로토타입은 다음과 같습니다.

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

여기서 매개 변수는 다음과 같습니다.

*wNotifyCode*<br/>
LVN_KEYDOWN와 같이 처리할 알림 메시지에 대 한 코드입니다.

*id*<br/>
연속 된 식별자 범위의 첫 번째 식별자입니다.

*idLast*<br/>
연속 된 식별자 범위의 마지막 식별자입니다.

*memberFxn*<br/>
이 알림을 보낼 때 호출 되는 멤버 함수입니다.

다음 프로토타입을 사용 하 여 멤버 함수를 선언 해야 합니다.

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

여기서 매개 변수는 다음과 같습니다.

*id*<br/>
알림을 보낸 컨트롤의 자식 식별자입니다.

*pNotifyStruct*<br/>
위에서 설명한 알림 구조에 대 한 포인터입니다.

*result*<br/>
반환 하기 전에 설정 하는 결과 코드에 대 한 포인터입니다.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

메시지를 처리 하기 위해 알림 라우팅에 개체가 두 개 이상 필요한 경우에는 ON_NOTIFY (또는 ON_NOTIFY_RANGE) 대신 ON_NOTIFY_EX 또는 ON_NOTIFY_EX_RANGE를 사용할 수 있습니다. **Ex** 버전과 일반 버전의 유일한 차이점은 **ex** 버전에 대해 호출 된 멤버 함수가 메시지 처리를 계속할지 여부를 나타내는 **BOOL** 을 반환 한다는 것입니다. 이 함수에서 **FALSE** 를 반환 하면 둘 이상의 개체에서 동일한 메시지를 처리할 수 있습니다.

클래스 마법사는 ON_NOTIFY_EX 또는 ON_NOTIFY_EX_RANGE를 처리 하지 않습니다. 둘 중 하나를 사용 하려는 경우 메시지 맵을 직접 편집 해야 합니다.

ON_NOTIFY_EX 및 ON_NOTIFY_EX_RANGE에 대 한 메시지 맵 항목 및 함수 프로토타입은 다음과 같습니다. 매개 변수의 의미는 비 **EX** 버전의 경우와 동일 합니다.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

위의 두 가지 모두에 대 한 프로토타입은 동일 합니다.

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

두 경우 모두 *id* 는 알림을 보낸 컨트롤의 자식 식별자를 보유 합니다.

알림 메시지가 완전히 처리 된 경우 함수는 **TRUE** 를 반환 하 고, 명령 라우팅의 다른 개체에서 메시지를 처리할 수 있는 기회가 있으면 **FALSE** 를 반환 해야 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
