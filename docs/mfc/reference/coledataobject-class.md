---
description: '자세히 알아보기: COleDataObject 클래스'
title: COleDataObject 클래스
ms.date: 11/04/2016
f1_keywords:
- COleDataObject
- AFXOLE/COleDataObject
- AFXOLE/COleDataObject::COleDataObject
- AFXOLE/COleDataObject::Attach
- AFXOLE/COleDataObject::AttachClipboard
- AFXOLE/COleDataObject::BeginEnumFormats
- AFXOLE/COleDataObject::Detach
- AFXOLE/COleDataObject::GetData
- AFXOLE/COleDataObject::GetFileData
- AFXOLE/COleDataObject::GetGlobalData
- AFXOLE/COleDataObject::GetNextFormat
- AFXOLE/COleDataObject::IsDataAvailable
- AFXOLE/COleDataObject::Release
helpviewer_keywords:
- COleDataObject [MFC], COleDataObject
- COleDataObject [MFC], Attach
- COleDataObject [MFC], AttachClipboard
- COleDataObject [MFC], BeginEnumFormats
- COleDataObject [MFC], Detach
- COleDataObject [MFC], GetData
- COleDataObject [MFC], GetFileData
- COleDataObject [MFC], GetGlobalData
- COleDataObject [MFC], GetNextFormat
- COleDataObject [MFC], IsDataAvailable
- COleDataObject [MFC], Release
ms.assetid: d1cc84be-2e1c-4bb3-a8a0-565eb08aaa34
ms.openlocfilehash: ae94ed51f3f644efa73847c8e80300ebc5543190
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97227366"
---
# <a name="coledataobject-class"></a>COleDataObject 클래스

끌어 놓기를 통해 클립보드에서 또는 포함된 OLE 항목에서 다양한 형식의 데이터를 검색하기 위해 데이터를 전송하는 데 사용됩니다.

## <a name="syntax"></a>구문

```
class COleDataObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleDataObject:: COleDataObject](#coledataobject)|`COleDataObject` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleDataObject:: Attach](#attach)|지정 된 OLE 데이터 개체를에 연결 `COleDataObject` 합니다.|
|[COleDataObject:: AttachClipboard](#attachclipboard)|클립보드에 있는 데이터 개체를 연결 합니다.|
|[COleDataObject:: BeginEnumFormats](#beginenumformats)|하나 이상의 후속 호출을 준비 `GetNextFormat` 합니다.|
|[COleDataObject::D etach](#detach)|연결 된 개체를 분리 `IDataObject` 합니다.|
|[COleDataObject:: GetData](#getdata)|지정 된 형식의 연결 된 OLE 데이터 개체에서 데이터를 복사 합니다.|
|[COleDataObject:: GetFileData](#getfiledata)|연결 된 OLE 데이터 개체의 데이터를 지정 된 `CFile` 형식의 포인터로 복사 합니다.|
|[COleDataObject:: GetGlobalData](#getglobaldata)|연결 된 OLE 데이터 개체의 데이터를 지정 된 `HGLOBAL` 형식의로 복사 합니다.|
|[COleDataObject:: GetNextFormat](#getnextformat)|사용할 수 있는 다음 데이터 형식을 반환 합니다.|
|[COleDataObject:: IsDataAvailable](#isdataavailable)|지정 된 형식으로 데이터를 사용할 수 있는지 여부를 확인 합니다.|
|[COleDataObject:: Release](#release)|연결 된 개체를 분리 하 고 해제 `IDataObject` 합니다.|

## <a name="remarks"></a>설명

`COleDataObject` 에 기본 클래스가 없습니다.

이러한 종류의 데이터 전송에는 원본 및 대상이 포함 됩니다. 데이터 원본은 [Coledatasource](../../mfc/reference/coledatasource-class.md) 클래스의 개체로 구현 됩니다. 대상 응용 프로그램에 삭제 된 데이터가 있거나 클립보드에서 붙여넣기 작업을 수행 하 라는 메시지가 표시 될 때마다 클래스의 개체를 만들어야 합니다 `COleDataObject` .

이 클래스를 사용 하면 데이터가 지정 된 형식으로 존재 하는지 여부를 확인할 수 있습니다. 사용 가능한 데이터 형식을 열거 하거나 지정 된 형식을 사용할 수 있는지 여부를 확인 한 다음 기본 형식으로 데이터를 검색할 수도 있습니다. 개체 검색은 [CFile](../../mfc/reference/cfile-class.md), HGLOBAL 또는 구조체를 사용 하는 등 여러 가지 방법으로 수행할 수 있습니다 `STGMEDIUM` .

자세한 내용은 Windows SDK [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 참조 하세요.

응용 프로그램에서 데이터 개체를 사용 하는 방법에 대 한 자세한 내용은 [데이터 개체 및 데이터 소스 (OLE)](../../mfc/data-objects-and-data-sources-ole.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`COleDataObject`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="coledataobjectattach"></a><a name="attach"></a> COleDataObject:: Attach

OLE 데이터 개체와 개체를 연결 하려면이 함수를 호출 `COleDataObject` 합니다.

```cpp
void Attach(
    LPDATAOBJECT lpDataObject,
    BOOL bAutoRelease = TRUE);
