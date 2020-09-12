---
title: MFC에서 사용하는 콜백 함수
ms.date: 11/04/2016
helpviewer_keywords:
- callback functions [MFC], MFC
- MFC, callback functions
- functions [MFC], callback
- callback functions [MFC]
ms.assetid: b2a6857c-fdd3-45ec-8fd8-2e71fac77582
ms.openlocfilehash: 553e87320828590c9e1e9204b54622f2f1ca6d80
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040888"
---
# <a name="callback-functions-used-by-mfc"></a>MFC에서 사용하는 콜백 함수

MFC 라이브러리에는 세 가지 콜백 함수가 표시 됩니다. 이러한 콜백 함수는 Cdc: [: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects), [Cdc:: GrayString](../../mfc/reference/cdc-class.md#graystring)및 [cdc:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)에 전달 됩니다. 모든 콜백 함수는 콜백 경계에서 예외가 throw 될 수 없으므로 Windows로 반환 하기 전에 MFC 예외를 트래핑 해야 합니다. 예외에 대 한 자세한 내용은 [예외](../../mfc/exception-handling-in-mfc.md)문서를 참조 하세요.

[CDC:: EnumObjects에 대 한 콜백 함수](#enum_objects)\
[CDC:: GrayString에 대 한 콜백 함수](#graystring)\
[CDC::SetAbortProc에 대한 콜백 함수](#setabortproc)

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="callback-function-for-cdcenumobjects"></a><a name="enum_objects"></a> CDC:: EnumObjects에 대 한 콜백 함수

*Objectfunc* name은 응용 프로그램에서 제공 하는 함수 이름에 대 한 자리 표시자입니다.

### <a name="syntax"></a>구문

```
int CALLBACK EXPORT ObjectFunc(
    LPSTR lpszLogObject,
    LPSTR* lpData);
```

### <a name="parameters"></a>매개 변수

*lpszLogObject*<br/>
개체의 논리적 특성에 대 한 정보를 포함 하는 [Logpen](/windows/win32/api/Wingdi/ns-wingdi-logpen) 또는 [logpen](/windows/win32/api/wingdi/ns-wingdi-logbrush) 데이터 구조를 가리킵니다.

*lpData*<br/>
함수에 전달 되는 응용 프로그램 제공 데이터를 가리킵니다 `EnumObjects` .

### <a name="return-value"></a>반환 값

콜백 함수는를 반환 합니다 **`int`** . 이 반환 값은 사용자가 정의 합니다. 콜백 함수에서 0을 반환 하는 경우는 `EnumObjects` 초기에 열거를 중지 합니다.

### <a name="remarks"></a>설명

실제 이름을 내보내야 합니다.

## <a name="callback-function-for-cdcgraystring"></a><a name="graystring"></a> CDC:: GrayString에 대 한 콜백 함수

*Outputfunc* 는 응용 프로그램에서 제공 하는 콜백 함수 이름에 대 한 자리 표시자입니다.

### <a name="syntax"></a>구문

```
BOOL CALLBACK EXPORT OutputFunc(
    HDC hDC,
    LPARAM lpData,
    int nCount);
```

### <a name="parameters"></a>매개 변수

*hDC*<br/>
이상 및에 지정 된 너비와 높이의 비트맵을 사용 하 여 메모리 장치 컨텍스트를 식별 `nWidth` `nHeight` `GrayString` 합니다.

*lpData*<br/>
그릴 문자열을 가리킵니다.

*nCount*<br/>
출력할 문자 수를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 여부를 나타내려면 콜백 함수의 반환 값은 TRUE 여야 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

콜백 함수 (*Outputfunc*)는 (*x*, *y*)가 아닌 좌표 (0, 0)를 기준으로 이미지를 그려야 합니다.

## <a name="callback-function-for-cdcsetabortproc"></a><a name="setabortproc"></a> CDC:: SetAbortProc에 대 한 콜백 함수

*AbortFunc* 이름은 응용 프로그램에서 제공 하는 함수 이름에 대 한 자리 표시자입니다.

### <a name="syntax"></a>구문

```
BOOL CALLBACK EXPORT AbortFunc(
    HDC hPr,
    int code);
```

### <a name="parameters"></a>매개 변수

*hPr*<br/>
장치 컨텍스트를 식별 합니다.

*code*<br/>
오류가 발생 했는지 여부를 지정 합니다. 오류가 발생 하지 않은 경우 0입니다. 현재 인쇄 관리자의 디스크 공간이 부족 하 고 응용 프로그램이 대기 하는 경우 더 많은 디스크 공간을 사용할 수 있게 되 면 SP_OUTOFDISK 됩니다. *코드가* SP_OUTOFDISK 경우에는 응용 프로그램에서 인쇄 작업을 중단할 필요가 없습니다. 그렇지 않으면 `PeekMessage` 또는 Windows 함수를 호출 하 여 인쇄 관리자에 게 양보 해야 합니다 `GetMessage` .

### <a name="return-value"></a>반환 값

중단 처리기 함수의 반환 값은 인쇄 작업을 계속 진행 하는 경우 0이 아니고 취소 된 경우 0입니다.

### <a name="remarks"></a>설명

[CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)의 설명 섹션에 설명 된 대로 실제 이름을 내보내야 합니다.

## <a name="see-also"></a>참고 항목

[구조체, 스타일, 콜백 및 메시지 맵](structures-styles-callbacks-and-message-maps.md)<br/>
[CDC:: EnumObjects](../../mfc/reference/cdc-class.md#enumobjects)<br/>
[CDC:: SetAbortProc](../../mfc/reference/cdc-class.md#setabortproc)<br/>
[CDC:: GrayString](../../mfc/reference/cdc-class.md#graystring)
