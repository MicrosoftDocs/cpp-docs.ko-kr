---
title: CDBPropSet 클래스
ms.date: 11/04/2016
f1_keywords:
- CDBPropSet
- ATL.CDBPropSet
- ATL::CDBPropSet
- CDBPropSet::AddProperty
- CDBPropSet.AddProperty
- AddProperty
- ATL::CDBPropSet::AddProperty
- ATL.CDBPropSet.AddProperty
- CDBPropSet.CDBPropSet
- CDBPropSet::CDBPropSet
- ATL::CDBPropSet::CDBPropSet
- ATL.CDBPropSet.CDBPropSet
- CDBPropSet.operator=
- ATL::CDBPropSet::operator=
- ATL.CDBPropSet.operator=
- CDBPropSet::operator=
- ATL.CDBPropSet.SetGUID
- CDBPropSet.SetGUID
- ATL::CDBPropSet::SetGUID
- CDBPropSet::SetGUID
helpviewer_keywords:
- CDBPropSet class
- AddProperty method
- CDBPropSet class, constructor
- operator =, property sets
- = operator, with OLE DB templates
- operator=, property sets
- SetGUID method
- AddProperty method
ms.assetid: 54190149-c277-4679-b81a-ef484d4d1c00
ms.openlocfilehash: 45772896cac520eba35ec475f8b6ae7bd2993045
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502464"
---
# <a name="cdbpropset-class"></a>CDBPropSet 클래스

구조체에서 상속 `DBPROPSET` 하 고 키 필드와 액세스 메서드를 초기화 하는 생성자를 추가 합니다 `AddProperty` .

## <a name="syntax"></a>구문

```cpp
class CDBPropSet : public tagDBPROPSET
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[AddProperty](#addproperty)|속성 집합에 속성을 추가 합니다.|
|[CDBPropSet](#cdbpropset)|생성자입니다.|
|[SetGUID](#setguid)|`guidPropertySet`구조체의 필드를 설정 `DBPROPSET` 합니다.|

### <a name="operators"></a>연산자

| 속성 | 설명 |
|-|-|
|[연산자 =](#op_equal)|한 속성 집합의 내용을 다른 속성에 할당 합니다.|

## <a name="remarks"></a>설명

OLE DB 공급자 및 소비자는 `DBPROPSET` 구조체를 사용 하 여 `DBPROP` 구조체 배열을 전달 합니다. 각 `DBPROP` 구조는 설정할 수 있는 단일 속성을 나타냅니다.

## <a name="cdbpropsetaddproperty"></a><a name="addproperty"></a> CDBPropSet:: AddProperty

속성 집합에 속성을 추가 합니다.

### <a name="syntax"></a>구문

```cpp
bool AddProperty(DWORD dwPropertyID,
   constVARIANT& var,
   DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCSTR szValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   LPCWSTR szValue,DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   bool bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   BYTE bValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   short nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   long nValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   float fltValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED);bool AddProperty(DWORD dwPropertyID,
   double dblValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();bool AddProperty(DWORD dwPropertyID,
   CY cyValue,  DBPROPOPTIONS propoptions = DBPROPOPTIONS_REQUIRED) throw();
```

#### <a name="parameters"></a>매개 변수

*dwPropertyID*<br/>
진행 추가할 속성의 ID입니다. `dwPropertyID`속성 집합에 추가 된 구조의를 초기화 하는 데 사용 `DBPROP` 됩니다.

*var*<br/>
진행 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 variant `DBPROP` 입니다.

*szValue*<br/>
진행 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 문자열 `DBPROP` 입니다.

*되며 bvalue*<br/>
진행 `BYTE` 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 또는 부울 값 `DBPROP` 입니다.

*N 값*<br/>
진행 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 정수 값 `DBPROP` 입니다.

*fltValue*<br/>
진행 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 부동 소수점 값 `DBPROP` 입니다.

*dblValue*<br/>
진행 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 배정밀도 부동 소수점 값 `DBPROP` 입니다.

*cyValue*<br/>
진행 속성 집합에 추가 된 구조체의 속성 값을 초기화 하는 데 사용 되는 CY 통화 값 `DBPROP` 입니다.

### <a name="return-value"></a>반환 값

**`true`** 속성이 성공적으로 추가 되었으면이 고, 그렇지 않으면 **`false`** 입니다.

## <a name="cdbpropsetcdbpropset"></a><a name="cdbpropset"></a> CDBPropSet:: CDBPropSet

생성자입니다. `rgProperties` `cProperties` `guidPropertySet` [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의, 및 필드를 초기화 합니다.

### <a name="syntax"></a>구문

```cpp
CDBPropSet(const GUID& guid);

CDBPropSet(const CDBPropSet& propset);

CDBPropSet();
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
진행 필드를 초기화 하는 데 사용 되는 GUID `guidPropertySet` 입니다.

*propset*<br/>
[in] 복사 생성을 위한 다른 `CDBPropSet` 개체입니다.

## <a name="cdbpropsetsetguid"></a><a name="setguid"></a> CDBPropSet:: SetGUID

`guidPropertySet`구조체의 필드를 설정 합니다 `DBPROPSET` .

### <a name="syntax"></a>구문

```cpp
void SetGUID(const GUID& guid) throw();
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
진행 `guidPropertySet` [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 필드를 설정 하는 데 사용 되는 GUID입니다.

### <a name="remarks"></a>설명

이 필드는 [생성자](#cdbpropset) 로도 설정할 수 있습니다.

## <a name="cdbpropsetoperator-"></a><a name="op_equal"></a> CDBPropSet:: operator =

한 속성 집합의 내용을 다른 속성 집합에 할당 합니다.

### <a name="syntax"></a>구문

```cpp
CDBPropSet& operator =(CDBPropSet& propset) throw();
```

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CDBPropIDSet 클래스](../../data/oledb/cdbpropidset-class.md)<br/>
[DBPROPSET 구조체](/previous-versions/windows/desktop/ms714367(v=vs.85)) 
 [Dbprop 구조체](/previous-versions/windows/desktop/ms717970(v=vs.85))