```

### <a name="parameters"></a>매개 변수

*lpDataObject*<br/>
OLE 데이터 개체를 가리킵니다.

*bAutoRelease*<br/>
개체가 소멸 될 때 OLE 데이터 개체를 해제 해야 하면 TRUE `COleDataObject` 이 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 을 참조 하세요.

## <a name="coledataobjectattachclipboard"></a><a name="attachclipboard"></a> COleDataObject:: AttachClipboard

현재 클립보드에 있는 데이터 개체를 개체에 연결 하려면이 함수를 호출 `COleDataObject` 합니다.

```
BOOL AttachClipboard();
```

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 이 함수를 호출 하면이 데이터 개체가 해제 될 때까지 클립보드가 잠깁니다. 데이터 개체는의 소멸자에 릴리스됩니다 `COleDataObject` . 자세한 내용은 Win32 설명서의 [Openclipboard](/windows/win32/api/winuser/nf-winuser-openclipboard) 및 [CloseClipboard](/windows/win32/api/winuser/nf-winuser-closeclipboard) 를 참조 하세요.

## <a name="coledataobjectbeginenumformats"></a><a name="beginenumformats"></a> COleDataObject:: BeginEnumFormats

항목에서 데이터 형식 목록을 검색 하기 위해에 대 한 후속 호출을 준비 하려면이 함수를 호출 `GetNextFormat` 합니다.

```cpp
void BeginEnumFormats();
```

### <a name="remarks"></a>설명

를 호출한 후 `BeginEnumFormats` 이 데이터 개체에서 지 원하는 첫 번째 형식의 위치가 저장 됩니다. 에 대 한 후속 호출 `GetNextFormat` 에서는 데이터 개체에서 사용 가능한 형식의 목록을 열거 합니다.

지정 된 형식의 데이터 사용 가능 여부를 확인 하려면 [Coledataobject:: IsDataAvailable](#isdataavailable)를 사용 합니다.

자세한 내용은 Windows SDK에서 [IDataObject:: enumformatetc 메서드의](/windows/win32/api/objidl/nf-objidl-idataobject-enumformatetc) 를 참조 하세요.

## <a name="coledataobjectcoledataobject"></a><a name="coledataobject"></a> COleDataObject:: COleDataObject

`COleDataObject` 개체를 생성합니다.

```
COleDataObject();
```

### <a name="remarks"></a>설명

다른 함수를 호출 하기 전에 [Coledataobject:: Attach](#attach) 또는 [Coledataobject:: AttachClipboard](#attachclipboard) 를 호출 해야 합니다 `COleDataObject` .

> [!NOTE]
> 끌어서 놓기 처리기에 대 한 매개 변수 중 하나가에 대 한 포인터 이므로 `COleDataObject` 끌어서 놓기를 지원 하기 위해이 생성자를 호출할 필요가 없습니다.

## <a name="coledataobjectdetach"></a><a name="detach"></a> COleDataObject::D etach

`COleDataObject`데이터 개체를 해제 하지 않고 연결 된 OLE 데이터 개체에서 개체를 분리 하려면이 함수를 호출 합니다.

```
LPDATAOBJECT Detach();
```

### <a name="return-value"></a>반환 값

분리 된 OLE 데이터 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

## <a name="coledataobjectgetdata"></a><a name="getdata"></a> COleDataObject:: GetData

지정 된 형식의 항목에서 데이터를 검색 하려면이 함수를 호출 합니다.

```
BOOL GetData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터가 반환 되는 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpStgMedium*<br/>
데이터를 수신 하는 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1) 구조체를 가리킵니다.

*lpFormatEtc*<br/>
데이터가 반환 되는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. NULL 인 경우 기본값은 구조체의 다른 필드에 사용 됩니다 `FORMATETC` .

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata), [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium-r1)및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 를 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledataobjectgetfiledata"></a><a name="getfiledata"></a> COleDataObject:: GetFileData

`CFile`또는 파생 개체를 만들고 지정 된 형식의 데이터를 포인터로 검색 하려면이 함수를 호출 `CFile` `CFile` 합니다.

