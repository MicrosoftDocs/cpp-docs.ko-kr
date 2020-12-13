---
description: '자세한 정보: CRegKey 클래스'
title: CRegKey 클래스
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: f95a4f165d2d2d3d964c74c0c2c07db7a03e6fb3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140870"
---
# <a name="cregkey-class"></a>CRegKey 클래스

이 클래스는 시스템 레지스트리에서 항목을 조작 하는 메서드를 제공 합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
class CRegKey
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CRegKey:: CRegKey](#cregkey)|생성자입니다.|
|[CRegKey:: ~ CRegKey](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CRegKey:: Attach](#attach)|`CRegKey` [M_hKey](#m_hkey) 멤버 핸들을로 설정 하 여이 메서드를 호출 하 여 HKEY를 개체에 연결 `hKey` 합니다.|
|[CRegKey:: Close](#close)|[M_hKey](#m_hkey) 멤버 핸들을 해제 하 고이를 NULL로 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: Create](#create)|지정 된 키가의 하위 키가 아닌 경우이 메서드를 호출 하 여 지정 된 키를 만듭니다 `hKeyParent` .|
|[CRegKey::D eleteSubKey](#deletesubkey)|레지스트리에서 지정 된 키를 제거 하려면이 메서드를 호출 합니다.|
|[CRegKey::D eleteValue](#deletevalue)|[M_hKey](#m_hkey)에서 값 필드를 제거 하려면이 메서드를 호출 합니다.|
|[CRegKey::D etach](#detach)|개체에서 [m_hKey](#m_hkey) 멤버 핸들을 분리 하 `CRegKey` 고를 NULL로 설정 하려면이 메서드를 호출 `m_hKey` 합니다.|
|[CRegKey:: EnumKey](#enumkey)|Open 레지스트리 키의 하위 키를 열거 하려면이 메서드를 호출 합니다.|
|[CRegKey:: Flush](#flush)|열려 있는 레지스트리 키의 모든 특성을 레지스트리에 쓰려면이 메서드를 호출 합니다.|
|[CRegKey:: GetKeySecurity](#getkeysecurity)|Open 레지스트리 키를 보호 하는 보안 설명자의 복사본을 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: NotifyChangeKeyValue](#notifychangekeyvalue)|이 메서드는 열린 레지스트리 키의 특성 또는 내용에 대 한 변경 내용을 호출자에 게 알립니다.|
|[CRegKey:: Open](#open)|지정 된 키를 열고 [m_hKey](#m_hkey) 을이 키의 핸들로 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryBinaryValue](#querybinaryvalue)|지정 된 값 이름에 대 한 이진 데이터를 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryDWORDValue](#querydwordvalue)|지정 된 값 이름에 대 한 DWORD 데이터를 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryGUIDValue](#queryguidvalue)|지정 된 값 이름에 대 한 GUID 데이터를 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryMultiStringValue](#querymultistringvalue)|지정 된 값 이름에 대 한 다중 문자열 데이터를 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryQWORDValue](#queryqwordvalue)|지정 된 값 이름에 대 한 QWORD(64 데이터를 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryStringValue](#querystringvalue)|지정 된 값 이름에 대 한 문자열 데이터를 검색 하려면이 메서드를 호출 합니다.|
|[CRegKey:: QueryValue](#queryvalue)|[M_hKey](#m_hkey)의 지정 된 값 필드에 대 한 데이터를 검색 하려면이 메서드를 호출 합니다. 이 메서드의 이전 버전은 더 이상 지원 되지 않으며 ATL_DEPRECATED로 표시 됩니다.|
|[CRegKey:: RecurseDeleteKey](#recursedeletekey)|레지스트리에서 지정 된 키를 제거 하 고 모든 하위 키를 명시적으로 제거 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetBinaryValue](#setbinaryvalue)|레지스트리 키의 이진 값을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetDWORDValue](#setdwordvalue)|레지스트리 키의 DWORD 값을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetGUIDValue](#setguidvalue)|레지스트리 키의 GUID 값을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetKeySecurity](#setkeysecurity)|레지스트리 키의 보안을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetKeyValue](#setkeyvalue)|지정 된 키의 지정 된 값 필드에 데이터를 저장 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetMultiStringValue](#setmultistringvalue)|레지스트리 키의 다중 문자열 값을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetQWORDValue](#setqwordvalue)|레지스트리 키의 QWORD(64 값을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetStringValue](#setstringvalue)|레지스트리 키의 문자열 값을 설정 하려면이 메서드를 호출 합니다.|
|[CRegKey:: SetValue](#setvalue)|[M_hKey](#m_hkey)의 지정 된 값 필드에 데이터를 저장 하려면이 메서드를 호출 합니다. 이 메서드의 이전 버전은 더 이상 지원 되지 않으며 ATL_DEPRECATED로 표시 됩니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CRegKey:: operator HKEY](#operator_hkey)|개체를 `CRegKey` HKEY 변환 합니다.|
|[CRegKey:: operator =](#operator_eq)|대입 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CRegKey:: m_hKey](#m_hkey)|개체와 연결 된 레지스트리 키의 핸들을 포함 `CRegKey` 합니다.|
|[CRegKey:: m_pTM](#m_ptm)|개체에 대 한 포인터 `CAtlTransactionManager`|

## <a name="remarks"></a>설명

`CRegKey` 시스템 레지스트리에서 키 및 값을 만들고 삭제 하는 메서드를 제공 합니다. 레지스트리에는 소프트웨어 버전 번호, 설치 된 하드웨어의 논리적-물리적 매핑 및 COM 개체와 같은 시스템 구성 요소에 대 한 설치 별 정의 집합이 포함 되어 있습니다.

`CRegKey` 지정 된 컴퓨터에 대 한 시스템 레지스트리에 프로그래밍 인터페이스를 제공 합니다. 예를 들어 특정 레지스트리 키를 열려면를 호출 `CRegKey::Open` 합니다. 데이터 값을 검색 하거나 수정 하려면 `CRegKey::QueryValue` `CRegKey::SetValue` 각각 또는를 호출 합니다. 키를 닫으려면를 호출 `CRegKey::Close` 합니다.

키를 닫으면 해당 레지스트리 데이터가 하드 디스크에 기록 (플러시) 됩니다. 이 프로세스는 몇 초 정도 걸릴 수 있습니다. 응용 프로그램에서 하드 디스크에 레지스트리 데이터를 명시적으로 작성 해야 하는 경우 [Regflushkey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32 함수를 호출할 수 있습니다. 그러나에서는 `RegFlushKey` 많은 시스템 리소스를 사용 하며 반드시 필요한 경우에만 호출 해야 합니다.

> [!IMPORTANT]
> 호출자가 레지스트리 위치를 지정할 수 있도록 허용 하는 모든 메서드는 신뢰할 수 없는 데이터를 읽을 가능성이 있습니다. [Regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 를 사용 하는 메서드는이 함수가 NULL로 끝나는 문자열을 명시적으로 처리 하지 않는다는 점을 고려해 야 합니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="requirements"></a>요구 사항

**헤더:** 서 기. h

## <a name="cregkeyattach"></a><a name="attach"></a> CRegKey:: Attach

`CRegKey` [M_hKey](#m_hkey) 멤버 핸들을 *HKEY* 로 설정 하 여 HKEY를 개체에 연결 하려면이 메서드를 호출 합니다.

```cpp
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>매개 변수

*hKey*<br/>
레지스트리 키의 핸들입니다.

### <a name="remarks"></a>설명

`Attach``m_hKey`가 NULL이 아닌 경우를 어설션 합니다.

## <a name="cregkeyclose"></a><a name="close"></a> CRegKey:: Close

[M_hKey](#m_hkey) 멤버 핸들을 해제 하 고이를 NULL로 설정 하려면이 메서드를 호출 합니다.

```
LONG Close() throw();
```

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 그렇지 않으면 오류 값을 반환 합니다.

## <a name="cregkeycreate"></a><a name="create"></a> CRegKey:: Create

*HKeyParent* 의 하위 키로 존재 하지 않는 경우이 메서드를 호출 하 여 지정 된 키를 만듭니다.

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*hKeyParent*<br/>
열린 키의 핸들입니다.

*lpszKeyName*<br/>
만들거나 열 키의 이름을 지정 합니다. 이 이름은 *hKeyParent* 의 하위 키 여야 합니다.

*lpszClass*<br/>
만들거나 열 키의 클래스를 지정 합니다. 기본값은 REG_NONE입니다.

*dwOptions*<br/>
키에 대 한 옵션입니다. 기본값은 REG_OPTION_NON_VOLATILE입니다. 사용할 수 있는 값 및 설명 목록은 Windows SDK의 [Regcreatekeyex](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) 를 참조 하십시오.

*samDesired*<br/>
키에 대 한 보안 액세스입니다. 기본값은 KEY_READ &#124; KEY_WRITE입니다. 사용할 수 있는 값 및 설명의 목록을 보려면을 참조 하십시오 `RegCreateKeyEx` .

*lpSecAttr*<br/>
자식 프로세스에서 키 핸들을 상속할 수 있는지 여부를 나타내는 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 구조체에 대 한 포인터입니다. 기본적으로이 매개 변수는 NULL입니다. 즉, 핸들이 상속 될 수 없습니다.

*Lstwstgga*<br/>
제한이 NULL이 아닌 경우 REG_CREATED_NEW_KEY (키가 존재 하지 않거나 만들어진 경우) 또는 REG_OPENED_EXISTING_KEY (키가 존재 하 고 열린 경우)를 검색 합니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 하 고 키를 엽니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

`Create`[m_hKey](#m_hkey) 멤버를이 키의 핸들로 설정 합니다.

## <a name="cregkeycregkey"></a><a name="cregkey"></a> CRegKey:: CRegKey

생성자입니다.

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
`CRegKey` 개체에 대한 참조입니다.

*hKey*<br/>
레지스트리 키에 대 한 핸들입니다.

*pTM*<br/>
CAtlTransactionManager 개체에 대한 포인터

### <a name="remarks"></a>설명

새 `CRegKey` 개체를 만듭니다. 개체는 기존 개체에서 만들거나 `CRegKey` 레지스트리 키에 대 한 핸들에서 만들 수 있습니다.

## <a name="cregkeycregkey"></a><a name="dtor"></a> CRegKey:: ~ CRegKey

소멸자입니다.

```
~CRegKey() throw();
```

### <a name="remarks"></a>설명

소멸자가 해제 `m_hKey` 됩니다.

## <a name="cregkeydeletesubkey"></a><a name="deletesubkey"></a> CRegKey::D eleteSubKey

레지스트리에서 지정 된 키를 제거 하려면이 메서드를 호출 합니다.

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>매개 변수

*lpszSubKey*<br/>
삭제할 키의 이름을 지정 합니다. 이 이름은 [m_hKey](#m_hkey)의 하위 키 여야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

`DeleteSubKey` 하위 키가 없는 키만 삭제할 수 있습니다. 키에 하위 키가 있는 경우 대신 [RecurseDeleteKey](#recursedeletekey) 를 호출 합니다.

## <a name="cregkeydeletevalue"></a><a name="deletevalue"></a> CRegKey::D eleteValue

[M_hKey](#m_hkey)에서 값 필드를 제거 하려면이 메서드를 호출 합니다.

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>매개 변수

*lpszValue*<br/>
제거할 값 필드를 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

## <a name="cregkeydetach"></a><a name="detach"></a> CRegKey::D etach

개체에서 [m_hKey](#m_hkey) 멤버 핸들을 분리 하 `CRegKey` 고를 NULL로 설정 하려면이 메서드를 호출 `m_hKey` 합니다.

```
HKEY Detach() throw();
```

### <a name="return-value"></a>반환 값

개체와 연결 된 HKEY `CRegKey` 입니다.

## <a name="cregkeyenumkey"></a><a name="enumkey"></a> CRegKey:: EnumKey

Open 레지스트리 키의 하위 키를 열거 하려면이 메서드를 호출 합니다.

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*iIndex*<br/>
하위 키 인덱스입니다. 이 매개 변수는 첫 번째 호출의 경우 0 이어야 하 고 후속 호출의 경우 증가 합니다.

*pszName*<br/>
종료 null 문자를 포함 하 여 하위 키의 이름을 받는 버퍼에 대 한 포인터입니다. 하위 키 이름만 버퍼에 복사 되 고 전체 키 계층 구조에는 복사 되지 않습니다.

*pnNameLength*<br/>
*PszName* 매개 변수로 지정 된 버퍼의 크기 (tchars)를 지정 하는 변수에 대 한 포인터입니다. 이 크기는 null 종결 문자를 포함 해야 합니다. 메서드가 반환 될 때 *pnNameLength* 가 가리키는 변수는 버퍼에 저장 된 문자 수를 포함 합니다. 반환 된 개수에는 null 종결 문자가 포함 되지 않습니다.

*pftLastWriteTime*<br/>
열거 된 하위 키를 마지막으로 쓴 시간을 받는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

하위 키를 열거 하려면 `CRegKey::EnumKey` 0의 인덱스를 사용 하 여를 호출 합니다. 인덱스 값을 증가 시키고 메서드가 ERROR_NO_MORE_ITEMS 반환 될 때까지 반복 합니다. 자세한 내용은 Windows SDK의 [Regenumkeyex](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) 를 참조 하세요.

## <a name="cregkeyflush"></a><a name="flush"></a> CRegKey:: Flush

열려 있는 레지스트리 키의 모든 특성을 레지스트리에 쓰려면이 메서드를 호출 합니다.

```
LONG Flush() throw();
```

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

자세한 내용은 Windows SDK의 [Regenumflush](/windows/win32/api/winreg/nf-winreg-regflushkey) 를 참조 하세요.

## <a name="cregkeygetkeysecurity"></a><a name="getkeysecurity"></a> CRegKey:: GetKeySecurity

Open 레지스트리 키를 보호 하는 보안 설명자의 복사본을 검색 하려면이 메서드를 호출 합니다.

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>매개 변수

*si*<br/>
요청 된 보안 정보를 나타내는 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information) 값입니다.

*내보내거나*<br/>
요청 된 보안 설명자의 복사본을 받는 버퍼에 대 한 포인터입니다.

*pnBytes*<br/>
*Psd* 에서 가리키는 버퍼의 크기 (바이트)입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 0이 아닌 오류 코드는 WINERROR.H에 정의 되어 있습니다.

### <a name="remarks"></a>설명

자세한 내용은 [Reggetkeysecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity)를 참조 하세요.

## <a name="cregkeym_hkey"></a><a name="m_hkey"></a> CRegKey:: m_hKey

개체와 연결 된 레지스트리 키의 핸들을 포함 `CRegKey` 합니다.

```
HKEY m_hKey;
```

## <a name="cregkeym_ptm"></a><a name="m_ptm"></a> CRegKey:: m_pTM

`CAtlTransactionManager` 개체에 대한 포인터입니다.

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>설명

## <a name="cregkeynotifychangekeyvalue"></a><a name="notifychangekeyvalue"></a> CRegKey:: NotifyChangeKeyValue

이 메서드는 열린 레지스트리 키의 특성 또는 내용에 대 한 변경 내용을 호출자에 게 알립니다.

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>매개 변수

*bWatchSubtree*<br/>
지정 된 키와 모든 하위 키에 대 한 변경 내용을 보고할지 아니면 지정 된 키만 표시할지를 나타내는 플래그를 지정 합니다. 이 매개 변수가 TRUE 이면 메서드는 키와 하위 키의 변경 내용을 보고 합니다. 매개 변수가 FALSE 이면 메서드는 키의 변경 내용만 보고 합니다.

*dwNotifyFilter*<br/>
보고 해야 하는 변경 내용을 제어 하는 플래그 집합을 지정 합니다. 이 매개 변수는 다음 값을 조합 하 여 사용할 수 있습니다.

|값|의미|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|하위 키가 추가 되거나 삭제 되 면 호출자에 게 알립니다.|
|REG_NOTIFY_CHANGE_ATTRIBUTES|보안 설명자 정보와 같은 키 특성에 대 한 변경 내용을 호출자에 게 알립니다.|
|REG_NOTIFY_CHANGE_LAST_SET|호출자에 게 키 값에 대 한 변경 내용을 알립니다. 여기에는 값을 추가 또는 삭제 하거나 기존 값을 변경할 수 있습니다.|
|REG_NOTIFY_CHANGE_SECURITY|호출자에 게 키의 보안 설명자에 대 한 변경 내용을 알립니다.|

*hEvent*<br/>
이벤트에 대한 핸들. *BAsync* 매개 변수가 TRUE 이면 메서드가 즉시 반환 되 고이 이벤트 신호를 통해 변경 내용이 보고 됩니다. *BAsync* 가 FALSE 인 경우 *hevent* 는 무시 됩니다.

*bAsync*<br/>
메서드가 변경 내용을 보고 하는 방법을 나타내는 플래그를 지정 합니다. 이 매개 변수가 TRUE 이면 메서드는 즉시 반환 하 고 지정 된 이벤트에 신호를 보내 변경 내용을 보고 합니다. 이 매개 변수가 FALSE 이면 변경 내용이 발생할 때까지 메서드가 반환 되지 않습니다. *Hevent* 가 유효한 이벤트를 지정 하지 않는 경우 *bAsync* 매개 변수는 TRUE가 될 수 없습니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

> [!NOTE]
> 이 메서드는 지정 된 키가 삭제 된 경우 호출자에 게 알리지 않습니다.

자세한 내용 및 샘플 프로그램은 [RegNotifyChangeKeyValue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue)를 참조 하세요.

## <a name="cregkeyopen"></a><a name="open"></a> CRegKey:: Open

지정 된 키를 열고 [m_hKey](#m_hkey) 을이 키의 핸들로 설정 하려면이 메서드를 호출 합니다.

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>매개 변수

*hKeyParent*<br/>
열린 키의 핸들입니다.

*lpszKeyName*<br/>
만들거나 열 키의 이름을 지정 합니다. 이 이름은 *hKeyParent* 의 하위 키 여야 합니다.

*samDesired*<br/>
키에 대 한 보안 액세스입니다. 기본값은 KEY_ALL_ACCESS입니다. 사용할 수 있는 값 및 설명 목록은 Windows SDK의 [Regcreatekeyex](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) 를 참조 하십시오.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 그렇지 않으면 WINERROR.H에 0이 아닌 오류 값이 정의 됩니다.

### <a name="remarks"></a>설명

*LpszKeyName* 매개 변수가 NULL 이거나 빈 문자열을 가리키는 경우는 hKeyParent에 `Open` 의해 식별 되는 키의 새 핸들을 열리지만 이전에 열린 핸들을 닫지 않습니다.

[Cregkey:: Create](#create)와 달리 `Open` 지정 된 키가 없는 경우에는이 키를 만들지 않습니다.

## <a name="cregkeyoperator-hkey"></a><a name="operator_hkey"></a> CRegKey:: operator HKEY

개체를 `CRegKey` HKEY 변환 합니다.

```
operator HKEY() const throw();
```

## <a name="cregkeyoperator-"></a><a name="operator_eq"></a> CRegKey:: operator =

대입 연산자입니다.

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>매개 변수

*key*<br/>
복사할 키입니다.

### <a name="return-value"></a>반환 값

새 키에 대 한 참조를 반환 합니다.

### <a name="remarks"></a>설명

이 연산자는 현재 개체에서 *키* 를 분리 하 고 `CRegKey` 대신 개체에 할당 합니다.

## <a name="cregkeyquerybinaryvalue"></a><a name="querybinaryvalue"></a> CRegKey:: QueryBinaryValue

지정 된 값 이름에 대 한 이진 데이터를 검색 하려면이 메서드를 호출 합니다.

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pValue*<br/>
값의 데이터를 받는 버퍼에 대 한 포인터입니다.

*pnBytes*<br/>
*Pvalue* 매개 변수가 가리키는 버퍼의 크기 (바이트)를 지정 하는 변수에 대 한 포인터입니다. 메서드가 반환 될 때이 변수에는 버퍼에 복사 된 데이터의 크기가 포함 됩니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 ERROR_SUCCESS 반환 됩니다. 메서드가 값을 읽지 못한 경우 WINERROR.H에 정의 된 0이 아닌 오류 코드를 반환 합니다. 참조 된 데이터가 REG_BINARY 형식이 아닌 경우 ERROR_INVALID_DATA 반환 됩니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 여 `RegQueryValueEx` 올바른 형식의 데이터가 반환 되는지 확인 합니다. 자세한 내용은 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 를 참조 하세요.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다. 또한이 메서드에서 사용 하는 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 함수는 NULL로 끝나는 문자열을 명시적으로 처리 하지 않습니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="cregkeyquerydwordvalue"></a><a name="querydwordvalue"></a> CRegKey:: QueryDWORDValue

지정 된 값 이름에 대 한 DWORD 데이터를 검색 하려면이 메서드를 호출 합니다.

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*dwValue*<br/>
DWORD를 수신 하는 버퍼에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 ERROR_SUCCESS 반환 됩니다. 메서드가 값을 읽지 못한 경우 WINERROR.H에 정의 된 0이 아닌 오류 코드를 반환 합니다. 참조 된 데이터가 REG_DWORD 형식이 아닌 경우 ERROR_INVALID_DATA 반환 됩니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 여 `RegQueryValueEx` 올바른 형식의 데이터가 반환 되는지 확인 합니다. 자세한 내용은 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 를 참조 하세요.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다. 또한이 메서드에서 사용 하는 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 함수는 NULL로 끝나는 문자열을 명시적으로 처리 하지 않습니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="cregkeyqueryguidvalue"></a><a name="queryguidvalue"></a> CRegKey:: QueryGUIDValue

지정 된 값 이름에 대 한 GUID 데이터를 검색 하려면이 메서드를 호출 합니다.

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*guidValue*<br/>
GUID를 받는 변수에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 ERROR_SUCCESS 반환 됩니다. 메서드가 값을 읽지 못한 경우 WINERROR.H에 정의 된 0이 아닌 오류 코드를 반환 합니다. 참조 된 데이터가 올바른 GUID가 아니면 ERROR_INVALID_DATA 반환 됩니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 `CRegKey::QueryStringValue` 고 [Clsidfromstring](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)을 사용 하 여 문자열을 GUID로 변환 합니다.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다.

## <a name="cregkeyquerymultistringvalue"></a><a name="querymultistringvalue"></a> CRegKey:: QueryMultiStringValue

지정 된 값 이름에 대 한 다중 문자열 데이터를 검색 하려면이 메서드를 호출 합니다.

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pszValue*<br/>
다중 문자열 데이터를 받는 버퍼에 대 한 포인터입니다. 다중 문자열는 null로 끝나는 문자열의 배열로, 두 개의 null 문자로 종료 됩니다.

*pnChars*<br/>
*PszValue* 가 가리키는 버퍼의 크기 (tchars)입니다. 메서드가 반환 될 때 *Pnchars* 는 종료 null 문자를 포함 하 여 검색 된 다중 문자열의 크기 (tchars)를 포함 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 ERROR_SUCCESS 반환 됩니다. 메서드가 값을 읽지 못한 경우 WINERROR.H에 정의 된 0이 아닌 오류 코드를 반환 합니다. 참조 된 데이터가 REG_MULTI_SZ 형식이 아닌 경우 ERROR_INVALID_DATA 반환 됩니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 여 `RegQueryValueEx` 올바른 형식의 데이터가 반환 되는지 확인 합니다. 자세한 내용은 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 를 참조 하세요.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다. 또한이 메서드에서 사용 하는 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 함수는 NULL로 끝나는 문자열을 명시적으로 처리 하지 않습니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="cregkeyqueryqwordvalue"></a><a name="queryqwordvalue"></a> CRegKey:: QueryQWORDValue

지정 된 값 이름에 대 한 QWORD(64 데이터를 검색 하려면이 메서드를 호출 합니다.

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*qwValue*<br/>
QWORD(64를 받는 버퍼에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 ERROR_SUCCESS 반환 됩니다. 메서드가 값을 읽지 못한 경우 WINERROR.H에 정의 된 0이 아닌 오류 코드를 반환 합니다. 참조 된 데이터가 REG_QWORD 형식이 아닌 경우 ERROR_INVALID_DATA 반환 됩니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 여 `RegQueryValueEx` 올바른 형식의 데이터가 반환 되는지 확인 합니다. 자세한 내용은 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 를 참조 하세요.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다. 또한이 메서드에서 사용 하는 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 함수는 NULL로 끝나는 문자열을 명시적으로 처리 하지 않습니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="cregkeyquerystringvalue"></a><a name="querystringvalue"></a> CRegKey:: QueryStringValue

지정 된 값 이름에 대 한 문자열 데이터를 검색 하려면이 메서드를 호출 합니다.

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*pszValue*<br/>
문자열 데이터를 받는 버퍼에 대 한 포인터입니다.

*pnChars*<br/>
*PszValue* 가 가리키는 버퍼의 크기 (tchars)입니다. 메서드가 반환 될 때 *Pnchars* 는 null 종결 문자를 포함 하 여 검색 된 문자열의 크기 (tchars)를 포함 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 ERROR_SUCCESS 반환 됩니다. 메서드가 값을 읽지 못한 경우 WINERROR.H에 정의 된 0이 아닌 오류 코드를 반환 합니다. 참조 된 데이터가 REG_SZ 형식이 아닌 경우 ERROR_INVALID_DATA 반환 됩니다. 메서드가 ERROR_MORE_DATA 반환 하는 경우에는 필요한 버퍼 크기 (바이트)가 아니라 *Pnchars* 가 0과 같습니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 여 `RegQueryValueEx` 올바른 형식의 데이터가 반환 되는지 확인 합니다. 자세한 내용은 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 를 참조 하세요.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다. 또한이 메서드에서 사용 하는 [regqueryvalueex가](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw) 함수는 NULL로 끝나는 문자열을 명시적으로 처리 하지 않습니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="cregkeyqueryvalue"></a><a name="queryvalue"></a> CRegKey:: QueryValue

[M_hKey](#m_hkey)의 지정 된 값 필드에 대 한 데이터를 검색 하려면이 메서드를 호출 합니다. 이 메서드의 이전 버전은 더 이상 지원 되지 않으며 ATL_DEPRECATED로 표시 됩니다.

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
쿼리할 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다. *PszValueName* 가 NULL 이거나 빈 문자열인 경우 메서드는 키의 명명 되지 않은 값 또는 기본값 (있는 경우)에 대 한 형식 및 데이터를 검색 합니다.

*pdwType*<br/>
지정 된 값에 저장 된 데이터 형식을 나타내는 코드를 받는 변수에 대 한 포인터입니다. 형식 코드가 필요 하지 않은 경우에는 *Pdwtype* 매개 변수가 NULL 일 수 있습니다.

*pData*<br/>
값의 데이터를 받는 버퍼에 대 한 포인터입니다. 데이터가 필요 하지 않은 경우이 매개 변수는 NULL 일 수 있습니다.

*pnBytes*<br/>
*.Pdata* 매개 변수가 가리키는 버퍼의 크기 (바이트)를 지정 하는 변수에 대 한 포인터입니다. 메서드가 반환 될 때이 변수에는 .Pdata로 복사 되는 데이터의 크기가 포함 *됩니다.*

*dwValue*<br/>
값 필드의 숫자 데이터입니다.

*lpszValueName*<br/>
쿼리할 값 필드를 지정 합니다.

*szValue*<br/>
값 필드의 문자열 데이터입니다.

*pdwCount*<br/>
문자열 데이터의 크기입니다. 해당 값은 처음에 *szvalue* 버퍼의 크기로 설정 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 그렇지 않으면 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

의 원래 두 버전은 `QueryValue` 더 이상 지원 되지 않으며 ATL_DEPRECATED로 표시 됩니다. 이러한 폼을 사용 하는 경우 컴파일러에서 경고를 실행 합니다.

나머지 메서드는 Regqueryvalueex가을 호출 합니다.

> [!IMPORTANT]
> 이 메서드를 사용 하면 호출자가 레지스트리 위치를 지정 하 여 신뢰할 수 없는 데이터를 읽을 수도 있습니다. 또한이 메서드에서 사용 하는 Regqueryvalueex가 함수는 NULL로 끝나는 문자열을 명시적으로 처리 하지 않습니다. 호출 코드에서 두 조건을 확인 해야 합니다.

## <a name="cregkeyrecursedeletekey"></a><a name="recursedeletekey"></a> CRegKey:: RecurseDeleteKey

레지스트리에서 지정 된 키를 제거 하 고 모든 하위 키를 명시적으로 제거 하려면이 메서드를 호출 합니다.

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>매개 변수

*lpszKey*<br/>
삭제할 키의 이름을 지정 합니다. 이 이름은 [m_hKey](#m_hkey)의 하위 키 여야 합니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 그렇지 않으면 WINERROR.H에 0이 아닌 오류 값이 정의 됩니다.

### <a name="remarks"></a>설명

키에 하위 키가 있는 경우이 메서드를 호출 하 여 키를 삭제 해야 합니다.

## <a name="cregkeysetbinaryvalue"></a><a name="setbinaryvalue"></a> CRegKey:: SetBinaryValue

레지스트리 키의 이진 값을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 아직 없는 경우 메서드는 키에 추가 합니다.

*pValue*<br/>
지정 된 값 이름으로 저장할 데이터를 포함 하는 버퍼에 대 한 포인터입니다.

*nBytes*<br/>
*Pvalue* 매개 변수가 가리키는 정보의 크기 (바이트)를 지정 합니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드는 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) 을 사용 하 여 값을 레지스트리에 씁니다.

## <a name="cregkeysetdwordvalue"></a><a name="setdwordvalue"></a> CRegKey:: SetDWORDValue

레지스트리 키의 DWORD 값을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 아직 없는 경우 메서드는 키에 추가 합니다.

*dwValue*<br/>
지정 된 값 이름으로 저장할 DWORD 데이터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드는 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) 을 사용 하 여 값을 레지스트리에 씁니다.

## <a name="cregkeysetguidvalue"></a><a name="setguidvalue"></a> CRegKey:: SetGUIDValue

레지스트리 키의 GUID 값을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 아직 없는 경우 메서드는 키에 추가 합니다.

*guidValue*<br/>
지정 된 값 이름으로 저장할 GUID에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드는를 사용 하 `CRegKey::SetStringValue` 고 [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2)를 사용 하 여 GUID를 문자열로 변환 합니다.

## <a name="cregkeysetkeyvalue"></a><a name="setkeyvalue"></a> CRegKey:: SetKeyValue

지정 된 키의 지정 된 값 필드에 데이터를 저장 하려면이 메서드를 호출 합니다.

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>매개 변수

*lpszKeyName*<br/>
만들거나 열 키의 이름을 지정 합니다. 이 이름은 [m_hKey](#m_hkey)의 하위 키 여야 합니다.

*lpszValue*<br/>
저장할 데이터를 지정 합니다. 이 매개 변수는 NULL이 아니어야 합니다.

*lpszValueName*<br/>
설정할 값 필드를 지정 합니다. 이 이름을 가진 값 필드가 키에 아직 없는 경우 추가 됩니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 그렇지 않으면 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드를 호출 하 여 *lpszKeyName* 키를 만들거나 열고 *lpszValueName* value 필드에 *lpszValue* 데이터를 저장 합니다.

## <a name="cregkeysetkeysecurity"></a><a name="setkeysecurity"></a> CRegKey:: SetKeySecurity

레지스트리 키의 보안을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>매개 변수

*si*<br/>
설정할 보안 설명자의 구성 요소를 지정 합니다. 값은 다음 값을 조합 하 여 사용할 수 있습니다.

|값|의미|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|키의 DACL (임의 액세스 제어 목록)을 설정 합니다. 키에 WRITE_DAC 액세스 권한이 있거나 호출 하는 프로세스가 개체의 소유자 여야 합니다.|
|GROUP_SECURITY_INFORMATION|키의 주 SID (보안 식별자)를 설정 합니다. 키에 WRITE_OWNER 액세스 권한이 있거나 호출 하는 프로세스가 개체의 소유자 여야 합니다.|
|OWNER_SECURITY_INFORMATION|키의 소유자 SID를 설정 합니다. 키에 WRITE_OWNER 액세스 권한이 있거나 호출 프로세스가 개체의 소유자 이거나 SE_TAKE_OWNERSHIP_NAME 권한을 설정 해야 합니다.|
|SACL_SECURITY_INFORMATION|키의 SACL (시스템 액세스 제어 목록)을 설정 합니다. 키에 ACCESS_SYSTEM_SECURITY 액세스 권한이 있어야 합니다. 이 액세스 권한을 부여 하는 적절 한 방법은 호출자의 현재 액세스 토큰에서 SE_SECURITY_NAME [권한을](/windows/win32/secauthz/privileges) 사용 하도록 설정 하 고 ACCESS_SYSTEM_SECURITY access에 대 한 핸들을 연 다음 권한을 사용 하지 않도록 설정 하는 것입니다.|

*내보내거나*<br/>
지정 된 키에 대해 설정할 보안 특성을 지정 하는 [SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor) 구조체에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

키의 보안 특성을 설정 합니다. 자세한 내용은 [Regsetkeysecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) 를 참조 하세요.

## <a name="cregkeysetmultistringvalue"></a><a name="setmultistringvalue"></a> CRegKey:: SetMultiStringValue

레지스트리 키의 다중 문자열 값을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 아직 없는 경우 메서드는 키에 추가 합니다.

*pszValue*<br/>
지정 된 값 이름으로 저장할 다중 문자열 데이터에 대 한 포인터입니다. 다중 문자열는 null로 끝나는 문자열의 배열로, 두 개의 null 문자로 종료 됩니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드는 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) 을 사용 하 여 값을 레지스트리에 씁니다.

## <a name="cregkeysetqwordvalue"></a><a name="setqwordvalue"></a> CRegKey:: SetQWORDValue

레지스트리 키의 QWORD(64 값을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 아직 없는 경우 메서드는 키에 추가 합니다.

*qwValue*<br/>
지정 된 값 이름으로 저장할 QWORD(64 데이터입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드는 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) 을 사용 하 여 값을 레지스트리에 씁니다.

## <a name="cregkeysetstringvalue"></a><a name="setstringvalue"></a> CRegKey:: SetStringValue

레지스트리 키의 문자열 값을 설정 하려면이 메서드를 호출 합니다.

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 아직 없는 경우 메서드는 키에 추가 합니다.

*pszValue*<br/>
지정 된 값 이름으로 저장할 문자열 데이터에 대 한 포인터입니다.

*dwType*<br/>
레지스트리에 쓸 문자열의 형식입니다. REG_SZ (기본값) 또는 REG_EXPAND_SZ (multistrings의 경우) 중 하나입니다.

### <a name="return-value"></a>반환 값

메서드가 성공 하면 반환 값은 ERROR_SUCCESS입니다. 메서드가 실패 하는 경우 반환 값은 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

이 메서드는 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw) 을 사용 하 여 값을 레지스트리에 씁니다.

## <a name="cregkeysetvalue"></a><a name="setvalue"></a> CRegKey:: SetValue

[M_hKey](#m_hkey)의 지정 된 값 필드에 데이터를 저장 하려면이 메서드를 호출 합니다. 이 메서드의 이전 버전은 더 이상 지원 되지 않으며 ATL_DEPRECATED로 표시 됩니다.

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>매개 변수

*pszValueName*<br/>
설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다. 이 이름을 가진 값이 키에 아직 없는 경우 메서드는 키에이를 추가 합니다. *PszValueName* 가 NULL 이거나 빈 문자열인 경우 메서드는 키의 이름이 지정 되지 않은 값 또는 기본값에 대 한 형식과 데이터를 설정 합니다.

*dwType*<br/>
*Pvalue* 매개 변수가 가리키는 데이터의 형식을 나타내는 코드를 지정 합니다.

*pValue*<br/>
지정 된 값 이름으로 저장할 데이터를 포함 하는 버퍼에 대 한 포인터입니다.

*nBytes*<br/>
*Pvalue* 매개 변수가 가리키는 정보의 크기 (바이트)를 지정 합니다. 데이터가 REG_SZ, REG_EXPAND_SZ 또는 REG_MULTI_SZ 형식인 경우 *Nbytes* 는 종료 null 문자의 크기를 포함 해야 합니다.

*hKeyParent*<br/>
열린 키의 핸들입니다.

*lpszKeyName*<br/>
만들거나 열 키의 이름을 지정 합니다. 이 이름은 *hKeyParent* 의 하위 키 여야 합니다.

*lpszValue*<br/>
저장할 데이터를 지정 합니다. 이 매개 변수는 NULL이 아니어야 합니다.

*lpszValueName*<br/>
설정할 값 필드를 지정 합니다. 이 이름을 가진 값 필드가 키에 아직 없는 경우 추가 됩니다.

*dwValue*<br/>
저장할 데이터를 지정 합니다.

*bMulti*<br/>
False 이면 문자열이 REG_SZ 형식 임을 나타냅니다. True 이면 문자열이 REG_MULTI_SZ 형식의 다중 문자열을 나타냅니다.

*nValueLen*<br/>
*Bmulti* 가 True 이면 *Nvaluelen* 은 *lpszValue* 문자열의 길이 (문자)입니다. *Bmulti* 가 false 인 경우 값이-1 이면 메서드가 자동으로 길이를 계산 함을 나타냅니다.

### <a name="return-value"></a>반환 값

성공 하면 ERROR_SUCCESS을 반환 합니다. 그렇지 않으면 WINERROR.H에 정의 된 0이 아닌 오류 코드입니다.

### <a name="remarks"></a>설명

의 두 가지 원래 버전은 `SetValue` ATL_DEPRECATED로 표시 되며 더 이상 사용할 수 없습니다. 이러한 폼을 사용 하는 경우 컴파일러에서 경고를 실행 합니다.

세 번째 메서드는 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)를 호출 합니다.

## <a name="see-also"></a>참고 항목

[DCOM 샘플](../../overview/visual-cpp-samples.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
