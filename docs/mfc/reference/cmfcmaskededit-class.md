---
description: '자세히 알아보기: 있도록 cmfcmaskededit 클래스'
title: 있도록 cmfcmaskededit 클래스
ms.date: 11/04/2016
f1_keywords:
- CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit
- AFXMASKEDEDIT/CMFCMaskedEdit::DisableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableGetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableMask
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSelectByGroup
- AFXMASKEDEDIT/CMFCMaskedEdit::EnableSetMaskedCharsOnly
- AFXMASKEDEDIT/CMFCMaskedEdit::GetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::SetValidChars
- AFXMASKEDEDIT/CMFCMaskedEdit::SetWindowText
- AFXMASKEDEDIT/CMFCMaskedEdit::IsMaskedChar
helpviewer_keywords:
- CMFCMaskedEdit [MFC], DisableMask
- CMFCMaskedEdit [MFC], EnableGetMaskedCharsOnly
- CMFCMaskedEdit [MFC], EnableMask
- CMFCMaskedEdit [MFC], EnableSelectByGroup
- CMFCMaskedEdit [MFC], EnableSetMaskedCharsOnly
- CMFCMaskedEdit [MFC], GetWindowText
- CMFCMaskedEdit [MFC], SetValidChars
- CMFCMaskedEdit [MFC], SetWindowText
- CMFCMaskedEdit [MFC], IsMaskedChar
ms.assetid: 13b1a645-2d5d-4c37-8599-16d5003f23a5
ms.openlocfilehash: 7ac61240e2941eafbbac3cbb03a4884e282cbca3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97265157"
---
# <a name="cmfcmaskededit-class"></a>있도록 cmfcmaskededit 클래스

`CMFCMaskedEdit`클래스는 마스크에 대해 사용자 입력의 유효성을 검사 하 고 템플릿에 따라 유효성 검사 된 결과를 표시 하는 마스킹된 편집 컨트롤을 지원 합니다.

## <a name="syntax"></a>구문

