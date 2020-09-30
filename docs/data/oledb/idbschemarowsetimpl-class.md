---
title: IDBSchemaRowsetImpl 클래스
ms.date: 11/04/2016
f1_keywords:
- IDBSchemaRowsetImpl
- CheckRestrictions
- IDBSchemaRowsetImpl::CheckRestrictions
- IDBSchemaRowsetImpl.CheckRestrictions
- IDBSchemaRowsetImpl::CreateSchemaRowset
- ATL::IDBSchemaRowsetImpl::CreateSchemaRowset
- CreateSchemaRowset
- IDBSchemaRowsetImpl.CreateSchemaRowset
- ATL.IDBSchemaRowsetImpl.CreateSchemaRowset
- IDBSchemaRowsetImpl::SetRestrictions
- SetRestrictions
- IDBSchemaRowsetImpl.SetRestrictions
- ATL::IDBSchemaRowsetImpl::GetRowset
- ATL.IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl<SessionClass>::GetRowset
- IDBSchemaRowsetImpl.GetRowset
- IDBSchemaRowsetImpl::GetRowset
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetRowset
- GetRowset
- ATL::IDBSchemaRowsetImpl::GetSchemas
- GetSchemas
- IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- ATL.IDBSchemaRowsetImpl.GetSchemas
- ATL::IDBSchemaRowsetImpl<SessionClass>::GetSchemas
- IDBSchemaRowsetImpl.GetSchemas
- IDBSchemaRowsetImpl::GetSchemas
helpviewer_keywords:
- IDBSchemaRowsetImpl class
- CheckRestrictions method
- CreateSchemaRowset method
- SetRestrictions method
- GetRowset method
- GetSchemas method
ms.assetid: bd7bf0d7-a1c6-4afa-88e3-cfdbdf560703
ms.openlocfilehash: d78aa23469cc0fa94498f93e9a6975e0a7c827e9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509034"
---
# <a name="idbschemarowsetimpl-class"></a>IDBSchemaRowsetImpl 클래스

스키마 행 집합에 대한 구현을 제공합니다.

## <a name="syntax"></a>구문

```cpp
template <class SessionClass>
class ATL_NO_VTABLE IDBSchemaRowsetImpl : public IDBSchemaRowset
```

### <a name="parameters"></a>매개 변수

