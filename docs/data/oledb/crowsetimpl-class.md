---
description: '자세히 알아보기: CRowsetImpl 클래스'
title: CRowsetImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- CRowsetImpl
- ATL.CRowsetImpl
- ATL::CRowsetImpl
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
- CRowsetImpl.GetColumnInfo
- CRowsetImpl::GetColumnInfo
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
- CRowsetImpl.m_rgRowData
- CRowsetImpl::m_rgRowData
- CRowsetImpl::m_strCommandText
- CRowsetImpl.m_strCommandText
- CRowsetImpl::m_strIndexText
- CRowsetImpl.m_strIndexText
helpviewer_keywords:
- CRowsetImpl class
- NameFromDBID method
- SetCommandText method
- GetColumnInfo method
- GetCommandFromID method
- ValidateCommandID method
- m_rgRowData
- m_strCommandText
- m_strIndexText
ms.assetid: e97614b3-b11d-4806-a0d3-b9401331473f
ms.openlocfilehash: e517806cc7083700d4fad7fc053777b11a7de665
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268446"
---
# <a name="crowsetimpl-class"></a>CRowsetImpl 클래스

여러 구현 인터페이스를 여러 번 상속 하지 않고도 표준 OLE DB 행 집합 구현을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
template <
   class T,
   class Storage,
   class CreatorClass,
   class ArrayType = CAtlArray<Storage>,
   class RowClass = CSimpleRow,
   class RowsetInterface = IRowsetImpl <T, IRowset>
>
class CRowsetImpl :
   public CComObjectRootEx<CreatorClass::_ThreadModel>,
   public CRowsetBaseImpl<T, Storage, ArrayType, RowsetInterface>,
   public IRowsetInfoImpl<T, CreatorClass::_PropClass>
```

### <a name="parameters"></a>매개 변수

*T*<br/>
에서 파생 되는 사용자의 클래스 `CRowsetImpl` 입니다.

*스토리지*<br/>
사용자 레코드 클래스입니다.

*CreatorClass*<br/>
행 집합에 대 한 속성을 포함 하는 클래스입니다. 일반적으로 명령입니다.

*ArrayType*<br/>
행 집합 데이터의 저장소 역할을 하는 클래스입니다. 이 매개 변수는 기본적으로로 설정 `CAtlArray` 되지만 필요한 기능을 지 원하는 모든 클래스가 될 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[NameFromDBID](#namefromdbid)|에서 문자열을 추출 하 여 `DBID` 전달 된 *bstr* 에 복사 합니다.|
|[SetCommandText](#setcommandtext)|의 유효성을 검사 하 고 `DBID` 두 문자열에 저장 합니다 ([m_strCommandText](#strcommandtext) 및 [m_strIndexText](#strindextext)).|

### <a name="overridable-methods"></a>재정의 가능한 메서드

| Name | 설명 |
|-|-|
|[GetColumnInfo](#getcolumninfo)|특정 클라이언트 요청에 대 한 열 정보를 검색 합니다.|
|[GetCommandFromID](#getcommandfromid)|두 매개 변수 중 하나에 문자열 값이 포함 되어 있는지 확인 하 고, 그럴 경우 문자열 값을 [m_strCommandText](#strcommandtext) 데이터 멤버에 복사 하 고 [m_strIndexText](#strindextext)합니다.|
|[ValidateCommandID](#validatecommandid)|둘 중 하나 또는 둘 다에 `DBID` 문자열 값이 포함 되어 있는지 확인 하 고, 그럴 경우 [m_strCommandText](#strcommandtext) 하 고 [m_strIndexText](#strindextext)를 데이터 멤버에 복사 합니다.|

### <a name="data-members"></a>데이터 멤버

| Name | 설명 |
|-|-|
|[m_rgRowData](#rgrowdata)|기본적으로에 대 한 `CAtlArray` 사용자 레코드 템플릿 인수에 templatizes 하는입니다 `CRowsetImpl` . 다른 배열 형식 클래스는 템플릿 인수를로 변경 하 여 사용할 수 있습니다 `ArrayType` `CRowsetImpl` .|
|[m_strCommandText](#strcommandtext)|행 집합의 초기 명령을 포함 합니다.|
|[m_strIndexText](#strindextext)|행 집합의 초기 인덱스를 포함 합니다.|

## <a name="remarks"></a>설명

`CRowsetImpl` 정적 upcasts의 형태로 재정의를 제공 합니다. 메서드는 지정 된 행 집합이 명령 텍스트의 유효성을 검사 하는 방식을 제어 합니다. `CRowsetImpl`구현 인터페이스를 다중 상속 하도록 설정 하 여 사용자 지정 스타일 클래스를 만들 수 있습니다. 구현을 제공 해야 하는 유일한 방법은 `Execute` 입니다. 만든 행 집합의 유형에 따라 작성자 메서드는에 대해 서로 다른 서명을 사용할 것 `Execute` 입니다. 예를 들어, 파생 클래스를 사용 하 여 `CRowsetImpl` 스키마 행 집합을 구현 하는 경우 `Execute` 메서드의 시그니처는 다음과 같습니다.

`HRESULT Execute(LONG* pcRows, ULONG cRestrictions, const VARIANT* rgRestrictions)`

`CRowsetImpl`파생 클래스를 만들어 명령 또는 세션의 행 집합을 구현 하는 경우 `Execute` 메서드는 다음과 같은 시그니처를 갖게 됩니다.

`HRESULT Execute(LONG* pcRows, DBPARAMS* pParams)`

파생 메서드를 구현 하려면 `CRowsetImpl` `Execute` 내부 데이터 버퍼 ([m_rgRowData](#rgrowdata))를 채워야 합니다.

## <a name="crowsetimplnamefromdbid"></a><a name="namefromdbid"></a> CRowsetImpl:: NameFromDBID

에서 문자열을 추출 하 여 `DBID` 전달 된 *bstr* 에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,
   CComBSTR& bstr,
   bool bIndex);
```

