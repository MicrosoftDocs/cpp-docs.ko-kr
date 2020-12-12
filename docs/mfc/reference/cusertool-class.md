---
description: '자세한 정보: CUserTool 클래스'
title: CUserTool 클래스
ms.date: 11/04/2016
f1_keywords:
- CUserTool
- AFXUSERTOOL/CUserTool
- AFXUSERTOOL/CUserTool::CopyIconToClipboard
- AFXUSERTOOL/CUserTool::DrawToolIcon
- AFXUSERTOOL/CUserTool::GetCommand
- AFXUSERTOOL/CUserTool::GetCommandId
- AFXUSERTOOL/CUserTool::Invoke
- AFXUSERTOOL/CUserTool::Serialize
- AFXUSERTOOL/CUserTool::SetCommand
- AFXUSERTOOL/CUserTool::SetToolIcon
- AFXUSERTOOL/CUserTool::LoadDefaultIcon
- AFXUSERTOOL/CUserTool::m_strArguments
- AFXUSERTOOL/CUserTool::m_strInitialDirectory
- AFXUSERTOOL/CUserTool::m_strLabel
helpviewer_keywords:
- CUserTool [MFC], CopyIconToClipboard
- CUserTool [MFC], DrawToolIcon
- CUserTool [MFC], GetCommand
- CUserTool [MFC], GetCommandId
- CUserTool [MFC], Invoke
- CUserTool [MFC], Serialize
- CUserTool [MFC], SetCommand
- CUserTool [MFC], SetToolIcon
- CUserTool [MFC], LoadDefaultIcon
- CUserTool [MFC], m_strArguments
- CUserTool [MFC], m_strInitialDirectory
- CUserTool [MFC], m_strLabel
ms.assetid: 7c287d3e-d012-488d-b4e1-aa0f83f294bb
ms.openlocfilehash: 1a05d89543bdf3c0f873dadf9d2fbffb87ce680f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318509"
---
# <a name="cusertool-class"></a>CUserTool 클래스

사용자 도구는 외부 애플리케이션을 실행하는 메뉴 항목입니다. 사용자 **지정** 대화 상자의 **도구** 탭 ( [CMFCToolBarsCustomizeDialog 클래스](../../mfc/reference/cmfctoolbarscustomizedialog-class.md))을 사용 하면 사용자 도구를 추가 하 고 각 사용자 도구에 대해 이름, 명령, 인수 및 초기 디렉터리를 지정할 수 있습니다.

## <a name="syntax"></a>구문

