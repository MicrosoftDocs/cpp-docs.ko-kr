---
description: 'TN024: MFC-Defined 메시지 및 리소스에 대해 자세히 알아보세요.'
title: 'TN024: MFC에서 정의한 메시지 및 리소스'
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC]
- Windows messages [MFC], MFC-defined
- messages [MFC], MFC
- TN024
ms.assetid: c65353ce-8096-454b-ad22-1a7a1dd9a788
ms.openlocfilehash: 7ead4d72588b9acae125cbe90be67d1e03230de8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97215757"
---
# <a name="tn024-mfc-defined-messages-and-resources"></a>TN024: MFC에서 정의한 메시지 및 리소스

> [!NOTE]
> 다음 기술 노트는 온라인 설명서에 먼저 포함되어 있었으므로 업데이트되지 않았습니다. 따라서 일부 절차 및 항목은 만료되거나 올바르지 않을 수 있습니다. 최신 정보를 보려면 온라인 설명서 색인에서 관심 있는 항목을 검색하는 것이 좋습니다.

이 참고에서는 MFC에서 사용 하는 내부 Windows 메시지 및 리소스 형식을 설명 합니다. 이 정보는 프레임 워크의 구현에 대해 설명 하 고 응용 프로그램을 디버깅 하는 데 도움이 됩니다. 모험의 경우이 정보는 공식적으로 지원 되지 않지만 고급 구현에는이 정보 중 일부를 사용할 수 있습니다.

이 메모는 MFC 개인 구현 세부 정보를 포함 합니다. 모든 콘텐츠는 나중에 변경 될 수 있습니다. MFC 개인 Windows 메시지는 한 응용 프로그램의 범위 내에서 의미가 있지만 나중에 시스템 차원의 메시지를 포함 하도록 변경 됩니다.

MFC 개인 Windows 메시지 및 리소스 종류의 범위는 Microsoft Windows에서 별도로 설정 된 예약 된 "시스템" 범위에 있습니다. 현재 범위의 모든 숫자가 사용 되는 것은 아닙니다. 앞으로는 범위의 새 숫자가 사용 될 수 있습니다. 현재 사용 되는 숫자가 변경 될 수 있습니다.

MFC 개인 Windows 메시지는 0x360->0x37F의 범위에 있습니다.

MFC 개인 리소스 형식은 0->0xFF 범위에 있습니다.

**MFC 전용 Windows 메시지**

이러한 Windows 메시지는 window 개체와 c + + 가상 함수가 적절 하지 않은 경우 비교적 느슨한 결합이 필요한 c + + 가상 함수 대신 사용 됩니다.

이러한 개인 Windows 메시지 및 연결 된 매개 변수 구조는 MFC 전용 헤더 ' AFXPRIV.H에 선언 됩니다. H '. 이 헤더를 포함 하는 코드는 문서화 되지 않은 동작에 의존 하 고 이후 버전의 MFC에서 중단 될 수 있다는 경고를 표시 합니다.

드문 경우 지만 이러한 메시지 중 하나를 처리 해야 하는 경우 ON_MESSAGE 메시지 맵 매크로를 사용 하 고 일반 LRESULT/WPARAM/LPARAM 형식의 메시지를 처리 해야 합니다.

**WM_QUERYAFXWNDPROC**

이 메시지는 생성 중인 창으로 전송 됩니다. 이는 WndProc가 AfxWndProc 여부를 확인 하는 방법으로 만들기 프로세스의 초기에 전송 됩니다 **. AfxWndProc** 는 1을 반환 합니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용되지 않음|
|lParam|사용되지 않음|
|다음을 반환합니다.|**AfxWndProc** 에서 처리 되는 경우 1|

**WM_SIZEPARENT**

이 메시지는 크기를 조정 하는 동안 프레임 창에서 직계 자식으로 전송 되어 `CFrameWnd::OnSize` `CFrameWnd::RecalcLayout` `CWnd::RepositionBars` 프레임의 측면을 기준으로 컨트롤 막대의 위치를 변경 합니다. AFX_SIZEPARENTPARAMS 구조체에는 다시 `DeferWindowPos` 그리기를 최소화 하기 위해 호출 하는 HDWP (NULL 일 수 있음)의 현재 사용 가능한 클라이언트 사각형이 포함 되어 있습니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용되지 않음|
|lParam|AFX_SIZEPARENTPARAMS 구조체의 주소|
|다음을 반환합니다.|사용 안 함 (0)|

메시지를 무시 하면 창이 레이아웃에 포함 되지 않는다는 것을 나타냅니다.

**WM_SETMESSAGESTRING**

이 메시지는 상태 표시줄에서 메시지 줄을 업데이트 하 라는 메시지를 표시 하기 위해 프레임 창으로 전송 됩니다. 문자열 ID 또는 LPCSTR 중 하나만 지정할 수 있습니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|문자열 ID (또는 0)|
|lParam|문자열의 LPCSTR (또는 NULL)|
|다음을 반환합니다.|사용 안 함 (0)|

