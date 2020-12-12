---
description: '자세히 알아보기: CFont 클래스'
title: CFont 클래스
ms.date: 11/04/2016
f1_keywords:
- CFont
- AFXWIN/CFont
- AFXWIN/CFont::CFont
- AFXWIN/CFont::CreateFont
- AFXWIN/CFont::CreateFontIndirect
- AFXWIN/CFont::CreatePointFont
- AFXWIN/CFont::CreatePointFontIndirect
- AFXWIN/CFont::FromHandle
- AFXWIN/CFont::GetLogFont
helpviewer_keywords:
- CFont [MFC], CFont
- CFont [MFC], CreateFont
- CFont [MFC], CreateFontIndirect
- CFont [MFC], CreatePointFont
- CFont [MFC], CreatePointFontIndirect
- CFont [MFC], FromHandle
- CFont [MFC], GetLogFont
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
ms.openlocfilehash: 4c3df138c80aeb572a4e449e7fe1065e70b5fe49
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184415"
---
# <a name="cfont-class"></a>CFont 클래스

Windows GDI(그래픽 디바이스 인터페이스) 글꼴을 캡슐화하고 글꼴 조작을 위한 멤버 함수를 제공합니다.

## <a name="syntax"></a>구문

```
class CFont : public CGdiObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CFont::CFont](#cfont)|`CFont` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CFont::CreateFont](#createfont)|지정 된 `CFont` 특성을 사용 하 여를 초기화 합니다.|
|[CFont:: Create글꼴 간접](#createfontindirect)|`CFont`구조체에 지정 된 특성을 사용 하 여 개체를 초기화 `LOGFONT` 합니다.|
|[CFont:: CreatePointFont](#createpointfont)|지정 된 `CFont` 높이 (포인트의 1/10)와 서체를 사용 하 여를 초기화 합니다.|
|[CFont::CreatePointFontIndirect](#createpointfontindirect)|`CreateFontIndirect`글꼴 높이가 논리적 단위가 아닌 1/10 단위로 측정 된다는 점을 제외 하 고와 동일 합니다.|
|[CFont:: FromHandle](#fromhandle)|`CFont`Windows HFONT가 지정 된 경우 개체에 대 한 포인터를 반환 합니다.|
|[CFont::GetLogFont](#getlogfont)|`LOGFONT`개체에 연결 된 논리적 글꼴에 대 한 정보로를 채웁니다 `CFont` .|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CFont:: operator HFONT](#operator_hfont)|개체에 연결 된 Windows GDI 글꼴 핸들을 반환 합니다 `CFont` .|

## <a name="remarks"></a>설명

개체 `CFont`를 사용 하려면 `CFont` 개체를 생성하고 [createfont](#createfont), [CreateFontIndirect](#createfontindirect), [createpointfont](#createpointfont) 또는 [CreatePointFontIndirect](#createpointfontindirect)을 간접적으로 사용하여 Windows 글꼴을 연결하고 개체의 멤버를 사용합니다.

`CreatePointFont`및 `CreatePointFontIndirect` 함수는 `CreateFont` `CreateFontIndirect` 포인트 크기에서 논리적 단위로 글꼴 높이를 자동으로 변환 하기 때문에 또는를 사용 하는 것이 더 쉽습니다.

에 대 한 자세한 내용은 `CFont` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CFont`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cfontcfont"></a><a name="cfont"></a> CFont:: CFont

`CFont` 개체를 생성합니다.

```
CFont();
```

### <a name="remarks"></a>설명

결과 개체 `CreateFont` 를 `CreateFontIndirect` `CreatePointFont` `CreatePointFontIndirect` 사용 하려면 먼저,, 또는를 사용 하 여 초기화 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#70](../../mfc/codesnippet/cpp/cfont-class_1.cpp)]

## <a name="cfontcreatefont"></a><a name="createfont"></a> CFont:: CreateFont

지정 된 `CFont` 특성을 사용 하 여 개체를 초기화 합니다.

