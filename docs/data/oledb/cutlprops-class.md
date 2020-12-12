---
description: '자세히 알아보기: 가공선 클래스'
title: CUtlProps 클래스
ms.date: 11/04/2016
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
ms.openlocfilehash: 535da4b2dd7d3214633a1e76c04be1e4627b965a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97287751"
---
# <a name="cutlprops-class"></a>CUtlProps 클래스

다양 한 OLE DB 속성 인터페이스 (예:, 및)에 대 한 속성을 구현 `IDBProperties` `IDBProperties` `IRowsetInfo` 합니다.

## <a name="syntax"></a>구문

```cpp
template < class T >
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase
```

### <a name="parameters"></a>매개 변수

*T*<br/>
을 포함 하는 클래스입니다 `BEGIN_PROPSET_MAP` .

## <a name="requirements"></a>요구 사항

**헤더:** atldb.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[GetPropValue](#getpropvalue)|속성 집합에서 속성을 가져옵니다.|
|[IsValidValue](#isvalidvalue)|속성을 설정 하기 전에 값의 유효성을 검사 하는 데 사용 됩니다.|
|[OnInterfaceRequested](#oninterfacerequested)|소비자가 개체 생성 인터페이스에서 메서드를 호출할 때 선택적 인터페이스에 대 한 요청을 처리 합니다.|
|[OnPropertyChanged](#onpropertychanged)|속성을 설정 하 여 연결 된 속성을 처리 한 후에 호출 됩니다.|
|[SetPropValue](#setpropvalue)|속성 집합의 속성을 설정 합니다.|

## <a name="remarks"></a>설명

이 클래스의 대부분은 구현 세부 정보입니다.

`CUtlProps` 내부적으로 속성을 설정 하기 위한 두 가지 멤버인 [getpropvalue](#getpropvalue) 및 [setpropvalue](#setpropvalue)가 포함 되어 있습니다.

속성 집합 맵에서 사용 되는 매크로에 대 한 자세한 내용은 [BEGIN_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#begin_propset_map) 및 [END_PROPSET_MAP](./macros-for-ole-db-provider-templates.md#end_propset_map)를 참조 하세요.

## <a name="cutlpropsgetpropvalue"></a><a name="getpropvalue"></a> 가공선 Lprops:: GetPropValue

속성 집합에서 속성을 가져옵니다.

### <a name="syntax"></a>구문

```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>매개 변수

*pguidPropSet*<br/>
진행 PropSet에 대 한 GUID입니다.

*dwPropId*<br/>
진행 속성 인덱스입니다.

*pvValue*<br/>
제한이 새 속성 값을 포함 하는 변형에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`Failure` 실패 하 고 성공 하면 S_OK 합니다.

## <a name="cutlpropsisvalidvalue"></a><a name="isvalidvalue"></a> 가공선 Lprops:: Is유효한 값

속성을 설정 하기 전에 값의 유효성을 검사 하는 데 사용 됩니다.

### <a name="syntax"></a>구문

```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>매개 변수

*iCurSet*<br/>
속성 집합 배열의 인덱스입니다. 속성 집합이 하나만 있는 경우 0입니다.

*pDBProp*<br/>
[Dbprop](/previous-versions/windows/desktop/ms717970(v=vs.85)) 구조의 속성 ID 및 새 값입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다. 기본 반환 값은 S_OK입니다.

### <a name="remarks"></a>설명

속성을 설정 하는 데 사용 하려는 값에 대해 실행 하려는 유효성 검사 루틴이 있는 경우이 함수를 재정의 해야 합니다. 예를 들어 암호 테이블에 대해 DBPROP_AUTH_PASSWORD 유효성을 검사 하 여 올바른 값을 확인할 수 있습니다.

## <a name="cutlpropsoninterfacerequested"></a><a name="oninterfacerequested"></a> 가공선:: OnInterfaceRequested

소비자가 개체 생성 인터페이스 중 하나에서 메서드를 호출할 때 선택적 인터페이스에 대 한 요청을 처리 합니다.

### <a name="syntax"></a>구문

```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);
```

#### <a name="parameters"></a>매개 변수

*riid*<br/>
진행 요청 된 인터페이스의 IID입니다. 자세한 내용은  `ICommand::Execute` *OLE DB 프로그래머 참조* ( *MDAC SDK*)에서의 riid 매개 변수에 대 한 설명을 참조 하세요.

### <a name="remarks"></a>설명

`OnInterfaceRequested` 소비자가 개체 생성 인터페이스 (예:,, 또는) 중 하나에서 메서드를 호출할 때 선택적 인터페이스에 대 한 소비자 요청을 처리 `IDBCreateSession` `IDBCreateCommand` `IOpenRowset` `ICommand` 합니다. 요청 된 인터페이스에 해당 하는 OLE DB 속성을 설정 합니다. 예를 들어 소비자가 요청 하는 경우는 `IID_IRowsetLocate` `OnInterfaceRequested` 인터페이스를 설정 `DBPROP_IRowsetLocate` 합니다. 이렇게 하면 행 집합을 만드는 동안 올바른 상태가 유지 됩니다.

이 메서드는 소비자가 또는를 호출할 때 호출 됩니다 `IOpenRowset::OpenRowset` `ICommand::Execute` .

소비자가 개체를 열고 선택적 인터페이스를 요청 하는 경우 공급자는 해당 인터페이스와 연결 된 속성을 VARIANT_TRUE 설정 해야 합니다. 속성 관련 처리를 허용 하기 위해 `OnInterfaceRequested` 는 공급자의 메서드가 호출 되기 전에 호출 됩니다 `Execute` . 기본적으로는 `OnInterfaceRequested` 다음 인터페이스를 처리 합니다.

- `IRowsetLocate`

- `IRowsetChange`

- `IRowsetUpdate`

- `IConnectionPointContainer`

- `IRowsetScroll`

다른 인터페이스를 처리 하려면 데이터 원본, 세션, 명령 또는 행 집합 클래스에서 함수를 처리 하도록이 함수를 재정의 합니다. 재정의는 속성 설정으로 연결 된 속성도 설정 되도록 하기 위해 일반 set/get 속성 인터페이스를 통해 수행 해야 합니다 ( [OnPropertyChanged](#onpropertychanged)참조).

## <a name="cutlpropsonpropertychanged"></a><a name="onpropertychanged"></a> 가공선:: OnPropertyChanged

속성을 설정 하 여 연결 된 속성을 처리 한 후에 호출 됩니다.

### <a name="syntax"></a>구문

```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,
   DBPROP* pDBProp);
```

#### <a name="parameters"></a>매개 변수

*iCurSet*<br/>
속성 집합 배열의 인덱스입니다. 속성 집합이 하나만 있는 경우 0입니다.

*pDBProp*<br/>
[Dbprop](/previous-versions/windows/desktop/ms717970(v=vs.85)) 구조의 속성 ID 및 새 값입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다. 기본 반환 값은 S_OK입니다.

### <a name="remarks"></a>설명

값이 다른 속성의 값에 종속 된 책갈피 또는 업데이트와 같은 연결 된 속성을 처리 하려면이 함수를 재정의 해야 합니다.

### <a name="example"></a>예제

이 함수에서 사용자는 매개 변수에서 속성 ID를 가져옵니다 `DBPROP*` . 이제 속성에 대 한 ID를 chain과 비교할 수 있습니다. 속성이 있으면 `SetProperties` 다른 속성과 함께 설정 되는 속성을 사용 하 여가 호출 됩니다. 이 경우, 또는 속성을 가져오는 경우 `DBPROP_IRowsetLocate` `DBPROP_LITERALBOOKMARKS` 속성을 `DBPROP_ORDEREDBOOKMARKS` 설정할 수 있습니다 `DBPROP_BOOKMARKS` .

[!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]

## <a name="cutlpropssetpropvalue"></a><a name="setpropvalue"></a> 가공선 Lprops:: SetPropValue

속성 집합의 속성을 설정 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,
   DBPROPID dwPropId,
   VARIANT* pvValue);
```

#### <a name="parameters"></a>매개 변수

*pguidPropSet*<br/>
진행 PropSet에 대 한 GUID입니다.

*dwPropId*<br/>
진행 속성 인덱스입니다.

*pvValue*<br/>
진행 새 속성 값을 포함 하는 변형에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

`Failure` 실패 하 고 성공 하면 S_OK 합니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 공급자 템플릿 아키텍처](../../data/oledb/ole-db-provider-template-architecture.md)