```
class CUserTool : public CObject
```

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CUserTool:: CopyIconToClipboard](#copyicontoclipboard)||
|[CUserTool::D rawToolIcon](#drawtoolicon)|지정 된 사각형에 사용자 도구 아이콘을 그립니다.|
|[CUserTool:: GetCommand](#getcommand)|사용자 도구와 연결 된 명령의 텍스트를 포함 하는 문자열을 반환 합니다.|
|[CUserTool:: GetCommandId](#getcommandid)|사용자 도구의 메뉴 항목에 대 한 명령 ID를 반환 합니다.|
|[CUserTool:: Invoke](#invoke)|사용자 도구와 연결 된 명령을 실행 합니다.|
|[CUserTool:: Serialize](#serialize)|이 개체를 보관 저장소에서 읽어오거나 보관 저장소에 씁니다. ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)를 재정의합니다.)|
|[CUserTool:: SetCommand](#setcommand)|사용자 도구와 연결 된 명령을 설정 합니다.|
|[CUserTool:: SetToolIcon](#settoolicon)|도구와 연결 된 응용 프로그램에서 사용자 도구에 대 한 아이콘을 로드 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CUserTool:: LoadDefaultIcon](#loaddefaulticon)|사용자 도구에 대 한 기본 아이콘을 로드 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|----------|-----------------|
|[CUserTool:: m_strArguments](#m_strarguments)|사용자 도구에 대 한 명령줄 인수입니다.|
|[CUserTool:: m_strInitialDirectory](#m_strinitialdirectory)|사용자 도구에 대 한 초기 디렉터리입니다.|
|[CUserTool:: m_strLabel](#m_strlabel)|도구에 대 한 메뉴 항목에 표시 되는 도구 이름입니다.|

## <a name="remarks"></a>설명

응용 프로그램에서 사용자 도구를 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 [CUserToolsManager 클래스](../../mfc/reference/cusertoolsmanager-class.md)를 참조 하세요.

## <a name="example"></a>예제

다음 예제에서는 개체에서 도구를 만들고, `CUserToolsManager` 멤버 변수를 설정 하 `m_strLabel` 고, 사용자 도구에서 실행 하는 응용 프로그램을 설정 하는 방법을 보여 줍니다. 이 코드 조각은 [Visual Studio Demo 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_VisualStudioDemo#35](../../mfc/codesnippet/cpp/cusertool-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CUserTool](../../mfc/reference/cusertool-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxusertool

## <a name="cusertoolcopyicontoclipboard"></a><a name="copyicontoclipboard"></a> CUserTool:: CopyIconToClipboard

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
BOOL CopyIconToClipboard();
```

### <a name="return-value"></a>반환 값

### <a name="remarks"></a>설명

## <a name="cusertooldrawtoolicon"></a><a name="drawtoolicon"></a> CUserTool::D rawToolIcon

지정 된 사각형의 중앙에 사용자 도구 아이콘을 그립니다.

```cpp
void DrawToolIcon(
    CDC* pDC,
    const CRect& rectImage);
```

### <a name="parameters"></a>매개 변수

*컨트롤러가*<br/>
진행 장치 컨텍스트에 대 한 포인터입니다.

*rectImage*<br/>
진행 아이콘을 표시할 영역의 좌표를 지정 합니다.

## <a name="cusertoolgetcommand"></a><a name="getcommand"></a> CUserTool:: GetCommand

사용자 도구와 연결 된 명령의 텍스트를 포함 하는 문자열을 반환 합니다.

```
const CString& GetCommand() const;
```

### <a name="return-value"></a>반환 값

`CString`사용자 도구와 연결 된 명령의 텍스트를 포함 하는 개체에 대 한 참조입니다.

## <a name="cusertoolgetcommandid"></a><a name="getcommandid"></a> CUserTool:: GetCommandId

사용자 도구의 명령 ID를 반환 합니다.

```
UINT GetCommandId() const;
```

### <a name="return-value"></a>반환 값

이 사용자 도구의 명령 ID입니다.

## <a name="cusertoolinvoke"></a><a name="invoke"></a> CUserTool:: Invoke

사용자 도구와 연결 된 명령을 실행 합니다.

```
virtual BOOL Invoke();
```

### <a name="return-value"></a>반환 값

명령이 성공적으로 실행 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) 를 호출 하 여 사용자 도구와 연결 된 명령을 실행 합니다. 명령이 비어 있거나 [ShellExecute](/windows/win32/api/shellapi/nf-shellapi-shellexecutew) 가 실패 한 경우 함수가 실패 합니다.

## <a name="cusertoolloaddefaulticon"></a><a name="loaddefaulticon"></a> CUserTool:: LoadDefaultIcon

사용자 도구에 대 한 기본 아이콘을 로드 합니다.

```
virtual HICON LoadDefaultIcon();
```

### <a name="return-value"></a>반환 값

로드 된 아이콘에 대 한 핸들 (HICON) 이거나, 기본 아이콘을 로드할 수 없는 경우 NULL입니다.

### <a name="remarks"></a>설명

도구의 실행 파일에서 사용자 정의 도구에 대 한 아이콘을 로드할 수 없는 경우 프레임 워크는이 메서드를 호출 합니다.

사용자 고유의 기본 도구 아이콘을 제공 하려면이 메서드를 재정의 합니다.

## <a name="cusertoolm_strarguments"></a><a name="m_strarguments"></a> CUserTool:: m_strArguments

사용자 도구에 대 한 명령줄 인수입니다.

```
CString m_strArguments;
```

### <a name="remarks"></a>설명

이 문자열은 [Cusertool:: Invoke](#invoke) 를 호출 하거나 사용자가이 도구와 연결 된 명령을 클릭할 때 도구로 전달 됩니다.

## <a name="cusertoolm_strinitialdirectory"></a><a name="m_strinitialdirectory"></a> CUserTool:: m_strInitialDirectory

사용자 도구에 대 한 초기 디렉터리를 지정 합니다.

```
CString m_strInitialDirectory;
```

### <a name="remarks"></a>설명

이 변수는 [Cusertool:: Invoke](#invoke) 를 호출 하거나 사용자가이 도구와 연결 된 명령을 클릭할 때 도구가 실행 하는 초기 디렉터리를 지정 합니다.

## <a name="cusertoolm_strlabel"></a><a name="m_strlabel"></a> CUserTool:: m_strLabel

도구에 대 한 메뉴 항목에 표시 되는 레이블입니다.

```
CString m_strLabel;
```

## <a name="cusertoolserialize"></a><a name="serialize"></a> CUserTool:: Serialize

자세한 내용은 Visual Studio 설치의 **VC \\ s\mfc \\ src \\ mfc** 폴더에 있는 소스 코드를 참조 하세요.

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>매개 변수

[in] *ar*<br/>

### <a name="remarks"></a>설명

## <a name="cusertoolsetcommand"></a><a name="setcommand"></a> CUserTool:: SetCommand

사용자 도구에서 실행 하는 응용 프로그램을 설정 합니다.

```cpp
void SetCommand(LPCTSTR lpszCmd);
```

### <a name="parameters"></a>매개 변수

*lpszCmd*<br/>
진행 사용자 도구와 연결할 새 응용 프로그램을 지정 합니다.

### <a name="remarks"></a>설명

사용자 도구에서 실행 하는 새 응용 프로그램을 설정 하려면이 메서드를 호출 합니다. 메서드는 이전 아이콘을 소멸 시키고 지정 된 응용 프로그램에서 새 아이콘을 로드 합니다. 응용 프로그램에서 아이콘을 로드할 수 없는 경우 [Cusertool:: LoadDefaultIcon](#loaddefaulticon)를 호출 하 여 사용자 도구에 대 한 기본 아이콘을 로드 합니다.

## <a name="cusertoolsettoolicon"></a><a name="settoolicon"></a> CUserTool:: SetToolIcon

도구에서 사용 하는 응용 프로그램에서 사용자 도구에 대 한 아이콘을 로드 합니다.

```
virtual HICON SetToolIcon();
```

### <a name="return-value"></a>반환 값

로드 된 아이콘에 대 한 핸들입니다.

### <a name="remarks"></a>설명

메뉴 항목에 표시할 아이콘을 로드 하려면이 메서드를 호출 합니다. 이 메서드는 도구에서 사용 하는 실행 파일의 아이콘을 검색 합니다. 기본 아이콘이 없는 경우 [Cusertool:: LoadDefaultIcon](#loaddefaulticon) 에서 제공 하는 아이콘이 대신 사용 됩니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)<br/>
[CUserToolsManager 클래스](../../mfc/reference/cusertoolsmanager-class.md)