```
BOOL CreateFont(
    int nHeight,
    int nWidth,
    int nEscapement,
    int nOrientation,
    int nWeight,
    BYTE bItalic,
    BYTE bUnderline,
    BYTE cStrikeOut,
    BYTE nCharSet,
    BYTE nOutPrecision,
    BYTE nClipPrecision,
    BYTE nQuality,
    BYTE nPitchAndFamily,
    LPCTSTR lpszFacename);
```

### <a name="parameters"></a>매개 변수

*nHeight*<br/>
글꼴의 원하는 높이 (논리 단위)를 지정 합니다. `lfHeight`Windows SDK에서 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)구조체의 멤버를 참조 하십시오. *Nheight* 의 절대값은 변환 된 후 16384 장치 단위를 초과 해서는 안 됩니다. 모든 높이 비교의 경우 글꼴 매퍼는 요청한 크기를 초과 하지 않는 가장 큰 글꼴 또는 모든 글꼴이 요청 된 크기를 초과 하는 경우 가장 작은 글꼴을 찾습니다.

*nWidth*<br/>
글꼴의 평균 문자 너비 (논리 단위)를 지정 합니다. *Nwidth* 가 0 이면 장치의 가로 세로 비율이 가장 근접 한 일치 항목을 찾기 위해 사용 가능한 글꼴의 digitization 가로 세로 비율과 일치 하 게 됩니다 .이 값은 차이의 절대값에 의해 결정 됩니다.

*nEscapement*<br/>
표시 표면의 표시 벡터와 x 축 사이의 각도 (0.1-도 단위)를 지정 합니다. 문자 방향 벡터는 줄의 첫 번째 및 마지막 문자 원본을 통한 선입니다. 각도는 x 축에서 시계 반대 방향으로 측정 됩니다. `lfEscapement` `LOGFONT` 자세한 내용은 Windows SDK 구조의 멤버를 참조 하십시오.

*nOrientation*<br/>
문자 기준선과 x 축 사이의 각도 (0.1-도 단위)를 지정 합니다. Y 방향이 위쪽 인 좌표계의 x 축에서 시계 방향으로 y 방향으로 이동 하 고 시계 방향으로 측정 한 각도는 x 축에서 시계 반대 방향으로 측정 됩니다.

*nWeight*<br/>
글꼴 두께 (1000 당 잉크가 픽셀)를 지정 합니다. 자세한 내용은 Windows SDK 구조의 *lfWeight* 멤버를 참조 하십시오 `LOGFONT` . 설명 된 값은 근사치입니다. 실제 모양은 서체에 따라 다릅니다. 일부 글꼴에는 FW_NORMAL, FW_REGULAR 및 FW_BOLD 가중치가 있습니다. FW_DONTCARE 지정 된 경우 기본 가중치가 사용 됩니다.

*bItalic*<br/>
글꼴을 기울임꼴로 표시할지 여부를 지정 합니다.

*bUnderline*<br/>
글꼴에 밑줄이 있는지 여부를 지정 합니다.

*cStrikeOut*<br/>
글꼴의 문자가 취소선 인지 여부를 지정 합니다. 0이 아닌 값으로 설정 된 경우 취소선 글꼴을 지정 합니다.

*nCharSet*<br/>
`lfCharSet` `LOGFONT` 값의 목록에 대 한 Windows SDK 구조의 멤버를 참조 하 여 글꼴의 문자 집합을 지정 합니다.

OEM 문자 집합은 시스템에 따라 다릅니다.

시스템에 다른 문자 집합을 사용 하는 글꼴이 있을 수 있습니다. 알 수 없는 문자 집합의 글꼴을 사용 하는 응용 프로그램에서는 해당 글꼴로 렌더링 되는 문자열을 변환 하거나 해석 하려고 해서는 안 됩니다. 대신 문자열을 출력 장치 드라이버로 직접 전달 해야 합니다.

