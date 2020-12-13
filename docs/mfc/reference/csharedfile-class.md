---
description: '다음에 대 한 자세한 정보: CSharedFile 클래스'
title: CSharedFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CSharedFile
- AFXADV/CSharedFile
- AFXADV/CSharedFile::CSharedFile
- AFXADV/CSharedFile::Detach
- AFXADV/CSharedFile::SetHandle
helpviewer_keywords:
- CSharedFile [MFC], CSharedFile
- CSharedFile [MFC], Detach
- CSharedFile [MFC], SetHandle
ms.assetid: 5d000422-9ede-4318-a8c9-f7412b674f39
ms.openlocfilehash: 0eb2f76bdfa9e10c660f405e225698289b506014
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342833"
---
# <a name="csharedfile-class"></a>CSharedFile 클래스

공유 메모리 파일을 지 원하는 [Cmemfile](../../mfc/reference/cmemfile-class.md)파생 클래스입니다.

## <a name="syntax"></a>구문

```
class CSharedFile : public CMemFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSharedFile:: CSharedFile](#csharedfile)|`CSharedFile` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSharedFile::D etach](#detach)|공유 메모리 파일을 닫고 해당 메모리 블록의 핸들을 반환 합니다.|
|[CSharedFile:: SetHandle](#sethandle)|메모리 블록에 공유 메모리 파일을 연결 합니다.|

## <a name="remarks"></a>설명

메모리 파일은 디스크 파일 처럼 동작 합니다. 차이점은 메모리 파일이 디스크가 아닌 RAM에 저장 된다는 것입니다. 메모리 파일은 빠른 임시 저장소를 만들거나 독립적인 프로세스 간에 원시 바이트 또는 직렬화 된 개체를 전송 하는 데 유용 합니다.

공유 메모리 파일은 해당 메모리가 [Globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 함수를 사용 하 여 할당 된 메모리 파일과 다릅니다. 클래스는를 사용 하 여 `CSharedFile` 만든 전역적으로 할당 된 메모리 블록에 데이터를 저장 하 고,를 사용 하는 등의 방법으로 `GlobalAlloc` DDE, 클립보드 또는 기타 OLE/COM 균일 데이터 전송 작업을 사용 하 여이 메모리 블록을 공유할 수 있습니다 `IDataObject` .

`GlobalAlloc`[malloc](../../c-runtime-library/reference/malloc.md)에서 반환 하는 포인터와 같은 메모리에 대 한 포인터가 아닌 HGLOBAL 핸들을 반환 합니다. HGLOBAL 핸들은 특정 응용 프로그램에 필요 합니다. 예를 들어 클립보드에 데이터를 저장 하려면 HGLOBAL 핸들이 필요 합니다.

`CSharedFile` 는 메모리 매핑된 파일을 사용 하지 않으며 프로세스 간에 데이터를 직접 공유할 수 없습니다.

`CSharedFile` 개체는 자체 메모리를 자동으로 할당할 수 있습니다. 또는 `CSharedFile` [Csharedfile:: SetHandle](#sethandle)를 호출 하 여 개체에 사용자 고유의 메모리 블록을 연결할 수 있습니다. 두 경우 모두 메모리 파일을 늘리기 위한 메모리가 `nGrowBytes` 0이 아닌 경우 자동으로 크기가 증가 `nGrowBytes` 합니다.

자세한 내용은 *런타임 라이브러리 참조* 에서 [MFC의 파일](../../mfc/files-in-mfc.md) 및 [파일 처리](../../c-runtime-library/file-handling.md) 문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CMemFile](../../mfc/reference/cmemfile-class.md)

`CSharedFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxadv

## <a name="csharedfilecsharedfile"></a><a name="csharedfile"></a> CSharedFile:: CSharedFile

개체를 생성 `CSharedFile` 하 고 해당 개체에 대 한 메모리를 할당 합니다.

```
CSharedFile(
    UINT nAllocFlags = GMEM_DDESHARE | GMEM_MOVEABLE,
    UINT nGrowBytes = 4096);
```

### <a name="parameters"></a>매개 변수

*nAllocFlags*<br/>
메모리를 할당 하는 방법을 나타내는 플래그입니다. 유효한 플래그 값 목록은 [Globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc) 를 참조 하세요.

*nGrowBytes*<br/>
메모리 할당 증가값 (바이트)입니다.

## <a name="csharedfiledetach"></a><a name="detach"></a> CSharedFile::D etach

메모리 파일을 닫고 메모리 블록에서 분리 하려면이 함수를 호출 합니다.

```
HGLOBAL Detach();
```

### <a name="return-value"></a>반환 값

메모리 파일의 내용이 포함 된 메모리 블록의 핸들입니다.

### <a name="remarks"></a>설명

**Detach** 에서 반환 된 핸들을 사용 하 여 [SetHandle](#sethandle)를 호출 하 여 다시 열 수 있습니다.

## <a name="csharedfilesethandle"></a><a name="sethandle"></a> CSharedFile:: SetHandle

이 함수를 호출 하 여 전역 메모리 블록을 개체에 연결 `CSharedFile` 합니다.

```cpp
void SetHandle(
    HGLOBAL hGlobalMemory,
    BOOL bAllowGrow = TRUE);
```

### <a name="parameters"></a>매개 변수

*hGlobalMemory*<br/>
에 연결할 전역 메모리에 대 한 핸들 `CSharedFile` 입니다.

*bAllowGrow*<br/>
메모리 블록을 늘릴 수 있는지 여부를 지정 합니다.

### <a name="remarks"></a>설명

*Ballowgrow* 0이 아니면 메모리 블록 크기 보다 더 많은 바이트를 파일에 쓰려고 시도 하는 경우와 같이 필요한 경우 메모리 블록의 크기가 증가 합니다.

## <a name="see-also"></a>참고 항목

[CMemFile 클래스](../../mfc/reference/cmemfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMemFile 클래스](../../mfc/reference/cmemfile-class.md)
