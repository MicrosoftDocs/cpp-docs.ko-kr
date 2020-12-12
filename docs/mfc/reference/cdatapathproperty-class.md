---
description: '자세히 알아보기: CDataPathProperty 클래스'
title: CDataPathProperty 클래스
ms.date: 11/04/2016
f1_keywords:
- CDataPathProperty
- AFXCTL/CDataPathProperty
- AFXCTL/CDataPathProperty::CDataPathProperty
- AFXCTL/CDataPathProperty::GetControl
- AFXCTL/CDataPathProperty::GetPath
- AFXCTL/CDataPathProperty::Open
- AFXCTL/CDataPathProperty::ResetData
- AFXCTL/CDataPathProperty::SetControl
- AFXCTL/CDataPathProperty::SetPath
helpviewer_keywords:
- CDataPathProperty [MFC], CDataPathProperty
- CDataPathProperty [MFC], GetControl
- CDataPathProperty [MFC], GetPath
- CDataPathProperty [MFC], Open
- CDataPathProperty [MFC], ResetData
- CDataPathProperty [MFC], SetControl
- CDataPathProperty [MFC], SetPath
ms.assetid: 1f96efdb-54e4-460b-862c-eba5d4103488
ms.openlocfilehash: 7d9ff9f380fd44d5261374879bab63c9925c4442
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247958"
---
# <a name="cdatapathproperty-class"></a>CDataPathProperty 클래스

비동기적으로 로드할 수 있는 OLE 컨트롤 속성을 구현합니다.

## <a name="syntax"></a>구문

```
class CDataPathProperty : public CAsyncMonikerFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDataPathProperty::CDataPathProperty](#cdatapathproperty)|`CDataPathProperty` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDataPathProperty:: GetControl](#getcontrol)|개체와 연결 된 비동기 OLE 컨트롤을 검색 합니다 `CDataPathProperty` .|
|[CDataPathProperty:: GetPath](#getpath)|속성의 경로 이름을 검색 합니다.|
|[CDataPathProperty:: Open](#open)|연결 된 ActiveX (OLE) 컨트롤의 비동기 속성 로드를 시작 합니다.|
|[CDataPathProperty:: ResetData](#resetdata)|`CAsyncMonikerFile::OnDataAvailable`를 호출 하 여 컨트롤 속성이 변경 되었음을 컨테이너에 알립니다.|
|[CDataPathProperty:: SetControl](#setcontrol)|속성과 연결 된 비동기 ActiveX (OLE) 컨트롤을 설정 합니다.|
|[CDataPathProperty:: SetPath](#setpath)|속성의 경로 이름을 설정 합니다.|

## <a name="remarks"></a>설명

비동기 속성은 동기 시작 후에 로드 됩니다.

클래스는 `CDataPathProperty` 에서 파생 됩니다 `CAysncMonikerFile` . OLE 컨트롤에서 비동기 속성을 구현 하려면에서 클래스를 파생 시키고 `CDataPathProperty` [Ondataavailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable)를 재정의 합니다.

인터넷 응용 프로그램에서 비동기 모니커 및 ActiveX 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [인터넷 우선 단계: ActiveX 컨트롤](../../mfc/activex-controls-on-the-internet.md)

- [인터넷 우선 단계: 비동기 모니커](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

`CDataPathProperty`

## <a name="requirements"></a>요구 사항

**헤더:** afxctl

## <a name="cdatapathpropertycdatapathproperty"></a><a name="cdatapathproperty"></a> CDataPathProperty::CDataPathProperty

`CDataPathProperty` 개체를 생성합니다.

```
CDataPathProperty(COleControl* pControl = NULL);
CDataPathProperty(LPCTSTR lpszPath, COleControl* pControl = NULL);
```

### <a name="parameters"></a>매개 변수

*pControl*<br/>
이 개체와 연결 될 OLE 컨트롤 개체에 대 한 포인터 `CDataPathProperty` 입니다.

*lpszPath*<br/>
절대 또는 상대 경로일 수 있는 경로는 속성의 실제 절대 위치를 참조 하는 비동기 모니커를 만드는 데 사용 됩니다. `CDataPathProperty` 파일 이름이 아닌 Url을 사용 합니다. `CDataPathProperty`파일에 대 한 개체를 원하는 경우 경로 앞에를 추가 `file://` 합니다.

### <a name="remarks"></a>설명

`COleControl` *Pcontrol* 이 가리키는 개체는에서 사용 되 `Open` 고 파생 클래스에서 검색 됩니다. *Pcontrol* 이 NULL 이면와 함께 사용 되는 컨트롤을 `Open` 로 설정 해야 합니다 `SetControl` . *LpszPath* 가 NULL 이면 경로를 통해 전달 `Open` 하거나로 설정할 수 있습니다 `SetPath` .

## <a name="cdatapathpropertygetcontrol"></a><a name="getcontrol"></a> CDataPathProperty:: GetControl