글꼴 매퍼는 DEFAULT_CHARSET 값을 사용 하지 않습니다. 응용 프로그램은이 값을 사용 하 여 글꼴의 이름과 크기가 논리적 글꼴을 완벽 하 게 설명할 수 있도록 합니다. 지정 된 이름의 글꼴이 없으면 문자 집합의 글꼴을 지정 된 글꼴로 대체할 수 있습니다. 예기치 않은 결과를 방지 하기 위해 응용 프로그램에서는 DEFAULT_CHARSET 값을 사용 하지 않아도 됩니다.

*nOutPrecision*<br/>
원하는 출력 전체 자릿수를 지정 합니다. 출력 전체 자릿수는 해당 출력이 요청 된 글꼴의 높이, 너비, 문자 방향, 이스케이프 및 피치와 얼마나 일치 해야 하는지를 정의 합니다. `lfOutPrecision` `LOGFONT` 값 목록과 자세한 정보는 Windows SDK 구조의 멤버를 참조 하십시오.

*nClipPrecision*<br/>
원하는 클리핑 전체 자릿수를 지정 합니다. 클리핑 전체 자릿수는 클리핑 영역을 부분적으로 벗어난 문자를 자르는 방법을 정의 합니다. `lfClipPrecision` `LOGFONT` 값 목록은 Windows SDK 구조의 멤버를 참조 하십시오.

포함 된 읽기 전용 글꼴을 사용 하려면 응용 프로그램에서 CLIP_ENCAPSULATE를 지정 해야 합니다.

장치, TrueType 및 벡터 글꼴을 일관 되 게 회전 하기 위해 응용 프로그램은 OR 연산자를 사용 하 여 CLIP_LH_ANGLES 값을 다른 *nClipPrecision* 값과 결합할 수 있습니다. CLIP_LH_ANGLES 비트가 설정 된 경우 모든 글꼴에 대 한 회전은 좌표계의 방향이 왼쪽 인지 또는 오른손 인지에 따라 달라 집니다. 좌표계의 방향에 대 한 자세한 내용은 *nOrientation* 매개 변수에 대 한 설명을 참조 하십시오. CLIP_LH_ANGLES 설정 하지 않으면 장치 글꼴은 항상 시계 반대 방향으로 회전 하지만 다른 글꼴의 회전은 좌표계의 방향에 따라 달라 집니다.

*nQuality*<br/>
글꼴의 출력 품질을 지정 합니다 .이는 GDI에서 논리적 글꼴 특성을 실제 실제 글꼴의 특성과 일치 시 키 려 고 하는 정도를 정의 합니다. `lfQuality` `LOGFONT` 값 목록은 Windows SDK 구조의 멤버를 참조 하십시오.

*nPitchAndFamily*<br/>
글꼴의 피치와 패밀리를 지정 합니다. `lfPitchAndFamily` `LOGFONT` 값 목록과 자세한 정보는 Windows SDK 구조의 멤버를 참조 하십시오.

*lpszFacename*<br/>
`CString`글꼴의 서체 이름을 지정 하는 null로 끝나는 문자열에 대 한 또는 포인터입니다. 이 문자열의 길이는 30 자를 초과 하면 안 됩니다. Windows [Enum글꼴 패밀리](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesw) 함수를 사용 하 여 현재 사용 가능한 모든 글꼴을 열거할 수 있습니다. *LpszFacename* 가 NULL 인 경우 GDI는 장치 독립적 서체를 사용 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에 모든 장치 컨텍스트의 글꼴로 글꼴을 선택할 수 있습니다.

`CreateFont`함수는 새 WINDOWS GDI 글꼴을 만들지 않습니다. GDI에 사용할 수 있는 실제 글꼴에서 가장 일치 하는 항목을 선택 하기만 하면 됩니다.