#### <a name="parameters"></a>매개 변수

*기타 입찰*<br/>
진행 문자열을 추출할에 대 한 포인터입니다 `DBID` .

*bstr*<br/>
진행 문자열의 복사본을 저장 하는 [CComBSTR](../../atl/reference/ccombstr-class.md) 참조 `DBID` 입니다.

*bIndex*<br/>
[in] **`true`** 인덱스 이면 `DBID` 이 고, **`false`** 테이블의 경우입니다 `DBID` .

### <a name="return-value"></a>반환 값

표준 HRESULT입니다. `DBID`가 테이블 인지 인덱스 ( *bindex* 로 표시 됨) 인지에 따라 메서드는 DB_E_NOINDEX 또는 DB_E_NOTABLE을 반환 합니다.

### <a name="remarks"></a>설명

이 메서드는 `CRowsetImpl` [Validatecom마나트](#validatecommandid) 의 구현 및 [getcommandfromid](#getcommandfromid)에서 호출 됩니다.

## <a name="crowsetimplsetcommandtext"></a><a name="setcommandtext"></a> CRowsetImpl:: SetCommandText

의 유효성을 검사 하 고 `DBID` 두 문자열에 저장 합니다 ([m_strCommandText](#strcommandtext) 및 [m_strIndexText](#strindextext)).

### <a name="syntax"></a>구문

```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>매개 변수

*pTableID*<br/>
진행 테이블 ID를 나타내는에 대 한 포인터 `DBID` 입니다.

*pIndexID*<br/>
진행 인덱스 ID를 나타내는에 대 한 포인터 `DBID` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

`SetCommentText`메서드는 `CreateRowset` 의 정적 템플릿 화 메서드인에 의해 호출 됩니다 `IOpenRowsetImpl` .

이 메서드는 캐스팅 되지 않은 된 포인터를 통해 [validatecom마나트](#validatecommandid) 및 [getcommandfromid](#getcommandfromid) 를 호출 하 여 작업을 위임 합니다.

## <a name="crowsetimplgetcolumninfo"></a><a name="getcolumninfo"></a> CRowsetImpl:: GetColumnInfo

특정 클라이언트 요청에 대 한 열 정보를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
static ATLCOLUMNINFO* CRowsetBaseImpl::GetColumnInfo(T* pv,
   ULONG* pcCols);
```

#### <a name="parameters"></a>매개 변수

*pv*<br/>
진행 사용자의 파생 클래스에 대 한 포인터 `CRowsetImpl` 입니다.

*pcCols*<br/>
진행 반환 되는 열 수에 대 한 포인터 (출력)입니다.

### <a name="return-value"></a>반환 값

정적 구조체에 대 한 포인터 `ATLCOLUMNINFO` 입니다.

### <a name="remarks"></a>설명

이 메서드는 고급 재정의입니다.

이 메서드는 특정 클라이언트 요청에 대 한 열 정보를 검색 하기 위해 여러 기본 구현 클래스에서 호출 됩니다. 일반적으로이 메서드는에 의해 호출 됩니다 `IColumnsInfoImpl` . 이 메서드를 재정의 하는 경우 파생 클래스에 메서드 버전을 두어야 합니다 `CRowsetImpl` . 메서드는 비 템플릿 화 클래스에 배치 될 수 있으므로 *pv* 를 적절 한 파생 클래스로 변경 해야 합니다 `CRowsetImpl` .

다음 예제에서는 사용법을 보여 줍니다 `GetColumnInfo` . 이 예제에서는 `CMyRowset` `CRowsetImpl` 파생 클래스입니다. `GetColumnInfo`이 클래스의 모든 인스턴스에 대해를 재정의 하려면 클래스 정의에 다음 메서드를 추가 합니다 `CMyRowset` .

[!code-cpp[NVC_OLEDB_Provider#1](../../data/oledb/codesnippet/cpp/crowsetimpl-getcolumninfo_1.h)]

## <a name="crowsetimplgetcommandfromid"></a><a name="getcommandfromid"></a> CRowsetImpl:: GetCommandFromID

두 매개 변수 중 하나에 문자열 값이 포함 되어 있는지 확인 하 고, 그럴 경우 문자열 값을 [m_strCommandText](#strcommandtext) 데이터 멤버에 복사 하 고 [m_strIndexText](#strindextext)합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>매개 변수

*pTableID*<br/>
진행 테이블 ID를 나타내는에 대 한 포인터 `DBID` 입니다.

*pIndexID*<br/>
진행 인덱스 ID를 나타내는에 대 한 포인터 `DBID` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 `CRowsetImpl` [m_strCommandText](#strcommandtext) 및 [m_strIndexText](#strindextext)데이터 멤버를 채우도록 정적 업 캐스트를 통해 호출 됩니다. 기본적으로이 메서드는 두 매개 변수 중 하나에 문자열 값이 포함 되어 있는지 여부를 확인 합니다. 문자열 값을 포함 하는 경우이 메서드는 문자열 값을 데이터 멤버에 복사 합니다. 파생 클래스에서이 시그니처에 메서드를 배치 하면 `CRowsetImpl` 기본 구현 대신 메서드가 호출 됩니다.

## <a name="crowsetimplvalidatecommandid"></a><a name="validatecommandid"></a> CRowsetImpl:: Validatecom마나트

둘 중 하나 또는 둘 다에 `DBID` 문자열 값이 포함 되어 있는지 확인 하 고, 그럴 경우 [m_strCommandText](#strcommandtext) 하 고 [m_strIndexText](#strindextext)를 데이터 멤버에 복사 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,
   DBID* pIndexID);
```

#### <a name="parameters"></a>매개 변수

*pTableID*<br/>
진행 테이블 ID를 나타내는에 대 한 포인터 `DBID` 입니다.

*pIndexID*<br/>
진행 인덱스 ID를 나타내는에 대 한 포인터 `DBID` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 `CRowsetImpl` [m_strCommandText](#strcommandtext) 및 [m_strIndexText](#strindextext)데이터 멤버를 채우기 위해 정적 업 캐스트를 통해 호출 됩니다. 기본적으로이 메서드는 둘 중 하나 또는 둘 다에 `DBID` 문자열 값이 포함 되어 있는지 확인 하 고, 그럴 경우 데이터 멤버에 복사 합니다. 파생 클래스에서이 시그니처에 메서드를 배치 하면 `CRowsetImpl` 기본 구현 대신 메서드가 호출 됩니다.

## <a name="crowsetimplm_rgrowdata"></a><a name="rgrowdata"></a> CRowsetImpl:: m_rgRowData

기본적으로에 대 한 `CAtlArray` 사용자 레코드 템플릿 인수에 templatizes 하는입니다 `CRowsetImpl` .

### <a name="syntax"></a>구문

```cpp
ArrayType CRowsetBaseImpl::m_rgRowData;
```

### <a name="remarks"></a>설명

*ArrayType* 은에 대 한 템플릿 매개 변수입니다 `CRowsetImpl` .

## <a name="crowsetimplm_strcommandtext"></a><a name="strcommandtext"></a> CRowsetImpl:: m_strCommandText

행 집합의 초기 명령을 포함 합니다.

### <a name="syntax"></a>Syntax

```cpp
CComBSTR CRowsetBaseImpl::m_strCommandText;
```

## <a name="crowsetimplm_strindextext"></a><a name="strindextext"></a> CRowsetImpl:: m_strIndexText

행 집합의 초기 인덱스를 포함 합니다.

### <a name="syntax"></a>구문

```cpp
CComBSTR CRowsetBaseImpl::m_strIndexText;
```