```
class CMFCMaskedEdit : public CEdit
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|`CMFCMaskedEdit::CMFCMaskedEdit`|기본 생성자입니다.|
|`CMFCMaskedEdit::~CMFCMaskedEdit`|소멸자|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[있도록 cmfcmaskededit::D isableMask](#disablemask)|사용자 입력 유효성 검사를 사용 하지 않습니다.|
|[있도록 cmfcmaskededit:: EnableGetMaskedCharsOnly](#enablegetmaskedcharsonly)|메서드가 마스킹된 문자만 검색 하는지 여부를 지정 합니다 `GetWindowText` .|
|[있도록 cmfcmaskededit:: EnableMask](#enablemask)|마스킹된 편집 컨트롤을 초기화 합니다.|
|[있도록 cmfcmaskededit:: EnableSelectByGroup](#enableselectbygroup)|마스킹된 편집 컨트롤에서 특정 사용자 입력 그룹 또는 모든 사용자 입력을 선택할지 여부를 지정 합니다.|
|[있도록 cmfcmaskededit:: EnableSetMaskedCharsOnly](#enablesetmaskedcharsonly)|마스킹된 문자 또는 전체 마스크에 대해 텍스트의 유효성을 검사할지 여부를 지정 합니다.|
|`CMFCMaskedEdit::GetThisClass`|프레임 워크에서이 클래스 형식과 연결 된 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 개체에 대 한 포인터를 가져오는 데 사용 됩니다.|
|[있도록 cmfcmaskededit:: GetWindowText](#getwindowtext)|마스킹된 편집 컨트롤에서 유효성이 검사 된 텍스트를 검색 합니다.|
|[있도록 cmfcmaskededit:: Set유효 문자](#setvalidchars)|사용자가 입력할 수 있는 유효한 문자 문자열을 지정 합니다.|
|[있도록 cmfcmaskededit:: SetWindowText](#setwindowtext)|마스킹된 편집 컨트롤에 프롬프트를 표시 합니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[있도록 cmfcmaskededit:: IsMaskedChar](#ismaskedchar)|지정 된 문자가 해당 마스크 문자에 대해 유효성을 검사 하기 위해 프레임 워크에서 호출 됩니다.|

## <a name="remarks"></a>설명

응용 프로그램에서 컨트롤을 사용 하려면 다음 단계를 수행 합니다 `CMFCMaskedEdit` .

1. `CMFCMaskedEdit`창 클래스에 개체를 포함 합니다.

2. [있도록 cmfcmaskededit:: EnableMask](#enablemask) 메서드를 호출 하 여 마스크를 지정 합니다.

3. [있도록 cmfcmaskededit:: setvalid chars](#setvalidchars) 메서드를 호출 하 여 유효한 문자 목록을 지정 합니다.

4. [있도록 cmfcmaskededit:: SetWindowText](#setwindowtext) 메서드를 호출 하 여 마스킹된 편집 컨트롤에 대 한 기본 텍스트를 지정 합니다.

5. [있도록 cmfcmaskededit:: GetWindowText](#getwindowtext) 메서드를 호출 하 여 유효성이 검사 된 텍스트를 검색 합니다.

하나 이상의 메서드를 호출 하 여 마스크, 유효한 문자 및 기본 텍스트를 초기화 하지 않는 경우 마스킹된 편집 컨트롤은 표준 편집 컨트롤이 동작 하는 것 처럼 동작 합니다.

## <a name="example"></a>예제

다음 예제에서는 메서드를 사용 하 여 `EnableMask` 마스킹된 편집 컨트롤에 대 한 마스크를 만들고, 메서드를 사용 하 여 `SetValidChars` 사용자가 입력할 수 있는 유효한 문자 문자열을 지정 하 고, 메서드를 사용 하 여 마스크를 설정 하 고, `SetWindowText` 마스킹된 편집 컨트롤에서 프롬프트를 표시 하는 방법을 보여 줍니다. 이 예제는 [새 컨트롤 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_NewControls#11](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#12](../../mfc/reference/codesnippet/cpp/cmfcmaskededit-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

[CMFCMaskedEdit](../../mfc/reference/cmfcmaskededit-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** afxmaskededit

## <a name="cmfcmaskededitdisablemask"></a><a name="disablemask"></a> 있도록 cmfcmaskededit::D isableMask

사용자 입력 유효성 검사를 사용 하지 않습니다.

```cpp
void DisableMask();
```

### <a name="remarks"></a>설명

사용자 입력 유효성 검사를 사용 하지 않도록 설정 하면 마스킹된 편집 컨트롤이 표준 편집 컨트롤 처럼 동작 합니다.

## <a name="cmfcmaskededitenablegetmaskedcharsonly"></a><a name="enablegetmaskedcharsonly"></a> 있도록 cmfcmaskededit:: EnableGetMaskedCharsOnly

메서드가 마스킹된 문자만 검색 하는지 여부를 지정 합니다 `GetWindowText` .

```cpp
void EnableGetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 [있도록 cmfcmaskededit:: GetWindowText](#getwindowtext) 메서드가 마스킹된 문자만 검색 하도록 지정 하려면 TRUE로 설정 합니다. 메서드가 전체 텍스트를 검색 하도록 지정 하려면 FALSE로 설정 합니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

마스킹된 문자를 검색할 수 있도록 하려면이 메서드를 사용 합니다. 그런 다음 전화 번호 (예: (425) 555-0187)에 해당 하는 마스킹된 편집 컨트롤을 만듭니다. 메서드를 호출 하는 경우 `GetWindowText` "4255550187"을 반환 합니다. 마스킹된 문자 검색을 사용 하지 않도록 설정 하는 경우 `GetWindowText` 메서드는 편집 컨트롤에 표시 되는 텍스트 (예: "(425) 555-0187")를 반환 합니다.

## <a name="cmfcmaskededitenablemask"></a><a name="enablemask"></a> 있도록 cmfcmaskededit:: EnableMask

마스킹된 편집 컨트롤을 초기화 합니다.

```cpp
void EnableMask(
    LPCTSTR lpszMask,
    LPCTSTR lpszInputTemplate,
    TCHAR chMaskInputTemplate=_T('_'),
    LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszMask*<br/>
진행 사용자 입력의 각 위치에 나타날 수 있는 문자 형식을 지정 하는 마스크 문자열입니다. *LpszInputTemplate* 및 *lpszMask* 매개 변수 문자열의 길이는 동일 해야 합니다. 마스크 문자에 대 한 자세한 내용은 설명 섹션을 참조 하세요.

*lpszInputTemplate*<br/>
진행 사용자 입력의 각 위치에 표시 될 수 있는 리터럴 문자를 지정 하는 마스크 템플릿 문자열입니다. 밑줄 문자 (' _ ')를 문자 자리 표시자로 사용 합니다. *LpszInputTemplate* 및 *lpszMask* 매개 변수 문자열의 길이는 동일 해야 합니다.

*chMaskInputTemplate*<br/>
진행 프레임 워크에서 사용자 입력의 잘못 된 각 문자를 대체 하는 기본 문자입니다. 이 매개 변수의 기본값은 밑줄 (' _ ')입니다.

*lpszValid*<br/>
진행 유효한 문자 집합을 포함 하는 문자열입니다. NULL은 모든 문자가 유효함을 나타냅니다. 이 매개 변수의 기본값은 NULL입니다.

### <a name="remarks"></a>설명

마스킹된 편집 컨트롤에 대 한 마스크를 만들려면이 메서드를 사용 합니다. 클래스에서 클래스를 파생 시키고 `CMFCMaskedEdit` [있도록 cmfcmaskededit:: IsMaskedChar](#ismaskedchar) 메서드를 재정의 하 여 사용자 지정 마스크 처리에 고유한 코드를 사용 합니다.

다음 표에서는 기본 마스크 문자를 나열 합니다.

|마스크 문자|정의|
|--------------------|----------------|
|D|분모.|
|일|숫자 또는 공간.|
|+|더하기 (' + '), 빼기 ('-') 또는 공백입니다.|
|C|영문자.|
|c|알파벳 문자 또는 공백입니다.|
|A|영숫자 문자입니다.|
|a|영숫자 문자 또는 공백입니다.|
|*|인쇄할 수 있는 문자입니다.|

## <a name="cmfcmaskededitenableselectbygroup"></a><a name="enableselectbygroup"></a> 있도록 cmfcmaskededit:: EnableSelectByGroup

마스킹된 편집 컨트롤을 통해 사용자가 특정 그룹 입력 또는 모든 입력을 선택할 수 있는지 여부를 지정 합니다.

```cpp
void EnableSelectByGroup(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 그룹만 선택 하려면 TRUE이 고, FALSE 이면 전체 텍스트를 선택 합니다. 기본값은 TRUE입니다.

### <a name="remarks"></a>설명

이 함수를 사용 하 여 마스킹된 편집 컨트롤을 통해 사용자가 그룹별 또는 전체 텍스트를 선택할 수 있는지 여부를 지정할 수 있습니다.

기본적으로 그룹에의 한 선택은 사용 하도록 설정 됩니다. 이 경우 사용자는 유효한 문자의 연속 그룹만 선택할 수 있습니다.

예를 들어 다음 마스킹된 편집 컨트롤을 사용 하 여 전화 번호의 유효성을 검사할 수 있습니다.

```cpp
m_wndMaskEdit.EnableMask(
    _T(" ddd  ddd dddd"),  // Mask string
    _T("(___) ___-____"),  // Template string
    _T(' '));              // Default char

m_wndMaskEdit.SetValidChars(NULL); // All characters are valid.

m_wndMaskEdit.SetWindowText(_T("(425) 555-0187")); // Prompt
```

그룹으로 선택이 설정 된 경우 사용자는 "425", "555" 또는 "0187" 문자열 그룹만 검색할 수 있습니다. 그룹 선택을 사용 하지 않도록 설정 된 경우 사용자는 전화 번호 "(425) 555-0187"의 전체 텍스트를 검색할 수 있습니다.

## <a name="cmfcmaskededitenablesetmaskedcharsonly"></a><a name="enablesetmaskedcharsonly"></a> 있도록 cmfcmaskededit:: EnableSetMaskedCharsOnly

마스킹된 문자 또는 전체 마스크에 대해 텍스트의 유효성을 검사할지 여부를 지정 합니다.

```cpp
void EnableSetMaskedCharsOnly(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>매개 변수

*bEnable*<br/>
진행 마스킹된 문자만 사용 하 여 사용자 입력의 유효성을 검사 하려면 TRUE이 고, 전체 마스크에 대해 유효성을 검사 하려면 FALSE입니다. 기본값은 TRUE입니다.

## <a name="cmfcmaskededitgetwindowtext"></a><a name="getwindowtext"></a> 있도록 cmfcmaskededit:: GetWindowText

마스킹된 편집 컨트롤에서 유효성이 검사 된 텍스트를 검색 합니다.

```
int GetWindowText(
    LPTSTR lpszStringBuf,
    int nMaxCount) const;

void GetWindowText(CString& rstrString) const;
```

### <a name="parameters"></a>매개 변수

*lpszStringBuf*<br/>
제한이 편집 컨트롤에서 텍스트를 받는 버퍼에 대 한 포인터입니다.

*nMaxCount*<br/>
진행 받을 최대 문자 수입니다.

*rstrString*<br/>
제한이 편집 컨트롤에서 텍스트를 받는 문자열 개체에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

첫 번째 메서드 오버 로드는 *lpszStringBuf* 매개 변수 버퍼에 복사 된 문자열의 바이트 수를 반환 합니다. 마스킹된 편집 컨트롤에 텍스트가 없는 경우 0입니다.

### <a name="remarks"></a>설명

이 메서드는 마스킹된 편집 컨트롤의 텍스트를 *lpszStringBuf* 버퍼 또는 *rstrString* 문자열에 복사 합니다.

이 메서드는 [CWnd:: GetWindowText](../../mfc/reference/cwnd-class.md#getwindowtext)를 다시 정의 합니다.

## <a name="cmfcmaskededitismaskedchar"></a><a name="ismaskedchar"></a> 있도록 cmfcmaskededit:: IsMaskedChar

지정 된 문자가 해당 마스크 문자에 대해 유효성을 검사 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL IsMaskedChar(
    TCHAR chChar,
    TCHAR chMaskChar) const;
```

### <a name="parameters"></a>매개 변수

*chChar*<br/>
진행 유효성을 검사할 문자입니다.

*chMaskChar*<br/>
진행 마스크 문자열에서 해당 하는 문자입니다.

### <a name="return-value"></a>반환 값

*Chchar* 매개 변수가 *chMaskChar* 매개 변수에서 허용 하는 문자 형식인 경우 TRUE입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

입력 문자에 대 한 유효성을 검사 하려면이 메서드를 재정의 합니다. 마스크 문자에 대 한 자세한 내용은 [있도록 cmfcmaskededit:: EnableMask](#enablemask) 메서드를 참조 하세요.

## <a name="cmfcmaskededitsetvalidchars"></a><a name="setvalidchars"></a> 있도록 cmfcmaskededit:: Set유효 문자

사용자가 입력할 수 있는 유효한 문자 문자열을 지정 합니다.

```cpp
void SetValidChars(LPCTSTR lpszValid=NULL);
```

### <a name="parameters"></a>매개 변수

*lpszValid*<br/>
진행 유효한 입력 문자 집합을 포함 하는 문자열입니다. NULL은 모든 문자를 사용할 수 있음을 의미 합니다. 이 매개 변수의 기본값은 NULL입니다.

### <a name="remarks"></a>설명

유효한 문자 목록을 정의 하려면이 메서드를 사용 합니다. 입력 문자가이 목록에 없는 경우 마스킹된 편집 컨트롤은이를 허용 하지 않습니다.

다음 코드 예제에서는 16 진수 번호만 허용 합니다.

```cpp
//Mask: 0xFFFF
m_wndMaskEdit.EnableMask(
    _T(" AAAA"),                // The mask string.
    _T("0x____"),               // The literal template string.
    _T('_'));                   // The default character that
                                // replaces the backspace character.
// Valid string characters
m_wndMaskEdit.SetValidChars(_T("1234567890ABCDEFabcdef"));m_wndMaskEdit.SetWindowText(_T("0x01AF"));
```

## <a name="cmfcmaskededitsetwindowtext"></a><a name="setwindowtext"></a> 있도록 cmfcmaskededit:: SetWindowText

마스킹된 편집 컨트롤에 프롬프트를 표시 합니다.

```cpp
void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>매개 변수

*lpszString*<br/>
진행 프롬프트로 사용 되는 null로 끝나는 문자열을 가리킵니다.

### <a name="remarks"></a>설명

이 메서드는 컨트롤 텍스트를 설정 합니다.

이 메서드는 [CWnd:: SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)를 다시 정의 합니다.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CEdit 클래스](../../mfc/reference/cedit-class.md)