```
CFile* GetFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터가 반환 되는 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpFormatEtc*<br/>
데이터가 반환 되는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. NULL 인 경우 기본값은 구조체의 다른 필드에 사용 됩니다 `FORMATETC` .

### <a name="return-value"></a>반환 값

`CFile` `CFile` 성공 하면 데이터를 포함 하는 새 또는 파생 개체에 대 한 포인터이 고, 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

데이터가 저장 되는 미디어에 따라 반환 값이 가리키는 실제 형식은, 또는 일 수 있습니다 `CFile` `CSharedFile` `COleStreamFile` .

> [!NOTE]
> `CFile`이 함수의 반환 값으로 액세스 되는 개체는 호출자가 소유 합니다. 호출자가 개체를 담당 하므로 파일을 **`delete`** `CFile` 닫습니다.

자세한 내용은 Windows SDK에서 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 을 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledataobjectgetglobaldata"></a><a name="getglobaldata"></a> COleDataObject:: GetGlobalData

이 함수를 호출 하 여 전역 메모리 블록을 할당 하 고 지정 된 형식의 데이터를 HGLOBAL에 검색 합니다.

```
HGLOBAL GetGlobalData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
데이터가 반환 되는 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpFormatEtc*<br/>
데이터가 반환 되는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려면이 매개 변수에 대 한 값을 제공 합니다. NULL 인 경우 기본값은 구조체의 다른 필드에 사용 됩니다 `FORMATETC` .

### <a name="return-value"></a>반환 값

성공 하는 경우 데이터를 포함 하는 전역 메모리 블록의 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK에서 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 을 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

## <a name="coledataobjectgetnextformat"></a><a name="getnextformat"></a> COleDataObject:: GetNextFormat

항목에서 데이터를 검색 하는 데 사용할 수 있는 모든 형식을 가져오려면이 함수를 반복적으로 호출 합니다.

```
BOOL GetNextFormat(LPFORMATETC lpFormatEtc);
```

### <a name="parameters"></a>매개 변수

*lpFormatEtc*<br/>
함수 호출이 반환 될 때 형식 정보를 받는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조체를 가리킵니다.

### <a name="return-value"></a>반환 값

다른 형식을 사용할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[Coledataobject:: BeginEnumFormats](#beginenumformats)를 호출한 후이 데이터 개체에서 지 원하는 첫 번째 형식의 위치가 저장 됩니다. 에 대 한 후속 호출 `GetNextFormat` 에서는 데이터 개체에서 사용 가능한 형식의 목록을 열거 합니다. 이러한 함수를 사용 하 여 사용 가능한 형식을 나열 합니다.

지정 된 형식의 가용성을 확인 하려면 [Coledataobject:: IsDataAvailable](#isdataavailable)를 호출 합니다.

자세한 내용은 Windows SDK의 [IEnumXXXX:: Next (다음](/previous-versions/ms695273\(v=vs.85\)) )를 참조 하세요.

## <a name="coledataobjectisdataavailable"></a><a name="isdataavailable"></a> COleDataObject:: IsDataAvailable

OLE 항목에서 데이터를 검색 하는 데 특정 형식을 사용할 수 있는지 확인 하려면이 함수를 호출 합니다.

```
BOOL IsDataAvailable(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>매개 변수

*cfFormat*<br/>
*LpFormatEtc* 가 가리키는 구조에 사용할 클립보드 데이터 형식입니다. 이 매개 변수는 미리 정의 된 클립보드 형식 또는 네이티브 Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 함수에서 반환 되는 값 중 하나일 수 있습니다.

*lpFormatEtc*<br/>
원하는 형식을 설명 하는 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 구조를 가리킵니다. *Cfformat* 으로 지정 된 클립보드 형식을 벗어나는 추가 형식 정보를 지정 하려는 경우에만이 매개 변수에 대 한 값을 제공 합니다. NULL 인 경우 기본값은 구조체의 다른 필드에 사용 됩니다 `FORMATETC` .

### <a name="return-value"></a>반환 값

지정 된 형식으로 데이터를 사용할 수 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는, 또는를 호출 하기 전에 유용 `GetData` `GetFileData` `GetGlobalData` 합니다.

자세한 내용은 Windows SDK에서 [IDataObject:: QueryGetData](/windows/win32/api/objidl/nf-objidl-idataobject-querygetdata) 및 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 를 참조 하세요.

자세한 내용은 Windows SDK에서 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 을 참조 하세요.

### <a name="example"></a>예제

  [CRichEditView:: QueryAcceptData](../../mfc/reference/cricheditview-class.md#queryacceptdata)의 예제를 참조 하세요.

## <a name="coledataobjectrelease"></a><a name="release"></a> COleDataObject:: Release

이전에 개체와 연결 된 [IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject) 개체의 소유권을 해제 하려면이 함수를 호출 `COleDataObject` 합니다.

```cpp
void Release();
```

### <a name="remarks"></a>설명

는 `IDataObject` `COleDataObject` `Attach` 또는를 `AttachClipboard` 명시적으로 또는 프레임 워크에서 호출 하 여와 연결 되었습니다. 의 *bAutoRelease* 매개 변수가 `Attach` FALSE 이면 `IDataObject` 개체가 해제 되지 않습니다. 이 경우 호출자는 `IDataObject` [IUnknown:: Release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)를 호출 하 여를 해제 해야 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC 샘플 OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[COleDataSource 클래스](../../mfc/reference/coledatasource-class.md)<br/>
[COleClientItem 클래스](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerItem 클래스](../../mfc/reference/coleserveritem-class.md)
