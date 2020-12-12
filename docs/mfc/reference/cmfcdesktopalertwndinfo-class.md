---
description: '자세히 알아보기: CMFCDesktopAlertWndInfo 클래스'
title: CMFCDesktopAlertWndInfo 클래스
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
helpviewer_keywords:
- CMFCDesktopAlertWndInfo [MFC], m_hIcon
- CMFCDesktopAlertWndInfo [MFC], m_nURLCmdID
- CMFCDesktopAlertWndInfo [MFC], m_strText
- CMFCDesktopAlertWndInfo [MFC], m_strURL
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
ms.openlocfilehash: 1c23e5b890e892df9bccce51542f2d36b3d6f7d4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250688"
---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo 클래스

`CMFCDesktopAlertWndInfo`클래스는 [CMFCDesktopAlertWnd 클래스](../../mfc/reference/cmfcdesktopalertwnd-class.md)와 함께 사용 됩니다. 바탕 화면 경고 창이 표시될 경우 표시되는 컨트롤을 지정합니다.

## <a name="syntax"></a>구문

```
class CMFCDesktopAlertWndInfo
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo:: operator =](#operator_eq)||

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CMFCDesktopAlertWndInfo:: m_hIcon](#m_hicon)|표시 되는 아이콘에 대 한 핸들입니다.|
|[CMFCDesktopAlertWndInfo:: m_nURLCmdID](#m_nurlcmdid)|바탕 화면 경고 창의 링크와 연결 된 명령 ID입니다.|
|[CMFCDesktopAlertWndInfo:: m_strText](#m_strtext)|바탕 화면 경고 창에 표시 되는 텍스트입니다.|
|[CMFCDesktopAlertWndInfo:: m_strURL](#m_strurl)|바탕 화면 경고 창에 표시 되는 링크입니다.|

## <a name="remarks"></a>설명

`CMFCDesktopAlertWndInfo`클래스는 [CMFCDesktopAlertWnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) 메서드로 전달 되어 바탕 화면 경고 창의 기본 대화 상자에 표시 되는 요소를 지정 합니다. 기본 대화 상자에는 다음과 같은 세 가지 항목이 포함 될 수 있습니다.

- [CMFCDesktopAlertWndInfo:: m_hIcon](#m_hicon)를 호출 하 여 설정 되는 아이콘입니다.

- [CMFCDesktopAlertWndInfo:: m_strText](#m_strtext)를 호출 하 여 설정 된 레이블 또는 텍스트 메시지입니다.

- [CMFCDesktopAlertWndInfo:: m_strURL](#m_strurl)를 호출 하 여 설정 되는 링크입니다. 링크를 클릭할 때 실행 되는 명령을 설정 하려면 [CMFCDesktopAlertWndInfo:: m_nURLCmdID](#m_nurlcmdid)를 호출 합니다.

기본 대화 상자에 충분 하지 않은 경우 사용자 지정 대화 상자를 만들어이 클래스를 사용 하는 대신 [CMFCDesktopAlertWnd:: create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create) 메서드에 전달할 수 있습니다. 자세한 내용은 [Cmfcdesktopalertdialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 클래스에서 다양 한 멤버를 사용 하는 방법을 보여 줍니다 `CMFCDesktopAlertWndInfo` . 이 예제에서는 표시 되는 아이콘, 바탕 화면 경고 창에 표시 되는 텍스트, 바탕 화면 경고 창에 표시 되는 링크 및 바탕 화면 경고 창의 링크와 연결 된 명령 ID로 핸들을 설정 하는 방법을 보여 줍니다. 이 예제는 [데스크톱 경고 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_DesktopAlertDemo#3](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxDesktopAlertDialog

## <a name="cmfcdesktopalertwndinfooperator"></a><a name="operator_eq"></a> CMFCDesktopAlertWndInfo:: operator =

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```

### <a name="parameters"></a>매개 변수

진행 *src*<br/>

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndinfom_hicon"></a><a name="m_hicon"></a> CMFCDesktopAlertWndInfo:: m_hIcon

표시 되는 아이콘에 대 한 핸들입니다.

```
HICON m_hIcon;
```

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndinfom_nurlcmdid"></a><a name="m_nurlcmdid"></a> CMFCDesktopAlertWndInfo:: m_nURLCmdID

바탕 화면 경고 창의 링크와 연결 된 명령 ID입니다.

```
UINT m_nURLCmdID;
```

### <a name="remarks"></a>설명

사용자가 [CMFCDesktopAlertWndInfo:: m_strURL](#m_strurl)에 지정 된 링크를 클릭 하면 명령 ID가 팝업 창의 소유자에 게 전송 됩니다.

## <a name="cmfcdesktopalertwndinfom_strtext"></a><a name="m_strtext"></a> CMFCDesktopAlertWndInfo:: m_strText

바탕 화면 경고 창에 표시 되는 텍스트입니다.

```
CString m_strText;
```

### <a name="remarks"></a>설명

## <a name="cmfcdesktopalertwndinfom_strurl"></a><a name="m_strurl"></a> CMFCDesktopAlertWndInfo:: m_strURL

바탕 화면 경고 창에 표시 되는 링크입니다.

```
CString m_strURL;
```

### <a name="remarks"></a>설명

사용자가 링크를 클릭 하면 [CMFCDesktopAlertWndInfo:: m_nURLCmdID](#m_nurlcmdid) 명령 ID를 가진 명령이 팝업 창의 소유자에 게 전송 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWnd 클래스](../../mfc/reference/cmfcdesktopalertwnd-class.md)<br/>
[CMFCDesktopAlertWnd:: Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)<br/>
[CMFCDesktopAlertDialog 클래스](../../mfc/reference/cmfcdesktopalertdialog-class.md)