**WM_IDLEUPDATECMDUI**

이 메시지는 업데이트 명령 UI 처리기의 유휴 시간 업데이트를 구현 하기 위해 유휴 시간에 전송 됩니다. 창 (일반적으로 컨트롤 막대)이 메시지를 처리 하는 경우 `CCmdUI` 개체 (또는 파생 클래스의 개체)를 만들고 `CCmdUI::DoUpdate` 창에서 각 "항목"에 대해를 호출 합니다. 그러면 명령 처리기 체인의 개체에 대 한 ON_UPDATE_COMMAND_UI 처리기가 검사 됩니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|BOOL bDisableIfNoHandler|
|lParam|사용 안 함 (0)|
|다음을 반환합니다.|사용 안 함 (0)|

ON_UPDATE_COMMAND_UI 또는 ON_COMMAND 처리기가 모두 없는 경우 *Bdisableifnohandler* 는 0이 아닌 값으로 설정 됩니다.

**WM_EXITHELPMODE**

이 메시지는 상황에 맞는 `CFrameWnd` 도움말 모드를 종료 하기 위해에 게시 됩니다. 이 메시지가 수신 되 면에서 시작한 모달 루프가 종료 `CFrameWnd::OnContextHelp` 됩니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용 안 함 (0)|
|lParam|사용 안 함 (0)|
|다음을 반환합니다.|사용되지 않음|

**WM_INITIALUPDATE**

이 메시지는 문서 템플릿에서 초기 업데이트를 수행 하는 데 안전 하면 프레임 창의 모든 하위 항목에 전송 됩니다. 에 대 한 호출에 매핑되고 `CView::OnInitialUpdate` `CWnd` 다른 단일 샷 업데이트의 경우 다른 파생 클래스에서 사용할 수 있습니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용 안 함 (0)|
|lParam|사용 안 함 (0)|
|다음을 반환합니다.|사용 안 함 (0)|

**WM_RECALCPARENT**

이 메시지는 레이아웃 다시 계산을 강제로 수행 하기 위해 뷰에서 부모 창에 전송 됩니다 ( `GetParent` 일반적으로 부모가 호출 됨) `RecalcLayout` . 이는 보기의 총 크기가 증가 함에 따라 프레임 크기가 증가 해야 하는 OLE 서버 응용 프로그램에서 사용 됩니다.

부모 창에서이 메시지를 처리 하는 경우 TRUE를 반환 하 고 lParam에 전달 된 RECT를 클라이언트 영역의 새 크기로 채웁니다. `CScrollView`서버 개체가 활성화 되어 있을 때 스크롤 막대를 적절 하 게 처리 (추가 될 때 창 외부에 삽입) 하는 데 사용 됩니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용 안 함 (0)|
|lParam|LPRECT rectClient, NULL 일 수 있습니다.|
|다음을 반환합니다.|새 클라이언트 사각형이 반환 되 면 TRUE이 고, 그렇지 않으면 FALSE입니다.|

**WM_SIZECHILD**

이 메시지는 `COleResizeBar` `GetOwner` 사용자가 크기 조정 핸들을 사용 하 여 크기 조정 막대의 크기를 조정할 때에서를 통해 소유자 창으로 전송 됩니다. `COleIPFrameWnd` 사용자가 요청한 대로 프레임 창의 위치를 변경 하 여이 메시지에 응답 합니다.

크기 조정 막대를 포함 하는 프레임 창에 상대적인 클라이언트 좌표에 지정 된 새 사각형은 lParam에서 가리킵니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용 안 함 (0)|
|lParam|LPRECT rectNew|
|다음을 반환합니다.|사용 안 함 (0)|

**WM_DISABLEMODAL**

이 메시지는 비활성화 되는 프레임 창이 소유 하는 모든 팝업 창으로 전송 됩니다. 프레임 창에서는 결과를 사용 하 여 팝업 창을 사용 하지 않도록 설정할지 여부를 결정 합니다.

프레임이 모달 상태로 들어가거나 특정 팝업 창을 사용 하지 않도록 설정할 때 팝업 창에서 특수 처리를 수행 하는 데 사용할 수 있습니다. 도구 설명 예를 들어 프레임 창이 모달 상태로 전환 될 때이 메시지를 사용 하 여 자신을 제거 합니다.

| 매개 변수 및 반환 값 | 설명 |
|-|-|
|wParam|사용 안 함 (0)|
|lParam|사용 안 함 (0)|
|다음을 반환합니다.|창을 사용 **하지 않도록 설정 하려면 0** 이 아닌 값을 지정 합니다. 0은 창을 사용 하지 않도록 설정 합니다.|

**WM_FLOATSTATUS**

