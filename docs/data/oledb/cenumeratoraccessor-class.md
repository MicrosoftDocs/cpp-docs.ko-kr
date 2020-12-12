---
description: '자세히 알아보기: CEnumeratorAccessor 클래스'
title: CEnumeratorAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: f37de34c508487f3ee54f47db1b0a64df8a97b25
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170570"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor 클래스

[CEnumerator](../../data/oledb/cenumerator-class.md) 에서 열거자 행 집합의 데이터에 액세스 하는 데 사용 됩니다.

## <a name="syntax"></a>Syntax

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="data-members"></a>데이터 멤버

| Name | 설명 |
|-|-|
|[m_bIsParent](#bisparent)|열거자가 부모 열거자 인지 여부를 나타내는 변수입니다 (행이 열거자 인 경우).|
|[m_nType](#ntype)|행이 데이터 소스 또는 열거자를 설명 하는지 여부를 나타내는 변수입니다.|
|[m_szDescription](#szdescription)|데이터 원본 또는 열거자에 대 한 설명입니다.|
|[m_szName](#szname)|데이터 소스 또는 열거자의 이름입니다.|
|[m_szParseName](#szparsename)|데이터 소스 또는 열거자에 대 한 모니커를 가져오기 위해 [Iparsedisplayname](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) 에 전달할 문자열입니다.|

## <a name="remarks"></a>설명

이 행 집합은 현재 열거자에서 표시 되는 데이터 소스와 열거자로 구성 됩니다.

## <a name="cenumeratoraccessorm_bisparent"></a><a name="bisparent"></a> CEnumeratorAccessor:: m_bIsParent

열거자가 부모 열거자 인지 여부를 나타내는 변수입니다 (행이 열거자 인 경우).

### <a name="syntax"></a>구문

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ISourcesRowset:: getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 을 참조 하세요.

## <a name="cenumeratoraccessorm_ntype"></a><a name="ntype"></a> CEnumeratorAccessor:: m_nType

행이 데이터 소스 또는 열거자를 설명 하는지 여부를 나타내는 변수입니다.

### <a name="syntax"></a>구문

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ISourcesRowset:: getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 을 참조 하세요.

## <a name="cenumeratoraccessorm_szdescription"></a><a name="szdescription"></a> CEnumeratorAccessor:: m_szDescription

데이터 원본 또는 열거자에 대 한 설명입니다.

### <a name="syntax"></a>구문

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ISourcesRowset:: getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 을 참조 하세요.

## <a name="cenumeratoraccessorm_szname"></a><a name="szname"></a> CEnumeratorAccessor:: m_szName

데이터 소스 또는 열거자의 이름입니다.

### <a name="syntax"></a>구문

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ISourcesRowset:: getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 을 참조 하세요.

## <a name="cenumeratoraccessorm_szparsename"></a><a name="szparsename"></a> CEnumeratorAccessor:: m_szParseName

데이터 소스 또는 열거자에 대 한 모니커를 가져오기 위해 [Iparsedisplayname](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) 에 전달할 문자열입니다.

### <a name="syntax"></a>구문

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>설명

자세한 내용은 *OLE DB 프로그래머 참조* 에서 [ISourcesRowset:: getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 을 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
