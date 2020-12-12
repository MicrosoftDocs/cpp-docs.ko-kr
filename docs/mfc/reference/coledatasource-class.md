---
description: 다음에 대해 자세히 알아보세요. COleDataSource 클래스
title: COleDataSource 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 1fc6dd8a7df1d8b841c4f95a14c2bd1708c94fd2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227327"
---
# <a name="coledatasource-class"></a>COleDataSource 클래스

애플리케이션이 데이터를 넣어 두었다 클립보드 또는 끌어 놓기 작업과 같은 데이터 전송 작업에서 해당 데이터를 제공하는 캐시의 역할을 합니다.

## <a name="syntax"></a>구문

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDataSource:: COleDataSource](#coledatasource)|`COleDataSource` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDataSource:: CacheData](#cachedata)|구조를 사용 하 여 지정 된 형식의 데이터를 제공 `STGMEDIUM` 합니다.|
|[COleDataSource:: CacheGlobalData](#cacheglobaldata)|HGLOBAL를 사용 하 여 지정 된 형식의 데이터를 제공 합니다.|
|[COleDataSource::D elayRenderData](#delayrenderdata)|지연 렌더링을 사용 하 여 지정 된 형식의 데이터를 제공 합니다.|
|[COleDataSource::D elayRenderFileData](#delayrenderfiledata)|포인터에서 지정 된 형식의 데이터를 제공 `CFile` 합니다.|
|[COleDataSource::D elaySetData](#delaysetdata)|에서 지원 되는 모든 형식에 대해 호출 됩니다 `OnSetData` .|
|[COleDataSource::D oDragDrop](#dodragdrop)|데이터 소스를 사용 하 여 끌어서 놓기 작업을 수행 합니다.|
|[COleDataSource:: Empty](#empty)|`COleDataSource`데이터의 개체를 비웁니다.|
|[COleDataSource:: FlushClipboard](#flushclipboard)|모든 데이터를 클립보드에 렌더링 합니다.|
|[COleDataSource:: GetClipboardOwner](#getclipboardowner)|클립보드에 저장 된 데이터가 여전히 있는지 확인 합니다.|
|[COleDataSource:: OnRenderData](#onrenderdata)|지연 된 렌더링의 일부로 데이터를 검색 합니다.|
|[COleDataSource:: OnRenderFileData](#onrenderfiledata)|지연 된 렌더링의 일부로로 데이터를 검색 `CFile` 합니다.|
|[COleDataSource:: OnRenderGlobalData](#onrenderglobaldata)|지연 된 렌더링의 일부로 HGLOBAL 데이터를 검색 합니다.|
|[COleDataSource:: OnSetData](#onsetdata)|개체의 데이터를 바꾸기 위해 호출 `COleDataSource` 됩니다.|
|[COleDataSource:: SetClipboard](#setclipboard)|개체를 `COleDataSource` 클립보드에 배치 합니다.|

## <a name="remarks"></a>설명

OLE 데이터 원본을 직접 만들 수 있습니다. 또는 [COleClientItem](../../mfc/reference/coleclientitem-class.md) 및 [COleServerItem](../../mfc/reference/coleserveritem-class.md) 클래스는 `CopyToClipboard` 및 멤버 함수에 대 한 응답으로 OLE 데이터 원본을 만듭니다 `DoDragDrop` . 간략 한 설명은 [COleServerItem:: CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) 를 참조 하세요. `OnGetClipboardData`클라이언트 항목 또는 서버 항목 클래스의 멤버 함수를 재정의 하 여 `CopyToClipboard` 또는 멤버 함수에 대해 생성 된 OLE 데이터 원본의 데이터에 클립보드 형식을 추가 합니다 `DoDragDrop` .

전송에 대 한 데이터를 준비 하려는 경우 언제 든 지이 클래스의 개체를 만들고 데이터에 가장 적합 한 방법을 사용 하 여 데이터를 채워야 합니다. 데이터를 데이터 소스에 삽입 하는 방법은 데이터가 즉시 제공 되는지 (즉시 렌더링) 또는 요청 시 (지연 렌더링)에 따라 직접적인 영향을 받습니다. 사용할 클립보드 형식 및 선택적 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 전달 하 여 데이터를 제공 하는 모든 클립보드 형식에 대해 [delayrenderdata](#delayrenderdata)를 호출 합니다.

데이터 원본 및 데이터 전송에 대 한 자세한 내용은 [데이터 개체 및 데이터 원본 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)문서를 참조 하세요. 또한 문서 [클립보드 항목](../../mfc/clipboard.md) 에서는 OLE 클립보드 메커니즘에 대해 설명 합니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coledatasourcecachedata"></a><a name="cachedata"></a> COleDataSource:: CacheData

데이터 전송 작업 중 데이터를 제공 하는 형식을 지정 하려면이 함수를 호출 합니다.

```cpp
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터를 제공할 클립보드 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpStgMedium*<br/>
지정 된 형식의 데이터를 포함 하는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 가리킵니다.

*lpFormatEtc*<br/>
데이터를 제공 하는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. 이 값이 NULL 이면 구조체의 다른 필드에 기본값이 사용 됩니다 `FORMATETC` .

### <a name="remarks"></a>설명

이 함수는 즉시 렌더링을 사용 하 여 데이터를 제공 하므로 데이터를 제공 해야 합니다. 데이터는 필요할 때까지 캐시 됩니다.

[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 사용 하 여 데이터를 제공 합니다. `CacheGlobalData`제공 하는 데이터 양이 HGLOBAL를 사용 하 여 효율적으로 전송할 수 있을 만큼 작은 경우에도 멤버 함수를 사용할 수 있습니다.

의 멤버에 대 `CacheData` `ptd` 한 호출 `lpFormatEtc` 및 *lpStgMedium* 의 내용은 호출자가 아닌 데이터 개체에서 소유 합니다.

지연 렌더링을 사용 하려면 [delayrenderdata](#delayrenderdata) 또는 [delayrenderfiledata](#delayrenderfiledata) 멤버 함수를 호출 합니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

자세한 내용은 Windows SDK [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) and [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 참조 하십시오.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledatasourcecacheglobaldata"></a><a name="cacheglobaldata"></a> COleDataSource:: CacheGlobalData

데이터 전송 작업 중 데이터를 제공 하는 형식을 지정 하려면이 함수를 호출 합니다.

```cpp
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터를 제공할 클립보드 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*hGlobal*<br/>
지정 된 형식의 데이터를 포함 하는 전역 메모리 블록에 대 한 핸들입니다.

*lpFormatEtc*<br/>
데이터를 제공 하는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. 이 값이 NULL 이면 구조체의 다른 필드에 기본값이 사용 됩니다 `FORMATETC` .

### <a name="remarks"></a>설명

이 함수는 즉시 렌더링을 사용 하 여 데이터를 제공 하므로 함수를 호출할 때 데이터를 제공 해야 합니다. 데이터는 필요할 때까지 캐시 됩니다. `CacheData`많은 양의 데이터를 제공 하거나 구조적 저장소 미디어가 필요한 경우 멤버 함수를 사용 합니다.

지연 렌더링을 사용 하려면 [delayrenderdata](#delayrenderdata) 또는 [delayrenderfiledata](#delayrenderfiledata) 멤버 함수를 호출 합니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

자세한 내용은 Windows SDK [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledatasourcecoledatasource"></a><a name="coledatasource"></a> COleDataSource:: COleDataSource

`COleDataSource` 개체를 생성합니다.

```
COleDataSource();
```

## <a name="coledatasourcedelayrenderdata"></a><a name="delayrenderdata"></a> COleDataSource::D elayRenderData

데이터 전송 작업 중 데이터를 제공 하는 형식을 지정 하려면이 함수를 호출 합니다.

```cpp
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터를 제공할 클립보드 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpFormatEtc*<br/>
데이터를 제공 하는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. 이 값이 NULL 이면 구조체의 다른 필드에 기본값이 사용 됩니다 `FORMATETC` .

### <a name="remarks"></a>설명

이 함수는 지연 된 렌더링을 사용 하 여 데이터를 제공 하므로 데이터를 즉시 제공 하지 않습니다. [Onrenderdata](#onrenderdata) 또는 [onrenderglobaldata](#onrenderglobaldata) 멤버 함수를 호출 하 여 데이터를 요청 합니다.

개체를 통해 데이터를 제공 하지 않으려면이 함수를 사용 `CFile` 합니다. 개체를 통해 데이터를 제공 하려는 경우 `CFile` [Delayrenderfiledata](#delayrenderfiledata) 멤버 함수를 호출 합니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

즉시 렌더링을 사용 하려면 [cachedata](#cachedata) 또는 [cacheglobaldata](#cacheglobaldata) 멤버 함수를 호출 합니다.

자세한 내용은 Windows SDK [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledatasourcedelayrenderfiledata"></a><a name="delayrenderfiledata"></a> COleDataSource::D elayRenderFileData

데이터 전송 작업 중 데이터를 제공 하는 형식을 지정 하려면이 함수를 호출 합니다.

```cpp
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터를 제공할 클립보드 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpFormatEtc*<br/>
데이터를 제공 하는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. 이 값이 NULL 이면 구조체의 다른 필드에 기본값이 사용 됩니다 `FORMATETC` .

### <a name="remarks"></a>설명

이 함수는 지연 된 렌더링을 사용 하 여 데이터를 제공 하므로 데이터를 즉시 제공 하지 않습니다. [Onrenderfiledata](#onrenderfiledata) 멤버 함수를 호출 하 여 데이터를 요청 합니다.

개체를 사용 하 여 데이터를 제공 하려는 경우이 함수를 사용 `CFile` 합니다. 개체를 사용 하지 않으려면 `CFile` [Delayrenderdata](#delayrenderdata) 멤버 함수를 호출 합니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

즉시 렌더링을 사용 하려면 [cachedata](#cachedata) 또는 [cacheglobaldata](#cacheglobaldata) 멤버 함수를 호출 합니다.

자세한 내용은 Windows SDK [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledatasourcedelaysetdata"></a><a name="delaysetdata"></a> COleDataSource::D elaySetData

이 함수를 호출 하 여 데이터 소스의 내용 변경을 지원 합니다.

```cpp
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터를 배치할 클립보드 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpFormatEtc*<br/>
데이터를 바꿀 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. 이 값이 NULL 이면 구조체의 다른 필드에 기본값이 사용 됩니다 `FORMATETC` .

### <a name="remarks"></a>설명

이 경우 [Onsetdata](#onsetdata) 는 프레임 워크에서 호출 됩니다. 프레임 워크에서 [COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)의 데이터 원본을 반환 하는 경우에만 사용 됩니다. `DelaySetData`가 호출 되지 않으면 `OnSetData` 함수가 호출 되지 않습니다. `DelaySetData` 지원 되는 각 클립보드 또는 형식에 대해를 호출 해야 합니다 `FORMATETC` .

자세한 내용은 Windows SDK [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledatasourcedodragdrop"></a><a name="dodragdrop"></a> COleDataSource::D oDragDrop

`DoDragDrop`멤버 함수를 호출 하 여이 데이터 원본에 대해 일반적으로 [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown) 처리기에서 끌어서 놓기 작업을 수행 합니다.

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>매개 변수

*dwEffects*<br/>
이 데이터 소스에서 허용 되는 끌어서 놓기 작업입니다. 다음 중 하나 이상이 될 수 있습니다.

- 복사 작업을 수행할 수 DROPEFFECT_COPY.

- DROPEFFECT_MOVE 이동 작업을 수행할 수 있습니다.

- 삭제 된 데이터에서 원래 데이터로의 링크를 설정할 수 DROPEFFECT_LINK.

- DROPEFFECT_SCROLL는 끌기 스크롤 작업이 발생할 수 있음을 나타냅니다.

*lpRectStartDrag*<br/>
끌기가 실제로 시작 되는 위치를 정의 하는 사각형에 대 한 포인터입니다. 자세한 내용은 아래 설명 부분을 참조하십시오.

*pDropSource*<br/>
놓기 소스를 가리킵니다. NULL 이면 [Coledropsource](../../mfc/reference/coledropsource-class.md) 의 기본 구현이 사용 됩니다.

### <a name="return-value"></a>반환 값

끌어서 놓기 작업에 의해 생성 된 삭제 효과입니다. 그렇지 않으면 사용자가 제공 된 사각형을 벗어나기 전에 마우스 단추를 놓았음을 작업을 시작 하지 않을 경우 DROPEFFECT_NONE 합니다.

### <a name="remarks"></a>설명

끌어서 놓기 작업은 즉시 시작 되지 않습니다. 마우스 커서가 *lpRectStartDrag* 로 지정 된 사각형을 벗어날 때까지 또는 지정 된 시간 (밀리초)이 경과 될 때까지 대기 합니다. *LpRectStartDrag* 가 NULL 인 경우 사각형의 크기는 1 픽셀입니다.

지연 시간은 레지스트리 키 설정에 의해 지정 됩니다. [Cwinapp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring) 또는 [Cwinapp:: writeprofilestring](../../mfc/reference/cwinapp-class.md#writeprofileint)를 호출 하 여 지연 시간을 변경할 수 있습니다. 지연 시간을 지정 하지 않으면 기본값인 200 밀리초가 사용 됩니다. 끌기 지연 시간은 다음과 같이 저장 됩니다.

- Windows NT 끌어서 지연 시간은 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini \Windows\DragDelay.에 저장 됩니다.

- Windows 2.x 끌어 놓기 지연 시간은 WIN.INI 파일의 [Windows} 섹션 아래에 저장 됩니다.

- Windows 95/98 끌어서 지연 시간은 캐시 된 버전의 WIN.INI에 저장 됩니다.

레지스트리 또는에서 끌어서 지연 정보를 저장 하는 방법에 대 한 자세한 내용 INI 파일 Windows SDK의 [Writeprofilestring](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 을 참조 하십시오.

자세한 내용은 [OLE 끌어서 놓기](../../mfc/drag-and-drop-ole.md)문서를 참조 하세요.

## <a name="coledatasourceempty"></a><a name="empty"></a> COleDataSource:: Empty

데이터 개체를 비우려면이 함수를 호출 합니다 `COleDataSource` .

```cpp
void Empty();
```

### <a name="remarks"></a>설명

캐시 된 및 지연 렌더링 형식이 모두 비워집니다. 다시 사용할 수 있습니다.

자세한 내용은 Windows SDK에서 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 을 참조 하세요.

## <a name="coledatasourceflushclipboard"></a><a name="flushclipboard"></a> COleDataSource:: FlushClipboard

클립보드에 있는 데이터를 렌더링 한 다음 응용 프로그램이 종료 된 후 클립보드의 데이터를 붙여 넣을 수 있습니다.

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>설명

[Setclipboard](#setclipboard) 를 사용 하 여 클립보드에 데이터를 저장 합니다.

## <a name="coledatasourcegetclipboardowner"></a><a name="getclipboardowner"></a> COleDataSource:: GetClipboardOwner

[Setclipboard](#setclipboard) 가 마지막으로 호출 된 이후 클립보드의 데이터가 변경 되었는지 여부를 확인 하 고, 그럴 경우 현재 소유자를 식별 합니다.

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>반환 값

현재 클립보드에 있는 데이터 소스 이거나, 클립보드에 아무 것도 없거나 호출 응용 프로그램에서 클립보드를 소유 하지 않은 경우 NULL입니다.

## <a name="coledatasourceonrenderdata"></a><a name="onrenderdata"></a> COleDataSource:: OnRenderData

지정 된 형식의 데이터를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
정보를 요청 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*lpStgMedium*<br/>
데이터가 반환 되는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 형식은 이전에 `COleDataSource` 지연 렌더링을 위해 [delayrenderdata](#delayrenderdata) 또는 [delayrenderfiledata](#delayrenderfiledata) 멤버 함수를 사용 하 여 개체에 배치 되었습니다. 이 함수의 기본 구현은 제공 된 저장소 미디어가 각각 파일 또는 메모리 일 경우 [Onrenderfiledata](#onrenderfiledata) 또는 [onrenderfiledata](#onrenderglobaldata) 를 호출 합니다. 이러한 형식이 모두 제공 되지 않으면 기본 구현은 0을 반환 하 고 아무 작업도 수행 하지 않습니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

*LpStgMedium* ->  *tymed* 가 TYMED_NULL 경우 `STGMEDIUM` *>lpFormatEtc tymed* 에 지정 된 대로를 할당 하 고 채워야 합니다. TYMED_NULL 되지 않은 경우 `STGMEDIUM` 데이터를 입력 해야 합니다.

이는 고급 재정의 가능입니다. 요청 된 형식 및 중간에 데이터를 제공 하려면이 함수를 재정의 합니다. 데이터에 따라이 함수의 다른 버전 중 하나를 대신 재정의할 수 있습니다. 데이터가 작고 크기가 고정 되어 있으면를 재정의 `OnRenderGlobalData` 합니다. 데이터가 파일에 있거나 가변 크기인 경우를 재정의 `OnRenderFileData` 합니다.

자세한 내용은 Windows SDK에서 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체, [TYMED](/windows/win32/api/objidl/ne-objidl-tymed) 열거형 형식 및 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 를 참조 하세요.

## <a name="coledatasourceonrenderfiledata"></a><a name="onrenderfiledata"></a> COleDataSource:: OnRenderFileData

지정 된 저장 미디어가 파일인 경우 지정 된 형식으로 데이터를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
정보를 요청 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*.Pfile*<br/>
데이터가 렌더링 될 [CFile](../../mfc/reference/cfile-class.md) 개체를 가리킵니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 형식은 이전에 `COleDataSource` 지연 된 렌더링을 위해 [Delayrenderdata](#delayrenderdata) 멤버 함수를 사용 하 여 개체에 배치 되었습니다. 이 함수의 기본 구현은 단순히 FALSE를 반환 합니다.

이는 고급 재정의 가능입니다. 요청 된 형식 및 중간에 데이터를 제공 하려면이 함수를 재정의 합니다. 데이터에 따라이 함수의 다른 버전 중 하나를 대신 재정의 하는 것이 좋습니다. 여러 저장소 미디어를 처리 하려는 경우 [Onrenderdata](#onrenderdata)를 재정의 합니다. 데이터가 파일에 있거나 가변 크기인 경우를 재정의 `OnRenderFileData` 합니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

자세한 내용은 Windows SDK [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) Structure and [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 를 참조 하십시오.

## <a name="coledatasourceonrenderglobaldata"></a><a name="onrenderglobaldata"></a> COleDataSource:: OnRenderGlobalData

지정 된 저장 미디어가 전역 메모리 인 경우 지정 된 형식의 데이터를 검색 하기 위해 프레임 워크에서 호출 됩니다.

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
정보를 요청 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*phGlobal*<br/>
데이터가 반환 될 전역 메모리의 핸들을 가리킵니다. 아직 할당 되지 않은 경우이 매개 변수는 NULL 일 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

지정 된 형식은 이전에 `COleDataSource` 지연 된 렌더링을 위해 [Delayrenderdata](#delayrenderdata) 멤버 함수를 사용 하 여 개체에 배치 되었습니다. 이 함수의 기본 구현은 단순히 FALSE를 반환 합니다.

*Phglobal* 이 NULL 인 경우 새 HGLOBAL을 할당 하 고 *phglobal* 에 반환 해야 합니다. 그렇지 않으면 *Phglobal* 로 지정 된 HGLOBAL 데이터를 채워야 합니다. HGLOBAL에 배치 되는 데이터의 양은 메모리 블록의 현재 크기를 초과 하면 안 됩니다. 또한 블록을 더 큰 크기에 다시 할당할 수 없습니다.

이는 고급 재정의 가능입니다. 요청 된 형식 및 중간에 데이터를 제공 하려면이 함수를 재정의 합니다. 데이터에 따라이 함수의 다른 버전 중 하나를 대신 재정의할 수 있습니다. 여러 저장소 미디어를 처리 하려는 경우 [Onrenderdata](#onrenderdata)를 재정의 합니다. 데이터가 파일에 있거나 가변 크기인 경우 [Onrenderfiledata](#onrenderfiledata)를 재정의 합니다. MFC에서 처리 되는 지연 된 렌더링에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스: 조작](../../mfc/data-objects-and-data-sources-manipulation.md)문서를 참조 하세요.

자세한 내용은 Windows SDK [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) Structure and [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 를 참조 하십시오.

## <a name="coledatasourceonsetdata"></a><a name="onsetdata"></a> COleDataSource:: OnSetData

개체의 데이터를 지정 된 형식으로 설정 하거나 바꾸기 위해 프레임 워크에서 호출 `COleDataSource` 됩니다.

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
데이터를 대체 하는 형식을 지정 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

*lpStgMedium*<br/>
개체의 현재 콘텐츠를 대체할 데이터를 포함 하는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 가리킵니다 `COleDataSource` .

*bRelease*<br/>
함수 호출을 완료 한 후 저장소 미디어의 소유권이 있는 사용자를 나타냅니다. 호출자는 저장소 미디어를 대신해 할당 된 리소스를 해제할 책임이 있는 사용자를 결정 합니다. 호출자가 *bRelease* 를 설정 하 여이를 수행 합니다. *BRelease* 가 0이 아닌 경우 데이터 원본은 소유권을 가지 며 사용이 끝나면 미디어를 해제 합니다. *BRelease* 가 0 이면 호출자가 소유권을 유지 하 고 데이터 소스는 호출 기간 동안만 저장소 미디어를 사용할 수 있습니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

데이터 소스는 데이터를 성공적으로 가져올 때까지 데이터 소유권을 받지 않습니다. 즉,가 0을 반환 하는 경우에는 소유권을 사용 하지 않습니다 `OnSetData` . 데이터 원본에서 소유권을 가져오는 경우 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 함수를 호출 하 여 저장소 미디어를 해제 합니다.

기본 구현은 아무 작업도 수행하지 않습니다. 지정 된 형식의 데이터를 바꾸려면이 함수를 재정의 합니다. 이는 고급 재정의 가능입니다.

자세한 내용은 Windows SDK에서 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체와 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 및 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 함수를 참조 하세요.

## <a name="coledatasourcesetclipboard"></a><a name="setclipboard"></a> COleDataSource:: SetClipboard

`COleDataSource` [Cachedata](#cachedata), [cacheglobaldata](#cacheglobaldata), [Delayrenderdata](#delayrenderdata)또는 [delayrenderfiledata](#delayrenderfiledata)함수 중 하나를 호출한 후 개체에 포함 된 데이터를 클립보드에 넣습니다.

```cpp
void SetClipboard();
```

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget 클래스](../../mfc/reference/ccmdtarget-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject 클래스](../../mfc/reference/coledataobject-class.md)
