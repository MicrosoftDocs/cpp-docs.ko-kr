---
description: '자세히 알아보기: COleStreamFile 클래스'
title: COleStreamFile 클래스
ms.date: 11/04/2016
f1_keywords:
- COleStreamFile
- AFXOLE/COleStreamFile
- AFXOLE/COleStreamFile::COleStreamFile
- AFXOLE/COleStreamFile::Attach
- AFXOLE/COleStreamFile::CreateMemoryStream
- AFXOLE/COleStreamFile::CreateStream
- AFXOLE/COleStreamFile::Detach
- AFXOLE/COleStreamFile::GetStream
- AFXOLE/COleStreamFile::OpenStream
helpviewer_keywords:
- COleStreamFile [MFC], COleStreamFile
- COleStreamFile [MFC], Attach
- COleStreamFile [MFC], CreateMemoryStream
- COleStreamFile [MFC], CreateStream
- COleStreamFile [MFC], Detach
- COleStreamFile [MFC], GetStream
- COleStreamFile [MFC], OpenStream
ms.assetid: e4f93698-e17c-4a18-a7c0-4b4df8eb4d93
ms.openlocfilehash: b856dc5b408c43f61a11f7c68035587bc16bbeaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97226638"
---
# <a name="colestreamfile-class"></a>COleStreamFile 클래스

OLE 구조적 스토리지의 일부로 복합 파일의 데이터 스트림(`IStream`)을 나타냅니다.

## <a name="syntax"></a>구문

```
class COleStreamFile : public CFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[COleStreamFile:: COleStreamFile](#colestreamfile)|`COleStreamFile` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[COleStreamFile:: Attach](#attach)|스트림을 개체와 연결 합니다.|
|[COleStreamFile:: CreateMemoryStream](#creatememorystream)|전역 메모리에서 스트림을 만들고이를 개체에 연결 합니다.|
|[COleStreamFile:: CreateStream](#createstream)|스트림을 만들고이를 개체에 연결 합니다.|
|[COleStreamFile::D etach](#detach)|개체에서 스트림을 분리 합니다.|
|[COleStreamFile:: System.resources.resourcemanager.getstream](#getstream)|현재 스트림을 반환 합니다.|
|[COleStreamFile:: OpenStream](#openstream)|스트림을 안전 하 게 열고 개체와 연결 합니다.|

## <a name="remarks"></a>설명

`IStorage`개체가 메모리 스트림이 아닌 경우에는 스트림을 열거나 만들 수 있도록 개체가 있어야 합니다.

`COleStreamFile` 개체는 [CFile](../../mfc/reference/cfile-class.md) 개체와 정확히 같은 방식으로 조작 됩니다.

스트림과 저장소를 조작 하는 방법에 대 한 자세한 내용은 [컨테이너: 복합 파일](../../mfc/containers-compound-files.md)(영문) 문서를 참조 하세요.

자세한 내용은 Windows SDK에서 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 및 [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`COleStreamFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="colestreamfileattach"></a><a name="attach"></a> COleStreamFile:: Attach

제공 된 OLE 스트림을 개체와 연결 `COleStreamFile` 합니다.

```cpp
void Attach(LPSTREAM lpStream);
```

### <a name="parameters"></a>매개 변수

*lpStream*<br/>
`IStream`개체와 연결 될 OLE 스트림 ()을 가리킵니다. NULL이 될 수 없습니다.

### <a name="remarks"></a>설명

개체는 OLE 스트림과 연결 되어 있지 않아야 합니다.

자세한 내용은 Windows SDK의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 을 참조 하십시오.

## <a name="colestreamfilecolestreamfile"></a><a name="colestreamfile"></a> COleStreamFile:: COleStreamFile

`COleStreamFile` 개체를 만듭니다.

```
COleStreamFile(LPSTREAM lpStream = NULL);
```

### <a name="parameters"></a>매개 변수

*lpStream*<br/>
개체와 연결 될 OLE 스트림에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*Lpstream* 이 NULL 이면 개체가 ole 스트림과 연결 되지 않은 것이 고, 그렇지 않으면 개체가 제공 된 ole 스트림과 연결 됩니다.

자세한 내용은 Windows SDK의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 을 참조 하십시오.

## <a name="colestreamfilecreatememorystream"></a><a name="creatememorystream"></a> COleStreamFile:: CreateMemoryStream

오류가 정상적인 정상적인 조건인 전역 공유 메모리에서 새 스트림을 안전 하 게 만듭니다.

