---
description: '자세히 알아보기: TN001: 창 클래스 등록'
title: 'TN001: 창 클래스 등록'
ms.date: 11/04/2016
f1_keywords:
- vc.registration
helpviewer_keywords:
- TN001
- WNDCLASS [MFC]
- AfxRegisterClass function
ms.assetid: 1abf678e-f220-4606-85e0-03df32f64c54
ms.openlocfilehash: fc54b6f783a50bb35f87f542772b9a1921f1f7b7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216108"
---
# <a name="tn001-window-class-registration"></a>TN001: 창 클래스 등록

이 참고에서는 Microsoft Windows에 필요한 특별 한 [예: wndclassa](/windows/win32/api/winuser/ns-winuser-wndclassw)es를 등록 하는 MFC 루틴에 대해 설명 합니다. `WNDCLASS`MFC 및 창에서 사용 되는 특정 특성에 대해 설명 합니다.

## <a name="the-problem"></a>문제

Windows의 핸들과 같은 [CWnd](../mfc/reference/cwnd-class.md) 개체의 특성은 `HWND` 창 개체와의 두 위치에 저장 됩니다 `WNDCLASS` . 의 이름은 `WNDCLASS` *lpszClassName* 매개 변수에서 [CWnd:: create](../mfc/reference/cwnd-class.md#create) 및 [CFrameWnd:: create](../mfc/reference/cframewnd-class.md#create) 와 같은 일반 창 생성 함수에 전달 됩니다.

`WNDCLASS`다음 네 가지 방법 중 하나를 사용 하 여 등록 해야 합니다.

- 제공 된 MFC를 사용 하 여 암시적으로 `WNDCLASS`

- Windows 컨트롤 (또는 다른 컨트롤)을 서브클래싱 하 여 암시적으로

- MFC [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) 또는 [AfxRegisterClass](../mfc/reference/application-information-and-management.md#afxregisterclass)를 호출 하 여 명시적으로

- Windows 루틴 [RegisterClass](/windows/win32/api/winuser/nf-winuser-registerclassw)를 호출 하 여 명시적으로

## <a name="wndclass-fields"></a>예: WNDCLASSA 필드

`WNDCLASS`구조체는 창 클래스를 설명 하는 다양 한 필드로 구성 됩니다. 다음 표에서는 필드를 보여 주고 MFC 응용 프로그램에서이를 사용 하는 방법을 지정 합니다.

|필드|설명|
|-----------|-----------------|
|*lpfnWndProc*|창 프로시저는 이어야 합니다. `AfxWndProc`|
|*cbClsExtra*|사용 되지 않음 (0 이어야 함)|
|*cbWndExtra*|사용 되지 않음 (0 이어야 함)|
|*hInstance*|자동으로 [AfxGetInstanceHandle](../mfc/reference/application-information-and-management.md#afxgetinstancehandle) 으로 채워짐|
|*hIcon*|프레임 창 아이콘, 아래 참조|
|*hCursor*|마우스가 창 위에 있을 때 커서를 표시 합니다. 아래를 참조 하십시오.|
|*hbrBackground*|배경색, 아래 참조|
|*lpszMenuName*|사용 되지 않음 (NULL 이어야 함)|
|*lpszClassName*|클래스 이름, 아래 참조|

## <a name="provided-wndclasses"></a>제공 된 WNDCLASSes

이전 버전의 MFC (MFC 4.0 이전 버전)에서는 몇 가지 미리 정의 된 창 클래스를 제공 했습니다. 이러한 창 클래스는 더 이상 기본적으로 제공 되지 않습니다. 응용 프로그램은 `AfxRegisterWndClass` 적절 한 매개 변수와 함께를 사용 해야 합니다.

응용 프로그램이 지정 된 리소스 ID (예: AFX_IDI_STD_FRAME)를 사용 하 여 리소스를 제공 하는 경우 MFC는 해당 리소스를 사용 합니다. 그렇지 않은 경우에는 기본 리소스를 사용 합니다. 아이콘의 경우 표준 응용 프로그램 아이콘을 사용 하 고 커서의 경우 표준 화살표 커서를 사용 합니다.

두 아이콘은 단일 문서 유형을 포함 하는 MDI 응용 프로그램을 지원 합니다. 주 응용 프로그램에 대 한 아이콘 하나는 아이콘 document/MDIChild windows에 대 한 다른 아이콘입니다. 다른 아이콘을 사용 하는 여러 문서 형식의 경우 추가 es를 등록 `WNDCLASS` 하거나 [CFrameWnd:: loadframe](../mfc/reference/cframewnd-class.md#loadframe) 함수를 사용 해야 합니다.

`CFrameWnd::LoadFrame` 는 지정 된 `WNDCLASS` 아이콘 ID를 사용 하 여를 등록 하 고 첫 번째 매개 변수로 다음 표준 특성을 사용 합니다.

- 클래스 스타일: CS_DBLCLKS &#124; CS_HREDRAW &#124; CS_VREDRAW;

- 아이콘 AFX_IDI_STD_FRAME

- 화살표 커서

- COLOR_WINDOW 배경색

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) 에 대 한 배경색 및 커서 값은의 클라이언트 영역이 `CMDIFrameWnd` **MDICLIENT** 창에 완전히 포함 되어 있기 때문에 사용 되지 않습니다. Microsoft는 **MDICLIENT** 창의 하위 클래스화를 권장 하지 않으므로 가능 하면 표준 색 및 커서 유형을 사용 합니다.

## <a name="subclassing-and-superclassing-controls"></a>컨트롤 서브클래싱 및 Superclassing

Windows 컨트롤 (예: [Cbutton](../mfc/reference/cbutton-class.md))의 하위 클래스 또는 슈퍼 클래스를 사용할 경우 클래스 `WNDCLASS` 는 해당 컨트롤의 windows 구현에서 제공 되는 특성을 자동으로 가져옵니다.

## <a name="the-afxregisterwndclass-function"></a>AfxRegisterWndClass 함수

MFC는 창 클래스를 등록 하기 위한 도우미 함수를 제공 합니다. 특성 집합 (창 클래스 스타일, 커서, 배경 브러시 및 아이콘)을 지정 하면 가상 이름이 생성 되 고 결과 창 클래스가 등록 됩니다. 예를 들면 다음과 같습니다.

```
const char* AfxRegisterWndClass(UINT nClassStyle,
    HCURSOR hCursor,
    HBRUSH hbrBackground,
    HICON hIcon);
```

이 함수는 생성 된 등록 창 클래스 이름의 임시 문자열을 반환 합니다. 이 함수에 대 한 자세한 내용은 [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass)를 참조 하세요.

반환 된 문자열은 정적 문자열 버퍼에 대 한 임시 포인터입니다. 다음에를 호출할 때까지 유효 `AfxRegisterWndClass` 합니다. 이 문자열을 유지 하려는 경우 다음 예제와 같이 [CString](../atl-mfc-shared/using-cstring.md) 변수에 저장 합니다.

```
CString strWndClass = AfxRegisterWndClass(CS_DBLCLK, ...);

...
CWnd* pWnd = new CWnd;
pWnd->Create(strWndClass, ...);

...
```

`AfxRegisterWndClass` 는 잘못 된 매개 변수 또는 Windows 메모리 부족으로 인해 창 클래스를 등록 하지 못한 경우 [Cresourceexception](../mfc/reference/cresourceexception-class.md) 을 throw 합니다.

## <a name="the-registerclass-and-afxregisterclass-functions"></a>RegisterClass 및 AfxRegisterClass 함수

에서 제공 하는 것 보다 더 복잡 한 작업을 수행 하려는 경우에는 `AfxRegisterWndClass` WINDOWS API `RegisterClass` 또는 MFC 함수를 호출 하면 `AfxRegisterClass` 됩니다. `CWnd`, [CFrameWnd](../mfc/reference/cframewnd-class.md) 및 [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) `Create` 함수는 창 클래스에 대 한 *lpszClassName* 문자열 이름을 첫 번째 매개 변수로 사용 합니다. 등록 하는 데 사용한 메서드에 관계 없이 등록 된 창 클래스 이름을 사용할 수 있습니다.

`AfxRegisterClass`Win32의 DLL에서 (또는)를 사용 하는 것이 중요 `AfxRegisterWndClass` 합니다. Win32는 DLL에서 등록 된 클래스의 등록을 자동으로 취소 하지 않으므로 DLL이 종료 될 때 명시적으로 클래스의 등록을 취소 해야 합니다. 대신를 사용 하 여 `AfxRegisterClass` `RegisterClass` 자동으로 처리 됩니다. `AfxRegisterClass` DLL에서 등록 한 고유 클래스의 목록을 유지 관리 하 고 DLL이 종료 되 면 자동으로 등록을 취소 합니다. DLL에서를 사용 하는 경우에는 `RegisterClass` [DllMain](/windows/win32/Dlls/dllmain) 함수에서 dll이 종료 될 때 모든 클래스가 등록 취소 되도록 해야 합니다. 이렇게 하지 않으면 `RegisterClass` 다른 클라이언트 응용 프로그램에서 DLL을 사용 하려고 할 때 예기치 않은 오류가 발생할 수 있습니다.

## <a name="see-also"></a>참고 항목

[번호로 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)
