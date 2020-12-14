---
description: '자세히 알아보기: CPen 클래스'
title: CPen 클래스
ms.date: 11/04/2016
f1_keywords:
- CPen
- AFXWIN/CPen
- AFXWIN/CPen::CPen
- AFXWIN/CPen::CreatePen
- AFXWIN/CPen::CreatePenIndirect
- AFXWIN/CPen::FromHandle
- AFXWIN/CPen::GetExtLogPen
- AFXWIN/CPen::GetLogPen
helpviewer_keywords:
- CPen [MFC], CPen
- CPen [MFC], CreatePen
- CPen [MFC], CreatePenIndirect
- CPen [MFC], FromHandle
- CPen [MFC], GetExtLogPen
- CPen [MFC], GetLogPen
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
ms.openlocfilehash: b85e0de8a5ce9048851b3f0a8ee5a701e749f0af
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97345149"
---
# <a name="cpen-class"></a>CPen 클래스

Windows GDI(그래픽 디바이스 인터페이스) 펜을 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CPen : public CGdiObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPen:: CPen](#cpen)|`CPen` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPen:: CreatePen](#createpen)|지정 된 스타일, 너비 및 브러시 특성을 사용 하 여 논리적 코스메틱 또는 기하학적 펜을 만든 다음 개체에 연결 `CPen` 합니다.|
|[CPen:: CreatePenIndirect](#createpenindirect)|[Logpen](/windows/win32/api/wingdi/ns-wingdi-logpen) 구조에 지정 된 스타일, 너비 및 색을 사용 하 여 펜을 만들고 개체에 연결 `CPen` 합니다.|
|[CPen:: FromHandle](#fromhandle)|`CPen`Windows HPEN이 지정 된 경우 개체에 대 한 포인터를 반환 합니다.|
|[CPen:: GetExtLogPen](#getextlogpen)|[Extlogpen](/windows/win32/api/wingdi/ns-wingdi-extlogpen) 의 내부 구조를 가져옵니다.|
|[CPen:: GetLogPen](#getlogpen)|[Logpen](/windows/win32/api/wingdi/ns-wingdi-logpen) 의 내부 구조를 가져옵니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CPen:: operator HPEN](#operator_hpen)|개체에 연결 된 Windows 핸들을 반환 합니다 `CPen` .|

## <a name="remarks"></a>설명

사용에 대 한 자세한 내용은 `CPen` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CPen`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cpencpen"></a><a name="cpen"></a> CPen:: CPen

`CPen` 개체를 생성합니다.

```
CPen();

CPen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

CPen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*nPenStyle*<br/>
펜 스타일을 지정 합니다. 생성자의 첫 번째 버전에 있는이 매개 변수는 다음 값 중 하나일 수 있습니다.

- PS_SOLID 단색 펜을 만듭니다.

- PS_DASH 파선 펜을 만듭니다. 장치 단위에서 펜 너비가 1 이하인 경우에만 유효 합니다.

- PS_DOT는 점으로 구분 된 펜을 만듭니다. 장치 단위에서 펜 너비가 1 이하인 경우에만 유효 합니다.

- PS_DASHDOT 대시와 점이 교대로 반복 되는 펜을 만듭니다. 장치 단위에서 펜 너비가 1 이하인 경우에만 유효 합니다.

- PS_DASHDOTDOT 대시와 이중 점이 교대로 반복 되는 펜을 만듭니다. 장치 단위에서 펜 너비가 1 이하인 경우에만 유효 합니다.

- PS_NULL은 NULL 펜을 만듭니다.

- PS_INSIDEFRAME 경계 사각형 (예:,,, `Ellipse` `Rectangle` `RoundRect` `Pie` 및 `Chord` 멤버 함수)을 지정 하는 Windows GDI 출력 함수에서 생성 된 닫힌 모양의 프레임 안에 선을 그리는 펜을 만듭니다. 이 스타일이 경계 사각형을 지정 하지 않는 Windows GDI 출력 함수 (예: 멤버 함수)와 함께 사용 되는 경우 `LineTo` 펜의 그리기 영역은 프레임으로 제한 되지 않습니다.

생성자의 두 번째 버전은 `CPen` 형식, 스타일, 끝 캡 및 조인 특성의 조합을 지정 합니다. 비트 OR 연산자 (&#124;)를 사용 하 여 각 범주의 값을 결합 해야 합니다. 펜 종류는 다음 값 중 하나일 수 있습니다.

- PS_GEOMETRIC 기하학적 펜을 만듭니다.

- PS_COSMETIC는 코스메틱 펜을 만듭니다.

   생성자의 두 번째 버전은 `CPen` *nPenStyle* 에 대해 다음 펜 스타일을 추가 합니다.

- PS_ALTERNATE 다른 모든 픽셀을 설정 하는 펜을 만듭니다. 이 스타일은 코스메틱 펜에만 적용 됩니다.

- PS_USERSTYLE 사용자가 제공한 스타일 지정 배열을 사용 하는 펜을 만듭니다.

   끝 캡은 다음 값 중 하나일 수 있습니다.

- PS_ENDCAP_ROUND 끝 캡은 ROUND입니다.

- PS_ENDCAP_SQUARE 끝 캡은 사각형입니다.

- PS_ENDCAP_FLAT End 캡은 평평 합니다.

   조인은 다음 값 중 하나일 수 있습니다.

- PS_JOIN_BEVEL 조인은 경사진입니다.

- PS_JOIN_MITER 조인은 [SetMiterLimit](/windows/win32/api/wingdi/nf-wingdi-setmiterlimit) 함수에 의해 설정 된 현재 제한 내에 있을 때 마이터 됩니다. 조인이이 제한을 초과 하면 빗면이 됩니다.

- PS_JOIN_ROUND 조인은 반올림입니다.

*nWidth*<br/>
펜의 너비를 지정 합니다.

- 생성자의 첫 번째 버전의 경우이 값이 0 이면 매핑 모드에 관계 없이 장치 단위의 너비가 항상 1 픽셀입니다.

- 생성자의 두 번째 버전에서는 *nPenStyle* 가 PS_GEOMETRIC 경우 너비가 논리 단위로 제공 됩니다. *NPenStyle* 가 PS_COSMETIC 경우 너비를 1로 설정 해야 합니다.

*crColor*<br/>
펜의 RGB 색을 포함 합니다.

*pLogBrush*<br/>
는 구조체를 가리킵니다 `LOGBRUSH` . *NPenStyle* 가 PS_COSMETIC 되는 경우 구조체의 *lbColor* 멤버는 `LOGBRUSH` 펜의 색을 지정 하 고 구조체의 *lbStyle* 멤버를 `LOGBRUSH` BS_SOLID으로 설정 해야 합니다. *NPenStyle* 가 PS_GEOMETRIC 경우 모든 멤버를 사용 하 여 펜의 브러시 특성을 지정 해야 합니다.

*nStyleCount*<br/>
*Lpstyle* 배열의 길이를 더블 워드 단위로 지정 합니다. *NPenStyle* 가 PS_USERSTYLE 되지 않은 경우이 값은 0 이어야 합니다.

*lpStyle*<br/>
는 더블 워드 값의 배열을 가리킵니다. 첫 번째 값은 사용자 정의 스타일에서 첫 번째 대시의 길이를 지정 하 고, 두 번째 값은 첫 번째 공백의 길이를 지정 하는 식입니다. *NPenStyle* 가 PS_USERSTYLE 되지 않은 경우이 포인터는 NULL 이어야 합니다.

### <a name="remarks"></a>설명

인수 없이 생성자를 사용 하는 경우 `CPen` `CreatePen` , `CreatePenIndirect` 또는 `CreateStockObject` 멤버 함수를 사용 하 여 결과 개체를 초기화 해야 합니다.

인수를 사용 하는 생성자를 사용 하는 경우에는 더 이상 초기화할 필요가 없습니다. 인수가 있는 생성자는 오류가 발생 하는 경우 예외를 throw 할 수 있지만 인수가 없는 생성자는 항상 성공 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#99](../../mfc/codesnippet/cpp/cpen-class_1.cpp)]

## <a name="cpencreatepen"></a><a name="createpen"></a> CPen:: CreatePen

지정 된 스타일, 너비 및 브러시 특성을 사용 하 여 논리적 코스메틱 또는 기하학적 펜을 만든 다음 개체에 연결 `CPen` 합니다.

```
BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    COLORREF crColor);

BOOL CreatePen(
    int nPenStyle,
    int nWidth,
    const LOGBRUSH* pLogBrush,
    int nStyleCount = 0,
    const DWORD* lpStyle = NULL);
```

### <a name="parameters"></a>매개 변수

*nPenStyle*<br/>
펜의 스타일을 지정 합니다. 가능한 값 목록은 [Cpen](#cpen) 생성자에서 *nPenStyle* 매개 변수를 참조 하세요.

*nWidth*<br/>
펜의 너비를 지정 합니다.

- 첫 번째 버전의 경우 `CreatePen` 이 값이 0 이면 매핑 모드에 관계 없이 장치 단위의 너비가 항상 1 픽셀입니다.

- 두 번째 버전의에서는 `CreatePen` *nPenStyle* 가 PS_GEOMETRIC 경우 너비가 논리 단위로 지정 됩니다. *NPenStyle* 가 PS_COSMETIC 경우 너비를 1로 설정 해야 합니다.

*crColor*<br/>
펜의 RGB 색을 포함 합니다.

*pLogBrush*<br/>
[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) 구조체를 가리킵니다. *NPenStyle* 가 PS_COSMETIC 경우 구조체의 `lbColor` 멤버는 `LOGBRUSH` 펜의 색을 지정 하 고 구조체의 *lbStyle* 멤버를 `LOGBRUSH` BS_SOLID로 설정 해야 합니다. NPenStyle가 PS_GEOMETRIC 경우 모든 멤버를 사용 하 여 펜의 브러시 특성을 지정 해야 합니다.

*nStyleCount*<br/>
*Lpstyle* 배열의 길이를 더블 워드 단위로 지정 합니다. *NPenStyle* 가 PS_USERSTYLE 되지 않은 경우이 값은 0 이어야 합니다.

*lpStyle*<br/>
는 더블 워드 값의 배열을 가리킵니다. 첫 번째 값은 사용자 정의 스타일에서 첫 번째 대시의 길이를 지정 하 고, 두 번째 값은 첫 번째 공백의 길이를 지정 하는 식입니다. *NPenStyle* 가 PS_USERSTYLE 되지 않은 경우이 포인터는 NULL 이어야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 0이 아닌 값이 고, 메서드가 실패 하면 0입니다.

### <a name="remarks"></a>설명

의 첫 번째 버전은 `CreatePen` 지정 된 스타일, 너비 및 색을 사용 하 여 펜을 초기화 합니다. 이후에 모든 장치 컨텍스트의 현재 펜으로 펜을 선택할 수 있습니다.

너비가 1 픽셀 보다 큰 펜은 항상 PS_NULL, PS_SOLID 또는 PS_INSIDEFRAME 스타일을 포함 해야 합니다.

펜에 PS_INSIDEFRAME 스타일이 있고 논리적 색 테이블의 색과 일치 하지 않는 색이 있는 경우에는 디더링된 색으로 펜이 그려집니다. PS_SOLID 펜 스타일은 디더링된 색으로 펜을 만드는 데 사용할 수 없습니다. 펜 너비가 1 보다 작거나 같으면 스타일 PS_INSIDEFRAME PS_SOLID와 동일 합니다.

의 두 번째 버전은 `CreatePen` 지정 된 스타일, 너비 및 브러시 특성을 가진 논리적 코스메틱 또는 기하학적 펜을 초기화 합니다. 코스메틱 펜의 너비는 항상 1입니다. 기하학적 펜의 너비는 항상 세계 단위로 지정 됩니다. 응용 프로그램에서 논리적 펜을 만든 후 [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) 함수를 호출 하 여 해당 펜을 장치 컨텍스트로 선택할 수 있습니다. 장치 컨텍스트에 펜을 선택한 후 선과 곡선을 그리는 데 사용할 수 있습니다.

- *NPenStyle* 가 PS_COSMETIC 되 고 PS_USERSTYLE 경우 *lpstyle* 배열의 항목은 스타일 단위의 대시 및 공백을 지정 합니다. 스타일 단위는 펜을 사용 하 여 선을 그리는 장치에서 정의 합니다.

- *NPenStyle* 가 PS_GEOMETRIC 되 고 PS_USERSTYLE 경우 *lpstyle* 배열의 항목은 논리 단위에서 대시 및 공백의 길이를 지정 합니다.

- *NPenStyle* 가 PS_ALTERNATE 경우 스타일 단위는 무시 되 고 다른 모든 픽셀은 설정 됩니다.

응용 프로그램에 지정 된 펜이 더 이상 필요 하지 않은 경우 [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) 멤버 함수를 호출 하거나 `CPen` 리소스를 더 이상 사용 하지 않도록 개체를 삭제 해야 합니다. 장치 컨텍스트에서 펜을 선택 하면 응용 프로그램에서 펜을 삭제 하면 안 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#100](../../mfc/codesnippet/cpp/cpen-class_2.cpp)]

## <a name="cpencreatepenindirect"></a><a name="createpenindirect"></a> CPen:: CreatePenIndirect

*LpLogPen* 가 가리키는 구조체에 지정 된 스타일, 너비 및 색을 가진 펜을 초기화 합니다.

```
BOOL CreatePenIndirect(LPLOGPEN lpLogPen);
```

### <a name="parameters"></a>매개 변수

*lpLogPen*<br/>
펜에 대 한 정보를 포함 하는 Windows [Logpen](/windows/win32/api/Wingdi/ns-wingdi-logpen) 구조를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

너비가 1 픽셀 보다 큰 펜은 항상 PS_NULL, PS_SOLID 또는 PS_INSIDEFRAME 스타일을 포함 해야 합니다.

펜에 PS_INSIDEFRAME 스타일이 있고 논리적 색 테이블의 색과 일치 하지 않는 색이 있는 경우에는 디더링된 색으로 펜이 그려집니다. 펜 너비가 1 보다 작거나 같으면 PS_INSIDEFRAME 스타일이 PS_SOLID와 동일 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#101](../../mfc/codesnippet/cpp/cpen-class_3.cpp)]

## <a name="cpenfromhandle"></a><a name="fromhandle"></a> CPen:: FromHandle

`CPen`WINDOWS GDI 펜 개체에 대 한 핸들을 지정 하 여 개체에 대 한 포인터를 반환 합니다.

```
static CPen* PASCAL FromHandle(HPEN hPen);
```

### <a name="parameters"></a>매개 변수

*hPen*<br/>
`HPEN` Windows GDI 펜에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CPen` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`CPen` 개체가 핸들에 연결되지 않은 경우 임시 `CPen` 개체를 만들어 연결합니다. 이 임시 `CPen` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과 하 여 모든 임시 그래픽 개체가 삭제 될 때 까지만 유효 합니다. 즉, 임시 개체는 하나의 창 메시지를 처리 하는 동안에만 유효 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#105](../../mfc/codesnippet/cpp/cpen-class_4.cpp)]

## <a name="cpengetextlogpen"></a><a name="getextlogpen"></a> CPen:: GetExtLogPen

`EXTLOGPEN`내부 구조를 가져옵니다.

```
int GetExtLogPen(EXTLOGPEN* pLogPen);
```

### <a name="parameters"></a>매개 변수

*pLogPen*<br/>
펜에 대 한 정보를 포함 하는 [Extlogpen](/windows/win32/api/wingdi/ns-wingdi-extlogpen) 구조를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`EXTLOGPEN`구조체는 펜의 스타일, 너비 및 브러시 특성을 정의 합니다. 예를 들어 `GetExtLogPen` 를 호출 하 여 펜의 특정 스타일과 일치 합니다.

펜 특성에 대 한 자세한 내용은 Windows SDK의 다음 항목을 참조 하세요.

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [EXTLOGPEN](/windows/win32/api/wingdi/ns-wingdi-extlogpen)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

- [ExtCreatePen](/windows/win32/api/wingdi/nf-wingdi-extcreatepen)

### <a name="example"></a>예제

다음 코드 예제에서는를 호출 `GetExtLogPen` 하 여 펜의 특성을 검색 한 다음 동일한 색으로 새 코스메틱 펜을 만드는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#102](../../mfc/codesnippet/cpp/cpen-class_5.cpp)]

## <a name="cpengetlogpen"></a><a name="getlogpen"></a> CPen:: GetLogPen

`LOGPEN`내부 구조를 가져옵니다.

```
int GetLogPen(LOGPEN* pLogPen);
```

### <a name="parameters"></a>매개 변수

*pLogPen*<br/>
펜에 대 한 정보를 포함 하는 [logpen](/windows/win32/api/wingdi/ns-wingdi-logpen) 구조를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`LOGPEN`구조체는 펜의 스타일, 색 및 패턴을 정의 합니다.

예를 들어 `GetLogPen` 를 호출 하 여 펜의 특정 스타일과 일치 합니다.

펜 특성에 대 한 자세한 내용은 Windows SDK의 다음 항목을 참조 하세요.

- [GetObject](/windows/win32/api/wingdi/nf-wingdi-getobject)

- [LOGPEN](/windows/win32/api/wingdi/ns-wingdi-logpen)

### <a name="example"></a>예제

다음 코드 예제에서는를 호출 `GetLogPen` 하 여 펜 문자를 검색 한 다음 동일한 색을 사용 하 여 새 단색 펜을 만드는 방법을 보여 줍니다.

[!code-cpp[NVC_MFCDocView#103](../../mfc/codesnippet/cpp/cpen-class_6.cpp)]

## <a name="cpenoperator-hpen"></a><a name="operator_hpen"></a> CPen:: operator HPEN

개체의 연결 된 Windows GDI 핸들을 가져옵니다 `CPen` .

```
operator HPEN() const;
```

### <a name="return-value"></a>반환 값

성공 하면 개체가 나타내는 Windows GDI 개체에 대 한 핸들이 고, `CPen` 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 연산자는 HPEN 개체의 직접 사용을 지 원하는 캐스팅 연산자입니다.

그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [그래픽 개체](/windows/win32/gdi/graphic-objects) 문서를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#104](../../mfc/codesnippet/cpp/cpen-class_7.cpp)]

## <a name="see-also"></a>참고 항목

[CGdiObject 클래스](../../mfc/reference/cgdiobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CBrush 클래스](../../mfc/reference/cbrush-class.md)
