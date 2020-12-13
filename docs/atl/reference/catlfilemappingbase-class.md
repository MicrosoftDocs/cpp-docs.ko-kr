---
description: '자세히 알아보기: CAtlFileMappingBase 클래스'
title: CAtlFileMappingBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CAtlFileMappingBase
- ATLFILE/ATL::CAtlFileMappingBase::CopyFrom
- ATLFILE/ATL::CAtlFileMappingBase::GetData
- ATLFILE/ATL::CAtlFileMappingBase::GetHandle
- ATLFILE/ATL::CAtlFileMappingBase::GetMappingSize
- ATLFILE/ATL::CAtlFileMappingBase::MapFile
- ATLFILE/ATL::CAtlFileMappingBase::MapSharedMem
- ATLFILE/ATL::CAtlFileMappingBase::OpenMapping
- ATLFILE/ATL::CAtlFileMappingBase::Unmap
helpviewer_keywords:
- CAtlFileMappingBase class
ms.assetid: be555723-2790-4f57-a8fb-be4d68460775
ms.openlocfilehash: 14bf275024dc95a3fdaf76c4e4d699127feaa8f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147461"
---
# <a name="catlfilemappingbase-class"></a>CAtlFileMappingBase 클래스

이 클래스는 메모리 매핑된 파일을 나타냅니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlFileMappingBase
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAtlFileMappingBase::CAtlFileMappingBase](#catlfilemappingbase)|생성자입니다.|
|[CAtlFileMappingBase:: ~ CAtlFileMappingBase](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAtlFileMappingBase:: CopyFrom](#copyfrom)|파일 매핑 개체에서 복사 하려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase:: GetData](#getdata)|파일 매핑 개체에서 데이터를 가져오려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase:: GetHandle](#gethandle)|파일 핸들을 반환 하려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase::GetMappingSize](#getmappingsize)|파일 매핑 개체에서 매핑 크기를 가져오려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase:: 맵 파일](#mapfile)|파일 매핑 개체를 만들려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase:: MapSharedMem](#mapsharedmem)|모든 프로세스에 대 한 모든 액세스를 허용 하는 파일 매핑 개체를 만들려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase:: OpenMapping](#openmapping)|파일 매핑 개체에 대 한 핸들을 반환 하려면이 메서드를 호출 합니다.|
|[CAtlFileMappingBase:: 매핑 해제](#unmap)|파일 매핑 개체의 매핑을 해제 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CAtlFileMappingBase:: operator =](#operator_eq)|현재 파일 매핑 개체를 다른 파일 매핑 개체로 설정 합니다.|

## <a name="remarks"></a>설명

파일 매핑은 프로세스의 가상 주소 공간 일부와 파일 내용을 연결 하는 것입니다. 이 클래스는 프로그램에서 데이터에 쉽게 액세스 하 고 공유할 수 있도록 하는 파일 매핑 개체를 만드는 메서드를 제공 합니다.

자세한 내용은 Windows SDK [파일 매핑](/windows/win32/Memory/file-mapping) 을 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:** 이 파일 .h

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="catlfilemappingbase"></a> CAtlFileMappingBase::CAtlFileMappingBase

생성자입니다.

```cpp
CAtlFileMappingBase(CAtlFileMappingBase& orig);
CAtlFileMappingBase() throw();
```

### <a name="parameters"></a>매개 변수

*orig*<br/>
새 개체를 만들기 위해 복사할 원본 파일 매핑 개체입니다.

### <a name="remarks"></a>설명

선택적으로 기존 개체를 사용 하 여 새 파일 매핑 개체를 만듭니다. 특정 파일에 대 한 파일 매핑 개체를 열거나 만들려면 [CAtlFileMappingBase:: 맵](#mapfile) 파일을 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Utilities#71](../../atl/codesnippet/cpp/catlfilemappingbase-class_1.cpp)]

## <a name="catlfilemappingbasecatlfilemappingbase"></a><a name="dtor"></a> CAtlFileMappingBase:: ~ CAtlFileMappingBase

소멸자입니다.

```cpp
~CAtlFileMappingBase() throw();
```

### <a name="remarks"></a>설명

클래스에서 할당 한 모든 리소스를 해제 하 고 [CAtlFileMappingBase:: 매핑](#unmap) 해제 메서드를 호출 합니다.

## <a name="catlfilemappingbasecopyfrom"></a><a name="copyfrom"></a> CAtlFileMappingBase:: CopyFrom

파일 매핑 개체에서 복사 하려면이 메서드를 호출 합니다.

```cpp
HRESULT CopyFrom(CAtlFileMappingBase& orig) throw();
```

### <a name="parameters"></a>매개 변수

*orig*<br/>
복사할 원본 파일 매핑 개체입니다.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

## <a name="catlfilemappingbasegetdata"></a><a name="getdata"></a> CAtlFileMappingBase:: GetData

파일 매핑 개체에서 데이터를 가져오려면이 메서드를 호출 합니다.

```cpp
void* GetData() const throw();
```

### <a name="return-value"></a>반환 값

데이터에 대 한 포인터를 반환 합니다.

## <a name="catlfilemappingbasegethandle"></a><a name="gethandle"></a> CAtlFileMappingBase:: GetHandle

파일 매핑 개체에 대 한 핸들을 반환 하려면이 메서드를 호출 합니다.

```cpp
HANDLE GetHandle() throw ();
```

### <a name="return-value"></a>반환 값

파일 매핑 개체에 대 한 핸들을 반환 합니다.

## <a name="catlfilemappingbasegetmappingsize"></a><a name="getmappingsize"></a> CAtlFileMappingBase::GetMappingSize

파일 매핑 개체에서 매핑 크기를 가져오려면이 메서드를 호출 합니다.

```cpp
SIZE_T GetMappingSize() throw();
```

### <a name="return-value"></a>반환 값

매핑 크기를 반환 합니다.

### <a name="example"></a>예제

[CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase)의 예제를 참조 하세요.

## <a name="catlfilemappingbasemapfile"></a><a name="mapfile"></a> CAtlFileMappingBase:: 맵 파일

이 메서드를 호출 하 여 지정 된 파일에 대 한 파일 매핑 개체를 열거나 만듭니다.

```cpp
HRESULT MapFile(
    HANDLE hFile,
    SIZE_T nMappingSize = 0,
    ULONGLONG nOffset = 0,
    DWORD dwMappingProtection = PAGE_READONLY,
    DWORD dwViewDesiredAccess = FILE_MAP_READ) throw();
```

### <a name="parameters"></a>매개 변수

*hFile*<br/>
매핑 개체를 만들 파일에 대 한 핸들입니다. *Hfile* 은 유효 해야 하며 INVALID_HANDLE_VALUE로 설정할 수 없습니다.

*nMappingSize*<br/>
매핑 크기입니다. 0 인 경우 파일 매핑 개체의 최대 크기는 *Hfile* 로 식별 되는 파일의 현재 크기와 같습니다.

*nOffset*<br/>
매핑을 시작할 파일 오프셋입니다. 오프셋 값은 시스템의 메모리 할당 세분성의 배수 여야 합니다.

*dwMappingProtection*<br/>
파일이 매핑될 때 파일 보기에 필요한 보호입니다. Windows SDK에서 *Flprotect* in [createfilemapping에서](/windows/win32/api/winbase/nf-winbase-createfilemappinga) 를 참조 하세요.

*dwViewDesiredAccess*<br/>
파일 보기에 대 한 액세스 형식을 지정 합니다. 따라서 파일에 의해 매핑되는 페이지의 보호를 지정 합니다. Windows SDK에서 *dwDesiredAccess* 의 [mapviewoffileex가](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

파일 매핑 개체를 만든 후 파일 크기는 파일 매핑 개체의 크기를 초과 하지 않아야 합니다. 이 경우 모든 파일의 콘텐츠를 공유할 수 있는 것은 아닙니다. 자세한 내용은 Windows SDK [createfilemapping에서](/windows/win32/api/winbase/nf-winbase-createfilemappinga) and [mapviewoffileex가](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) 을 참조 하세요.

### <a name="example"></a>예제

[CAtlFileMappingBase:: CAtlFileMappingBase](#catlfilemappingbase)의 예제를 참조 하세요.

## <a name="catlfilemappingbasemapsharedmem"></a><a name="mapsharedmem"></a> CAtlFileMappingBase:: MapSharedMem

모든 프로세스에 대 한 모든 액세스를 허용 하는 파일 매핑 개체를 만들려면이 메서드를 호출 합니다.

```cpp
HRESULT MapSharedMem(
    SIZE_T nMappingSize,
    LPCTSTR szName,
    BOOL* pbAlreadyExisted = NULL,
    LPSECURITY_ATTRIBUTES lpsa = NULL,
    DWORD dwMappingProtection = PAGE_READWRITE,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>매개 변수

*nMappingSize*<br/>
매핑 크기입니다. 0 인 경우 파일 매핑 개체의 최대 크기는 *szName* 로 식별 되는 파일 매핑 개체의 현재 크기와 같습니다.

*szName*<br/>
매핑 개체의 이름입니다.

*pbAlreadyExisted*<br/>
매핑 개체가 이미 존재 하는 경우 TRUE로 설정 된 부울 값을 가리킵니다.

*lpsa*<br/>
`SECURITY_ATTRIBUTES`반환 된 핸들이 자식 프로세스에서 상속 될 수 있는지 여부를 결정 하는 구조체에 대 한 포인터입니다. Windows SDK에서 *Lpattributes* in [createfilemapping에서](/windows/win32/api/winbase/nf-winbase-createfilemappinga) 를 참조 하세요.

*dwMappingProtection*<br/>
파일이 매핑될 때 파일 보기에 필요한 보호입니다. Windows SDK에서 *Flprotect* 를 참조 하세요 `CreateFileMapping` .

*dwViewDesiredAccess*<br/>
파일 보기에 대 한 액세스 형식을 지정 합니다. 따라서 파일에 의해 매핑되는 페이지의 보호를 지정 합니다. Windows SDK에서 *dwDesiredAccess* 의 [mapviewoffileex가](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

`MapShareMem`[createfilemapping에서](/windows/win32/api/winbase/nf-winbase-createfilemappinga)에서 만든 기존 파일 매핑 개체를 프로세스 간에 공유할 수 있도록 합니다.

## <a name="catlfilemappingbaseopenmapping"></a><a name="openmapping"></a> CAtlFileMappingBase:: OpenMapping

지정 된 파일에 대 한 명명 된 파일 매핑 개체를 열려면이 메서드를 호출 합니다.

```cpp
HRESULT OpenMapping(
    LPCTSTR szName,
    SIZE_T nMappingSize,
    ULONGLONG nOffset = 0,
    DWORD dwViewDesiredAccess = FILE_MAP_ALL_ACCESS) throw();
```

### <a name="parameters"></a>매개 변수

*szName*<br/>
매핑 개체의 이름입니다. 이 이름을 사용 하 여 파일 매핑 개체에 대 한 열린 핸들이 있고 매핑 개체의 보안 설명자가 *dwViewDesiredAccess* 매개 변수와 충돌 하지 않으면 열기 작업이 성공 합니다.

*nMappingSize*<br/>
매핑 크기입니다. 0 인 경우 파일 매핑 개체의 최대 크기는 *szName* 로 식별 되는 파일 매핑 개체의 현재 크기와 같습니다.

*nOffset*<br/>
매핑을 시작할 파일 오프셋입니다. 오프셋 값은 시스템의 메모리 할당 세분성의 배수 여야 합니다.

*dwViewDesiredAccess*<br/>
파일 보기에 대 한 액세스 형식을 지정 합니다. 따라서 파일에 의해 매핑되는 페이지의 보호를 지정 합니다. Windows SDK에서 *dwDesiredAccess* 의 [mapviewoffileex가](/windows/win32/api/memoryapi/nf-memoryapi-mapviewoffileex) 을 참조 하세요.

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

디버그 빌드에서는 입력 매개 변수가 잘못 된 경우 어설션 오류가 발생 합니다.

## <a name="catlfilemappingbaseoperator-"></a><a name="operator_eq"></a> CAtlFileMappingBase:: operator =

현재 파일 매핑 개체를 다른 파일 매핑 개체로 설정 합니다.

```cpp
CAtlFileMappingBase& operator=(CAtlFileMappingBase& orig);
```

### <a name="parameters"></a>매개 변수

*orig*<br/>
현재 파일 매핑 개체입니다.

### <a name="return-value"></a>반환 값

현재 개체에 대 한 참조를 반환 합니다.

## <a name="catlfilemappingbaseunmap"></a><a name="unmap"></a> CAtlFileMappingBase:: 매핑 해제

파일 매핑 개체의 매핑을 해제 하려면이 메서드를 호출 합니다.

```cpp
HRESULT Unmap() throw();
```

### <a name="return-value"></a>반환 값

성공 시 S_OK 또는 실패 시 오류 HRESULT를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK의 [unmapviewoffile이](/windows/win32/api/memoryapi/nf-memoryapi-unmapviewoffile) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CAtlFileMapping 클래스](../../atl/reference/catlfilemapping-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