이 메시지는 다른 최상위 프레임 창에서 프레임을 활성화 하거나 비활성화 한 경우 프레임 창이 소유 하는 모든 팝업 창에 전송 됩니다. 이는 `CMiniFrameWnd` 최상위 프레임 창의 활성화와 동기화 된 이러한 팝업 창의 활성화를 유지 하기 위해에서 MFS_SYNCACTIVE를 구현 하는 데 사용 됩니다.

| 매개 변수 | 설명 |
|-|-|
|wParam|"Admin"<br /><br /> FS_SHOW<br /><br /> FS_HIDE<br /><br /> FS_ACTIVATE<br /><br /> FS_DEACTIVATE<br /><br /> FS_ENABLEFS_DISABLE<br /><br /> FS_SYNCACTIVE|
|lParam|사용 안 함 (0)|

FS_SYNCACTIVE 설정 되 고 창이 부모 프레임을 사용 하 여 활성화를 syncronizes 경우 반환 값은 0이 아니어야 합니다. `CMiniFrameWnd` 스타일이 MFS_SYNCACTIVE로 설정 된 경우 0이 아닌 값을 반환 합니다.

자세한 내용은의 구현을 참조 하십시오 `CMiniFrameWnd` .

## <a name="wm_activatetoplevel"></a>WM_ACTIVATETOPLEVEL

이 메시지는 "최상위 그룹"의 창이 활성화 또는 비활성화 된 경우 최상위 창으로 전송 됩니다. 최상위 창 (부모 또는 소유자가 아님) 이거나 이러한 창이 소유 하 고 있는 경우 창이 최상위 그룹의 일부입니다. 이 메시지는 WM_ACTIVATEAPP 하는 데 사용 하는 것과 유사 하지만 서로 다른 프로세스에 속하는 창이 단일 창 계층 구조 (OLE 응용 프로그램에서는 일반)에서 혼합 되어 있는 경우에 작동 합니다.

## <a name="wm_commandhelp-wm_helphittest-wm_exithelpmode"></a>WM_COMMANDHELP, WM_HELPHITTEST, WM_EXITHELPMODE

이러한 메시지는 상황에 맞는 도움말을 구현 하는 데 사용 됩니다. 자세한 내용은 [Technical Note 28](../mfc/tn028-context-sensitive-help-support.md) 을 참조 하십시오.

## <a name="mfc-private-resource-formats"></a>MFC 전용 리소스 형식

현재 MFC에서는 두 개의 개인 리소스 형식 RT_TOOLBAR 및 RT_DLGINIT을 정의 합니다.

## <a name="rt_toolbar-resource-format"></a>RT_TOOLBAR 리소스 형식

응용 프로그램 마법사에서 제공 하는 기본 도구 모음은 MFC 4.0에 도입 된 RT_TOOLBAR 사용자 지정 리소스를 기반으로 합니다. 도구 모음 편집기를 사용 하 여이 리소스를 편집할 수 있습니다.

## <a name="rt_dlginit-resource-format"></a>RT_DLGINIT 리소스 형식

하나의 MFC 개인 리소스 형식을 사용 하 여 추가 대화 상자 초기화 정보를 저장 합니다. 여기에는 콤보 상자에 저장 된 초기 문자열이 포함 됩니다. 이 리소스의 형식은 수동으로 편집할 수 없지만 Visual C++에 의해 처리 됩니다.

리소스의 정보를 사용 하는 대신 API를 사용할 수 있기 때문에 Visual C++이 RT_DLGINIT 리소스는 MFC의 관련 기능을 사용 하는 데 필요 하지 않습니다. Visual C++를 사용 하면 장기 실행에서 응용 프로그램을 더 쉽게 작성 하 고 유지 관리 하 고 변환할 수 있습니다.

RT_DLGINIT 리소스의 기본 구조는 다음과 같습니다.

```
+---------------+    \
| Control ID    |   UINT             |
+---------------+    |
| Message #     |   UINT             |
+---------------+    |
|length of data |   DWORD            |
+---------------+    |   Repeated
|   Data        |   Variable Length  |   for each control
|   ...         |   and Format       |   and message
+---------------+    /
|     0         |   BYTE
+---------------+
```

반복 되는 섹션에는 메시지를 보낼 컨트롤 ID, 보낼 메시지 (일반적인 Windows 메시지) 및 가변 길이 데이터가 포함 되어 있습니다. Windows 메시지는 다음과 같은 형식으로 전송 됩니다.

```
SendDlgItemMessage(<Control ID>, <Message #>, 0, &<Data>);
```

이것은 Windows 메시지 및 데이터 콘텐츠를 허용 하는 매우 일반적인 형식입니다. Visual C++ 리소스 편집기와 MFC는 Windows 메시지의 제한 된 하위 집합만 지원 합니다. 콤보 상자에 대 한 초기 목록 선택 (데이터는 텍스트 문자열)의 경우 CB_ADDSTRING 합니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
