---
description: '자세히 알아보기: CBrush 클래스'
title: CBrush 클래스
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: 7787d35eb96e3c7767855a13064cfe2f381addb1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97122670"
---
# <a name="cbrush-class"></a>CBrush 클래스

Windows GDI(그래픽 디바이스 인터페이스) 브러시를 캡슐화합니다.

## <a name="syntax"></a>구문

```
class CBrush : public CGdiObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|`CBrush` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) 구조체에 지정 된 스타일, 색 및 패턴으로 브러시를 초기화 합니다.|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|DIB (장치 독립적 비트맵)로 지정 된 패턴을 사용 하 여 브러시를 초기화 합니다.|
|[CBrush:: CreateHatchBrush](#createhatchbrush)|지정 된 해치 패턴 및 색을 사용 하 여 브러시를 초기화 합니다.|
|[CBrush:: CreatePatternBrush](#createpatternbrush)|비트맵으로 지정 된 패턴을 사용 하 여 브러시를 초기화 합니다.|
|[CBrush:: CreateSolidBrush](#createsolidbrush)|지정 된 단색으로 브러시를 초기화 합니다.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|기본 시스템 색의 브러시를 만듭니다.|
|[CBrush:: FromHandle](#fromhandle)|`CBrush`Windows 개체에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 `HBRUSH` 합니다.|
|[CBrush::GetLogBrush](#getlogbrush)|[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) 구조체를 가져옵니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CBrush:: operator HBRUSH](#operator_hbrush)|개체에 연결 된 Windows 핸들을 반환 합니다 `CBrush` .|

## <a name="remarks"></a>설명

개체를 사용 하려면 `CBrush` 개체를 생성 하 `CBrush` 고 `CDC` 브러시를 필요로 하는 멤버 함수에 전달 합니다.

브러시는 단색, 빗금 또는 패턴화 될 수 있습니다.

에 대 한 자세한 내용은 `CBrush` [그래픽 개체](../../mfc/graphic-objects.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>요구 사항

**헤더:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a> CBrush:: CBrush

`CBrush` 개체를 생성합니다.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>매개 변수

*crColor*<br/>
브러시의 전경색을 RGB 색으로 지정 합니다. 브러시가 해치 이면이 매개 변수는 해칭 색을 지정 합니다.

*nIndex*<br/>
브러시의 빗살 무늬 스타일을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- HS_BDIAGONAL 하향 해치 (왼쪽에서 오른쪽)를 45도로

- HS_CROSS 가로 및 세로 교차 무늬

- 45도에서 교차 하는 HS_DIAGCROSS

- HS_FDIAGONAL 위쪽 해치 (왼쪽에서 오른쪽)를 45도로

- HS_HORIZONTAL 가로 해치

- HS_VERTICAL 세로 해치

*pBitmap*<br/>
`CBitmap`브러시가 그리는 데 사용 되는 비트맵을 지정 하는 개체를 가리킵니다.

### <a name="remarks"></a>설명

`CBrush` 에는 네 개의 오버 로드 된 생성자가 있습니다. 인수가 없는 생성자는 초기화 되지 않은 개체를 생성 한 후에 `CBrush` 사용할 수 있습니다.

인수 없이 생성자를 사용 하는 경우 `CBrush` [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)또는 [CreateDIBPatternBrush](#createdibpatternbrush)를 사용 하 여 결과 개체를 초기화 해야 합니다. 인수를 사용 하는 생성자 중 하나를 사용 하는 경우 추가 초기화가 필요 하지 않습니다. 인수가 있는 생성자는 오류가 발생 하는 경우 예외를 throw 할 수 있지만 인수가 없는 생성자는 항상 성공 합니다.

단일 [Colorref](/windows/win32/gdi/colorref) 매개 변수가 있는 생성자는 지정 된 색을 사용 하 여 단색 브러시를 생성 합니다. 색은 RGB 값을 지정 하며, WINDOWS의 RGB 매크로를 사용 하 여 생성할 수 있습니다.

두 매개 변수가 있는 생성자는 빗살 무늬 브러시를 생성 합니다. *Nindex* 매개 변수는 해치 패턴의 인덱스를 지정 합니다. *Crcolor* 매개 변수는 색을 지정 합니다.

매개 변수가 있는 생성자는 `CBitmap` 패턴화 된 브러시를 생성 합니다. 매개 변수는 비트맵을 식별 합니다. 비트맵은 [cbitmap:: createbitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [Cbitmap:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [cbitmap:: loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)또는 [cbitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)를 사용 하 여 생성 된 것으로 간주 됩니다. 채우기 패턴에서 사용할 비트맵의 최소 크기는 8 픽셀입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a> CBrush:: CreateBrushIndirect

[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) 구조체에 지정 된 스타일, 색 및 패턴으로 브러시를 초기화 합니다.

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>매개 변수

*lpLogBrush*<br/>
브러시에 대 한 정보를 포함 하는 [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에 브러시를 모든 장치 컨텍스트의 현재 브러시로 선택할 수 있습니다.

단색 (1 평면, 픽셀당 1 비트) 비트맵을 사용 하 여 만든 브러시는 현재 텍스트 및 배경색을 사용 하 여 그려집니다. 비트가 0으로 설정 되어 표시 되는 픽셀은 현재 텍스트 색을 사용 하 여 그려집니다. 1로 설정 된 비트가 나타내는 픽셀은 현재 배경색으로 그려집니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a> CBrush:: CreateDIBPatternBrush

DIB (장치 독립적 비트맵)로 지정 된 패턴을 사용 하 여 브러시를 초기화 합니다.

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>매개 변수

*hPackedDIB*<br/>
압축 된 DIB (장치 독립적 비트맵)를 포함 하는 전역 메모리 개체를 식별 합니다.

*nUsage*<br/>
[BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) 데이터 구조의 `bmiColors[]` 필드 ("압축 된 DIB"의 일부)에 명시적 RGB 값이나 인덱스가 현재 인식되는 논리 색상표에 포함되는지 여부를 지정합니다. 매개 변수는 다음 값 중 하나 여야 합니다.

- 색 테이블은 16 비트 인덱스 배열로 구성 됩니다 DIB_PAL_COLORS 합니다.

- 색상표 DIB_RGB_COLORS 리터럴 RGB 값을 포함 합니다.

*lpPackedDIB*<br/>
`BITMAPINFO`바로 뒤에 비트맵의 픽셀을 정의 하는 바이트 배열로 구성 된 압축 된 DIB를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에는 래스터 작업을 지 원하는 모든 장치 컨텍스트에 브러시를 선택할 수 있습니다.

두 버전은 DIB를 처리 하는 방식에 따라 다릅니다.

- 첫 번째 버전에서 DIB에 대 한 핸들을 가져오려면 Windows 함수를 호출 하 여 `GlobalAlloc` 전역 메모리 블록을 할당 한 다음 압축 된 DIB로 메모리를 채웁니다.

- 두 번째 버전에서는를 호출 하 여 `GlobalAlloc` 압축 된 DIB에 대해 메모리를 할당할 필요가 없습니다.

압축 된 DIB는 `BITMAPINFO` 비트맵의 픽셀을 정의 하는 바이트 배열이 바로 뒤에 오는 데이터 구조로 구성 됩니다. 채우기 패턴으로 사용 되는 비트맵은 8 픽셀 x 픽셀 이어야 합니다. 비트맵이 큰 경우 Windows는 비트맵의 왼쪽 위 모퉁이에 있는 처음 8 개 행과 8 열 픽셀에 해당 하는 비트만 사용 하 여 채우기 패턴을 만듭니다.

응용 프로그램에서 단색 장치 컨텍스트로 2 색 DIB 패턴 브러시를 선택 하면 Windows에서 DIB에 지정 된 색을 무시 하 고 대신 장치 컨텍스트의 현재 텍스트와 배경색을 사용 하 여 패턴 브러시를 표시 합니다. 텍스트 색을 사용 하 여 DIB의 첫 번째 색 (DIB 색 테이블의 오프셋 0)에 매핑되는 픽셀을 표시 합니다. 배경색을 사용 하 여 두 번째 색으로 매핑되는 픽셀 (색 테이블의 오프셋 1)이 표시 됩니다.

다음 Windows 함수를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (이 함수는 3.0 이전 버전의 Windows 용으로 작성 된 응용 프로그램과의 호환성을 위해서만 제공 됩니다 `CreateDIBPatternBrushPt` . 함수를 사용 하십시오.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (이 함수는 Win32 기반 응용 프로그램에 사용 해야 합니다.)

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a> CBrush:: CreateHatchBrush

지정 된 해치 패턴 및 색을 사용 하 여 브러시를 초기화 합니다.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
브러시의 빗살 무늬 스타일을 지정 합니다. 다음 값 중 하나일 수 있습니다.

- HS_BDIAGONAL 하향 해치 (왼쪽에서 오른쪽)를 45도로

- HS_CROSS 가로 및 세로 교차 무늬

- 45도에서 교차 하는 HS_DIAGCROSS

- HS_FDIAGONAL 위쪽 해치 (왼쪽에서 오른쪽)를 45도로

- HS_HORIZONTAL 가로 해치

- HS_VERTICAL 세로 해치

*crColor*<br/>
브러시의 전경색을 RGB 색 (해치 색)으로 지정 합니다. 자세한 내용은 Windows SDK의 [Colorref](/windows/win32/gdi/colorref) 를 참조 하세요.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에 브러시를 모든 장치 컨텍스트의 현재 브러시로 선택할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a> CBrush:: CreatePatternBrush

비트맵으로 지정 된 패턴을 사용 하 여 브러시를 초기화 합니다.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>매개 변수

*pBitmap*<br/>
비트맵을 식별 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에는 래스터 작업을 지 원하는 모든 장치 컨텍스트에 브러시를 선택할 수 있습니다. *Pbitmap* 으로 식별 된 비트맵은 일반적으로 [Cbitmap:: createbitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [cbitmap:: CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [Cbitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)또는 [cbitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) 함수를 사용 하 여 초기화 됩니다.

채우기 패턴으로 사용 되는 비트맵은 8 픽셀 x 픽셀 이어야 합니다. 비트맵이 큰 경우 Windows는 비트맵의 왼쪽 위 모퉁이에 있는 처음 8 개 행과 픽셀의 열에 해당 하는 비트만 사용 합니다.

패턴 브러시는 연결 된 비트맵에 영향을 주지 않고 삭제할 수 있습니다. 즉, 비트맵을 사용 하 여 패턴 브러시를 원하는 수 만큼 만들 수 있습니다.

단색 비트맵을 사용 하 여 만든 브러시 (1 개 색 평면, 픽셀당 1 비트)는 현재 텍스트 및 배경색을 사용 하 여 그려집니다. 0으로 설정 된 비트가 나타내는 픽셀은 현재 텍스트 색을 사용 하 여 그려집니다. 1로 설정 된 비트가 나타내는 픽셀은 현재 배경색으로 그려집니다.

Windows 함수인 [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a> CBrush:: CreateSolidBrush

지정 된 단색으로 브러시를 초기화 합니다.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>매개 변수

*crColor*<br/>
브러시의 색을 지정 하는 [Colorref](/windows/win32/gdi/colorref) 구조체입니다. 색은 RGB 값을 지정 하며, WINDOWS의 RGB 매크로를 사용 하 여 생성할 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에 브러시를 모든 장치 컨텍스트의 현재 브러시로 선택할 수 있습니다.

응용 프로그램이에서 만든 브러시를 사용 하 여 완료 되 면 `CreateSolidBrush` 장치 컨텍스트에서 브러시를 선택 해야 합니다.

### <a name="example"></a>예제

  [Cbrush:: cbrush](#cbrush)의 예제를 참조 하세요.

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a> CBrush:: CreateSysColorBrush

브러시 색을 초기화 합니다.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
색 인덱스를 지정 합니다. 이 값은 21 개의 창 요소 중 하나를 칠하는 데 사용 되는 색에 해당 합니다. 값 목록은 Windows SDK의 [Getsyscolor](/windows/win32/api/winuser/nf-winuser-getsyscolor) 를 참조 하십시오.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이후에 브러시를 모든 장치 컨텍스트의 현재 브러시로 선택할 수 있습니다.

응용 프로그램이에서 만든 브러시를 사용 하 여 완료 되 면 `CreateSysColorBrush` 장치 컨텍스트에서 브러시를 선택 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a> CBrush:: FromHandle

`CBrush`Windows [hbrush](#operator_hbrush) 개체에 대 한 핸들을 지정 하면 개체에 대 한 포인터를 반환 합니다.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>매개 변수

*hBrush*<br/>
Windows GDI 브러시에 대 한 핸들입니다.

### <a name="return-value"></a>반환 값

성공 하면 개체에 대 한 포인터 `CBrush` 이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

`CBrush`개체가 핸들에 아직 연결 되지 않은 경우 임시 `CBrush` 개체가 생성 되 고 연결 됩니다. 이 임시 `CBrush` 개체는 다음에 응용 프로그램이 이벤트 루프에서 유휴 시간을 초과할 때 까지만 유효 합니다. 지금은 모든 임시 그래픽 개체가 삭제 됩니다. 즉, 임시 개체는 하나의 창 메시지를 처리 하는 동안에만 유효 합니다.

그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [그래픽 개체](/windows/win32/gdi/graphic-objects) 를 참조 하세요.

### <a name="example"></a>예제

  [Cbrush:: cbrush](#cbrush)의 예제를 참조 하세요.

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a> CBrush:: GetLogBrush

구조체를 검색 하려면이 멤버 함수를 호출 `LOGBRUSH` 합니다.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>매개 변수

*pLogBrush*<br/>
브러시에 대 한 정보를 포함 하는 [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

함수가 성공 하 고 *pLogBrush* 가 유효한 포인터인 경우 반환 값은 버퍼에 저장 된 바이트 수입니다.

함수가 성공 하 고 *pLogBrush* 가 NULL 이면 반환 값은 함수가 버퍼에 저장 하는 정보를 저장 하는 데 필요한 바이트 수입니다.

함수가 실패 하면 반환 값은 0입니다.

### <a name="remarks"></a>설명

`LOGBRUSH`구조체는 브러시의 스타일, 색 및 패턴을 정의 합니다.

예를 들어 `GetLogBrush` 를 호출 하 여 비트맵의 특정 색 또는 패턴을 일치 시킵니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a> CBrush:: operator HBRUSH

이 연산자를 사용 하 여 개체의 연결 된 Windows GDI 핸들을 가져옵니다 `CBrush` .

```
operator HBRUSH() const;
```

### <a name="return-value"></a>반환 값

성공 하면 개체가 나타내는 Windows GDI 개체에 대 한 핸들이 고, `CBrush` 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 연산자는 HBRUSH 개체의 직접 사용을 지 원하는 캐스팅 연산자입니다.

그래픽 개체를 사용 하는 방법에 대 한 자세한 내용은 Windows SDK의 [그래픽 개체](/windows/win32/gdi/graphic-objects) 를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>참고 항목

[MFC 샘플 PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject 클래스](../../mfc/reference/cgdiobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CBitmap 클래스](../../mfc/reference/cbitmap-class.md)<br/>
[CDC 클래스](../../mfc/reference/cdc-class.md)