응용 프로그램은 논리적 글꼴을 만들 때 대부분의 매개 변수에 대 한 기본 설정을 사용할 수 있습니다. 항상 특정 값을 지정 해야 하는 매개 변수는 *Nheight* 및 *lpszFacename* 입니다. 응용 프로그램에서 *Nheight* 및 *lpszFacename* 가 설정 되지 않은 경우 생성 되는 논리적 글꼴은 장치에 따라 다릅니다.

`CFont`함수에서 만든 개체를 마치면를 `CreateFont` 사용 `CDC::SelectObject` 하 여 장치 컨텍스트에 다른 글꼴을 선택한 다음 `CFont` 더 이상 필요 하지 않은 개체를 삭제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#71](../../mfc/codesnippet/cpp/cfont-class_2.cpp)]

## <a name="cfontcreatefontindirect"></a><a name="createfontindirect"></a> CFont:: Create글꼴 간접

[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체에 지정된 특성을 사용하여 `CFont` 개체를 초기화합니다.

```
BOOL CreateFontIndirect(const LOGFONT* lpLogFont);
```

### <a name="parameters"></a>매개 변수

*lpLogFont*<br/>
`LOGFONT`논리적 글꼴의 특징을 정의 하는 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에 모든 장치에 대 한 현재 글꼴로 글꼴을 선택할 수 있습니다.

이 글꼴에는 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조에 지정 된 특징이 있습니다. [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) 멤버 함수를 사용 하 여 글꼴을 선택 하면 GDI 글꼴 매퍼는 논리적 글꼴을 기존 실제 글꼴과 일치 시 키 려 고 시도 합니다. 글꼴 매퍼는 논리적 글꼴에 대해 정확히 일치 하는 항목을 찾지 못할 경우 필요한 특성 수와 일치 하는 특성이 있는 대체 글꼴을 제공 합니다.

함수에서 만든 개체가 더 이상 필요 하지 않은 경우를 `CFont` `CreateFontIndirect` 사용 `CDC::SelectObject` 하 여 장치 컨텍스트에 다른 글꼴을 선택한 다음 `CFont` 더 이상 필요 하지 않은 개체를 삭제 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#72](../../mfc/codesnippet/cpp/cfont-class_3.cpp)]

## <a name="cfontcreatepointfont"></a><a name="createpointfont"></a> CFont:: CreatePointFont

이 함수는 지정 된 서체 및 포인트 크기의 글꼴을 만드는 간단한 방법을 제공 합니다.

```
BOOL CreatePointFont(
    int nPointSize,
    LPCTSTR lpszFaceName,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>매개 변수

*nPointSize*<br/>
요청 된 글꼴 높이 (1/10 포인트)입니다. 예를 들어 120을 전달 하 여 12 포인트 글꼴을 요청 합니다.

*lpszFaceName*<br/>
`CString`글꼴의 서체 이름을 지정 하는 null로 끝나는 문자열에 대 한 또는 포인터입니다. 이 문자열의 길이는 30 자를 초과 하면 안 됩니다. Windows ' Enum글꼴 패밀리 함수를 사용 하 여 현재 사용 가능한 모든 글꼴을 열거할 수 있습니다. *LpszFaceName* 가 NULL 인 경우 GDI는 장치 독립적 서체를 사용 합니다.

*컨트롤러가*<br/>
*Npointsize* 의 높이를 논리 단위로 변환 하는 데 사용할 [CDC](../../mfc/reference/cdc-class.md) 개체에 대 한 포인터입니다. NULL 인 경우 화면 장치 컨텍스트가 변환에 사용 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

*PDC* 에서 가리키는 CDC 개체를 사용 하 여 *npointsize* 의 높이를 논리 단위로 자동 변환 합니다.

`CFont`함수에서 만든 개체를 마치면 `CreatePointFont` 먼저 장치 컨텍스트에서 글꼴을 선택한 다음 개체를 삭제 `CFont` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#73](../../mfc/codesnippet/cpp/cfont-class_4.cpp)]

## <a name="cfontcreatepointfontindirect"></a><a name="createpointfontindirect"></a> CFont:: Createpoint글꼴 간접

이 함수는 [](#createfontindirect) `lfHeight` 의 멤버가 `LOGFONT` 장치 단위가 아닌 1/10의 1/10으로 해석 된다는 점을 제외 하 고는 create글꼴 간접적인와 동일 합니다.

```
BOOL CreatePointFontIndirect(
    const LOGFONT* lpLogFont,
    CDC* pDC = NULL);
```

### <a name="parameters"></a>매개 변수

*lpLogFont*<br/>
논리적 글꼴의 특징을 정의 하는 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체를 가리킵니다. `lfHeight`구조체의 멤버는 `LOGFONT` 논리적 단위가 아닌 1/10 단위로 측정 됩니다. 예를 들어를 120로 설정 `lfHeight` 하 여 12 포인트 글꼴을 요청 합니다.

*컨트롤러가*<br/>
높이를 논리 단위로 변환 하는 데 사용할 [CDC](../../mfc/reference/cdc-class.md) 개체에 대 한 포인터 `lfHeight` 입니다. NULL 인 경우 화면 장치 컨텍스트가 변환에 사용 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 `lfHeight` Windows에 구조를 전달 하기 전에 *pDC* 가 가리키는 CDC 개체를 사용 하 여의 높이를 논리 단위로 자동 변환 합니다 `LOGFONT` .

`CFont`함수에서 만든 개체를 마치면 `CreatePointFontIndirect` 먼저 장치 컨텍스트에서 글꼴을 선택한 다음 개체를 삭제 `CFont` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#74](../../mfc/codesnippet/cpp/cfont-class_5.cpp)]

## <a name="cfontfromhandle"></a><a name="fromhandle"></a> CFont:: FromHandle

`CFont`WINDOWS GDI 글꼴 개체에 대 한 HFONT 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.

```
static CFont* PASCAL FromHandle(HFONT hFont);
```

### <a name="parameters"></a>매개 변수

*hFont*<br/>
Windows 글꼴의 HFONT 핸들입니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CFont` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`CFont`개체가 핸들에 아직 연결 되지 않은 경우 임시 `CFont` 개체가 생성 되 고 연결 됩니다. 이 임시 `CFont` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과 하 여 모든 임시 그래픽 개체가 삭제 될 때 까지만 유효 합니다. 이에 대 한 또 다른 방법은 임시 개체가 하나의 창 메시지를 처리 하는 동안에만 유효 하다는 것입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#75](../../mfc/codesnippet/cpp/cfont-class_6.cpp)]

## <a name="cfontgetlogfont"></a><a name="getlogfont"></a> CFont:: GetLogFont

이 함수를 호출 하 여 `LOGFONT` 에 대 한 구조체의 복사본을 검색 `CFont` 합니다.

```
int GetLogFont(LOGFONT* pLogFont);
```

### <a name="parameters"></a>매개 변수

*pLogFont*<br/>
글꼴 정보를 수신 하는 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#76](../../mfc/codesnippet/cpp/cfont-class_7.cpp)]

## <a name="cfontoperator-hfont"></a><a name="operator_hfont"></a> CFont:: operator HFONT

이 연산자를 사용 하 여 개체에 연결 된 글꼴의 Windows GDI 핸들을 가져옵니다 `CFont` .

```
operator HFONT() const;
```

### <a name="return-value"></a>반환 값

성공 하면 연결 된 Windows GDI 글꼴 개체의 핸들이 고 `CFont` , 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 연산자는에서 글꼴과 텍스트로의 변환에 자동으로 사용 되므로 `CFont` [](/windows/win32/gdi/fonts-and-text) `CFont` hfonts를 필요로 하는 함수에 개체를 전달할 수 있습니다.

그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [그래픽 개체](/windows/win32/gdi/graphic-objects) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#77](../../mfc/codesnippet/cpp/cfont-class_8.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 클래스](../../mfc/reference/cgdiobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