*SessionClass*<br/>
`IDBSchemaRowsetImpl` 이 상속되는 클래스입니다. 일반적으로 이 클래스는 사용자의 세션 클래스가 됩니다.

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[CheckRestrictions](#checkrestrictions)|스키마 행 집합에 대해 제한의 유효성을 검사합니다.|
|[CreateSchemaRowset](#createschemarowset)|템플릿 매개 변수로 지정된 개체에 대한 COM 개체 작성자 함수를 구현합니다.|
|[SetRestrictions](#setrestrictions)|특정 스키마 행 집합에서 지원되는 제한을 지정합니다.|

### <a name="interface-methods"></a>인터페이스 메서드

| 속성 | 설명 |
|-|-|
|[GetRowset](#getrowset)|스키마 행 집합을 반환합니다.|
|[GetSchemas](#getschemas)|[IDBSchemaRowsetImpl::GetRowset](#getrowset)에서 액세스할 수 있는 스키마 행 집합 목록을 반환합니다.|

## <a name="remarks"></a>설명

이 클래스는 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 인터페이스 및 템플릿화된 작성자 함수 [CreateSchemaRowset](#createschemarowset)를 구현합니다.

OLE DB는 스키마 행 집합을 사용하여 공급자의 데이터에 대한 데이터를 반환합니다. 이러한 데이터를 흔히 "메타데이터"라고 합니다. 기본적으로 공급자는 `DBSCHEMA_TABLES` `DBSCHEMA_COLUMNS` `DBSCHEMA_PROVIDER_TYPES` *OLE DB 프로그래머 참조*에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 에 설명 된 대로 항상, 및를 지원 해야 합니다. 스키마 행 집합은 스키마 맵에 지정됩니다. 스키마 맵 항목에 대한 자세한 내용은 [SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry)를 참조하세요.

ATL 개체 마법사의 OLE DB 공급자 마법사는 프로젝트의 스키마 행 집합에 대한 코드를 자동으로 생성합니다. 기본적으로 마법사는 앞에서 언급 한 필수 스키마 행 집합을 지원 합니다. ATL 개체 마법사를 사용 하 여 소비자를 만드는 경우 마법사는 스키마 행 집합을 사용 하 여 올바른 데이터를 공급자에 바인딩합니다. 올바른 메타데이터를 제공하는 스키마 행 집합을 구현하지 않은 경우 마법사는 올바른 데이터를 바인딩하지 않습니다.

공급자의 스키마 행 집합을 지원하는 방법에 대한 자세한 내용은 [스키마 행 집합 지원](../../data/oledb/supporting-schema-rowsets.md)을 참조하세요.

스키마 행 집합에 대한 자세한 내용은 [OLE DB 프로그래머 참조](/previous-versions/windows/desktop/ms712921(v=vs.85)) 에서 *스키마 행 집합*을 참조하세요.

## <a name="idbschemarowsetimplcheckrestrictions"></a><a name="checkrestrictions"></a> IDBSchemaRowsetImpl:: CheckRestrictions

스키마 행 집합에 대해 제한의 유효성을 검사합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT CheckRestrictions(REFGUID rguidSchema,
   ULONG cRestrictions,  const VARIANT rgRestrictions[]);
```

#### <a name="parameters"></a>매개 변수

*rguidSchema*<br/>
[in] 요청된 스키마 행 집합 GUID에 대한 참조입니다(예: `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] 스키마 행 집합에 대해 소비자가 전달한 제한 수입니다.

*rgRestrictions*<br/>
[in] 설정할 제한 값의 길이 *cRestrictions* 배열입니다. 자세한 내용은 [Setrestrictions](#setrestrictions) *rgRestrictions* 매개 변수에 대 한 설명을 참조 하세요.

### <a name="remarks"></a>설명

`CheckRestrictions` 를 사용하여 스키마 행 집합에 대해 제한의 유효성을 검사할 수 있습니다. `DBSCHEMA_TABLES`, `DBSCHEMA_COLUMNS` 및 스키마 행 집합에 대 한 제한을 검사 `DBSCHEMA_PROVIDER_TYPES` 합니다. 이를 호출 하 여 소비자의 호출이 올바른지 확인 `IDBSchemaRowset::GetRowset` 합니다. 위에 나열된 것과 다른 스키마 행 집합을 지원하려면 이 작업을 수행할 사용자 고유의 함수를 만들어야 합니다.

`CheckRestrictions` 소비자가 올바른 제한 및 공급자가 지 원하는 올바른 제한 유형 (예: 문자열의 VT_BSTR)을 사용 하 여 [Getrowset](#getrowset) 을 호출 하 고 있는지 여부를 확인 합니다. 또한 올바른 개수의 제한이 지원되는지 확인합니다. 기본적으로 `CheckRestrictions` 는 [SetRestrictions](#setrestrictions) 호출을 통해 지정된 행 집합에서 지원되는 제한을 공급자에 요청합니다. 그런 다음 공급자가 지원하는 제한과 소비자의 제한을 비교하여 성공 또는 실패를 반환합니다.

스키마 행 집합에 대 한 자세한 내용은 Windows SDK *OLE DB 프로그래머 참조* 에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 를 참조 하세요.

## <a name="idbschemarowsetimplcreateschemarowset"></a><a name="createschemarowset"></a> IDBSchemaRowsetImpl:: CreateSchemaRowset

템플릿 매개 변수로 지정된 개체에 대한 COM 개체 작성자 함수를 구현합니다.

### <a name="syntax"></a>구문

```cpp
template template <class SchemaRowsetClass>
HRESULT CreateSchemaRowset(IUnknown *pUnkOuter,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown** ppRowset,
   SchemaRowsetClass*& pSchemaRowset);
```

#### <a name="parameters"></a>매개 변수

*pUnkOuter*<br/>
진행 집계할 때 외부 [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) 이 고, 그렇지 않으면 NULL입니다.

*cRestrictions*<br/>
[in] 스키마 행 집합에 적용된 제한 수입니다.

*rgRestrictions*<br/>
[in] 행 집합에 적용할 `cRestrictions`**VARIANT**배열입니다.

*riid*<br/>
진행 출력에 대해 [QueryInterface](../../atl/queryinterface.md) 할 인터페이스 `IUnknown` 입니다.

*cPropertySets*<br/>
[in] 설정할 속성 집합 수입니다.

*rgPropertySets*<br/>
[in] 설정할 속성을 지정하는 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열입니다.

*ppRowset*<br/>
제한이 `IUnknown` *Riid*가 요청한 보내는입니다. `IUnknown`스키마 행 집합 개체의 인터페이스입니다.

*pSchemaRowset*<br/>
[out] 스키마 행 집합 클래스의 인스턴스에 대한 포인터입니다. 일반적으로 이 매개 변수는 사용되지 않지만 COM 개체로 전달하기 전에 스키마 행 집합에서 추가 작업을 수행해야 하는 경우에 사용될 수 있습니다. *PSchemaRowset* 의 수명은 *ppRowset*에 의해 바인딩됩니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

이 함수는 모든 형식의 스키마 행 집합에 대한 제네릭 작성자를 구현합니다. 일반적으로 사용자는 이 함수를 호출하지 않습니다. 스키마 맵 구현에 의해 호출됩니다.

## <a name="idbschemarowsetimplsetrestrictions"></a><a name="setrestrictions"></a> IDBSchemaRowsetImpl:: SetRestrictions 사항

특정 스키마 행 집합에서 지원되는 제한을 지정합니다.

### <a name="syntax"></a>구문

```cpp
void SetRestrictions(ULONG cRestrictions,
   GUID* /* rguidSchema */,
   ULONG* rgRestrictions);
```

#### <a name="parameters"></a>매개 변수

*cRestrictions*<br/>
진행 *RgRestrictions* 배열의 제한 수와 *rguidSchema* 배열의 guid 수입니다.

*rguidSchema*<br/>
[in] 제한을 페치할 스키마 행 집합의 GUID 배열입니다. 각 배열 요소는 스키마 행 집합 하나의 GUID를 포함합니다(예: `DBSCHEMA_TABLES`).

*rgRestrictions*<br/>
[in] 설정할 제한 값의 길이 *cRestrictions* 배열입니다. 각 요소는 GUID로 식별되는 스키마 행 집합에 대한 제한에 해당합니다. 공급자가 스키마 행 집합을 지원하지 않는 경우 요소는 0으로 설정됩니다. 그렇지 않은 경우에는 **ULONG** 값에 해당 스키마 행 집합에서 지원되는 제한을 나타내는 비트 마스크가 포함됩니다. 특정 스키마 행 집합에 해당 하는 제한 사항에 대 한 자세한 내용은 Windows SDK *OLE DB 프로그래머 참조* 에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 의 스키마 행 집합 guid 표를 참조 하세요.

### <a name="remarks"></a>설명

`IDBSchemaRowset`개체는 `SetRestrictions` 를 호출 하 여 특정 스키마 행 집합에서 지원 되는 제한 사항을 확인 합니다 .이는 캐스팅 되지 않은 된 포인터를 통해 [getschemas](#getschemas) 에 의해 호출 됩니다. 제한을 통해 소비자는 일치하는 행만 페치할 수 있습니다. 예를 들어 "MyTable" 테이블의 모든 열을 찾을 수 있습니다. 제한은 선택 사항이므로 지원되는 제한이 없는 경우(기본값) 항상 모든 데이터가 반환됩니다.

이 메서드의 기본 구현에서는 *rgRestrictions* 배열 요소를 0으로 설정 합니다. 기본값 이외의 다른 제한을 설정하도록 세션 클래스의 기본값을 재정의합니다.

스키마 행 집합 지원 구현에 대한 자세한 내용은 [스키마 행 집합 지원](../../data/oledb/supporting-schema-rowsets.md)을 참조하세요.

스키마 행 집합을 지원하는 공급자에 대한 예제는 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV) 샘플을 참조하세요.

스키마 행 집합에 대 한 자세한 내용은 Windows SDK *OLE DB 프로그래머 참조* 에서 [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) 를 참조 하세요.

## <a name="idbschemarowsetimplgetrowset"></a><a name="getrowset"></a> IDBSchemaRowsetImpl:: GetRowset

스키마 행 집합을 반환합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetRowset)(IUnknown *pUnkOuter,
   REFGUID rguidSchema,
   ULONG cRestrictions,
   const VARIANT rgRestrictions[],
   REFIID riid,
   ULONG cPropertySets,
   DBPROPSET rgPropertySets[],
   IUnknown **ppRowset);
```

#### <a name="parameters"></a>매개 변수

*pUnkOuter*<br/>
진행 `IUnknown` 집계할 때 외부이 고, 그렇지 않으면 NULL입니다.

*rguidSchema*<br/>
[in] 요청된 스키마 행 집합 GUID에 대한 참조입니다(예: `DBSCHEMA_TABLES`).

*cRestrictions*<br/>
[in] 행 집합에 적용할 제한 수입니다.

*rgRestrictions*<br/>
[in] 제한을 나타내는 `cRestrictions`**VARIANT**배열입니다.

*riid*<br/>
[in] 새로 만든 스키마 행 집합의 요청에 대한 IID입니다.

*cPropertySets*<br/>
[in] 설정할 속성 집합 수입니다.

*rgPropertySets*<br/>
[in/out] 새로 만든 스키마 행 집합에 설정할 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열입니다.

*ppRowset*<br/>
[out] 새로 만든 스키마 행 집합에서 요청된 인터페이스에 대한 포인터입니다.

### <a name="remarks"></a>설명

이 메서드를 사용하려면 사용자에게 세션 클래스의 스키마 맵이 있어야 합니다. `GetRowset` *RguidSchema* 매개 변수가 맵 항목 guid 중 하 나와 같은 경우 스키마 맵 정보를 사용 하 여 지정 된 행 집합 개체를 만듭니다. 맵 항목에 대한 설명은 [SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry) 를 참조하세요.

Windows SDK에서 [IDBSchemaRowset:: GetRowset](/previous-versions/windows/desktop/ms722634(v=vs.85)) 를 참조 하세요.

## <a name="idbschemarowsetimplgetschemas"></a><a name="getschemas"></a> IDBSchemaRowsetImpl:: GetSchemas

[IDBSchemaRowsetImpl::GetRowset](#getrowset)에서 액세스할 수 있는 스키마 행 집합 목록을 반환합니다.

### <a name="syntax"></a>구문

```cpp
STDMETHOD (GetSchema s )(ULONG * pcSchemas,
   GUID ** prgSchemas,
   ULONG** prgRest);
```

#### <a name="parameters"></a>매개 변수

*pcSchemas*<br/>
[out] 스키마 수로 채워진 **ULONG** 의 포인터입니다.

*prgSchemas*<br/>
[out] 스키마 행 집합 GUID 배열의 포인터로 채워진 GUID 배열의 포인터입니다.

*prgRest*<br/>
[out] 제한 배열로 채울 **ULONG**배열의 포인터입니다.

### <a name="remarks"></a>설명

이 메서드는 공급자가 지원하는 모든 스키마 행 집합의 배열을 반환합니다. Windows SDK [IDBSchemaRowset:: GetSchemas](/previous-versions/windows/desktop/ms719605(v=vs.85)) 를 참조 하세요.

이 함수를 구현하려면 사용자에게 세션 클래스의 스키마 맵이 있어야 합니다. 스키마 맵 정보를 사용하는 경우 맵의 스키마에 대한 GUID 배열로 응답합니다. 이는 공급자가 지원하는 스키마를 나타냅니다.

## <a name="see-also"></a>참고 항목

[스키마 행 집합 클래스 및 Typedef 클래스](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)<br/>
[스키마 행 집합 지원](../../data/oledb/supporting-schema-rowsets.md)<br/>
[SCHEMA_ENTRY](./macros-for-ole-db-provider-templates.md#schema_entry)<br/>
[UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider)
