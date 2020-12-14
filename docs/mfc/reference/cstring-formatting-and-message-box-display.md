---
description: '자세한 정보: CString 서식 지정 및 Message-Box 표시'
title: CString 서식 지정 및 메시지 상자 표시
ms.date: 11/04/2016
helpviewer_keywords:
- CString objects [MFC], formatting and message boxes
ms.assetid: d1068cf4-9cc5-4952-b9e7-d612c53cbc28
ms.openlocfilehash: a3c91a2a8a6f80235a834811433467797d5a37a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264520"
---
# <a name="cstring-formatting-and-message-box-display"></a>CString 서식 지정 및 메시지 상자 표시

개체의 형식을 지정 하 고 구문 분석 하는 다양 한 함수가 제공 됩니다 `CString` . 개체를 조작 해야 하는 경우 언제 든 지 이러한 함수를 사용할 수 `CString` 있지만, 메시지 상자 텍스트에 표시 되는 문자열의 형식을 지정 하는 데 특히 유용 합니다.

이 함수 그룹에는 메시지 상자를 표시 하는 전역 루틴이 포함 되어 있습니다.

### <a name="cstring-functions"></a>CString 함수

|Name|설명|
|-|-|
|[AfxExtractSubString](#afxextractsubstring)|지정 된 소스 문자열에서 단일 문자로 구분 된 부분 문자열을 추출 합니다.|
|[AfxFormatString1](#afxformatstring1)|문자열 테이블에 포함 된 문자열에서 서식 문자 "%1"에 대 한 지정 된 문자열을 대체 합니다.|
|[AfxFormatString2](#afxformatstring2)|문자열 테이블에 포함 된 문자열에서 서식 문자 "%1"과 (와) "%2"의 두 문자열을 대체 합니다.|
|[AfxMessageBox](#afxmessagebox)|메시지 상자를 표시합니다.|

### <a name="requirements"></a>요구 사항

  **헤더** afxwin.h

## <a name="afxextractsubstring"></a><a name="afxextractsubstring"></a> AfxExtractSubString

이 전역 함수를 사용 하 여 지정 된 소스 문자열에서 부분 문자열을 추출할 수 있습니다.

```
BOOL AFXAPI AfxExtractSubString (
    CString& rString,
    LPCTSTR lpszFullString,
    int iSubString,
    TCHAR chSep  = '\n');
```

### <a name="parameters"></a>매개 변수

*rString*<br/>
개별 부분 문자열을 받을 [CString](../../atl-mfc-shared/using-cstring.md) 개체에 대 한 참조입니다.

*lpszFullString*<br/>
추출할 문자열의 전체 텍스트를 포함 하는 문자열입니다.

*iSubString*<br/>
*LpszFullString* 에서 추출할 부분 문자열의 인덱스 (0부터 시작)입니다.

*chSep 월*<br/>
부분 문자열을 구분 하는 데 사용 되는 구분 기호 문자입니다.

### <a name="return-value"></a>반환 값

함수가 제공 된 인덱스에서 부분 문자열을 추출 했으면 TRUE이 고, 그렇지 않으면입니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 함수는 알려진 단일 문자가 각 부분 문자열을 구분 하는 경우 소스 문자열에서 여러 부분 문자열을 추출 하는 데 유용 합니다. 이 함수는 호출 될 때마다 *lpszFullString* 매개 변수의 시작 부분에서 검색 합니다.

이 함수는 *lpszFullString* 가 NULL로 설정 되어 있거나 함수가 지정 된 구분 기호 문자의 *isubstring*+ 1 회 발생을 찾지 않고 *lpszFullString* 의 끝에 도달 하는 경우 FALSE를 반환 합니다. *LpszFullString* 가 NULL로 설정 된 경우 *rstring* 매개 변수는 원래 값에서 수정 되지 않습니다. 그렇지 않으면 지정 된 인덱스에 대 한 부분 문자열을 추출할 수 없는 경우 *rstring* 매개 변수는 빈 문자열로 설정 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#48](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_1.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxwin.h

## <a name="afxformatstring1"></a><a name="afxformatstring1"></a> AfxFormatString1

*NIDS* 로 식별 되는 템플릿 문자열 리소스에서 문자 "%1"의 모든 인스턴스에 대해 *lpsz1* 가 가리키는 문자열을 대체 합니다.

```cpp
void  AfxFormatString1(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1);
```

### <a name="parameters"></a>매개 변수

*rString*<br/>
대체가 수행된 후 결과 문자열을 포함하는 `CString` 개체에 대한 참조입니다.

*nIDS*<br/>
대체가 수행될 템플릿 문자열의 리소스 ID입니다.

*lpsz1*<br/>
템플릿 문자열에서 서식 문자 "%1"을(를) 대체하는 문자열입니다.

### <a name="remarks"></a>설명

새로 구성 된 문자열은 *Rstring* 에 저장 됩니다. 예를 들어 문자열 테이블의 문자열이 "파일 %1을 (를) 찾을 수 없음"이 고 *lpsz1* 가 "C:\MYFILE.TXT" 이면 *Rstring* 에 "파일 C:\MYFILE.TXT 찾을 수 없음" 문자열이 포함 됩니다. 이 함수는 메시지 상자와 다른 창에 서식 지정 문자열을 전송하는 데 유용합니다.

서식 문자 "%1"이(가) 두 번 이상 문자열에 나타나는 경우 대체가 여러 번 수행됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#25](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_2.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxwin.h

## <a name="afxformatstring2"></a><a name="afxformatstring2"></a> AfxFormatString2

는 "%1" 문자 인스턴스에 대해 *lpsz1* 가 가리키는 문자열을, *nIDS* 로 식별 되는 템플릿 문자열 리소스에서 문자 "%2"의 모든 인스턴스에 대해 *lpsz2* 가 가리키는 문자열을 대체 합니다.

```cpp
void AfxFormatString2(
    CString& rString,
    UINT nIDS,
    LPCTSTR lpsz1,
    LPCTSTR lpsz2);
```

### <a name="parameters"></a>매개 변수

*rString*<br/>
`CString`대체가 수행 된 후 결과 문자열을 포함 하는에 대 한 참조입니다.

*nIDS*<br/>
대체가 수행 될 템플릿 문자열의 문자열 테이블 ID입니다.

*lpsz1*<br/>
템플릿 문자열에서 서식 문자 "%1"을(를) 대체하는 문자열입니다.

*lpsz2*<br/>
템플릿 문자열에서 서식 문자 "%2"을 (를) 바꿀 문자열입니다.

### <a name="remarks"></a>설명

새로 구성 된 문자열은 *Rstring* 에 저장 됩니다. 예를 들어 문자열 테이블의 문자열이 "%2 디렉터리에서 찾을 수 없는 파일" 인 경우 *lpsz1* 는 "MYFILE.TXT"을 가리키고 *lpsz2* 는 "c:\mydir"을 가리킵니다. *Rstring* 에는 "파일 MYFILE.TXT 디렉터리 c:\mydir에서 찾을 수 없습니다." 라는 문자열이 포함 됩니다.

서식 문자 "%1" 또는 "%2"이 (가) 문자열에 두 번 이상 표시 되는 경우 여러 대체가 수행 됩니다. 숫자 순서를 반드시 지정할 필요는 없습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#26](../../mfc/codesnippet/cpp/cstring-formatting-and-message-box-display_3.cpp)]

### <a name="requirements"></a>요구 사항

  **헤더** afxwin.h

## <a name="afxmessagebox"></a><a name="afxmessagebox"></a> AfxMessageBox

화면에 메시지 상자를 표시 합니다.

```
int AfxMessageBox(
    LPCTSTR lpszText,
    UINT nType = MB_OK,
    UINT nIDHelp = 0);

int AFXAPI AfxMessageBox(
    UINT nIDPrompt,
    UINT nType = MB_OK,
    UINT nIDHelp = (UINT) -1);
```

### <a name="parameters"></a>매개 변수

*lpszText*<br/>
`CString`메시지 상자에 표시할 메시지를 포함 하는 개체 또는 null로 끝나는 문자열을 가리킵니다.

*nType*<br/>
메시지 상자의 스타일입니다. 상자에 [메시지 상자 스타일](../../mfc/reference/styles-used-by-mfc.md#message-box-styles) 을 적용 합니다.

*nIDHelp*<br/>
메시지의 도움말 컨텍스트 ID입니다. 0은 응용 프로그램의 기본 도움말 컨텍스트가 사용 됨을 나타냅니다.

*nIDPrompt*<br/>
문자열 테이블의 문자열을 참조 하는 데 사용 되는 고유 ID입니다.

### <a name="return-value"></a>반환 값

메시지 상자를 표시 하는 데 충분 한 메모리가 없는 경우 0입니다. 그렇지 않으면 다음 값 중 하나가 반환 됩니다.

- IDABORT 중단 단추를 선택 했습니다.

- IDCANCEL 취소 단추를 선택 했습니다.

- 무시 단추를 선택 했습니다.

- IDNO 단추를 선택 하지 않았습니다.

- IDOK 확인 단추를 선택 했습니다.

- IDRETRY 다시 시도 단추를 선택 했습니다.

- IDYES 예 단추를 선택 했습니다.

메시지 상자에 취소 단추가 있는 경우 ESC 키를 누르거나 취소 단추를 선택 하면 IDCANCEL 값이 반환 됩니다. 메시지 상자에 취소 단추가 없으면 ESC 키를 누르면 아무런 효과가 없습니다.

[AfxFormatString1](#afxformatstring1) 및 [AfxFormatString2](#afxformatstring2) 함수는 메시지 상자에 표시 되는 텍스트의 서식을 지정 하는 데 유용할 수 있습니다.

### <a name="remarks"></a>설명

이 오버 로드 된 함수의 첫 번째 형태는 메시지 상자에서 *lpszText* 가 가리키는 텍스트 문자열을 표시 하 고 *nIDHelp* 를 사용 하 여 도움말 컨텍스트를 설명 합니다. 도움말 컨텍스트는 사용자가 도움말 키 (일반적으로 F1)를 누를 때 연결 된 도움말 항목으로 이동 하는 데 사용 됩니다.

함수의 두 번째 형태는 ID *nIDPrompt* 문자열 리소스를 사용 하 여 메시지 상자에 메시지를 표시 합니다. *NIDHelp* 의 값을 통해 연결 된 도움말 페이지를 찾을 수 있습니다. *NIDHelp* 의 기본값 (-1)을 사용 하는 경우에는 문자열 리소스 ID *nIDPrompt* 가 도움말 컨텍스트에 사용 됩니다. 도움말 컨텍스트를 정의 하는 방법에 대 한 자세한 내용은 [Technical Note 28](../../mfc/tn028-context-sensitive-help-support.md)을 참조 하십시오.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWindowing#133](../../mfc/reference/codesnippet/cpp/cstring-formatting-and-message-box-display_4.cpp)]

## <a name="see-also"></a>참고 항목

[매크로 및 전역](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[CStringT 클래스](../../atl-mfc-shared/reference/cstringt-class.md)
