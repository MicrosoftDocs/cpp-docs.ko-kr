---
description: '자세히 알아보기: CSettingsStore 클래스'
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: a1e2e52c59c4c7cf6139e1215c901a49095616b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342893"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Windows API 함수를 래핑하여 레지스트리에 액세스하는 데 사용할 수 있는 개체 지향 인터페이스를 제공합니다.

## <a name="syntax"></a>구문

```
class CSettingsStore : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSettingsStore:: CSettingsStore](#csettingsstore)|`CSettingsStore` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CSettingsStore:: Close](#close)|열린 레지스트리 키를 닫습니다.|
|[CSettingsStore:: CreateKey](#createkey)|지정 된 키가 없는 경우 해당 키를 열거나 만듭니다.|
|[CSettingsStore::D eleteKey](#deletekey)|지정 된 키와 모든 자식을 삭제 합니다.|
|[CSettingsStore::D eleteValue](#deletevalue)|열려 있는 키의 지정 된 값을 삭제 합니다.|
|[CSettingsStore:: Open](#open)|지정 된 키를 엽니다.|
|[CSettingsStore:: Read](#read)|지정 된 키 값에 대 한 데이터를 검색 합니다.|
|[CSettingsStore:: Write](#write)|레지스트리의 열기 키 아래에 값을 씁니다.|

## <a name="remarks"></a>설명

및 멤버 함수 `CreateKey` 는 `Open` 매우 유사 합니다. 레지스트리 키가 이미 있으면 `CreateKey` `Open` 동일한 방식으로 작동 합니다. 그러나 레지스트리 키가 존재 하지 않는 경우는 해당 키를 `CreateKey` 만들며 `Open` 는 오류 값을 반환 합니다.

## <a name="example"></a>예제

다음 예제에서는 클래스의 Open 및 Read 메서드를 사용 하는 방법을 보여 줍니다 `CSettingsStore` . 이 코드 조각은 [도구 설명 데모 샘플](../../overview/visual-cpp-samples.md)의 일부입니다.

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>요구 사항

**헤더:** afxsettingsstore

## <a name="csettingsstoreclose"></a><a name="close"></a> CSettingsStore:: Close

열린 레지스트리 키를 닫습니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

기본적으로이 메서드는 [Csettingsstore 클래스](../../mfc/reference/csettingsstore-class.md)의 소멸자에서 호출 됩니다.

## <a name="csettingsstorecreatekey"></a><a name="createkey"></a> CSettingsStore:: CreateKey

레지스트리 키가 없으면 새로 만듭니다.

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>매개 변수

*pszPath*<br/>
진행 만들거나 열 키의 이름을 지정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 0입니다. 그렇지 않으면 0이 아닌 값입니다.

### <a name="remarks"></a>설명

`CreateKey` 은 `m_hKey` 레지스트리 문의 루트로을 사용 합니다. *PszPath* 를의 하위 키로 검색 `m_hKey` 합니다. 키가 없는 경우에서 해당 키를 `CreateKey` 만듭니다. 그렇지 않으면 키를 엽니다. `CreateKey` 그런 다음 `m_hKey` 를 만들거나 열린 키로 설정 합니다.

## <a name="csettingsstorecsettingsstore"></a><a name="csettingsstore"></a> CSettingsStore:: CSettingsStore

`CSettngsStore` 개체를 만듭니다.

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>매개 변수

*bAdmin*<br/>
진행 개체가 관리자 모드에서 작동 하는지 여부를 지정 하는 부울 매개 변수입니다 `CSettingsStore` .

*bReadOnly*<br/>
진행 `CSettingsStore` 읽기 전용 모드에서 개체가 생성 되는지 여부를 지정 하는 부울 매개 변수입니다.

### <a name="remarks"></a>설명

*Badmin* 이 TRUE로 설정 된 경우 `m_hKey` 멤버 변수는 **HKEY_LOCAL_MACHINE** 로 설정 됩니다. *Badmin* 을 FALSE로 설정 하면 `m_hKey` 이 **HKEY_CURRENT_USER** 로 설정 됩니다.

보안 액세스는 *Breadonly* 매개 변수에 따라 달라 집니다. *Breadonly* 가 FALSE 인 경우 보안 액세스는 **KEY_ALL_ACCESS** 로 설정 됩니다. *BReadyOnly* 가 TRUE 이면 보안 액세스는 **KEY_QUERY_VALUE KEY_NOTIFY** 및 **KEY_ENUMERATE_SUB_KEYS** 의 조합으로 설정 됩니다. 레지스트리와 함께 보안 액세스에 대 한 자세한 내용은 [레지스트리 키 보안 및 액세스 권한](/windows/win32/SysInfo/registry-key-security-and-access-rights)을 참조 하세요.

에 대 한 소멸자는 `CSettingsStore` `m_hKey` 자동으로 해제 됩니다.

## <a name="csettingsstoredeletekey"></a><a name="deletekey"></a> CSettingsStore::D eleteKey

레지스트리에서 키와 모든 자식을 삭제 합니다.

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>매개 변수

*pszPath*<br/>
진행 삭제할 키의 이름입니다.

*bAdmin*<br/>
진행 삭제할 키의 위치를 지정 하는 스위치입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

개체가 읽기 전용 모드인 경우이 메서드는 실패 합니다 `CSettingsStore` .

*Badmin* 매개 변수가 0 인 경우 `DeleteKey` **HKEY_CURRENT_USER** 에서 삭제할 키를 검색 합니다. *Badmin* 이 0이 아닌 경우는 `DeleteKey` **HKEY_LOCAL_MACHINE** 에서 삭제할 키를 검색 합니다.

## <a name="csettingsstoredeletevalue"></a><a name="deletevalue"></a> CSettingsStore::D eleteValue

에서 값을 삭제 `m_hKey` 합니다.

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>매개 변수

*pszValue*<br/>
진행 제거할 값 필드를 지정 합니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

## <a name="csettingsstoreopen"></a><a name="open"></a> CSettingsStore:: Open

레지스트리 키를 엽니다.

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>매개 변수

*pszPath*<br/>
진행 레지스트리 키의 이름입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 메서드는 지정 된 키를 성공적으로 연 후 `m_hKey` 이 키의 핸들로 설정 합니다.

## <a name="csettingsstoreread"></a><a name="read"></a> CSettingsStore:: Read

레지스트리의 키에서 값을 읽습니다.

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>매개 변수

*pszKey*<br/>
진행 레지스트리에서 읽을 값의 이름을 포함 하는 null로 끝나는 문자열에 대 한 포인터입니다.

*iVal*<br/>
제한이 레지스트리 키에서 읽은 값을 수신 하는 정수 변수에 대 한 참조입니다.

*dwVal*<br/>
제한이 레지스트리 키에서 읽은 값을 수신 하는 32 비트 더블 워드 변수에 대 한 참조입니다.

*sVal*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 문자열 변수에 대 한 참조입니다.

*scStringList*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 문자열 목록 변수에 대 한 참조입니다.

*scArray*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 문자열 배열 변수에 대 한 참조입니다.

*dwcArray*<br/>
제한이 레지스트리 키에서 읽은 값을 수신 하는 32 비트 더블 워드 배열 변수에 대 한 참조입니다.

*wcArray*<br/>
제한이 레지스트리 키에서 읽은 값을 수신 하는 16 비트 단어 배열 변수에 대 한 참조입니다.

*bcArray*<br/>
제한이 레지스트리 키에서 읽은 값을 수신 하는 바이트 배열 변수에 대 한 참조입니다.

*lpPoint*<br/>
제한이 `POINT` 레지스트리 키에서 읽은 값을 수신 하는 구조체에 대 한 포인터에 대 한 참조입니다.

*rect*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 변수에 대 한 참조입니다.

*ppData*<br/>
제한이 레지스트리 키에서 읽은 값을 수신 하는 데이터에 대 한 포인터에 대 한 포인터입니다.

*pBytes*<br/>
제한이 부호 없는 정수 변수에 대 한 포인터입니다. 이 변수는 *Ppdata* 가 가리키는 버퍼의 크기를 수신 합니다.

*list*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 [CObList](../../mfc/reference/coblist-class.md) 변수에 대 한 참조입니다.

*obj*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 [CObject](../../mfc/reference/cobject-class.md) 변수에 대 한 참조입니다.

*pObj*<br/>
제한이 레지스트리 키에서 읽은 값을 받는 변수에 대 한 포인터에 대 한 참조 `CObject` 입니다.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`Read` 의 하위 키로 *pszKey* 를 확인 `m_hKey` 합니다.

## <a name="csettingsstorewrite"></a><a name="write"></a> CSettingsStore:: Write

레지스트리의 열기 키 아래에 값을 씁니다.

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>매개 변수

*pszKey*<br/>
진행 설정할 값의 이름을 포함 하는 문자열에 대 한 포인터입니다.

*iVal*<br/>
진행 저장할 데이터를 포함 하는 정수 변수에 대 한 참조입니다.

*dwVal*<br/>
진행 저장할 데이터를 포함 하는 32 비트 더블 워드 변수에 대 한 참조입니다.

*pszVal*<br/>
진행 저장할 데이터를 포함 하는 null로 끝나는 문자열 변수에 대 한 포인터입니다.

*scStringList*<br/>
진행 저장할 데이터를 포함 하는 [CStringList](../../mfc/reference/cstringlist-class.md) 변수에 대 한 참조입니다.

*bcArray*<br/>
진행 저장할 데이터를 포함 하는 바이트 배열 변수에 대 한 참조입니다.

*scArray*<br/>
진행 저장할 데이터를 포함 하는 문자열 배열 변수에 대 한 참조입니다.

*dwcArray*<br/>
진행 저장할 데이터를 포함 하는 32 비트 더블 워드 배열 변수에 대 한 참조입니다.

*wcArray*<br/>
진행 저장할 데이터를 포함 하는 16 비트 단어 배열 변수에 대 한 참조입니다.

*rect*<br/>
진행 저장할 데이터를 포함 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 변수에 대 한 참조입니다.

*lpPoint*<br/>
진행 `POINT` 저장할 데이터를 포함 하는 변수에 대 한 포인터에 대 한 참조입니다.

*pData*<br/>
진행 저장할 데이터를 포함 하는 버퍼에 대 한 포인터입니다.

*nBytes*<br/>
진행 *.Pdata* 매개 변수가 가리키는 데이터의 크기 (바이트)를 지정 합니다.

*list*<br/>
진행 저장할 데이터를 포함 하는 [CObList](../../mfc/reference/coblist-class.md) 변수에 대 한 참조입니다.

*obj*<br/>
진행 저장할 데이터를 포함 하는 [CObject](../../mfc/reference/cobject-class.md) 변수에 대 한 참조입니다.

*pObj*<br/>
진행 `CObject` 저장할 데이터를 포함 하는 변수에 대 한 포인터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 TRUE이고, 실패하면 FALSE입니다.

### <a name="remarks"></a>설명

레지스트리에 쓰려면 [Csettingsstore](../../mfc/reference/csettingsstore-class.md) 개체를 만들 때 *breadonly* 를 0이 아닌 값으로 설정 해야 합니다. 자세한 내용은 [csettingsstore:: csettingsstore](#csettingsstore)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[클래스](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx 클래스](../../mfc/reference/cwinappex-class.md)