이 멤버 함수를 호출 하 여 `COleControl` 개체와 연결 된 개체를 검색 `CDataPathProperty` 합니다.

```
COleControl* GetControl();
```

### <a name="return-value"></a>반환 값

개체와 연결 된 OLE 컨트롤에 대 한 포인터를 반환 합니다 `CDataPathProperty` . 컨트롤이 연결 되어 있지 않으면 NULL입니다.

## <a name="cdatapathpropertygetpath"></a><a name="getpath"></a> CDataPathProperty:: GetPath

이 멤버 함수를 호출 하 여 경로를 검색 하거나, `CDataPathProperty` 개체가 생성 되거나 `Open` , 또는 멤버 함수에 대 한 이전 호출에서 지정 된 경우에 설정 `SetPath` 합니다.

```
CString GetPath() const;
```

### <a name="return-value"></a>반환 값

속성 자체에 대 한 경로 이름을 반환 합니다. 경로가 지정 되지 않은 경우 비어 있을 수 있습니다.

## <a name="cdatapathpropertyopen"></a><a name="open"></a> CDataPathProperty:: Open

연결 된 컨트롤의 비동기 속성 로드를 시작 하려면이 멤버 함수를 호출 합니다.

```
virtual BOOL Open(
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    COleControl* pControl,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszPath,
    CFileException* pError = NULL);

virtual BOOL Open(CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*pControl*<br/>
이 개체와 연결 될 OLE 컨트롤 개체에 대 한 포인터 `CDataPathProperty` 입니다.

*pError*<br/>
파일 예외에 대 한 포인터입니다. 오류가 발생 하면가 원인으로 설정 됩니다.

*lpszPath*<br/>
절대 또는 상대 경로일 수 있는 경로는 속성의 실제 절대 위치를 참조 하는 비동기 모니커를 만드는 데 사용 됩니다. `CDataPathProperty` 파일 이름이 아닌 Url을 사용 합니다. `CDataPathProperty`파일에 대 한 개체를 원하는 경우 경로 앞에를 추가 `file://` 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

함수는 컨트롤에서 인터페이스를 가져오려고 시도 합니다 `IBindHost` .

경로 없이를 호출 하기 전에 `Open` 속성의 경로에 대 한 값을 설정 해야 합니다. 개체를 생성할 때 또는 멤버 함수를 호출 하 여이 작업을 수행할 수 있습니다 `SetPath` .

`Open`컨트롤 없이를 호출 하기 전에 ActiveX 컨트롤 (이전의 OLE 컨트롤)은 개체와 연결 될 수 있습니다. 개체를 생성할 때 또는을 호출 하 여이 작업을 수행할 수 있습니다 `SetControl` .

[CAsyncMonikerFile:: Open](../../mfc/reference/casyncmonikerfile-class.md#open) 의 모든 오버 로드도에서 사용할 수 있습니다 `CDataPathProperty` .

## <a name="cdatapathpropertyresetdata"></a><a name="resetdata"></a> CDataPathProperty:: ResetData

이 함수를 호출 하 여 `CAsyncMonikerFile::OnDataAvailable` 컨트롤 속성이 변경 되었음을 컨테이너에 알리고, 비동기적으로 로드 된 모든 정보는 더 이상 유용 하지 않습니다.

```
virtual void ResetData();
```

### <a name="remarks"></a>설명

열기를 다시 시작 해야 합니다. 파생 클래스는 다른 기본값에 대해이 함수를 재정의할 수 있습니다.

## <a name="cdatapathpropertysetcontrol"></a><a name="setcontrol"></a> CDataPathProperty:: SetControl

이 멤버 함수를 호출 하 여 비동기 OLE 컨트롤과 개체를 연결 `CDataPathProperty` 합니다.

```cpp
void SetControl(COleControl* pControl);
```

### <a name="parameters"></a>매개 변수

*pControl*<br/>
속성과 연결할 비동기 OLE 컨트롤에 대 한 포인터입니다.

## <a name="cdatapathpropertysetpath"></a><a name="setpath"></a> CDataPathProperty:: SetPath

이 멤버 함수를 호출 하 여 속성의 경로 이름을 설정 합니다.

```cpp
void SetPath(LPCTSTR lpszPath);
```

### <a name="parameters"></a>매개 변수

*lpszPath*<br/>
비동기적으로 로드 되는 속성에 대 한 절대 경로 또는 상대 경로일 수 있는 경로입니다. `CDataPathProperty` 파일 이름이 아닌 Url을 사용 합니다. `CDataPathProperty`파일에 대 한 개체를 원하는 경우 경로 앞에를 추가 `file://` 합니다.

## <a name="see-also"></a>참고 항목

[MFC 샘플 이미지](../../overview/visual-cpp-samples.md)<br/>
[CAsyncMonikerFile 클래스](../../mfc/reference/casyncmonikerfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 클래스](../../mfc/reference/casyncmonikerfile-class.md)
