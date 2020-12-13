---
description: '자세히 알아보기: CAtlTransactionManager 클래스'
title: CAtlTransactionManager 클래스
ms.date: 11/04/2016
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: 25d5ea7e9b4838f483dd7f9ee408cdd5bd4c88cb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97147188"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager 클래스

CAtlTransactionManager 클래스는 KTM (Kernel Transaction Manager) 함수에 대 한 래퍼를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
class CAtlTransactionManager;
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager 소멸자입니다.|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[닫기](#close)|트랜잭션 핸들 하나를 닫습니다.|
|[커밋](#commit)|트랜잭션이 커밋되는 것을 요청 합니다.|
|[만들기](#create)|트랜잭션 핸들을 만듭니다.|
|[CreateFile](#createfile)|파일, 파일 스트림 또는 디렉터리를 트랜잭션 작업으로 만들거나 엽니다.|
|[DeleteFile](#deletefile)|트 랜 잭 트 작업으로 기존 파일을 삭제 합니다.|
|[FindFirstFile](#findfirstfile)|디렉터리에서 파일 또는 하위 디렉터리를 트랜잭션 작업으로 검색 합니다.|
|[GetFileAttributes](#getfileattributes)|지정 된 파일 또는 디렉터리에 대 한 파일 시스템 특성을 트랜잭션 작업으로 검색 합니다.|
|[GetFileAttributesEx](#getfileattributesex)|지정 된 파일 또는 디렉터리에 대 한 파일 시스템 특성을 트랜잭션 작업으로 검색 합니다.|
|[GetHandle](#gethandle)|트랜잭션 핸들을 반환 합니다.|
|[IsFallback](#isfallback)|대체 (fallback) 호출이 사용 되는지 여부를 확인 합니다.|
|[MoveFile](#movefile)|기존 파일이 나 해당 자식을 포함 하는 디렉터리를 트랜잭션 된 작업으로 이동 합니다.|
|[RegCreateKeyEx](#regcreatekeyex)|지정 된 레지스트리 키를 만들고 트랜잭션과 연결 합니다. 키가 이미 있는 경우 함수에서 키를 엽니다.|
|[RegDeleteKey](#regdeletekey)|레지스트리의 지정 된 플랫폼별 뷰에서 하위 키와 해당 값을 트랜잭션 작업으로 삭제 합니다.|
|[RegOpenKeyEx](#regopenkeyex)|지정 된 레지스트리 키를 열고 트랜잭션과 연결 합니다.|
|[롤백](#rollback)|트랜잭션이 롤백되는 것을 요청 합니다.|
|[SetFileAttributes](#setfileattributes)|파일이 나 디렉터리에 대 한 특성을 트랜잭션 작업으로 설정 합니다.|

### <a name="protected-data-members"></a>보호된 데이터 멤버

|Name|설명|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|대체 (fallback)가 지원 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.|
|[m_hTransaction](#m_htransaction)|트랜잭션 핸들입니다.|

## <a name="remarks"></a>설명

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[ATL:: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>요구 사항

**헤더:** atltransactionmanager

## <a name="catltransactionmanager"></a><a name="dtor"></a>  ~ CAtlTransactionManager

CAtlTransactionManager 소멸자입니다.

```cpp
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>설명

정상적인 처리에서는 트랜잭션이 자동으로 커밋되고 닫힙니다. 예외 해제 중에 소멸자가 호출 되 면 트랜잭션이 롤백되고 닫힙니다.

## <a name="catltransactionmanager"></a><a name="catltransactionmanager"></a> CAtlTransactionManager

CAtlTransactionManager 생성자입니다.

```cpp
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>매개 변수

*bFallback*<br/>
TRUE는 대체를 지원 함을 나타냅니다. 트랜잭션 함수에서 오류가 발생 하는 경우 클래스는 "비트랜잭션" 함수를 자동으로 호출 합니다. FALSE는 "fallback" 호출이 없음을 나타냅니다.

*bAutoCreateTransaction*<br/>
TRUE는 트랜잭션 처리기가 생성자에 자동으로 생성 됨을 나타냅니다. FALSE는 그렇지 않음을 나타냅니다.

### <a name="remarks"></a>설명

## <a name="close"></a><a name="close"></a> 닫습니다

트랜잭션 핸들을 닫습니다.

```cpp
inline BOOL Close();
```

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `CloseHandle` 합니다. 메서드는 소멸자에서 자동으로 호출 됩니다.

## <a name="commit"></a><a name="commit"></a> 커밋이

트랜잭션이 커밋되는 것을 요청 합니다.

```cpp
inline BOOL Commit();
```

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `CommitTransaction` 합니다. 메서드는 소멸자에서 자동으로 호출 됩니다.

## <a name="create"></a><a name="create"></a> 만들기

트랜잭션 핸들을 만듭니다.

```cpp
inline BOOL Create();
```

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `CreateTransaction` 합니다. 확인 방법

## <a name="createfile"></a><a name="createfile"></a> CreateFile

파일, 파일 스트림 또는 디렉터리를 트랜잭션 작업으로 만들거나 엽니다.

```cpp
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>매개 변수

*lpFileName*<br/>
만들거나 열 개체의 이름입니다.

*dwDesiredAccess*<br/>
개체에 대 한 액세스로, 읽기, 쓰기, 둘 다 또는 둘 다 (0)로 요약할 수 있습니다. 가장 일반적으로 사용 되는 값은 GENERIC_READ, GENERIC_WRITE 또는 둘 다 GENERIC_READ &#124; GENERIC_WRITE입니다.

*dwShareMode*<br/>
개체의 공유 모드입니다. 여기에는 읽기, 쓰기, 모두, 삭제, 모두 또는 none: 0, FILE_SHARE_DELETE, FILE_SHARE_READ FILE_SHARE_WRITE 수 있습니다.

*lpSecurityAttributes*<br/>
선택적 보안 설명자를 포함 하 고 반환 된 핸들을 자식 프로세스에서 상속할 수 있는지 여부를 결정 하는 SECURITY_ATTRIBUTES 구조체에 대 한 포인터입니다. 매개 변수는 NULL 일 수 있습니다.

*dwCreationDisposition*<br/>
존재 하지 않는 파일에 대해 수행할 작업입니다. 이 매개 변수는 CREATE_ALWAYS, CREATE_NEW, OPEN_ALWAYS, OPEN_EXISTING 또는 TRUNCATE_EXISTING 값 중 하나 여야 합니다.

*dwFlagsAndAttributes*<br/>
파일 특성 및 플래그입니다. 이 매개 변수는 사용 가능한 파일 특성 (FILE_ATTRIBUTE_ *)의 조합을 포함할 수 있습니다. 다른 모든 파일 특성은 FILE_ATTRIBUTE_NORMAL를 재정의 합니다. 이 매개 변수에는 \* 버퍼링 동작, 액세스 모드 및 기타 특수 용도의 플래그를 제어 하기 위한 플래그 (FILE_FLAG_) 조합이 포함 될 수도 있습니다. 이러한 값은 모든 FILE_ATTRIBUTE_ \* 값과 결합 됩니다.

*H템플릿 파일*<br/>
GENERIC_READ 액세스 권한이 있는 템플릿 파일에 대 한 올바른 핸들입니다. 템플릿 파일은 생성 되는 파일에 대 한 파일 특성 및 확장 특성을 제공 합니다. 이 매개 변수는 NULL일 수 있습니다.

### <a name="return-value"></a>반환 값

개체에 액세스 하는 데 사용할 수 있는 핸들을 반환 합니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `CreateFileTransacted` 합니다.

## <a name="deletefile"></a><a name="deletefile"></a> DeleteFile

트 랜 잭 트 작업으로 기존 파일을 삭제 합니다.

```cpp
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>매개 변수

*lpFileName*<br/>
삭제할 파일의 이름입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `DeleteFileTransacted` 합니다.

## <a name="findfirstfile"></a><a name="findfirstfile"></a> FindFirstFile

디렉터리에서 파일 또는 하위 디렉터리를 트랜잭션 작업으로 검색 합니다.

```cpp
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>매개 변수

*lpFileName*<br/>
디렉터리 또는 경로와 검색할 파일 이름입니다. 이 매개 변수는 별표 (*) 또는 물음표 ()와 같은 와일드 카드 문자를 포함할 수 있습니다.

*pNextInfo*<br/>
찾은 파일이 나 하위 디렉터리에 대 한 정보를 수신 하는 WIN32_FIND_DATA 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 또는에 대 한 후속 호출에 사용 되는 검색 핸들 `FindNextFile` 입니다 `FindClose` . 함수가 실패 하거나 *Lpfilename* 매개 변수의 검색 문자열에서 파일을 찾지 못한 경우 반환 값은 INVALID_HANDLE_VALUE입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `FindFirstFileTransacted` 합니다.

## <a name="getfileattributes"></a><a name="getfileattributes"></a> GetFileAttributes

지정 된 파일 또는 디렉터리에 대 한 파일 시스템 특성을 트랜잭션 작업으로 검색 합니다.

```cpp
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>매개 변수

*lpFileName*<br/>
파일 또는 디렉터리의 이름입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `GetFileAttributesTransacted` 합니다.

## <a name="getfileattributesex"></a><a name="getfileattributesex"></a> GetFileAttributesEx

지정 된 파일 또는 디렉터리에 대 한 파일 시스템 특성을 트랜잭션 작업으로 검색 합니다.

```cpp
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>매개 변수

*lpFileName*<br/>
파일 또는 디렉터리의 이름입니다.

*fInfoLevelId*<br/>
검색할 특성 정보의 수준입니다.

*lpFileInformation*<br/>
특성 정보를 받는 버퍼에 대 한 포인터입니다. 이 버퍼에 저장 되는 특성 정보 유형은 *fInfoLevelId* 의 값에 따라 결정 됩니다. *FInfoLevelId* 매개 변수가 GetFileExInfoStandard 인 경우이 매개 변수는 WIN32_FILE_ATTRIBUTE_DATA 구조체를 가리킵니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `GetFileAttributesTransacted` 합니다.

## <a name="gethandle"></a><a name="gethandle"></a> GetHandle

트랜잭션 핸들을 반환 합니다.

```cpp
HANDLE GetHandle() const;
```

### <a name="return-value"></a>반환 값

클래스에 대 한 트랜잭션 핸들을 반환 합니다. `CAtlTransactionManager`가 핸들에 연결 되지 않은 경우 NULL을 반환 합니다.

### <a name="remarks"></a>설명

## <a name="isfallback"></a><a name="isfallback"></a> IsFallback

대체 (fallback) 호출이 사용 되는지 여부를 확인 합니다.

```cpp
BOOL IsFallback() const;
```

### <a name="return-value"></a>반환 값

클래스에서 대체 호출을 지원 하면 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

## <a name="m_bfallback"></a><a name="m_bfallback"></a> m_bFallback

대체 (fallback)가 지원 되 면 TRUE입니다. 그렇지 않으면 FALSE입니다.

```cpp
BOOL m_bFallback;
```

### <a name="remarks"></a>설명

## <a name="m_htransaction"></a><a name="m_htransaction"></a> m_hTransaction

트랜잭션 핸들입니다.

```cpp
HANDLE m_hTransaction;
```

### <a name="remarks"></a>설명

## <a name="movefile"></a><a name="movefile"></a> My.computer.filesystem.movefile

기존 파일이 나 해당 자식을 포함 하는 디렉터리를 트랜잭션 된 작업으로 이동 합니다.

```cpp
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>매개 변수

*lpOldFileName*<br/>
로컬 컴퓨터에 있는 기존 파일 또는 디렉터리의 현재 이름입니다.

*lpNewFileName*<br/>
파일이 나 디렉터리의 새 이름입니다. 이 이름은 이미 존재 해서는 안 됩니다. 새 파일이 다른 파일 시스템 또는 드라이브에 있을 수 있습니다. 새 디렉터리는 동일한 드라이브에 있어야 합니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `MoveFileTransacted` 합니다.

## <a name="regcreatekeyex"></a><a name="regcreatekeyex"></a> RegCreateKeyEx

지정 된 레지스트리 키를 만들고 트랜잭션과 연결 합니다. 키가 이미 있는 경우 함수에서 키를 엽니다.

```cpp
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*<br/>
이 함수가 열거나 만드는 하위 키의 이름입니다.

*dwReserved*<br/>
이 매개 변수는 예약 되어 있으며 0 이어야 합니다.

*lpClass*<br/>
이 키의 사용자 정의 클래스입니다. 이 매개 변수는 무시 해도 됩니다. 이 매개 변수는 NULL일 수 있습니다.

*dwOptions*<br/>
이 매개 변수는 REG_OPTION_BACKUP_RESTORE, REG_OPTION_NON_VOLATILE 또는 REG_OPTION_VOLATILE 값 중 하나일 수 있습니다.

*samDesired*<br/>
키에 대 한 액세스 권한을 지정 하는 마스크입니다.

*lpSecurityAttributes*<br/>
반환된 핸들이 자식 프로세스에 의해 상속되는지 여부를 결정하는 SECURITY_ATTRIBUTES 구조에 대한 포인터입니다. *Lpsecurityattributes* 가 NULL 인 경우 핸들을 상속할 수 없습니다.

*phkResult*<br/>
열리거나 만든 키에 대 한 핸들을 받는 변수에 대 한 포인터입니다. 키가 미리 정의 된 레지스트리 키 중 하나가 아닌 경우 `RegCloseKey` 핸들 사용을 마친 후 함수를 호출 합니다.

*Lstwstgga*<br/>
REG_CREATED_NEW_KEY 또는 REG_OPENED_EXISTING_KEY 처리 값 중 하나를 받는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `RegCreateKeyTransacted` 합니다.

## <a name="regdeletekey"></a><a name="regdeletekey"></a> RegDeleteKey

레지스트리의 지정 된 플랫폼별 뷰에서 하위 키와 해당 값을 트랜잭션 작업으로 삭제 합니다.

```cpp
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>매개 변수

*hKey*\
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*\
삭제할 키의 이름입니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `RegDeleteKeyTransacted` 합니다.

## <a name="regopenkeyex"></a><a name="regopenkeyex"></a> RegOpenKeyEx

지정 된 레지스트리 키를 열고 트랜잭션과 연결 합니다.

```cpp
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
열린 레지스트리 키에 대 한 핸들입니다.

*lpSubKey*<br/>
열려는 레지스트리 하위 키의 이름입니다.

*ulOptions*<br/>
이 매개 변수는 예약 되어 있으며 0 이어야 합니다.

*samDesired*<br/>
키에 대 한 액세스 권한을 지정 하는 마스크입니다.

*phkResult*<br/>
열리거나 만든 키에 대 한 핸들을 받는 변수에 대 한 포인터입니다. 키가 미리 정의 된 레지스트리 키 중 하나가 아닌 경우 `RegCloseKey` 핸들 사용을 마친 후 함수를 호출 합니다.

### <a name="return-value"></a>반환 값

함수가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 함수가 실패 하면 반환 값은 Winerror.h에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `RegOpenKeyTransacted` 합니다.

## <a name="rollback"></a><a name="rollback"></a> 롤백해야

트랜잭션이 롤백되는 것을 요청 합니다.

```cpp
inline BOOL Rollback();
```

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `RollbackTransaction` 합니다.

## <a name="setfileattributes"></a><a name="setfileattributes"></a> SetFileAttributes

파일이 나 디렉터리에 대 한 특성을 트랜잭션 작업으로 설정 합니다.

```cpp
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>매개 변수

*lpFileName*<br/>
파일 또는 디렉터리의 이름입니다.

*dwAttributes*<br/>
파일에 대해 설정할 파일 특성입니다. 자세한 내용은 [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)를 참조 하세요.

### <a name="remarks"></a>설명

이 래퍼는 함수를 호출 `SetFileAttributesTransacted` 합니다.

## <a name="see-also"></a>참고 항목

[ATL COM 데스크톱 구성 요소](../../atl/atl-com-desktop-components.md)
