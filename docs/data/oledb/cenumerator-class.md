---
title: CEnumerator 클래스
ms.date: 11/04/2016
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
ms.openlocfilehash: dfc358c06179d50cbf6442863fd2ed2c533cd00a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498538"
---
# <a name="cenumerator-class"></a>CEnumerator 클래스

[ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) 인터페이스를 노출 하 여 모든 데이터 소스와 열거자를 설명 하는 행 집합을 반환 하는 OLE DB 열거자 개체를 사용 합니다.

## <a name="syntax"></a>구문

```cpp
class CEnumerator :
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[찾기](#find)|사용 가능한 공급자 (데이터 원본)에서 지정 된 이름을 가진 하나를 검색 합니다.|
|[GetMoniker](#getmoniker)|`IMoniker`현재 레코드에 대 한 인터페이스를 검색 합니다.|
|[열기](#open)|열거자를 엽니다.|

## <a name="remarks"></a>설명

`ISourcesRowset`이 클래스에서 데이터를 간접적으로 검색할 수 있습니다.

## <a name="cenumeratorfind"></a><a name="find"></a> CEnumerator:: Find

사용 가능한 공급자 중에서 지정 된 이름을 찾습니다.

### <a name="syntax"></a>구문

```cpp
bool Find(TCHAR* szSearchName) throw();
```

#### <a name="parameters"></a>매개 변수

*szSearchName*<br/>
진행 검색할 이름입니다.

### <a name="return-value"></a>반환 값

**`true`** 이름을 찾았으면입니다. 그렇지 않으면 **`false`** 입니다.

### <a name="remarks"></a>설명

이 이름은 `SOURCES_NAME` [ISourcesRowset](/previous-versions/windows/desktop/ms715969(v=vs.85)) 인터페이스의 멤버에 매핑됩니다.

## <a name="cenumeratorgetmoniker"></a><a name="getmoniker"></a> CEnumerator:: GetMoniker

표시 이름을 구문 분석 하 여 모니커로 변환할 수 있는 문자열의 구성 요소를 추출 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();

HRESULT GetMoniker(LPMONIKER* ppMoniker,
   LPCTSTR lpszDisplayName) const throw();
```

#### <a name="parameters"></a>매개 변수

*ppMoniker*<br/>
제한이 현재 행의 표시 이름 ([Cenumeratoraccessor:: m_szParseName](./cenumeratoraccessor-class.md#szparsename))에서 구문 분석 된 모니커입니다.

*lpszDisplayName*<br/>
진행 구문 분석할 표시 이름입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cenumeratoropen"></a><a name="open"></a> CEnumerator:: Open

열거자에 대 한 모니커 (지정 된 경우)를 바인딩한 다음 [ISourcesRowset:: GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85))을 호출 하 여 열거자에 대 한 행 집합을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(LPMONIKER pMoniker) throw();

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();

HRESULT Open(const CEnumerator& enumerator) throw();
```

#### <a name="parameters"></a>매개 변수

*pMoniker*<br/>
진행 열거자의 모니커에 대 한 포인터입니다.

*pClsid*<br/>
진행 열거자의에 대 한 포인터 `CLSID` 입니다.

*열거*<br/>
진행 열거자에 대 한 참조입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="see-also"></a>참고 항목

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