```
BOOL CreateMemoryStream(CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*pError*<br/>
는 [Cfileexception](../../mfc/reference/cfileexception-class.md) 개체를 가리키거나 만들기 작업의 완료 상태를 나타내는 NULL을 지정 합니다. 스트림을 만들려고 시도 하 여 발생 가능한 예외를 모니터링 하려는 경우이 매개 변수를 제공 합니다.

### <a name="return-value"></a>반환 값

스트림이 성공적으로 생성 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

메모리는 OLE 하위 시스템에 의해 할당 됩니다.

자세한 내용은 Windows SDK에서 [CreateStreamOnHGlobal](/windows/win32/api/combaseapi/nf-combaseapi-createstreamonhglobal) 을 참조 하세요.

## <a name="colestreamfilecreatestream"></a><a name="createstream"></a> COleStreamFile:: CreateStream

제공 된 저장소 개체에서 오류가 정상적인 정상적인 조건인 새 스트림을 안전 하 게 만듭니다.

```
BOOL CreateStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive|modeCreate,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*lpStorage*<br/>
만들 스트림을 포함 하는 OLE 저장소 개체를 가리킵니다. NULL이 될 수 없습니다.

*lpszStreamName*<br/>
만들 스트림의 이름입니다. NULL이 될 수 없습니다.

*nOpenFlags*<br/>
스트림을 열 때 사용할 액세스 모드입니다. 기본적으로 배타, 읽기/쓰기 및 만들기 모드가 사용 됩니다. 사용 가능한 모드의 전체 목록은 [cfile:: cfile](../../mfc/reference/cfile-class.md#cfile)를 참조 하세요.

*pError*<br/>
는 [Cfileexception](../../mfc/reference/cfileexception-class.md) 개체 또는 NULL을 가리킵니다. 스트림을 만들려고 시도 하 여 발생 가능한 예외를 모니터링 하려는 경우이 매개 변수를 제공 합니다.

### <a name="return-value"></a>반환 값

스트림이 성공적으로 생성 되 면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Open이 실패 하 고 *pError* 가 NULL이 아닌 경우 파일 예외가 throw 됩니다.

자세한 내용은 Windows SDK에서 [IStorage:: CreateStream](/windows/win32/api/objidl/nf-objidl-istorage-createstream) 를 참조 하세요.

## <a name="colestreamfiledetach"></a><a name="detach"></a> COleStreamFile::D etach

스트림을 닫지 않고 개체에서 스트림을 분리 합니다.

```
LPSTREAM Detach();
```

### <a name="return-value"></a>반환 값

개체와 연결 된 스트림 ()에 대 한 포인터 `IStream` 입니다.

### <a name="remarks"></a>설명

스트림은 프로그램이 종료 되기 전에 다른 방식으로 닫혀야 합니다.

자세한 내용은 Windows SDK의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 을 참조 하십시오.

## <a name="colestreamfilegetstream"></a><a name="getstream"></a> COleStreamFile:: System.resources.resourcemanager.getstream

현재 스트림에 대 한 포인터를 반환 하려면이 함수를 호출 합니다.

```
IStream* GetStream() const;
```

### <a name="return-value"></a>반환 값

현재 스트림 인터페이스에 대 한 포인터입니다 ( [IStream](/windows/win32/api/objidl/nn-objidl-istream)).

## <a name="colestreamfileopenstream"></a><a name="openstream"></a> COleStreamFile:: OpenStream

기존 스트림을 엽니다.

```
BOOL OpenStream(
    LPSTORAGE lpStorage,
    LPCTSTR lpszStreamName,
    DWORD nOpenFlags = modeReadWrite|shareExclusive,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*lpStorage*<br/>
열 스트림을 포함 하는 OLE 저장소 개체를 가리킵니다. NULL이 될 수 없습니다.

*lpszStreamName*<br/>
열 스트림의 이름입니다. NULL이 될 수 없습니다.

*nOpenFlags*<br/>
스트림을 열 때 사용할 액세스 모드입니다. 기본적으로 배타 및 읽기/쓰기 모드가 사용 됩니다. 사용 가능한 모드의 전체 목록은 [cfile:: cfile](../../mfc/reference/cfile-class.md#cfile)를 참조 하세요.

*pError*<br/>
는 [Cfileexception](../../mfc/reference/cfileexception-class.md) 개체 또는 NULL을 가리킵니다. 스트림을 열려고 시도 하 여 발생 가능한 예외를 모니터링 하려는 경우이 매개 변수를 제공 합니다.

### <a name="return-value"></a>반환 값

스트림이 성공적으로 열리면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Open이 실패 하 고 *pError* 가 NULL이 아닌 경우 파일 예외가 throw 됩니다.

자세한 내용은 Windows SDK에서 [IStorage:: OpenStream](/windows/win32/api/objidl/nf-objidl-istorage-openstream) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[CFile 클래스](../../mfc/reference/cfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
