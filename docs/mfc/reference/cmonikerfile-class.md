---
description: '자세히 알아보기: CMonikerFile 클래스'
title: CMonikerFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CMonikerFile
- AFXOLE/CMonikerFile
- AFXOLE/CMonikerFile::CMonikerFile
- AFXOLE/CMonikerFile::Close
- AFXOLE/CMonikerFile::Detach
- AFXOLE/CMonikerFile::GetMoniker
- AFXOLE/CMonikerFile::Open
- AFXOLE/CMonikerFile::CreateBindContext
helpviewer_keywords:
- CMonikerFile [MFC], CMonikerFile
- CMonikerFile [MFC], Close
- CMonikerFile [MFC], Detach
- CMonikerFile [MFC], GetMoniker
- CMonikerFile [MFC], Open
- CMonikerFile [MFC], CreateBindContext
ms.assetid: 87be5966-f4f7-4235-bce2-1fa39e9417de
ms.openlocfilehash: d59de05f688c10d3dbfa6682777d5fd11d4f53ec
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331576"
---
# <a name="cmonikerfile-class"></a>CMonikerFile 클래스

[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)로 명명 된 데이터 스트림 ( [IStream](/windows/win32/api/objidl/nn-objidl-istream))을 나타냅니다.

## <a name="syntax"></a>구문

```
class CMonikerFile : public COleStreamFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMonikerFile:: CMonikerFile](#cmonikerfile)|`CMonikerFile` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMonikerFile:: Close](#close)|스트림을 분리 하 고 해제 하 고 모니커를 해제 합니다.|
|[CMonikerFile::D etach](#detach)|`IMoniker`이 개체에서를 분리 `CMonikerFile` 합니다.|
|[CMonikerFile:: GetMoniker](#getmoniker)|현재 모니커를 반환 합니다.|
|[CMonikerFile:: Open](#open)|지정 된 파일을 열어 스트림을 가져옵니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CMonikerFile:: CreateBindContext](#createbindcontext)|바인딩 컨텍스트를 얻거나 기본 초기화 된 바인드 컨텍스트를 만듭니다.|

## <a name="remarks"></a>설명

모니커에는 파일 경로 이름 등의 정보가 포함 되어 있습니다. 모니커 개체의 인터페이스에 대 한 포인터가 있는 경우 `IMoniker` 파일이 실제로 있는 위치에 대 한 다른 특정 정보 없이 식별 된 파일에 대 한 액세스 권한을 얻을 수 있습니다.

에서 파생 되는 모니커 또는 모니커에 `COleStreamFile` `CMonikerFile` 만들 수 있는 문자열 표현을 가져와 모니커가 이름인 스트림에 바인딩합니다. 그런 다음 해당 스트림을 읽고 쓸 수 있습니다. 의 실제 목적은에 `CMonikerFile` 의해 이름이 지정 된에 대 한 간단한 액세스를 제공 하는 것입니다 `IStream` `IMoniker` . 따라서 스트림에 직접 바인딩할 필요는 없지만 `CFile` 스트림에는 기능이 있습니다.

`CMonikerFile` 는 스트림이 아닌 다른 항목에 바인딩하는 데 사용할 수 없습니다. 저장소 또는 개체에 바인딩하려면 인터페이스를 직접 사용 해야 합니다 `IMoniker` .

스트림과 모니커에 대 한 자세한 내용은 *MFC 참조* 의 [Colestreamfile](../../mfc/reference/colestreamfile-class.md) 및 Windows SDK의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 및 [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) 을 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

`CMonikerFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="cmonikerfileclose"></a><a name="close"></a> CMonikerFile:: Close

스트림을 분리 및 해제 하 고 모니커를 해제 하려면이 함수를 호출 합니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

는 열려 있지 않거나 이미 닫혀 있는 스트림에서 호출할 수 있습니다.

## <a name="cmonikerfilecmonikerfile"></a><a name="cmonikerfile"></a> CMonikerFile:: CMonikerFile

`CMonikerFile` 개체를 생성합니다.

```
CMonikerFile();
```

## <a name="cmonikerfilecreatebindcontext"></a><a name="createbindcontext"></a> CMonikerFile:: CreateBindContext

이 함수를 호출 하 여 기본 초기화 바인딩 컨텍스트를 만듭니다.

```
IBindCtx* CreateBindContext(CFileException* pError);
```

### <a name="parameters"></a>매개 변수

*pError*<br/>
파일 예외에 대 한 포인터입니다. 오류가 발생 하면 원인으로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 바인딩할 바인드 컨텍스트 [ibindctx interface](/windows/win32/api/objidl/nn-objidl-ibindctx) 에 대 한 포인터입니다. 그렇지 않으면 NULL입니다. 인터페이스를 사용 하 여 인스턴스를 연 경우 `IBindHost` 에서 바인딩 컨텍스트를 검색 `IBindHost` 합니다. `IBindHost`인터페이스가 없거나 인터페이스에서 바인드 컨텍스트를 반환 하는 데 실패 하면 바인드 컨텍스트가 생성 됩니다. [Ibindhost](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775076\(v=vs.85\)) 인터페이스에 대 한 자세한 내용은 Windows SDK를 참조 하세요.

### <a name="remarks"></a>설명

바인드 컨텍스트는 특정 모니커 바인딩 작업에 대 한 정보를 저장 하는 개체입니다. 이 함수를 재정의 하 여 사용자 지정 바인드 컨텍스트를 제공할 수 있습니다.

## <a name="cmonikerfiledetach"></a><a name="detach"></a> CMonikerFile::D etach

이 함수를 호출 하 여 스트림을 닫습니다.

```
BOOL Detach(CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*pError*<br/>
파일 예외에 대 한 포인터입니다. 오류가 발생 하면 원인으로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="cmonikerfilegetmoniker"></a><a name="getmoniker"></a> CMonikerFile:: GetMoniker

현재 모니커에 대 한 포인터를 검색 하려면이 함수를 호출 합니다.

```
IMoniker* GetMoniker() const;
```

### <a name="return-value"></a>반환 값

현재 모니커 인터페이스 ( [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker))에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`CMonikerFile`는 인터페이스가 아니므로 반환 되는 포인터는 참조 횟수 ( [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)를 통해)를 증가 시 지 않으며 개체를 해제할 때 모니커를 해제 합니다 `CMonikerFile` . 모니커를 유지 하거나 직접 릴리스 하려는 경우에는 필요 합니다 `AddRef` .

## <a name="cmonikerfileopen"></a><a name="open"></a> CMonikerFile:: Open

이 멤버 함수를 호출 하 여 파일이 나 모니커 개체를 엽니다.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszURL*<br/>
열 파일의 URL 또는 파일 이름입니다.

*pError*<br/>
파일 예외에 대 한 포인터입니다. 오류가 발생 하면 원인으로 설정 됩니다.

*pMoniker*<br/>
스트림을 얻는 데 사용할 모니커 인터페이스에 대 한 포인터 `IMoniker` 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Macintosh에서는 *lpszURL* 매개 변수를 사용할 수 없습니다. 의 *Pmoniker* 형식만 `Open` Macintosh에서 사용할 수 있습니다.

*LpszURL* 매개 변수에 대 한 URL 또는 파일 이름을 사용할 수 있습니다. 예를 들어:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/cmonikerfile-class_1.cpp)]

\- 또는 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/cmonikerfile-class_2.cpp)]

## <a name="see-also"></a>참고 항목

[COleStreamFile 클래스](../../mfc/reference/colestreamfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CAsyncMonikerFile 클래스](../../mfc/reference/casyncmonikerfile-class.md)
