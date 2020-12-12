---
description: '자세히 알아보기: CStringData 클래스'
title: CStringData 클래스
ms.date: 11/04/2016
f1_keywords:
- CStringData
- ATLSIMPSTR/ATL::CStringData
- ATLSIMPSTR/ATL::AddRef
- ATLSIMPSTR/ATL::data
- ATLSIMPSTR/ATL::IsLocked
- ATLSIMPSTR/ATL::IsShared
- ATLSIMPSTR/ATL::Lock
- ATLSIMPSTR/ATL::Release
- ATLSIMPSTR/ATL::Unlock
- ATLSIMPSTR/ATL::nAllocLength
- ATLSIMPSTR/ATL::nDataLength
- ATLSIMPSTR/ATL::nRefs
- ATLSIMPSTR/ATL::pStringMgr
helpviewer_keywords:
- CStringData class
- shared classes, CStringData
ms.assetid: 4e31b5ca-3dbe-4fd5-b692-8211fbfb2593
ms.openlocfilehash: 74bf3563cb5dca506498ceef05ddc84f13c44f41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166592"
---
# <a name="cstringdata-class"></a>CStringData 클래스

이 클래스는 문자열 개체의 데이터를 나타냅니다.

## <a name="syntax"></a>구문

```
struct CStringData
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

|속성|설명|
|-|-|
|[AddRef](#addref)|문자열 데이터 개체의 참조 횟수를 늘립니다.|
|[data](#data)|문자열 개체의 문자 데이터를 검색 합니다.|
|[IsLocked](#islocked)|연결 된 문자열 개체의 버퍼가 잠겨 있는지 여부를 확인 합니다.|
|[IsShared](#isshared)|연결 된 문자열 개체의 버퍼가 현재 공유 되어 있는지 여부를 확인 합니다.|
|[잠금](#lock)|연결 된 문자열 개체의 버퍼를 잠급니다.|
|[릴리스](#release)|지정 된 문자열 개체를 해제 합니다.|
|[잠금 해제](#unlock)|연결 된 문자열 개체의 버퍼 잠금을 해제 합니다.|

### <a name="data-members"></a>데이터 멤버

|Name|설명|
|-|-|
|[nAllocLength](#nalloclength)|에서 할당 된 데이터의 길이 `XCHAR` (null 종결을 포함 하지 않음)|
|[nDataLength](#ndatalength)|S에서 현재 사용 되는 데이터의 길이 `XCHAR` (null 종결을 포함 하지 않음)|
|[nRefs](#nrefs)|개체의 현재 참조 수입니다.|
|[pStringMgr](#pstringmgr)|이 문자열 개체의 문자열 관리자에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

이 클래스는 사용자 지정 문자열 관리자를 구현 하는 개발자만 사용 해야 합니다. 사용자 지정 문자열 관리자에 대 한 자세한 내용은 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md) 를 참조 하세요.

이 클래스는 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md), [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)또는 [cfixedstringt](../../atl-mfc-shared/reference/cfixedstringt-class.md) 개체와 같은 더 높은 문자열 개체와 연결 된 다양 한 유형의 정보 및 데이터를 캡슐화 합니다. 상위 문자열 개체는 모두 연결 된 개체에 대 한 포인터를 포함 `CStringData` 하므로 여러 string 개체가 동일한 문자열 데이터 개체를 가리킬 수 있습니다. 이 관계는 개체의 참조 수 ()로 표시 됩니다 `nRefs` `CStringData` .

> [!NOTE]
> 경우에 따라 문자열 형식 (예:)은 둘 `CFixedString` 이상의 문자열 개체를 포함 하는 문자열 데이터 개체를 공유 하지 않습니다. 이에 대 한 자세한 내용은 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하세요.

이 데이터는 다음과 같은 요소로 구성 됩니다.

- 문자열의 메모리 관리자 ( [Iatlstringmgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)형식)입니다.

- 문자열의 현재 길이 ( [nDataLength](#ndatalength))입니다.

- 문자열의 할당 된 길이 ( [nAllocLength](#nalloclength))입니다. 성능상의 이유로이는 현재 문자열 길이와 다를 수 있습니다.

- 개체의 현재 참조 수 ( [Nrefs](#nrefs)) `CStringData` 입니다. 이 값은 동일한 개체를 공유 하는 문자열 개체의 수를 확인 하는 데 사용 됩니다 `CStringData` .

- 문자열의 실제 문자 버퍼 ( [데이터](#data))입니다.

   > [!NOTE]
   > 문자열 개체의 실제 문자 버퍼는 문자열 관리자에 의해 할당 되 고 개체에 추가 됩니다 `CStringData` .

## <a name="requirements"></a>요구 사항

**헤더:** atlsimpstr

## <a name="cstringdataaddref"></a><a name="addref"></a> CStringData:: AddRef

문자열 개체의 참조 횟수를 늘립니다.

```cpp
void AddRef() throw();
```

### <a name="remarks"></a>설명

문자열 개체의 참조 횟수를 늘립니다.

> [!NOTE]
> 음수는 문자열 버퍼가 잠겨 있음을 나타내므로 음수 참조 횟수를 사용 하는 문자열에 대해이 메서드를 호출 하지 마십시오.

## <a name="cstringdatadata"></a><a name="data"></a> CStringData: ata:d

문자열 개체의 문자 버퍼에 대 한 포인터를 반환 합니다.

```cpp
void* data() throw();
```

### <a name="return-value"></a>반환 값

문자열 개체의 문자 버퍼에 대 한 포인터입니다.

### <a name="remarks"></a>설명

연결 된 문자열 개체의 현재 문자 버퍼를 반환 하려면이 함수를 호출 합니다.

> [!NOTE]
> 이 버퍼는 개체에 의해 할당 되지 `CStringData` 않지만 필요한 경우 문자열 관리자에 의해 할당 됩니다. 할당 되 면 버퍼는 문자열 데이터 개체에 추가 됩니다.

## <a name="cstringdataislocked"></a><a name="islocked"></a> CStringData:: IsLocked

문자 버퍼가 잠겨 있는지 여부를 확인 합니다.

```
bool IsLocked() const throw();
```

### <a name="return-value"></a>반환 값

버퍼가 잠긴 경우 TRUE를 반환 합니다. 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

문자열 개체의 문자 버퍼가 현재 잠겨 있는지 확인 하려면이 함수를 호출 합니다.

## <a name="cstringdataisshared"></a><a name="isshared"></a> CStringData::IsShared

문자 버퍼가 공유 되는지 여부를 확인 합니다.

```
bool IsShared() const throw();
```

### <a name="return-value"></a>반환 값

버퍼가 공유 되 면 TRUE를 반환 하 고, 그렇지 않으면 FALSE입니다.

### <a name="remarks"></a>설명

이 함수를 호출 하 여 문자열 데이터 개체의 문자 버퍼가 여러 문자열 개체에서 현재 공유 되어 있는지 확인 합니다.

## <a name="cstringdatalock"></a><a name="lock"></a> CStringData:: Lock

연결 된 문자열 개체의 문자 버퍼를 잠급니다.

```cpp
void Lock() throw();
```

### <a name="remarks"></a>설명

문자열 데이터 개체의 문자 버퍼를 잠그려면이 함수를 호출 합니다. 잠금 및 잠금 해제는 개발자에 게 문자 버퍼에 대 한 직접 액세스를 요구 하는 경우에 사용 됩니다. 잠금에 대 한 좋은 예는의 [lockbuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) 및 [unlockbuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) 메서드를 통해 보여 줍니다 `CSimpleStringT` .

> [!NOTE]
> 문자 버퍼는 더 높은 문자열 개체에서 버퍼를 공유 하지 않는 경우에만 잠글 수 있습니다.

## <a name="cstringdatanalloclength"></a><a name="nalloclength"></a> CStringData::nAllocLength

할당 된 문자 버퍼의 길이입니다.

```
int nAllocLength;
```

### <a name="remarks"></a>설명

할당 된 데이터 버퍼의 길이 `XCHAR` (종료 null을 포함 하지 않음)를에 저장 합니다.

## <a name="cstringdatandatalength"></a><a name="ndatalength"></a> CStringData::nDataLength

문자열 개체의 현재 길이입니다.

```
int nDataLength;
```

### <a name="remarks"></a>설명

현재 사용 되는 데이터의 길이를 `XCHAR` s에 저장 합니다 (종료 null을 포함 하지 않음).

## <a name="cstringdatanrefs"></a><a name="nrefs"></a> CStringData:: nRefs

문자열 데이터 개체의 참조 수입니다.

```
long nRefs;
```

### <a name="remarks"></a>설명

문자열 데이터 개체의 참조 횟수를 저장 합니다. 이 개수는 문자열 데이터 개체와 연결 된 상위 문자열 개체의 수를 나타냅니다. 음수 값은 문자열 데이터 개체가 현재 잠겨 있음을 나타냅니다.

## <a name="cstringdatapstringmgr"></a><a name="pstringmgr"></a> CStringData::p StringMgr

연결 된 문자열 개체의 메모리 관리자입니다.

```
IAtlStringMgr* pStringMgr;
```

### <a name="remarks"></a>설명

연결 된 문자열 개체에 대 한 메모리 관리자를 저장 합니다. 메모리 관리자 및 문자열에 대 한 자세한 내용은 [메모리 관리 및 CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md)를 참조 하십시오.

## <a name="cstringdatarelease"></a><a name="release"></a> CStringData:: Release

문자열 데이터 개체의 참조 횟수를 감소 시킵니다.

```cpp
void Release() throw();
```

### <a name="remarks"></a>설명

참조 횟수가 0에 도달 하는 경우 구조체를 해제 하 여 참조 횟수를 감소 시키려면이 함수를 호출 합니다 `CStringData` . 이는 일반적으로 문자열 개체가 삭제 될 때 수행 되므로 더 이상 문자열 데이터 개체를 참조할 필요가 없습니다.

예를 들어 다음 코드는 `CStringData::Release` 와 연결 된 문자열 데이터 개체에 대해를 호출 합니다 `str1` .

[!code-cpp[NVC_ATLMFC_Utilities#104](../../atl-mfc-shared/codesnippet/cpp/cstringdata-class_1.cpp)]

## <a name="cstringdataunlock"></a><a name="unlock"></a> CStringData:: Unlock

연결 된 문자열 개체의 문자 버퍼를 잠금 해제 합니다.

```cpp
void Unlock() throw();
```

### <a name="remarks"></a>설명

문자열 데이터 개체의 문자 버퍼 잠금을 해제 하려면이 함수를 호출 합니다. 버퍼의 잠금이 해제 되 면 공유 가능 하 고 참조 횟수가 계산 될 수 있습니다.

> [!NOTE]
> 에 대 한 각 호출은 `Lock` 에 대 한 해당 호출로 일치 해야 합니다 `Unlock` .

잠금 및 잠금 해제는 개발자가 문자열 데이터를 공유 하지 않는지 확인 해야 하는 경우에 사용 됩니다. 잠금에 대 한 좋은 예는의 [lockbuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer) 및 [unlockbuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer) 메서드를 통해 보여 줍니다 `CSimpleStringT` .

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 공유 클래스](../../atl-mfc-shared/atl-mfc-shared-classes.md)
