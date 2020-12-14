---
description: '자세히 알아보기: CDaoRecordset 클래스'
title: CDaoRecordset 클래스
ms.date: 08/27/2018
f1_keywords:
- CDaoRecordset
- AFXDAO/CDaoRecordset
- AFXDAO/CDaoRecordset::CDaoRecordset
- AFXDAO/CDaoRecordset::AddNew
- AFXDAO/CDaoRecordset::CanAppend
- AFXDAO/CDaoRecordset::CanBookmark
- AFXDAO/CDaoRecordset::CancelUpdate
- AFXDAO/CDaoRecordset::CanRestart
- AFXDAO/CDaoRecordset::CanScroll
- AFXDAO/CDaoRecordset::CanTransact
- AFXDAO/CDaoRecordset::CanUpdate
- AFXDAO/CDaoRecordset::Close
- AFXDAO/CDaoRecordset::Delete
- AFXDAO/CDaoRecordset::DoFieldExchange
- AFXDAO/CDaoRecordset::Edit
- AFXDAO/CDaoRecordset::FillCache
- AFXDAO/CDaoRecordset::Find
- AFXDAO/CDaoRecordset::FindFirst
- AFXDAO/CDaoRecordset::FindLast
- AFXDAO/CDaoRecordset::FindNext
- AFXDAO/CDaoRecordset::FindPrev
- AFXDAO/CDaoRecordset::GetAbsolutePosition
- AFXDAO/CDaoRecordset::GetBookmark
- AFXDAO/CDaoRecordset::GetCacheSize
- AFXDAO/CDaoRecordset::GetCacheStart
- AFXDAO/CDaoRecordset::GetCurrentIndex
- AFXDAO/CDaoRecordset::GetDateCreated
- AFXDAO/CDaoRecordset::GetDateLastUpdated
- AFXDAO/CDaoRecordset::GetDefaultDBName
- AFXDAO/CDaoRecordset::GetDefaultSQL
- AFXDAO/CDaoRecordset::GetEditMode
- AFXDAO/CDaoRecordset::GetFieldCount
- AFXDAO/CDaoRecordset::GetFieldInfo
- AFXDAO/CDaoRecordset::GetFieldValue
- AFXDAO/CDaoRecordset::GetIndexCount
- AFXDAO/CDaoRecordset::GetIndexInfo
- AFXDAO/CDaoRecordset::GetLastModifiedBookmark
- AFXDAO/CDaoRecordset::GetLockingMode
- AFXDAO/CDaoRecordset::GetName
- AFXDAO/CDaoRecordset::GetParamValue
- AFXDAO/CDaoRecordset::GetPercentPosition
- AFXDAO/CDaoRecordset::GetRecordCount
- AFXDAO/CDaoRecordset::GetSQL
- AFXDAO/CDaoRecordset::GetType
- AFXDAO/CDaoRecordset::GetValidationRule
- AFXDAO/CDaoRecordset::GetValidationText
- AFXDAO/CDaoRecordset::IsBOF
- AFXDAO/CDaoRecordset::IsDeleted
- AFXDAO/CDaoRecordset::IsEOF
- AFXDAO/CDaoRecordset::IsFieldDirty
- AFXDAO/CDaoRecordset::IsFieldNull
- AFXDAO/CDaoRecordset::IsFieldNullable
- AFXDAO/CDaoRecordset::IsOpen
- AFXDAO/CDaoRecordset::Move
- AFXDAO/CDaoRecordset::MoveFirst
- AFXDAO/CDaoRecordset::MoveLast
- AFXDAO/CDaoRecordset::MoveNext
- AFXDAO/CDaoRecordset::MovePrev
- AFXDAO/CDaoRecordset::Open
- AFXDAO/CDaoRecordset::Requery
- AFXDAO/CDaoRecordset::Seek
- AFXDAO/CDaoRecordset::SetAbsolutePosition
- AFXDAO/CDaoRecordset::SetBookmark
- AFXDAO/CDaoRecordset::SetCacheSize
- AFXDAO/CDaoRecordset::SetCacheStart
- AFXDAO/CDaoRecordset::SetCurrentIndex
- AFXDAO/CDaoRecordset::SetFieldDirty
- AFXDAO/CDaoRecordset::SetFieldNull
- AFXDAO/CDaoRecordset::SetFieldValue
- AFXDAO/CDaoRecordset::SetFieldValueNull
- AFXDAO/CDaoRecordset::SetLockingMode
- AFXDAO/CDaoRecordset::SetParamValue
- AFXDAO/CDaoRecordset::SetParamValueNull
- AFXDAO/CDaoRecordset::SetPercentPosition
- AFXDAO/CDaoRecordset::Update
- AFXDAO/CDaoRecordset::m_bCheckCacheForDirtyFields
- AFXDAO/CDaoRecordset::m_nFields
- AFXDAO/CDaoRecordset::m_nParams
- AFXDAO/CDaoRecordset::m_pDAORecordset
- AFXDAO/CDaoRecordset::m_pDatabase
- AFXDAO/CDaoRecordset::m_strFilter
- AFXDAO/CDaoRecordset::m_strSort
helpviewer_keywords:
- CDaoRecordset [MFC], CDaoRecordset
- CDaoRecordset [MFC], AddNew
- CDaoRecordset [MFC], CanAppend
- CDaoRecordset [MFC], CanBookmark
- CDaoRecordset [MFC], CancelUpdate
- CDaoRecordset [MFC], CanRestart
- CDaoRecordset [MFC], CanScroll
- CDaoRecordset [MFC], CanTransact
- CDaoRecordset [MFC], CanUpdate
- CDaoRecordset [MFC], Close
- CDaoRecordset [MFC], Delete
- CDaoRecordset [MFC], DoFieldExchange
- CDaoRecordset [MFC], Edit
- CDaoRecordset [MFC], FillCache
- CDaoRecordset [MFC], Find
- CDaoRecordset [MFC], FindFirst
- CDaoRecordset [MFC], FindLast
- CDaoRecordset [MFC], FindNext
- CDaoRecordset [MFC], FindPrev
- CDaoRecordset [MFC], GetAbsolutePosition
- CDaoRecordset [MFC], GetBookmark
- CDaoRecordset [MFC], GetCacheSize
- CDaoRecordset [MFC], GetCacheStart
- CDaoRecordset [MFC], GetCurrentIndex
- CDaoRecordset [MFC], GetDateCreated
- CDaoRecordset [MFC], GetDateLastUpdated
- CDaoRecordset [MFC], GetDefaultDBName
- CDaoRecordset [MFC], GetDefaultSQL
- CDaoRecordset [MFC], GetEditMode
- CDaoRecordset [MFC], GetFieldCount
- CDaoRecordset [MFC], GetFieldInfo
- CDaoRecordset [MFC], GetFieldValue
- CDaoRecordset [MFC], GetIndexCount
- CDaoRecordset [MFC], GetIndexInfo
- CDaoRecordset [MFC], GetLastModifiedBookmark
- CDaoRecordset [MFC], GetLockingMode
- CDaoRecordset [MFC], GetName
- CDaoRecordset [MFC], GetParamValue
- CDaoRecordset [MFC], GetPercentPosition
- CDaoRecordset [MFC], GetRecordCount
- CDaoRecordset [MFC], GetSQL
- CDaoRecordset [MFC], GetType
- CDaoRecordset [MFC], GetValidationRule
- CDaoRecordset [MFC], GetValidationText
- CDaoRecordset [MFC], IsBOF
- CDaoRecordset [MFC], IsDeleted
- CDaoRecordset [MFC], IsEOF
- CDaoRecordset [MFC], IsFieldDirty
- CDaoRecordset [MFC], IsFieldNull
- CDaoRecordset [MFC], IsFieldNullable
- CDaoRecordset [MFC], IsOpen
- CDaoRecordset [MFC], Move
- CDaoRecordset [MFC], MoveFirst
- CDaoRecordset [MFC], MoveLast
- CDaoRecordset [MFC], MoveNext
- CDaoRecordset [MFC], MovePrev
- CDaoRecordset [MFC], Open
- CDaoRecordset [MFC], Requery
- CDaoRecordset [MFC], Seek
- CDaoRecordset [MFC], SetAbsolutePosition
- CDaoRecordset [MFC], SetBookmark
- CDaoRecordset [MFC], SetCacheSize
- CDaoRecordset [MFC], SetCacheStart
- CDaoRecordset [MFC], SetCurrentIndex
- CDaoRecordset [MFC], SetFieldDirty
- CDaoRecordset [MFC], SetFieldNull
- CDaoRecordset [MFC], SetFieldValue
- CDaoRecordset [MFC], SetFieldValueNull
- CDaoRecordset [MFC], SetLockingMode
- CDaoRecordset [MFC], SetParamValue
- CDaoRecordset [MFC], SetParamValueNull
- CDaoRecordset [MFC], SetPercentPosition
- CDaoRecordset [MFC], Update
- CDaoRecordset [MFC], m_bCheckCacheForDirtyFields
- CDaoRecordset [MFC], m_nFields
- CDaoRecordset [MFC], m_nParams
- CDaoRecordset [MFC], m_pDAORecordset
- CDaoRecordset [MFC], m_pDatabase
- CDaoRecordset [MFC], m_strFilter
- CDaoRecordset [MFC], m_strSort
ms.assetid: 2322067f-1027-4662-a5d7-aa2fc7488630
ms.openlocfilehash: cc24894c0efc61ae37d57ff3c01ca43e71beddf3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248213"
---
# <a name="cdaorecordset-class"></a>CDaoRecordset 클래스

데이터 소스에서 선택한 레코드 집합을 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class CDaoRecordset : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDaoRecordset:: CDaoRecordset](#cdaorecordset)|`CDaoRecordset` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoRecordset:: AddNew](#addnew)|새 레코드를 추가할 준비를 합니다. [업데이트](#update) 를 호출 하 여 추가를 완료 합니다.|
|[CDaoRecordset:: CanAppend](#canappend)|[AddNew](#addnew) 멤버 함수를 통해 레코드 집합에 새 레코드를 추가할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: CanBookmark](#canbookmark)|레코드 집합에서 책갈피를 지 원하는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: CancelUpdate](#cancelupdate)|[편집](#edit) 또는 [AddNew](#addnew) 작업으로 인해 보류 중인 모든 업데이트를 취소 합니다.|
|[CDaoRecordset:: CanRestart](#canrestart)|다시 쿼리를 호출 하 여 레코드 집합의 쿼리를 다시 실행할 수 [있는 경우 0](#requery) 이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: CanScroll](#canscroll)|레코드를 스크롤할 수 있는 경우 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: CanTransact](#cantransact)|데이터 원본이 트랜잭션을 지원 하면 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: CanUpdate](#canupdate)|레코드 집합을 업데이트할 수 있는 경우 0이 아닌 값을 반환 합니다. 레코드를 추가, 업데이트 또는 삭제할 수 있습니다.|
|[CDaoRecordset:: Close](#close)|레코드 집합을 닫습니다.|
|[CDaoRecordset::D e)](#delete)|레코드 집합에서 현재 레코드를 삭제 합니다. 삭제 한 후에는 다른 레코드로 명시적으로 스크롤해야 합니다.|
|[CDaoRecordset::DoFieldExchange](#dofieldexchange)|레코드 집합의 필드 데이터 멤버와 데이터 소스에 있는 해당 레코드 사이에서 데이터를 양방향으로 교환 하기 위해 호출 됩니다. DAO 레코드 필드 교환 (DFX)을 구현 합니다.|
|[CDaoRecordset:: Edit](#edit)|현재 레코드에 대 한 변경 내용을 준비 합니다. `Update`을 호출 하 여 편집을 완료 합니다.|
|[CDaoRecordset:: FillCache](#fillcache)|ODBC 데이터 원본의 데이터를 포함 하는 레코드 집합 개체에 대 한 로컬 캐시의 전체 또는 일부를 채웁니다.|
|[CDaoRecordset:: Find](#find)|지정 된 조건을 충족 하는 다이너셋 형식 레코드 집합에서 특정 문자열의 첫 번째, 다음, 이전 또는 마지막 위치를 찾은 다음 현재 레코드를 기록 합니다.|
|[CDaoRecordset:: FindFirst](#findfirst)|지정 된 조건을 충족 하는 다이너셋 형식 또는 스냅숏 형식 레코드 집합의 첫 번째 레코드를 찾은 다음 현재 레코드를 기록 합니다.|
|[CDaoRecordset:: FindLast](#findlast)|지정 된 조건을 충족 하는 다이너셋 형식 또는 스냅숏 형식 레코드 집합에서 마지막 레코드를 찾은 다음 현재 레코드를 기록 합니다.|
|[CDaoRecordset:: FindNext](#findnext)|지정 된 조건을 충족 하는 다이너셋 형식 또는 스냅숏 형식 레코드 집합에서 다음 레코드를 찾은 다음 현재 레코드를 기록 합니다.|
|[CDaoRecordset:: FindPrev](#findprev)|지정 된 조건을 충족 하는 다이너셋 형식 또는 스냅숏 형식 레코드 집합에서 이전 레코드를 찾은 다음 현재 레코드를 기록 합니다.|
|[CDaoRecordset:: GetAbsolutePosition](#getabsoluteposition)|레코드 집합 개체의 현재 레코드에 대 한 레코드 번호를 반환 합니다.|
|[CDaoRecordset:: GetBookmark](#getbookmark)|레코드의 책갈피를 나타내는 값을 반환 합니다.|
|[CDaoRecordset:: GetCacheSize](#getcachesize)|ODBC 데이터 원본에서 로컬로 캐시할 데이터를 포함 하는 다이너셋 형식 레코드 집합의 레코드 수를 지정 하는 값을 반환 합니다.|
|[CDaoRecordset:: GetCacheStart](#getcachestart)|캐시 될 레코드 집합에서 첫 번째 레코드의 책갈피를 지정 하는 값을 반환 합니다.|
|[CDaoRecordset:: GetCurrentIndex](#getcurrentindex)|`CString`인덱싱된 테이블 형식에서 가장 최근에 사용 된 인덱스의 이름을 포함 하는을 반환 합니다 `CDaoRecordset` .|
|[CDaoRecordset:: GetDateCreated](#getdatecreated)|개체의 기반이 되는 기본 테이블이 만들어진 날짜 및 시간을 반환 합니다. `CDaoRecordset`|
|[CDaoRecordset:: GetDateLastUpdated](#getdatelastupdated)|개체를 기반으로 하는 기본 테이블의 디자인에 대 한 가장 최근의 변경 날짜와 시간을 반환 합니다 `CDaoRecordset` .|
|[CDaoRecordset:: GetDefaultDBName](#getdefaultdbname)|기본 데이터 원본의 이름을 반환 합니다.|
|[CDaoRecordset:: GetDefaultSQL](#getdefaultsql)|실행할 기본 SQL 문자열을 가져오기 위해 호출 됩니다.|
|[CDaoRecordset:: GetEditMode](#geteditmode)|현재 레코드에 대 한 편집 상태를 나타내는 값을 반환 합니다.|
|[CDaoRecordset:: GetFieldCount](#getfieldcount)|레코드 집합의 필드 수를 나타내는 값을 반환 합니다.|
|[CDaoRecordset::GetFieldInfo](#getfieldinfo)|레코드 집합의 필드에 대 한 특정 종류의 정보를 반환 합니다.|
|[CDaoRecordset:: GetFieldValue](#getfieldvalue)|레코드 집합에 있는 필드의 값을 반환 합니다.|
|[CDaoRecordset:: GetIndexCount](#getindexcount)|레코드 집합을 기반으로 하는 테이블의 인덱스 수를 검색 합니다.|
|[CDaoRecordset:: GetIndexInfo](#getindexinfo)|인덱스에 대 한 다양 한 종류의 정보를 반환 합니다.|
|[CDaoRecordset:: GetLastModifiedBookmark](#getlastmodifiedbookmark)|가장 최근에 추가 되거나 업데이트 된 레코드를 확인 하는 데 사용 됩니다.|
|[CDaoRecordset:: GetLockingMode](#getlockingmode)|편집 하는 동안 적용 되는 잠금 유형을 나타내는 값을 반환 합니다.|
|[CDaoRecordset:: GetName](#getname)|`CString`레코드 집합의 이름을 포함 하는을 반환 합니다.|
|[CDaoRecordset:: GetParamValue](#getparamvalue)|기본 DAOParameter 개체에 저장 된 지정 된 매개 변수의 현재 값을 검색 합니다.|
|[CDaoRecordset:: GetPercentPosition](#getpercentposition)|현재 레코드의 위치를 총 레코드 수에 대 한 백분율로 반환 합니다.|
|[CDaoRecordset:: GetRecordCount](#getrecordcount)|레코드 집합 개체에서 액세스 한 레코드 수를 반환 합니다.|
|[CDaoRecordset:: GetSQL](#getsql)|레코드 집합에 대 한 레코드를 선택 하는 데 사용 되는 SQL 문자열을 가져옵니다.|
|[CDaoRecordset:: GetType](#gettype)|레코드 집합의 형식 (테이블 형식, 다이너셋 형식 또는 스냅숏 형식)을 결정 하기 위해 호출 됩니다.|
|[CDaoRecordset:: GetValidationRule](#getvalidationrule)|`CString`필드에 입력 될 때 데이터의 유효성을 검사 하는 값을 포함 하는을 반환 합니다.|
|[CDaoRecordset:: GetValidationText](#getvalidationtext)|유효성 검사 규칙이 충족 되지 않을 때 표시 되는 텍스트를 검색 합니다.|
|[CDaoRecordset:: IsBOF](#isbof)|레코드 집합이 첫 번째 레코드 앞에 배치 되 면 0이 아닌 값을 반환 합니다. 현재 레코드가 없습니다.|
|[CDaoRecordset:: IsDeleted](#isdeleted)|레코드 집합이 삭제 된 레코드에 배치 되 면 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: IsEOF](#iseof)|레코드 집합이 마지막 레코드 뒤에 배치 된 경우 0이 아닌 값을 반환 합니다. 현재 레코드가 없습니다.|
|[CDaoRecordset:: IsFieldDirty](#isfielddirty)|현재 레코드의 지정 된 필드가 변경 된 경우 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: IsFieldNull](#isfieldnull)|현재 레코드의 지정 된 필드가 Null (값이 없는 경우) 이면 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: IsFieldNullable](#isfieldnullable)|현재 레코드의 지정 된 필드를 Null로 설정할 수 있으면 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: IsOpen](#isopen)|[Open](#open) 이 이전에 호출 된 경우 0이 아닌 값을 반환 합니다.|
|[CDaoRecordset:: Move](#move)|현재 레코드의 지정 된 레코드 수에 레코드 집합을 두 방향으로 배치 합니다.|
|[CDaoRecordset:: MoveFirst](#movefirst)|레코드 집합의 첫 번째 레코드에 현재 레코드를 배치 합니다.|
|[CDaoRecordset:: MoveLast](#movelast)|레코드 집합의 마지막 레코드에 현재 레코드를 배치 합니다.|
|[CDaoRecordset:: MoveNext](#movenext)|레코드 집합의 다음 레코드에 현재 레코드를 배치 합니다.|
|[CDaoRecordset:: MovePrev](#moveprev)|레코드 집합의 이전 레코드에 현재 레코드를 배치 합니다.|
|[CDaoRecordset:: Open](#open)|테이블, 다이너셋 또는 스냅숏에서 새 레코드 집합을 만듭니다.|
|[CDaoRecordset:: Requery](#requery)|레코드 집합의 쿼리를 다시 실행 하 여 선택한 레코드를 새로 고칩니다.|
|[CDaoRecordset:: Seek](#seek)|현재 인덱스에 대해 지정 된 조건을 충족 하는 인덱싱된 테이블 형식 recordset 개체에서 레코드를 찾고 해당 레코드를 현재 레코드로 설정 합니다.|
|[CDaoRecordset:: SetAbsolutePosition](#setabsoluteposition)|레코드 집합 개체의 현재 레코드에 대 한 레코드 번호를 설정 합니다.|
|[CDaoRecordset:: SetBookmark](#setbookmark)|지정 된 책갈피를 포함 하는 레코드에 레코드 집합을 배치 합니다.|
|[CDaoRecordset:: SetCacheSize](#setcachesize)|ODBC 데이터 원본에서 로컬로 캐시할 데이터를 포함 하는 다이너셋 형식 레코드 집합의 레코드 수를 지정 하는 값을 설정 합니다.|
|[CDaoRecordset:: SetCacheStart](#setcachestart)|캐시 될 레코드 집합에서 첫 번째 레코드의 책갈피를 지정 하는 값을 설정 합니다.|
|[CDaoRecordset:: SetCurrentIndex](#setcurrentindex)|테이블 형식 레코드 집합에 대 한 인덱스를 설정 하기 위해 호출 됩니다.|
|[CDaoRecordset:: SetFieldDirty](#setfielddirty)|현재 레코드에서 지정 된 필드를 변경 된 것으로 표시 합니다.|
|[CDaoRecordset:: SetFieldNull](#setfieldnull)|현재 레코드에서 지정 된 필드의 값을 Null (값 없음)으로 설정 합니다.|
|[CDaoRecordset:: SetFieldValue](#setfieldvalue)|레코드 집합에 있는 필드의 값을 설정 합니다.|
|[CDaoRecordset:: SetFieldValueNull](#setfieldvaluenull)|레코드 집합의 필드 값을 Null로 설정 합니다. (값 없음).|
|[CDaoRecordset:: SetLockingMode](#setlockingmode)|편집 하는 동안 적용 될 잠금 유형을 나타내는 값을 설정 합니다.|
|[CDaoRecordset:: SetParamValue](#setparamvalue)|기본 DAOParameter 개체에 저장 된 지정 된 매개 변수의 현재 값을 설정 합니다.|
|[CDaoRecordset:: SetParamValueNull](#setparamvaluenull)|지정 된 매개 변수의 현재 값을 값이 없는 Null로 설정 합니다.|
|[CDaoRecordset:: SetPercentPosition](#setpercentposition)|레코드 집합의 총 레코드 수에 대 한 백분율에 해당 하는 위치로 현재 레코드의 위치를 설정 합니다.|
|[CDaoRecordset:: Update](#update)|`AddNew` `Edit` 새 데이터 또는 편집 된 데이터를 데이터 소스에 저장 하 여 또는 작업을 완료 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDaoRecordset:: m_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields)|필드를 자동으로 변경 된 것으로 표시할지 여부를 나타내는 플래그를 포함 합니다.|
|[CDaoRecordset:: m_nFields](#m_nfields)|레코드 집합 클래스의 필드 데이터 멤버 수와 데이터 원본의 레코드 집합에서 선택한 열 수를 포함 합니다.|
|[CDaoRecordset:: m_nParams](#m_nparams)|레코드 집합의 쿼리와 함께 전달 되는 매개 변수 수와 같은 레코드 집합 클래스의 매개 변수 데이터 멤버 수를 포함 합니다.|
|[CDaoRecordset:: m_pDAORecordset](#m_pdaorecordset)|레코드 집합 개체의 내부에 있는 DAO 인터페이스에 대 한 포인터입니다.|
|[CDaoRecordset:: m_pDatabase](#m_pdatabase)|이 결과 집합에 대 한 원본 데이터베이스입니다. [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터를 포함 합니다.|
|[CDaoRecordset:: m_strFilter](#m_strfilter)|SQL **WHERE** 문을 생성 하는 데 사용 되는 문자열을 포함 합니다.|
|[CDaoRecordset:: m_strSort](#m_strsort)|SQL **ORDER by** 문을 생성 하는 데 사용 되는 문자열을 포함 합니다.|

## <a name="remarks"></a>설명

"레코드 집합" 이라고 하 `CDaoRecordset` 는 개체는 다음과 같은 세 가지 형태로 사용할 수 있습니다.

- 테이블 형식 레코드 집합은 단일 데이터베이스 테이블에서 레코드를 검사, 추가, 변경 또는 삭제 하는 데 사용할 수 있는 기본 테이블을 나타냅니다.

- 다이너셋 형식 레코드 집합은 업데이트 가능한 레코드를 가질 수 있는 쿼리의 결과입니다. 이러한 레코드 집합은 기본 데이터베이스 테이블이 나 테이블에서 레코드를 검사, 추가, 변경 또는 삭제 하는 데 사용할 수 있는 레코드 집합입니다. 다이너셋 형식 레코드 집합은 데이터베이스에 있는 하나 이상의 테이블에 있는 필드를 포함할 수 있습니다.

- 스냅숏 형식 레코드 집합은 데이터를 찾거나 보고서를 생성 하는 데 사용할 수 있는 레코드 집합의 정적 복사본입니다. 이러한 레코드 집합은 데이터베이스에 있는 하나 이상의 테이블에 있는 필드를 포함할 수 있지만 업데이트할 수는 없습니다.

각 레코드 집합의 형태는 레코드 집합을 열 때 고정 된 레코드 집합을 나타냅니다. 테이블 형식 레코드 집합 또는 다이너셋 형식의 레코드 집합에 있는 레코드로 스크롤하면 다른 사용자나 응용 프로그램의 다른 레코드 집합에서 레코드 집합을 연 후 레코드에 대 한 변경 내용이 반영 됩니다. (스냅숏 형식의 레코드 집합은 업데이트할 수 없습니다.) `CDaoRecordset` 을 직접 사용 하거나에서 응용 프로그램별 레코드 집합 클래스를 파생할 수 있습니다 `CDaoRecordset` . 그러면 다음을 수행할 수 있습니다.

- 레코드를 스크롤합니다.

- 인덱스를 설정 하 고 [Seek](#seek) 를 사용 하 여 레코드를 빠르게 찾습니다 (테이블 형식 레코드 집합에만 해당).

- 문자열 비교를 기준으로 레코드 찾기: "<", " \<=", "=", "> =" 또는 ">" (다이너셋 형식 및 스냅숏 형식 레코드 집합)

- 레코드를 업데이트 하 고 잠금 모드 (스냅숏 유형 레코드 집합 제외)를 지정 합니다.

- 레코드 집합을 필터링 하 여 데이터 원본에서 사용할 수 있는 레코드를 제약 합니다.

- 레코드 집합을 정렬 합니다.

- 런타임에 알려지지 않은 정보를 사용 하 여 선택 항목을 사용자 지정 하려면 레코드 집합을 매개 변수화 합니다.

클래스 `CDaoRecordset` 는 클래스의 인터페이스와 비슷한 인터페이스를 제공 `CRecordset` 합니다. 주요 차이점은 클래스가 `CDaoRecordset` OLE 기반 DAO (Data Access Object)를 통해 데이터에 액세스 한다는 것입니다. 클래스 `CRecordset` 는 odbc (Open Database Connectivity) 및 해당 dbms에 대 한 odbc 드라이버를 통해 dbms에 액세스 합니다.

> [!NOTE]
> DAO 데이터베이스 클래스는 ODBC (Open Database Connectivity)를 기반으로 하는 MFC 데이터베이스 클래스와는 다릅니다. 모든 DAO 데이터베이스 클래스 이름에는 "CDao" 접두사가 있습니다. 여전히 DAO 클래스를 사용 하 여 ODBC 데이터 원본에 액세스할 수 있습니다. 일반적으로 DAO 클래스는 Microsoft Jet 데이터베이스 엔진과 관련 되므로 뛰어난 기능을 제공 합니다.

을 `CDaoRecordset` 직접 사용 하거나에서 클래스를 파생 시킬 수 있습니다 `CDaoRecordset` . 두 경우 모두 레코드 집합 클래스를 사용 하려면 데이터베이스를 열고 레코드 집합 개체를 생성 하 여 생성자에 게 개체에 대 한 포인터를 전달 `CDaoDatabase` 합니다. 개체를 생성 하 `CDaoRecordset` 고 MFC에서 임시 개체를 만들도록 할 수도 있습니다 `CDaoDatabase` . 그런 다음 레코드 집합의 [Open](#open) 멤버 함수를 호출 하 여 개체가 테이블 형식 레코드 집합 인지, 다이너셋 형식 레코드 집합 인지 또는 스냅숏 형식 레코드 집합 인지를 지정 합니다. 를 호출 하면 `Open` 데이터베이스에서 데이터를 선택 하 고 첫 번째 레코드를 검색 합니다.

개체의 멤버 함수 및 데이터 멤버를 사용 하 여 레코드를 스크롤하고 작업에 대해 작업을 수행 합니다. 사용 가능한 작업은 개체가 테이블 형식 레코드 집합 인지, 다이너셋 형식 레코드 집합 인지, 스냅숏 형식 레코드 집합 인지, 업데이트 가능한 지, 아니면 읽기 전용인 지에 따라 달라 집니다. 데이터베이스 또는 ODBC (Open Database Connectivity) 데이터 원본의 기능에 따라 달라 집니다. 호출 이후에 변경 되거나 추가 된 레코드를 새로 고치려면 `Open` 개체의 [Requery](#requery) 멤버 함수를 호출 합니다. 개체의 멤버 함수를 호출 하 `Close` 고 완료 되 면 개체를 삭제 합니다.

`CDaoRecordset` 는 DAO 레코드 필드 교환 (DFX)을 사용 하 여 또는 파생 클래스의 형식이 안전한 c + + 멤버를 통해 레코드 필드의 읽기 및 업데이트를 지원 `CDaoRecordset` `CDaoRecordset` 합니다. [GetFieldValue](#getfieldvalue) 및 [SetFieldValue](#setfieldvalue)를 사용 하 여 DFX 메커니즘을 사용 하지 않고 데이터베이스에서 열의 동적 바인딩을 구현할 수도 있습니다.

관련 내용은 DAO 도움말의 "레코드 집합 개체" 항목을 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDaoRecordset`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaorecordsetaddnew"></a><a name="addnew"></a> CDaoRecordset:: AddNew

이 멤버 함수를 호출 하 여 테이블 형식 또는 다이너셋 형식의 레코드 집합에 새 레코드를 추가 합니다.

```cpp
virtual void AddNew();
```

### <a name="remarks"></a>설명

레코드의 필드는 처음에 Null입니다. (데이터베이스 용어에서 Null은 "값을 갖지 않음"을 의미 하 고 c + +의 경우 NULL과 같지 않습니다.) 작업을 완료 하려면 [Update](#update) 멤버 함수를 호출 해야 합니다. `Update` 데이터 원본에 대 한 변경 내용을 저장 합니다.

> [!CAUTION]
> 레코드를 편집 하 고를 호출 하지 않고 다른 레코드로 스크롤하면 `Update` 변경 내용이 경고 없이 손실 됩니다.

[AddNew](#addnew)를 호출 하 여 다이너셋 형식의 레코드 집합에 레코드를 추가 하는 경우 레코드는 레코드 집합에 표시 되 고 기본 테이블에 포함 되어 새 개체에 표시 됩니다 `CDaoRecordset` .

새 레코드의 위치는 레코드 집합의 유형에 따라 달라 집니다.

- 새 레코드가 삽입 되는 다이너셋 형식의 레코드 집합에서 보장 되지 않습니다. 이 동작은 성능 및 동시성의 이유로 Microsoft Jet 3.0로 변경 되었습니다. 새로 추가 된 레코드를 현재 레코드로 설정 하는 것을 목표로 하는 경우 마지막으로 수정 된 레코드의 책갈피를 가져오고 해당 책갈피로 이동 합니다.

[!code-cpp[NVC_MFCDatabase#1](../../mfc/codesnippet/cpp/cdaorecordset-class_1.cpp)]

- 인덱스가 지정 된 테이블 형식 레코드 집합에서 레코드는 정렬 순서에서 적절 한 위치로 반환 됩니다. 인덱스를 지정 하지 않으면 레코드 집합의 끝에 새 레코드가 반환 됩니다.

를 사용 하기 전에 현재 레코드는 `AddNew` 최신 상태로 유지 됩니다. 새 레코드를 최신 레코드로 설정 하 고 레코드 집합에서 책갈피를 지 원하는 경우 기본 DAO 레코드 집합 개체의 LastModified 속성 설정으로 식별 된 책갈피에 대 한 [Setbookmark](#setbookmark) 를 호출 합니다. 이렇게 하면 추가 된 레코드의 카운터 (자동 증가) 필드에 대 한 값을 결정 하는 데 유용 합니다. 자세한 내용은 [GetLastModifiedBookmark](#getlastmodifiedbookmark)를 참조 하세요.

데이터베이스가 트랜잭션을 지 원하는 경우 트랜잭션 호출을 수행할 수 있습니다 `AddNew` . 트랜잭션에 대 한 자세한 내용은 클래스 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)를 참조 하세요. 를 호출 하기 전에 [CDaoWorkspace:: BeginTrans](../../mfc/reference/cdaoworkspace-class.md#begintrans) 를 호출 해야 `AddNew` 합니다.

`AddNew` [Open](#open) 멤버 함수가 호출 되지 않은 레코드 집합에 대해를 호출할 수 없습니다. 추가할 수 없는 `CDaoException` `AddNew` 레코드 집합에 대해를 호출 하면이 throw 됩니다. [CanAppend](#canappend)를 호출 하 여 레코드 집합을 업데이트할 수 있는지 여부를 확인할 수 있습니다.

이 프레임 워크는 변경 된 필드 데이터 멤버를 표시 하 여 DAO 레코드 필드 교환 (DFX) 메커니즘에 의해 데이터 원본의 레코드에 기록 되도록 합니다. 필드의 값을 변경 하는 것은 일반적으로 자동으로 필드를 설정 하지 않으므로 사용자가 직접 [SetFieldDirty](#setfielddirty) 를 호출할 필요가 없지만 필드 데이터 멤버의 값에 관계 없이 열이 명시적으로 업데이트 되거나 삽입 되도록 할 수도 있습니다. 또한 DFX 메커니즘은 **의사 (PSEUDO) NULL** 을 사용 합니다. 자세한 내용은 [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)를 참조 하세요.

이중 버퍼링 메커니즘이 사용 되지 않는 경우 필드의 값을 변경 해도 필드가 더티로 자동 설정 되지 않습니다. 이 경우 필드를 명확 하 게 설정 해야 합니다. [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) 에 포함 된 플래그는이 자동 필드 검사를 제어 합니다.

> [!NOTE]
> 레코드가 이중 버퍼링 되는 경우 (즉, 자동 필드 검사를 사용 하도록 설정 된 경우)를 호출 하면 `CancelUpdate` 멤버 변수가 이전 `AddNew` 또는 호출 된 값으로 복원 됩니다 `Edit` .

관련 정보는 DAO 도움말의 "AddNew 메서드", "CancelUpdate 메서드", "LastModified 속성" 및 "EditMode 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetcanappend"></a><a name="canappend"></a> CDaoRecordset:: CanAppend

이 멤버 함수를 호출 하 여 이전에 열린 레코드 집합에서 [AddNew](#addnew) 멤버 함수를 호출 하 여 새 레코드를 추가할 수 있는지 여부를 확인 합니다.

```cpp
BOOL CanAppend() const;
```

### <a name="return-value"></a>반환 값

레코드 집합에서 새 레코드 추가를 허용 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다. `CanAppend` 는 레코드 집합을 읽기 전용으로 연 경우 0을 반환 합니다.

### <a name="remarks"></a>설명

관련 내용은 DAO 도움말의 "Append 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetcanbookmark"></a><a name="canbookmark"></a> CDaoRecordset:: CanBookmark

이 멤버 함수를 호출 하 여 이전에 열린 레코드 집합에서 책갈피를 사용 하 여 레코드를 개별적으로 표시할 수 있는지 여부를 확인 합니다.

```cpp
BOOL CanBookmark();
```

### <a name="return-value"></a>반환 값

레코드 집합에서 책갈피를 지원 하면 0이 아니고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Microsoft Jet 데이터베이스 엔진 테이블에 전적으로 레코드 집합을 사용 하는 경우에는 앞 으로만 이동 가능한 스크롤 레코드 집합으로 플래그가 지정 된 스냅숏 형식 레코드 집합을 제외 하 고 책갈피를 사용할 수 있습니다. 다른 데이터베이스 제품 (외부 ODBC 데이터 원본)은 책갈피를 지원 하지 않을 수 있습니다.

관련 내용은 DAO 도움말의 "책갈피 가능 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetcancelupdate"></a><a name="cancelupdate"></a> CDaoRecordset:: CancelUpdate

`CancelUpdate`멤버 함수는 [Edit](#edit) 또는 [AddNew](#addnew) 작업으로 인해 보류 중인 모든 업데이트를 취소 합니다.

```cpp
virtual void CancelUpdate();
```

### <a name="remarks"></a>설명

예를 들어 응용 프로그램이 `Edit` 또는 `AddNew` 멤버 함수를 호출 하 고 [Update](#update)를 호출 하지 않은 경우는 `CancelUpdate` 또는가 호출 된 후에 변경 된 내용을 취소 `Edit` `AddNew` 합니다.

> [!NOTE]
> 레코드가 이중 버퍼링 되는 경우 (즉, 자동 필드 검사를 사용 하도록 설정 된 경우)를 호출 하면 `CancelUpdate` 멤버 변수가 이전 `AddNew` 또는 호출 된 값으로 복원 됩니다 `Edit` .

`Edit`보류 중인 또는 작업이 없는 경우는 `AddNew` MFC에서 예외를 `CancelUpdate` throw 합니다. [Geteditmode](#geteditmode) 멤버 함수를 호출 하 여 취소할 수 있는 보류 중인 작업이 있는지 확인 합니다.

관련 내용은 DAO 도움말의 "CancelUpdate 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetcanrestart"></a><a name="canrestart"></a> CDaoRecordset:: CanRestart

이 멤버 함수를 호출 하 여 레코드 집합에서 멤버 함수를 호출 하 여 쿼리를 다시 시작 하 여 해당 레코드를 새로 고칠 수 있는지 여부를 확인 합니다 `Requery` .

```cpp
BOOL CanRestart();
```

### <a name="return-value"></a>반환 값

`Requery`레코드 집합의 쿼리를 다시 실행 하기 위해를 호출할 수 있으면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

테이블 형식 레코드 집합은를 지원 하지 않습니다 `Requery` .

`Requery`가 지원 되지 않는 경우 [Close](#close) 를 호출 [](#open) 하 여 데이터를 새로 고칩니다. `Requery`매개 변수 값이 변경 된 후를 호출 하 여 레코드 집합 개체의 기본 매개 변수 쿼리를 업데이트할 수 있습니다.

관련 내용은 DAO 도움말의 "다시 시작 가능한 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetcanscroll"></a><a name="canscroll"></a> CDaoRecordset:: CanScroll

이 멤버 함수를 호출 하 여 레코드 집합에서 스크롤할 수 있는지 여부를 확인 합니다.

```cpp
BOOL CanScroll() const;
```

### <a name="return-value"></a>반환 값

레코드를 스크롤할 수 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

[연결 프로그램](#open) 을 호출 하 `dbForwardOnly` 는 경우에는 레코드 집합을 앞 으로만 스크롤할 수 있습니다.

관련 내용은 DAO 도움말의 "DAO를 사용 하 여 현재 레코드 포인터 위치 지정" 항목을 참조 하십시오.

## <a name="cdaorecordsetcantransact"></a><a name="cantransact"></a> CDaoRecordset:: CanTransact

이 멤버 함수를 호출 하 여 레코드 집합에서 트랜잭션을 허용 하는지 여부를 확인 합니다.

```cpp
BOOL CanTransact();
```

### <a name="return-value"></a>반환 값

기본 데이터 소스에서 트랜잭션을 지원 하면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

관련 내용은 DAO 도움말의 "트랜잭션 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetcanupdate"></a><a name="canupdate"></a> CDaoRecordset:: CanUpdate

이 멤버 함수를 호출 하 여 레코드 집합을 업데이트할 수 있는지 여부를 확인 합니다.

```cpp
BOOL CanUpdate() const;
```

### <a name="return-value"></a>반환 값

레코드 집합을 업데이트 (추가, 업데이트 및 삭제) 할 수 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

기본 데이터 원본이 읽기 전용 이거나 `dbReadOnly` 레코드 집합에 대해 [Open](#open) 을 호출할 때 *nOptions* 에 대해을 지정한 경우에는 레코드 집합이 읽기 전용일 수 있습니다.

관련 정보는 DAO 도움말의 "AddNew 메서드", "메서드 편집", "메서드 삭제", "업데이트 방법" 및 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetcdaorecordset"></a><a name="cdaorecordset"></a> CDaoRecordset:: CDaoRecordset

`CDaoRecordset` 개체를 생성합니다.

```cpp
CDaoRecordset(CDaoDatabase* pDatabase = NULL);
```

### <a name="parameters"></a>매개 변수

*pDatabase*<br/>
[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체에 대 한 포인터 또는 NULL 값을 포함 합니다. NULL이 아닌 경우 `CDaoDatabase` `Open` 데이터 소스에 연결 하기 위해 개체의 멤버 함수를 호출 하지 않은 경우에는 레코드 집합에서 자체 [열기](#open) 호출 중에 해당 함수를 열려고 시도 합니다. NULL을 전달 하는 경우 `CDaoDatabase` 에서 레코드 집합 클래스를 파생 한 경우 지정한 데이터 원본 정보를 사용 하 여 개체를 생성 하 고 연결 합니다 `CDaoRecordset` .

### <a name="remarks"></a>설명

을 `CDaoRecordset` 직접 사용 하거나에서 응용 프로그램별 클래스를 파생할 수 있습니다 `CDaoRecordset` . 클래스 마법사를 사용 하 여 레코드 집합 클래스를 파생할 수 있습니다.

> [!NOTE]
> 클래스를 파생 하는 경우 `CDaoRecordset` 파생 클래스는 자체 생성자를 제공 해야 합니다. 파생 클래스의 생성자에서 적절 한 매개 변수를 전달 하 여 생성자를 호출 `CDaoRecordset::CDaoRecordset` 합니다.

개체가 자동으로 생성 되 고 연결 되도록 레코드 집합 생성자에 NULL을 전달 `CDaoDatabase` 합니다. 이는 `CDaoDatabase` 레코드 집합을 생성 하기 전에 개체를 구성 하 고 연결할 필요가 없는 유용한 바로 가기입니다. `CDaoDatabase`개체가 열려 있지 않으면 기본 작업 영역을 사용 하는 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 개체도 생성 됩니다. 자세한 내용은 [CDaoDatabase:: CDaoDatabase](../../mfc/reference/cdaodatabase-class.md#cdaodatabase)를 참조 하세요.

## <a name="cdaorecordsetclose"></a><a name="close"></a> CDaoRecordset:: Close

개체를 닫으면 `CDaoRecordset` 연결 된 데이터베이스의 열린 레코드 집합 컬렉션에서 개체가 제거 됩니다.

```cpp
virtual void Close();
```

### <a name="remarks"></a>설명

는 `Close` 개체를 삭제 하지 않으므로 `CDaoRecordset` `Open` 동일한 데이터 소스 또는 다른 데이터 소스에서를 호출 하 여 개체를 다시 사용할 수 있습니다.

보류 중인 모든 [AddNew](#addnew) 또는 [Edit](#edit) 문이 취소 되 고 보류 중인 모든 트랜잭션이 롤백됩니다. 보류 중인 추가 또는 편집 내용을 유지 하려면 [](#update) `Close` 각 레코드 집합에 대해를 호출 하기 전에 Update를 호출 합니다.

를 호출한 후을 다시 호출할 수 있습니다 `Open` `Close` . 이렇게 하면 레코드 집합 개체를 다시 사용할 수 있습니다. 더 나은 방법은 [Requery](#requery)를 호출 하는 것입니다 (가능한 경우).

관련 정보는 DAO 도움말의 "Close 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetdelete"></a><a name="delete"></a> CDaoRecordset::D e)

열려 있는 다이너셋 형식 또는 테이블 형식 레코드 집합 개체에서 현재 레코드를 삭제 하려면이 멤버 함수를 호출 합니다.

```cpp
virtual void Delete();
```

### <a name="remarks"></a>설명

성공적으로 삭제 한 후에는 레코드 집합의 필드 데이터 멤버가 Null 값으로 설정 되 고, 삭제 된 레코드를 이동 하기 위해 레코드 집합 탐색 멤버 함수 ( [move](#move), [Seek](#seek), [setbookmark](#setbookmark)등) 중 하나를 명시적으로 호출 해야 합니다. 레코드 집합에서 레코드를 삭제 하는 경우를 호출 하기 전에 레코드 집합에 현재 레코드가 있어야 합니다. `Delete` 그렇지 않으면 MFC에서 예외를 throw 합니다.

`Delete` 현재 레코드를 제거 하 고이 레코드를 액세스할 수 없게 만듭니다. 삭제 된 레코드는 편집 하거나 사용할 수 없지만 현재는 그대로 남아 있습니다. 그러나 다른 레코드로 이동한 후에는 삭제 된 레코드를 최신 레코드로 다시 설정할 수 없습니다.

> [!CAUTION]
> 레코드 집합은 업데이트할 수 있어야 하며,를 호출할 때 레코드 집합에 유효한 레코드가 있어야 합니다 `Delete` . 예를 들어 레코드를 삭제 하지만을 다시 호출 하기 전에 새 레코드로 스크롤하지 않는 경우 `Delete` `Delete` 는 [CDaoException](../../mfc/reference/cdaoexception-class.md)을 throw 합니다.

트랜잭션을 사용 하 고 [CDaoWorkspace:: Rollback](../../mfc/reference/cdaoworkspace-class.md#rollback) 멤버 함수를 호출 하는 경우 레코드의 삭제를 취소할 수 있습니다. 기본 테이블이 하위 삭제 관계의 주 테이블인 경우 현재 레코드를 삭제 하면 외래 테이블에서 하나 이상의 레코드가 삭제 될 수도 있습니다. 자세한 내용은 DAO 도움말의 "cascade delete" 정의를 참조 하십시오.

및와는 달리에 대 한 `AddNew` `Edit` 호출은 `Delete` 다음에 대 한 호출을 수행 하지 않습니다 `Update` .

관련 정보는 DAO 도움말의 "AddNew 메서드", "메서드 편집", "메서드 삭제", "업데이트 방법" 및 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetdofieldexchange"></a><a name="dofieldexchange"></a> CDaoRecordset::D oFieldExchange

프레임 워크는이 멤버 함수를 호출 하 여 레코드 집합 개체의 필드 데이터 멤버와 데이터 소스에 있는 현재 레코드의 해당 열 간에 데이터를 자동으로 교환 합니다.

```cpp
virtual void DoFieldExchange(CDaoFieldExchange* pFX);
```

### <a name="parameters"></a>매개 변수

*pFX*<br/>
개체에 대 한 포인터를 포함 `CDaoFieldExchange` 합니다. 프레임 워크에는 필드 교환 작업의 컨텍스트를 지정 하는이 개체가 이미 설정 되어 있습니다.

### <a name="remarks"></a>설명

또한 매개 변수 데이터 멤버 (있는 경우)를 레코드 집합의 선택에 대 한 SQL 문 문자열의 매개 변수 자리 표시자에 바인딩합니다. DAO 레코드 필드 교환 (DFX) 이라고 하는 필드 데이터 교환은 레코드 집합 개체의 필드 데이터 멤버와 데이터 원본에 있는 레코드의 필드, 데이터 원본의 레코드에서 레코드 집합 개체로의 양방향으로 작동 합니다. 열을 동적으로 바인딩하는 경우에는를 구현할 필요가 없습니다 `DoFieldExchange` .

파생 된 레코드 집합 클래스에 대해 일반적으로를 구현 하기 위해 수행 해야 하는 작업은 `DoFieldExchange` 클래스 마법사를 사용 하 여 클래스를 만들고 필드 데이터 멤버의 이름과 데이터 형식을 지정 하는 것입니다. 매개 변수 데이터 멤버를 지정 하기 위해 클래스 마법사에서 작성 하는 코드를 추가할 수도 있습니다. 모든 필드를 동적으로 바인딩하는 경우 매개 변수 데이터 멤버를 지정 하지 않으면이 함수는 비활성화 됩니다.

클래스 마법사를 사용 하 여 파생 된 레코드 집합 클래스를 선언 하면 마법사가 다음 예제와 유사한의 재정의를 작성 합니다 `DoFieldExchange` .

[!code-cpp[NVC_MFCDatabase#2](../../mfc/codesnippet/cpp/cdaorecordset-class_2.cpp)]

## <a name="cdaorecordsetedit"></a><a name="edit"></a> CDaoRecordset:: Edit

현재 레코드를 변경할 수 있도록 하려면이 멤버 함수를 호출 합니다.

```cpp
virtual void Edit();
```

### <a name="remarks"></a>설명

멤버 함수를 호출 하면 `Edit` 현재 레코드의 필드에 대 한 변경 내용이 복사 버퍼에 복사 됩니다. 레코드를 원하는 대로 변경한 후 `Update` 에는를 호출 하 여 변경 내용을 저장 합니다. `Edit` 레코드 집합의 데이터 멤버 값을 저장 합니다. 을 호출 하는 경우 `Edit` 를 변경 하 고를 다시 호출 하면 `Edit` 레코드의 값이 첫 번째 호출 이전의 항목으로 복원 됩니다 `Edit` .

> [!CAUTION]
> 레코드를 편집한 다음 먼저를 호출 하지 않고 다른 레코드로 이동 하는 작업을 수행 하는 경우 `Update` 변경 내용이 경고 없이 손실 됩니다. 또한 레코드 집합 또는 부모 데이터베이스를 닫으면 편집 된 레코드는 경고 없이 삭제 됩니다.

일부 경우에는 데이터를 포함 하지 않는 열을 Null로 설정 하 여 열을 업데이트 하는 것이 좋습니다. 이렇게 하려면 `SetFieldNull` TRUE의 매개 변수를 사용 하 여를 호출 하 여 필드를 Null로 표시 합니다. 이렇게 하면 열도 업데이트 됩니다. 값이 변경 되지 않은 경우에도 데이터 소스에 필드를 기록 하려면 `SetFieldDirty` TRUE의 매개 변수를 사용 하 여를 호출 합니다. 필드의 값이 Null 인 경우에도 작동 합니다.

이 프레임 워크는 변경 된 필드 데이터 멤버를 표시 하 여 DAO 레코드 필드 교환 (DFX) 메커니즘에 의해 데이터 원본의 레코드에 기록 되도록 합니다. 필드의 값을 변경 하는 것은 일반적으로 자동으로 필드를 설정 하지 않으므로 사용자가 직접 [SetFieldDirty](#setfielddirty) 를 호출할 필요가 없지만 필드 데이터 멤버의 값에 관계 없이 열이 명시적으로 업데이트 되거나 삽입 되도록 할 수도 있습니다. 또한 DFX 메커니즘은 **의사 (PSEUDO) NULL** 을 사용 합니다. 자세한 내용은 [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)를 참조 하세요.

이중 버퍼링 메커니즘이 사용 되지 않는 경우 필드의 값을 변경 해도 필드가 더티로 자동 설정 되지 않습니다. 이 경우 필드를 명확 하 게 설정 해야 합니다. [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) 에 포함 된 플래그는이 자동 필드 검사를 제어 합니다.

다중 사용자 환경에서 레코드 집합 개체가 pessimistically 되 면 `Edit` 업데이트가 완료 될 때까지 해당 레코드는 해당 시점에서 잠긴 상태로 유지 됩니다. 레코드 집합이 낙관적으로 잠겨 있으면 레코드는 잠기고 데이터베이스에서 업데이트 되기 직전에 미리 편집 된 레코드와 비교 됩니다. 를 호출한 후에 레코드가 변경 된 경우 `Edit` `Update` 작업이 실패 하 고 MFC에서 예외가 throw 됩니다. 를 사용 하 여 잠금 모드를 변경할 수 있습니다 `SetLockingMode` .

> [!NOTE]
> 낙관적 잠금은 ODBC 및 설치 가능 ISAM과 같은 외부 데이터베이스 형식에서 항상 사용 됩니다.

를 호출한 후에는 현재 레코드가 최신 상태로 유지 됩니다 `Edit` . 을 호출 하려면 `Edit` 현재 레코드가 있어야 합니다. 현재 레코드가 없거나 레코드 집합이 열려 있는 테이블 형식 또는 다이너셋 형식의 레코드 집합 개체를 참조 하지 않는 경우 예외가 발생 합니다. 를 호출 `Edit` 하면 `CDaoException` 다음과 같은 경우이 throw 됩니다.

- 현재 레코드가 없습니다.

- 데이터베이스 또는 레코드 집합은 읽기 전용입니다.

- 레코드의 필드는 업데이트할 수 없습니다.

- 다른 사용자가 단독으로 사용 하도록 데이터베이스 또는 레코드 집합을 열었습니다.

- 다른 사용자가 레코드를 포함 하는 페이지를 잠 궜 습니다.

데이터 원본에서 트랜잭션을 지 원하는 경우 트랜잭션의 호출을 수행할 수 있습니다 `Edit` . 를 호출 `CDaoWorkspace::BeginTrans` 하기 전에 `Edit` 및 레코드 집합을 연 후를 호출 해야 합니다. 또한 호출은 작업을 `CDaoWorkspace::CommitTrans` `Update` 완료 하기 위해를 호출 하는 대신 사용할 수 없습니다 `Edit` . 트랜잭션에 대 한 자세한 내용은 클래스를 참조 하세요 `CDaoWorkspace` .

관련 정보는 DAO 도움말의 "AddNew 메서드", "메서드 편집", "메서드 삭제", "업데이트 방법" 및 "업데이트할 수 있는 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetfillcache"></a><a name="fillcache"></a> CDaoRecordset:: FillCache

이 멤버 함수를 호출 하 여 레코드 집합에서 지정 된 수의 레코드를 캐시 합니다.

```cpp
void FillCache(
    long* pSize = NULL,
    COleVariant* pBookmark = NULL);
```

### <a name="parameters"></a>매개 변수

*pSize*<br/>
캐시에 채울 행의 수를 지정 합니다. 이 매개 변수를 생략 하면 기본 DAO 개체의 CacheSize 속성 설정에 따라 값이 결정 됩니다.

*pBookmark*<br/>
책갈피를 지정 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 입니다. 캐시는이 책갈피로 표시 된 레코드부터 채워집니다. 이 매개 변수를 생략 하면 기본 DAO 개체의 CacheStart 속성이 나타내는 레코드부터 캐시가 채워집니다.

### <a name="remarks"></a>설명

캐싱은 원격 서버에서 데이터를 검색 하거나 인출 하는 응용 프로그램의 성능을 향상 시킵니다. 캐시는 응용 프로그램이 실행 되는 동안 데이터를 다시 요청 하는 것으로 가정 하 고 서버에서 가장 최근에 인출 된 데이터를 보유 하는 로컬 메모리의 공간입니다. 데이터가 요청 될 때 Microsoft Jet 데이터베이스 엔진은 서버에서 데이터를 인출 하지 않고 먼저 캐시를 검사 하 여 더 많은 시간을 사용 합니다. 데이터가 캐시에 저장 되지 않으므로 비 ODBC 데이터 원본에 대 한 데이터 캐싱을 사용 해도 아무런 효과가 없습니다.

인출 되는 레코드로 캐시가 채워질 때까지 기다리는 대신 멤버 함수를 호출 하 여 언제 든 지 캐시를 명시적으로 채울 수 있습니다 `FillCache` . 이는 여러 레코드를 한 번에 하나씩 인출 하기 때문에 캐시를 채우는 더 빠른 방법입니다 `FillCache` . 예를 들어 레코드의 각가 중에 표시 되는 동안 응용 프로그램을 호출 하 여 다음의 화면에 표시 되는 레코드를 가져올 수 있습니다 `FillCache` .

레코드 집합 개체를 사용 하 여 액세스 하는 모든 ODBC 데이터베이스에는 로컬 캐시가 있을 수 있습니다. 캐시를 만들려면 원격 데이터 원본에서 레코드 집합 개체를 연 다음 `SetCacheSize` `SetCacheStart` 레코드 집합의 및 멤버 함수를 호출 합니다. *Lsize* 및 *lsize* 가 및로 지정 된 범위를 벗어난 범위를 만드는 경우 `SetCacheSize` `SetCacheStart` 이 범위를 벗어난 레코드 집합의 부분은 무시 되 고 캐시로 로드 되지 않습니다. `FillCache`가 원격 데이터 원본에 남아 있는 것 보다 많은 레코드를 요청 하는 경우 나머지 레코드만 인출 되 고 예외가 throw 되지 않습니다.

캐시에서 가져온 레코드는 다른 사용자가 원본 데이터에 대해 동시에 변경한 내용을 반영 하지 않습니다.

`FillCache` 아직 캐시 되지 않은 레코드만 페치합니다. 모든 캐시 된 데이터를 강제로 업데이트 하려면 `SetCacheSize` 0과 동일한 *lsize* 매개 변수를 사용 하 여 멤버 함수를 호출 하 고, `SetCacheSize` 원래 요청한 캐시 크기와 동일한 *lsize* 매개 변수를 사용 하 여를 다시 호출한 다음을 호출 `FillCache` 합니다.

관련 내용은 DAO 도움말의 "FillCache 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetfind"></a><a name="find"></a> CDaoRecordset:: Find

비교 연산자를 사용 하 여 다이너셋 또는 스냅숏 형식 레코드 집합에서 특정 문자열을 찾으려면이 멤버 함수를 호출 합니다.

```cpp
virtual BOOL Find(
    long lFindType,
    LPCTSTR lpszFilter);
```

### <a name="parameters"></a>매개 변수

*lFindType*<br/>
원하는 찾기 작업의 유형을 나타내는 값입니다. 가능한 값은 다음과 같습니다.

- AFX_DAO_NEXT 일치 하는 문자열의 다음 위치를 찾습니다.

- AFX_DAO_PREV 일치 하는 문자열의 이전 위치를 찾습니다.

- AFX_DAO_FIRST 일치 하는 문자열의 첫 번째 위치를 찾습니다.

- 일치 하는 문자열의 마지막 위치를 찾을 AFX_DAO_LAST.

*lpszFilter*<br/>
레코드를 찾는 데 사용 되는 **where** 라는 단어가 없는 SQL 문의 **where** 절과 같은 문자열 식입니다. 예를 들어:

[!code-cpp[NVC_MFCDatabase#3](../../mfc/codesnippet/cpp/cdaorecordset-class_3.cpp)]

### <a name="return-value"></a>반환 값

일치 하는 레코드가 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

문자열의 첫 번째, 다음, 이전 또는 마지막 인스턴스를 찾을 수 있습니다. `Find` 는 가상 함수 이므로 재정의 하 고 사용자 고유의 구현을 추가할 수 있습니다. `FindFirst`, `FindLast` , `FindNext` 및 `FindPrev` 멤버 함수는 `Find` 멤버 함수를 호출 하므로를 사용 하 여 `Find` 모든 찾기 작업의 동작을 제어할 수 있습니다.

테이블 형식 레코드 집합에서 레코드를 찾으려면 [Seek](#seek) 멤버 함수를 호출 합니다.

> [!TIP]
> 레코드 집합 수가 작을수록 더 효율적 `Find` 입니다. 일반적으로 특히 ODBC 데이터를 사용 하는 경우 원하는 레코드만 검색 하는 새 쿼리를 만드는 것이 좋습니다.

관련 정보는 DAO 도움말의 "FindFirst, FindLast, FindNext, Findlast 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetfindfirst"></a><a name="findfirst"></a> CDaoRecordset:: FindFirst

이 멤버 함수를 호출 하 여 지정 된 조건과 일치 하는 첫 번째 레코드를 찾습니다.

```cpp
BOOL FindFirst(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>매개 변수

*lpszFilter*<br/>
레코드를 찾는 데 사용 되는 **where** 라는 단어가 없는 SQL 문의 **where** 절과 같은 문자열 식입니다.

### <a name="return-value"></a>반환 값

일치 하는 레코드가 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`FindFirst`멤버 함수는 레코드 집합의 시작 부분에서 검색을 시작 하 고 레코드 집합의 끝을 검색 합니다.

특정 조건을 충족 하는 레코드 뿐만 아니라 검색의 모든 레코드를 포함 하려는 경우 이동 작업 중 하나를 사용 하 여 레코드에서 레코드로 이동 합니다. 테이블 형식 레코드 집합에서 레코드를 찾으려면 `Seek` 멤버 함수를 호출 합니다.

기준과 일치 하는 레코드를 찾지 못하면 현재 레코드 포인터가 결정 되지 않고 `FindFirst` 0을 반환 합니다. 레코드 집합에 조건을 충족 하는 레코드가 두 개 이상 포함 되어 있으면이 `FindFirst` 고, 첫 번째 항목을 찾고, `FindNext` 다음 항목을 찾습니다.

> [!CAUTION]
> 현재 레코드를 편집 하는 경우 `Update` 다른 레코드로 이동 하기 전에 멤버 함수를 호출 하 여 변경 내용을 저장 해야 합니다. 업데이트 하지 않고 다른 레코드로 이동 하면 변경 내용이 경고 없이 손실 됩니다.

`Find`멤버 함수는 위치 및 다음 표에 지정 된 방향에서 검색 합니다.

|찾기 작업|시작|검색 방향|
|---------------------|-----------|----------------------|
|`FindFirst`|레코드 집합의 시작|레코드 집합의 끝|
|`FindLast`|레코드 집합의 끝|레코드 집합의 시작|
|`FindNext`|현재 레코드|레코드 집합의 끝|
|`FindPrevious`|현재 레코드|레코드 집합의 시작|

> [!NOTE]
> `FindLast`을 (를) 호출 하면 검색을 시작 하기 전에 Microsoft Jet 데이터베이스 엔진이 레코드 집합을 완전히 채웁니다 (아직 수행 하지 않은 경우). 첫 번째 검색은 후속 검색 보다 더 오래 걸릴 수 있습니다.

그러나 찾기 작업 중 하나를 사용 하는 것은 또는를 호출 하는 것과 동일 하지 않습니다 `MoveFirst` `MoveNext` . 그러나 단순히 조건을 지정 하지 않고 첫 번째 또는 다음 레코드를 최신으로 만듭니다. 이동 작업을 사용 하 여 찾기 작업을 수행할 수 있습니다.

찾기 작업을 사용할 때는 다음 사항에 유의 하세요.

- `Find`가 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않습니다. 이 경우 현재 레코드 포인터를 올바른 레코드로 다시 배치 해야 합니다.

- 앞 으로만 이동 가능한 스냅숏 형식의 레코드 집합에는 찾기 작업을 사용할 수 없습니다.

- 미국 버전의 Microsoft Jet 데이터베이스 엔진을 사용 하지 않는 경우에도 날짜를 포함 하는 필드를 검색 하는 경우 미국 날짜 형식 (월-일-연도)을 사용 해야 합니다. 그렇지 않으면 일치 하는 레코드를 찾을 수 없습니다.

- ODBC 데이터베이스 및 다량의 다이너셋을 사용할 때 특히 긴 레코드 집합으로 작업 하는 경우 찾기 작업을 사용 하는 속도가 느려지는 것을 알 수 있습니다. 사용자 지정 된 **ORDERBY** 또는 **WHERE** 절, 매개 변수 쿼리 또는 `CDaoQuerydef` 특정 인덱싱된 레코드를 검색 하는 개체를 사용 하 여 SQL 쿼리를 사용 하 여 성능을 향상 시킬 수 있습니다.

관련 정보는 DAO 도움말의 "FindFirst, FindLast, FindNext, Findlast 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetfindlast"></a><a name="findlast"></a> CDaoRecordset:: FindLast

지정 된 조건과 일치 하는 마지막 레코드를 찾으려면이 멤버 함수를 호출 합니다.

```cpp
BOOL FindLast(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>매개 변수

*lpszFilter*<br/>
레코드를 찾는 데 사용 되는 **where** 라는 단어가 없는 SQL 문의 **where** 절과 같은 문자열 식입니다.

### <a name="return-value"></a>반환 값

일치 하는 레코드가 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`FindLast`멤버 함수는 레코드 집합의 끝 부분에서 검색을 시작 하 고 레코드 집합의 시작 부분을 뒤로 검색 합니다.

특정 조건을 충족 하는 레코드 뿐만 아니라 검색의 모든 레코드를 포함 하려는 경우 이동 작업 중 하나를 사용 하 여 레코드에서 레코드로 이동 합니다. 테이블 형식 레코드 집합에서 레코드를 찾으려면 `Seek` 멤버 함수를 호출 합니다.

기준과 일치 하는 레코드를 찾지 못하면 현재 레코드 포인터가 결정 되지 않고 `FindLast` 0을 반환 합니다. 레코드 집합에 조건을 충족 하는 레코드가 두 개 이상 포함 되어 있으면, 첫 번째 항목을 `FindFirst` 찾고, `FindNext` 첫 번째 발생 후 다음 항목을 찾습니다.

> [!CAUTION]
> 현재 레코드를 편집 하는 경우 `Update` 다른 레코드로 이동 하기 전에 멤버 함수를 호출 하 여 변경 내용을 저장 해야 합니다. 업데이트 하지 않고 다른 레코드로 이동 하면 변경 내용이 경고 없이 손실 됩니다.

그러나 찾기 작업 중 하나를 사용 하는 것은 또는를 호출 하는 것과 동일 하지 않습니다 `MoveFirst` `MoveNext` . 그러나 단순히 조건을 지정 하지 않고 첫 번째 또는 다음 레코드를 최신으로 만듭니다. 이동 작업을 사용 하 여 찾기 작업을 수행할 수 있습니다.

찾기 작업을 사용할 때는 다음 사항에 유의 하세요.

- `Find`가 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않습니다. 이 경우 현재 레코드 포인터를 올바른 레코드로 다시 배치 해야 합니다.

- 앞 으로만 이동 가능한 스냅숏 형식의 레코드 집합에는 찾기 작업을 사용할 수 없습니다.

- 미국 버전의 Microsoft Jet 데이터베이스 엔진을 사용 하지 않는 경우에도 날짜를 포함 하는 필드를 검색 하는 경우 미국 날짜 형식 (월-일-연도)을 사용 해야 합니다. 그렇지 않으면 일치 하는 레코드를 찾을 수 없습니다.

- ODBC 데이터베이스 및 다량의 다이너셋을 사용할 때 특히 긴 레코드 집합으로 작업 하는 경우 찾기 작업을 사용 하는 속도가 느려지는 것을 알 수 있습니다. 사용자 지정 된 **ORDERBY** 또는 **WHERE** 절, 매개 변수 쿼리 또는 `CDaoQuerydef` 특정 인덱싱된 레코드를 검색 하는 개체를 사용 하 여 SQL 쿼리를 사용 하 여 성능을 향상 시킬 수 있습니다.

관련 정보는 DAO 도움말의 "FindFirst, FindLast, FindNext, Findlast 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetfindnext"></a><a name="findnext"></a> CDaoRecordset:: FindNext

이 멤버 함수를 호출 하 여 지정 된 조건과 일치 하는 다음 레코드를 찾습니다.

```cpp
BOOL FindNext(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>매개 변수

*lpszFilter*<br/>
레코드를 찾는 데 사용 되는 **where** 라는 단어가 없는 SQL 문의 **where** 절과 같은 문자열 식입니다.

### <a name="return-value"></a>반환 값

일치 하는 레코드가 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`FindNext`멤버 함수는 현재 레코드에서 검색을 시작 하 고 레코드 집합의 끝을 검색 합니다.

특정 조건을 충족 하는 레코드 뿐만 아니라 검색의 모든 레코드를 포함 하려는 경우 이동 작업 중 하나를 사용 하 여 레코드에서 레코드로 이동 합니다. 테이블 형식 레코드 집합에서 레코드를 찾으려면 `Seek` 멤버 함수를 호출 합니다.

기준과 일치 하는 레코드를 찾지 못하면 현재 레코드 포인터가 결정 되지 않고 `FindNext` 0을 반환 합니다. 레코드 집합에 조건을 충족 하는 레코드가 두 개 이상 포함 되어 있으면이 `FindFirst` 고, 첫 번째 항목을 찾고, `FindNext` 다음 항목을 찾습니다.

> [!CAUTION]
> 현재 레코드를 편집 하는 경우 `Update` 다른 레코드로 이동 하기 전에 멤버 함수를 호출 하 여 변경 내용을 저장 해야 합니다. 업데이트 하지 않고 다른 레코드로 이동 하면 변경 내용이 경고 없이 손실 됩니다.

그러나 찾기 작업 중 하나를 사용 하는 것은 또는를 호출 하는 것과 동일 하지 않습니다 `MoveFirst` `MoveNext` . 그러나 단순히 조건을 지정 하지 않고 첫 번째 또는 다음 레코드를 최신으로 만듭니다. 이동 작업을 사용 하 여 찾기 작업을 수행할 수 있습니다.

찾기 작업을 사용할 때는 다음 사항에 유의 하세요.

- `Find`가 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않습니다. 이 경우 현재 레코드 포인터를 올바른 레코드로 다시 배치 해야 합니다.

- 앞 으로만 이동 가능한 스냅숏 형식의 레코드 집합에는 찾기 작업을 사용할 수 없습니다.

- 미국 버전의 Microsoft Jet 데이터베이스 엔진을 사용 하지 않는 경우에도 날짜를 포함 하는 필드를 검색 하는 경우 미국 날짜 형식 (월-일-연도)을 사용 해야 합니다. 그렇지 않으면 일치 하는 레코드를 찾을 수 없습니다.

- ODBC 데이터베이스 및 다량의 다이너셋을 사용할 때 특히 긴 레코드 집합으로 작업 하는 경우 찾기 작업을 사용 하는 속도가 느려지는 것을 알 수 있습니다. 사용자 지정 된 **ORDERBY** 또는 **WHERE** 절, 매개 변수 쿼리 또는 `CDaoQuerydef` 특정 인덱싱된 레코드를 검색 하는 개체를 사용 하 여 SQL 쿼리를 사용 하 여 성능을 향상 시킬 수 있습니다.

관련 정보는 DAO 도움말의 "FindFirst, FindLast, FindNext, Findlast 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetfindprev"></a><a name="findprev"></a> CDaoRecordset:: FindPrev

지정 된 조건과 일치 하는 이전 레코드를 찾으려면이 멤버 함수를 호출 합니다.

```cpp
BOOL FindPrev(LPCTSTR lpszFilter);
```

### <a name="parameters"></a>매개 변수

*lpszFilter*<br/>
레코드를 찾는 데 사용 되는 **where** 라는 단어가 없는 SQL 문의 **where** 절과 같은 문자열 식입니다.

### <a name="return-value"></a>반환 값

일치 하는 레코드가 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`FindPrev`멤버 함수는 현재 레코드에서 검색을 시작 하 고 레코드 집합의 시작 부분을 뒤로 검색 합니다.

특정 조건을 충족 하는 레코드 뿐만 아니라 검색의 모든 레코드를 포함 하려는 경우 이동 작업 중 하나를 사용 하 여 레코드에서 레코드로 이동 합니다. 테이블 형식 레코드 집합에서 레코드를 찾으려면 `Seek` 멤버 함수를 호출 합니다.

기준과 일치 하는 레코드를 찾지 못하면 현재 레코드 포인터가 결정 되지 않고 `FindPrev` 0을 반환 합니다. 레코드 집합에 조건을 충족 하는 레코드가 두 개 이상 포함 되어 있으면이 `FindFirst` 고, 첫 번째 항목을 찾고, `FindNext` 다음 항목을 찾습니다.

> [!CAUTION]
> 현재 레코드를 편집 하는 경우 `Update` 다른 레코드로 이동 하기 전에 멤버 함수를 호출 하 여 변경 내용을 저장 해야 합니다. 업데이트 하지 않고 다른 레코드로 이동 하면 변경 내용이 경고 없이 손실 됩니다.

그러나 찾기 작업 중 하나를 사용 하는 것은 또는를 호출 하는 것과 동일 하지 않습니다 `MoveFirst` `MoveNext` . 그러나 단순히 조건을 지정 하지 않고 첫 번째 또는 다음 레코드를 최신으로 만듭니다. 이동 작업을 사용 하 여 찾기 작업을 수행할 수 있습니다.

찾기 작업을 사용할 때는 다음 사항에 유의 하세요.

- `Find`가 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않습니다. 이 경우 현재 레코드 포인터를 올바른 레코드로 다시 배치 해야 합니다.

- 앞 으로만 이동 가능한 스냅숏 형식의 레코드 집합에는 찾기 작업을 사용할 수 없습니다.

- 미국 버전의 Microsoft Jet 데이터베이스 엔진을 사용 하지 않는 경우에도 날짜를 포함 하는 필드를 검색 하는 경우 미국 날짜 형식 (월-일-연도)을 사용 해야 합니다. 그렇지 않으면 일치 하는 레코드를 찾을 수 없습니다.

- ODBC 데이터베이스 및 다량의 다이너셋을 사용할 때 특히 긴 레코드 집합으로 작업 하는 경우 찾기 작업을 사용 하는 속도가 느려지는 것을 알 수 있습니다. 사용자 지정 된 **ORDERBY** 또는 **WHERE** 절, 매개 변수 쿼리 또는 `CDaoQuerydef` 특정 인덱싱된 레코드를 검색 하는 개체를 사용 하 여 SQL 쿼리를 사용 하 여 성능을 향상 시킬 수 있습니다.

관련 정보는 DAO 도움말의 "FindFirst, FindLast, FindNext, Findlast 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetabsoluteposition"></a><a name="getabsoluteposition"></a> CDaoRecordset:: GetAbsolutePosition

레코드 집합 개체의 현재 레코드에 대 한 레코드 번호를 반환 합니다.

```cpp
long GetAbsolutePosition();
```

### <a name="return-value"></a>반환 값

0부터 레코드 집합의 레코드 수 까지의 정수입니다. 레코드 집합에서 현재 레코드의 서 수 위치에 해당 합니다.

### <a name="remarks"></a>설명

기본 DAO 개체의 AbsolutePosition 속성 값은 0부터 시작 합니다. 0의 설정은 레코드 집합의 첫 번째 레코드를 참조 합니다. [Getrecordcount](#getrecordcount)를 호출 하 여 레코드 집합에서 채워진 레코드 수를 확인할 수 있습니다. `GetRecordCount`모든 레코드에 액세스 하 여 개수를 결정 해야 하므로를 호출 하는 데 시간이 걸릴 수 있습니다.

레코드 집합에 레코드가 없는 경우와 같이 현재 레코드가 없는 경우-1이 반환 됩니다. 현재 레코드를 삭제 하면 AbsolutePosition 속성 값이 정의 되지 않고 MFC가 참조 되는 경우 예외를 throw 합니다. 다이너셋 형식 레코드 집합의 경우 시퀀스의 끝에 새 레코드가 추가 됩니다.

> [!NOTE]
> 이 속성은 서로게이트 레코드 번호로 사용 하기 위한 것이 아닙니다. 책갈피는 지정 된 위치를 유지 하 고 반환 하는 데 권장 되는 방법 이지만 모든 형식의 레코드 집합 개체에 대해 현재 레코드를 배치 하는 유일한 방법입니다. 특히, 앞의 레코드가 삭제 될 때 지정 된 레코드의 위치가 변경 됩니다. 또한 레코드 집합에 있는 개별 레코드의 순서는 **ORDERBY** 절을 사용 하 여 SQL 문을 사용 하 여 생성 된 경우를 제외 하 고는 다시 생성 될 경우 지정 된 레코드는 동일한 절대 위치를 갖게 됩니다.

> [!NOTE]
> 이 멤버 함수는 다이너셋 형식 및 스냅숏 형식 레코드 집합에 대해서만 유효 합니다.

관련 내용은 DAO 도움말의 "AbsolutePosition 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetbookmark"></a><a name="getbookmark"></a> CDaoRecordset:: GetBookmark

특정 레코드에서 책갈피 값을 가져오려면이 멤버 함수를 호출 합니다.

```cpp
COleVariant GetBookmark();
```

### <a name="return-value"></a>반환 값

현재 레코드의 책갈피를 나타내는 값을 반환 합니다.

### <a name="remarks"></a>설명

레코드 집합 개체를 만들거나 열 때 각 레코드는 해당 레코드를 지 원하는 경우 이미 고유한 책갈피를 가집니다. `CanBookmark`을 호출 하 여 레코드 집합에서 책갈피를 지원 하는지 여부를 확인 합니다.

책갈피 값을 개체에 할당 하 여 현재 레코드에 대 한 책갈피를 저장할 수 있습니다 `COleVariant` . 다른 레코드로 이동한 후 언제 든 지 해당 레코드로 신속 하 게 돌아가려면 `SetBookmark` 해당 개체의 값에 해당 하는 매개 변수를 사용 하 여를 호출 `COleVariant` 합니다.

> [!NOTE]
> [Requery](#requery) 를 호출 하면 DAO 책갈피가 변경 됩니다.

관련 내용은 DAO 도움말의 "책갈피 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetcachesize"></a><a name="getcachesize"></a> CDaoRecordset:: GetCacheSize

이 멤버 함수를 호출 하 여 캐시 된 레코드 수를 가져옵니다.

```cpp
long GetCacheSize();
```

### <a name="return-value"></a>반환 값

ODBC 데이터 원본에서 로컬로 캐시할 데이터를 포함 하는 다이너셋 형식 레코드 집합의 레코드 수를 지정 하는 값입니다.

### <a name="remarks"></a>설명

데이터 캐싱은 다이너셋 형식의 레코드 집합 개체를 통해 원격 서버에서 데이터를 검색 하는 응용 프로그램의 성능을 향상 시킵니다. 캐시는 응용 프로그램이 실행 되는 동안 데이터를 다시 요청 하는 경우 서버에서 가장 최근에 검색 된 데이터를 보관 하는 로컬 메모리의 공간입니다. 데이터가 요청 될 때 Microsoft Jet 데이터베이스 엔진은 서버에서 검색 하는 대신 요청 된 데이터에 대 한 캐시를 먼저 확인 하 여 더 많은 시간을 사용 합니다. ODBC 데이터 원본에서 가져오지 않은 데이터는 캐시에 저장 되지 않습니다.

모든 ODBC 데이터 원본 (예: 연결 된 테이블)에는 로컬 캐시를 사용할 수 있습니다.

관련 내용은 DAO 도움말의 "CacheSize, CacheStart 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetcachestart"></a><a name="getcachestart"></a> CDaoRecordset:: GetCacheStart

이 멤버 함수를 호출 하 여 캐시 될 레코드 집합에 있는 첫 번째 레코드의 책갈피 값을 가져옵니다.

```cpp
COleVariant GetCacheStart();
```

### <a name="return-value"></a>반환 값

`COleVariant`캐시 될 레코드 집합에 있는 첫 번째 레코드의 책갈피를 지정 하는입니다.

### <a name="remarks"></a>설명

Microsoft Jet 데이터베이스 엔진은 캐시 범위 내에서 레코드를 요청 하 고 서버에서 캐시 범위를 벗어난 레코드를 요청 합니다.

> [!NOTE]
> 캐시에서 검색 된 레코드는 다른 사용자가 원본 데이터에 대해 동시에 변경한 내용을 반영 하지 않습니다.

관련 내용은 DAO 도움말의 "CacheSize, CacheStart 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetcurrentindex"></a><a name="getcurrentindex"></a> CDaoRecordset:: GetCurrentIndex

인덱싱된 테이블 형식 개체에서 현재 사용 중인 인덱스를 확인 하려면이 멤버 함수를 호출 `CDaoRecordset` 합니다.

```cpp
CString GetCurrentIndex();
```

### <a name="return-value"></a>반환 값

`CString`테이블 형식 레코드 집합에서 현재 사용 중인 인덱스의 이름을 포함 하는입니다. 인덱스를 설정 하지 않은 경우 빈 문자열을 반환 합니다.

### <a name="remarks"></a>설명

이 인덱스는 테이블 형식 레코드 집합의 레코드를 정렬 하는 데 사용 되며 [Seek](#seek) 멤버 함수에서 레코드를 찾는 데 사용 됩니다.

개체는 인덱스를 두 개 이상 `CDaoRecordset` 포함할 수 있지만 한 번에 하나의 인덱스만 사용할 수 있습니다 ( [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 개체에 정의 된 인덱스가 여러 개 있을 수 있음).

관련 정보는 DAO 도움말의 "인덱스 개체" 및 정의 "현재 인덱스" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetdatecreated"></a><a name="getdatecreated"></a> CDaoRecordset:: GetDateCreated

이 멤버 함수를 호출 하 여 기본 테이블이 생성 된 날짜 및 시간을 검색 합니다.

```cpp
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>반환 값

기본 테이블을 만든 날짜와 시간을 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다.

### <a name="remarks"></a>설명

날짜 및 시간 설정은 기본 테이블이 생성 된 컴퓨터에서 파생 됩니다.

관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetdatelastupdated"></a><a name="getdatelastupdated"></a> CDaoRecordset:: GetDateLastUpdated

이 멤버 함수를 호출 하 여 스키마가 마지막으로 업데이트 된 날짜 및 시간을 검색 합니다.

```cpp
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>반환 값

기본 테이블 구조 (스키마)가 마지막으로 업데이트 된 날짜와 시간을 포함 하는 [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) 개체입니다.

### <a name="remarks"></a>설명

날짜 및 시간 설정은 기본 테이블 구조 (스키마)가 마지막으로 업데이트 된 컴퓨터에서 파생 됩니다.

관련 내용은 DAO 도움말에서 "DateCreated, LastUpdated 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetdefaultdbname"></a><a name="getdefaultdbname"></a> CDaoRecordset:: GetDefaultDBName

이 멤버 함수를 호출 하 여이 레코드 집합에 대 한 데이터베이스의 이름을 확인 합니다.

```cpp
virtual CString GetDefaultDBName();
```

### <a name="return-value"></a>반환 값

`CString`이 레코드 집합이 파생 된 데이터베이스의 경로와 이름을 포함 하는입니다.

### <a name="remarks"></a>설명

[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)에 대 한 포인터 없이 레코드 집합을 만드는 경우이 경로는 레코드 집합에서 기본 데이터베이스를 여는 데 사용 됩니다. 기본적으로이 함수는 빈 문자열을 반환 합니다. 클래스 마법사에서에서 새 레코드 집합을 파생 `CDaoRecordset` 시킬 때이 함수를 만듭니다.

다음 예제에서는 문자열의 이중 백슬래시 ()를 사용 하는 방법을 보여 줍니다 \\ \\ .이는 문자열을 올바르게 해석 하는 데 필요 합니다.

[!code-cpp[NVC_MFCDatabase#4](../../mfc/codesnippet/cpp/cdaorecordset-class_4.cpp)]

## <a name="cdaorecordsetgetdefaultsql"></a><a name="getdefaultsql"></a> CDaoRecordset:: GetDefaultSQL

프레임 워크는이 멤버 함수를 호출 하 여 레코드 집합의 기반이 되는 기본 SQL 문을 가져옵니다.

```cpp
virtual CString GetDefaultSQL();
```

### <a name="return-value"></a>반환 값

`CString`기본 SQL 문을 포함 하는입니다.

### <a name="remarks"></a>설명

테이블 이름 또는 SQL **SELECT** 문이 될 수 있습니다.

클래스 마법사를 사용 하 여 레코드 집합 클래스를 선언 하 여 기본 SQL 문을 간접적으로 정의 하 고 클래스 마법사에서이 작업을 수행 합니다.

[Open](#open)에 null sql 문자열을 전달 하는 경우이 함수를 호출 하 여 레코드 집합에 대 한 테이블 이름 또는 sql을 결정 합니다.

## <a name="cdaorecordsetgeteditmode"></a><a name="geteditmode"></a> CDaoRecordset:: GetEditMode

다음 값 중 하나인 편집 상태를 확인 하려면이 멤버 함수를 호출 합니다.

```cpp
short GetEditMode();
```

### <a name="return-value"></a>반환 값

현재 레코드에 대 한 편집 상태를 나타내는 값을 반환 합니다.

### <a name="remarks"></a>설명

|값|설명|
|-----------|-----------------|
|`dbEditNone`|편집 작업이 진행 되 고 있지 않습니다.|
|`dbEditInProgress`|`Edit`가 호출된 경우|
|`dbEditAdd`|`AddNew`가 호출된 경우|

관련 내용은 DAO 도움말의 "EditMode 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetfieldcount"></a><a name="getfieldcount"></a> CDaoRecordset:: GetFieldCount

이 멤버 함수를 호출 하 여 레코드 집합에 정의 된 필드 (열) 수를 검색 합니다.

```cpp
short GetFieldCount();
```

### <a name="return-value"></a>반환 값

레코드 집합의 필드 수입니다.

### <a name="remarks"></a>설명

관련 정보는 DAO 도움말의 "Count 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetfieldinfo"></a><a name="getfieldinfo"></a> CDaoRecordset:: GetFieldInfo

이 멤버 함수를 호출 하 여 레코드 집합의 필드에 대 한 정보를 가져옵니다.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 레코드 집합의 Fields 컬렉션에 있는 미리 정의 된 필드의 인덱스 (0부터 시작)입니다.

*fieldinfo*<br/>
[CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 구조체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 레코드 집합에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 항목과 함께 여기에 나열 됩니다. 최상의 성능을 위해 필요한 정보 수준만 검색 합니다.

- `AFX_DAO_PRIMARY_INFO` 기본 이름, 형식, 크기, 특성

- `AFX_DAO_SECONDARY_INFO` 기본 정보, 더하기: 서 수 위치, 필수, 0 길이 허용, 데이터 정렬 순서, 외래 이름, 원본 필드, 원본 테이블

- `AFX_DAO_ALL_INFO` 기본 및 보조 정보, 기본 값, 유효성 검사 규칙, 유효성 검사 텍스트

*lpszName*<br/>
필드의 이름입니다.

### <a name="remarks"></a>설명

한 버전의 함수를 사용 하 여 인덱스를 기준으로 필드를 조회할 수 있습니다. 다른 버전에서는 이름을 기준으로 필드를 조회할 수 있습니다.

반환 되는 정보에 대 한 설명은 [CDaoFieldInfo](../../mfc/reference/cdaofieldinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준에 대 한 정보도 얻을 수 있습니다.

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetfieldvalue"></a><a name="getfieldvalue"></a> CDaoRecordset:: GetFieldValue

이 멤버 함수를 호출 하 여 레코드 집합의 데이터를 검색 합니다.

```cpp
virtual void GetFieldValue(
    LPCTSTR lpszName,
    COleVariant& varValue);

virtual void GetFieldValue(
    int nIndex,
    COleVariant& varValue);

virtual COleVariant GetFieldValue(LPCTSTR lpszName);
virtual COleVariant GetFieldValue(int nIndex);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
필드 이름을 포함 하는 문자열에 대 한 포인터입니다.

*varValue*<br/>
`COleVariant`필드의 값을 저장 하는 개체에 대 한 참조입니다.

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 레코드 집합의 Fields 컬렉션에 있는 필드의 인덱스 (0부터 시작)입니다.

### <a name="return-value"></a>반환 값

`GetFieldValue`값을 반환 하는의 두 버전은 필드의 값을 포함 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 개체를 반환 합니다.

### <a name="remarks"></a>설명

이름 또는 서 수 위치를 기준으로 필드를 조회할 수 있습니다.

> [!NOTE]
> 개체를 `COleVariant` 반환 하는 버전을 호출 하는 것이 아니라 개체 참조를 매개 변수로 사용 하는이 멤버 함수의 버전 중 하나를 호출 하는 것이 더 효율적입니다 `COleVariant` . 이 함수의 두 번째 버전은 이전 버전과의 호환성을 위해 유지 됩니다.

`GetFieldValue`및 [SetFieldValue](#setfieldvalue) 를 사용 하 여 [DoFieldExchange](#dofieldexchange) 메커니즘을 사용 하 여 열을 정적으로 바인딩하지 않고 런타임에 필드를 동적으로 바인딩합니다.

`GetFieldValue` 그리고 `DoFieldExchange` 메커니즘을 결합 하 여 성능을 향상 시킬 수 있습니다. 예를 들어를 사용 `GetFieldValue` 하 여 요청 시에만 필요한 값을 검색 하 고 해당 호출을 인터페이스의 "추가 정보" 단추에 할당 합니다.

관련 내용은 DAO 도움말의 "Field Object" 및 "Value Property" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetindexcount"></a><a name="getindexcount"></a> CDaoRecordset:: GetIndexCount

이 멤버 함수를 호출 하 여 테이블 형식 레코드 집합에서 사용할 수 있는 인덱스 수를 확인 합니다.

```cpp
short GetIndexCount();
```

### <a name="return-value"></a>반환 값

테이블 형식 레코드 집합의 인덱스 수입니다.

### <a name="remarks"></a>설명

`GetIndexCount` 는 레코드 집합의 모든 인덱스를 반복 하는 데 유용 합니다. 이러한 목적을 위해 `GetIndexCount` [Getindexinfo](#getindexinfo)와 함께를 사용 합니다. 다이너셋 형식 또는 스냅숏 형식 레코드 집합에서이 멤버 함수를 호출 하는 경우 MFC는 예외를 throw 합니다.

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetindexinfo"></a><a name="getindexinfo"></a> CDaoRecordset:: GetIndexInfo

이 멤버 함수를 호출 하 여 레코드 집합의 기본 테이블에 정의 된 인덱스에 대 한 다양 한 종류의 정보를 얻을 수 있습니다.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
숫자 위치로 조회 하기 위해 테이블의 인덱스 컬렉션에 있는 인덱스 (0부터 시작)입니다.

*indexinfo*<br/>
[CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 구조체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 인덱스에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 항목과 함께 여기에 나열 됩니다. 최상의 성능을 위해 필요한 정보 수준만 검색 합니다.

- `AFX_DAO_PRIMARY_INFO` 기본 이름, 필드 정보, 필드

- `AFX_DAO_SECONDARY_INFO` 기본 정보 및 기본, 고유, 클러스터형, IgnoreNulls, 필수, 외래

- `AFX_DAO_ALL_INFO` 기본 및 보조 정보, 및: 고유 카운트

*lpszName*<br/>
이름으로 조회할 인덱스 개체의 이름에 대 한 포인터입니다.

### <a name="remarks"></a>설명

한 버전의 함수를 사용 하 여 컬렉션에서 인덱스를 찾을 수 있습니다. 다른 버전에서는 이름을 기준으로 인덱스를 조회할 수 있습니다.

반환 되는 정보에 대 한 설명은 [CDaoIndexInfo](../../mfc/reference/cdaoindexinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준에 대 한 정보도 얻을 수 있습니다.

관련 내용은 DAO 도움말의 "Attributes 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetlastmodifiedbookmark"></a><a name="getlastmodifiedbookmark"></a> CDaoRecordset:: GetLastModifiedBookmark

가장 최근에 추가 되었거나 업데이트 된 레코드의 책갈피를 검색 하려면이 멤버 함수를 호출 합니다.

```cpp
COleVariant GetLastModifiedBookmark();
```

### <a name="return-value"></a>반환 값

`COleVariant`가장 최근에 추가 되거나 변경 된 레코드를 나타내는 책갈피를 포함 하는입니다.

### <a name="remarks"></a>설명

레코드 집합 개체를 만들거나 열 때 각 레코드는 해당 레코드를 지 원하는 경우 이미 고유한 책갈피를 가집니다. [Getbookmark](#getbookmark) 를 호출 하 여 레코드 집합에서 책갈피를 지원 하는지 확인 합니다. 레코드 집합에서 책갈피를 지원 하지 않으면 `CDaoException` 이 throw 됩니다.

레코드를 추가 하면 레코드 집합의 끝에 표시 되며 현재 레코드가 아닙니다. 새 레코드를 최신 레코드로 설정 하려면를 호출 하 `GetLastModifiedBookmark` 고 `SetBookmark` 를 호출 하 여 새로 추가 된 레코드로 돌아갑니다.

관련 내용은 DAO 도움말의 "LastModified 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetlockingmode"></a><a name="getlockingmode"></a> CDaoRecordset:: GetLockingMode

이 멤버 함수를 호출 하 여 레코드 집합에 적용 되는 잠금 유형을 확인 합니다.

```cpp
BOOL GetLockingMode();
```

### <a name="return-value"></a>반환 값

잠금 유형이 비관적 이면 0이 아닌 값이 고, 낙관적 레코드 잠금의 경우 0입니다.

### <a name="remarks"></a>설명

비관적 잠금이 적용 되는 경우 편집 하는 레코드를 포함 하는 데이터 페이지는 [편집](#edit) 멤버 함수를 호출 하는 즉시 잠깁니다. [Update](#update) 또는 [Close](#close) 멤버 함수를 호출 하거나 이동 또는 찾기 작업 중 하나를 호출 하면 페이지 잠금이 해제 됩니다.

낙관적 잠금이 적용 되는 경우 레코드를 포함 하는 데이터 페이지는 멤버가 구성원 함수를 사용 하 여 업데이트 되는 동안에만 잠깁니다 `Update` .

ODBC 데이터 원본으로 작업할 때 잠금 모드는 항상 낙관적입니다.

관련 내용은 DAO 도움말의 "LockEdits 속성" 및 "다중 사용자 응용 프로그램의 잠금 동작" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetname"></a><a name="getname"></a> CDaoRecordset:: GetName

이 멤버 함수를 호출 하 여 레코드 집합의 이름을 검색 합니다.

```cpp
CString GetName();
```

### <a name="return-value"></a>반환 값

`CString`레코드 집합의 이름을 포함 하는입니다.

### <a name="remarks"></a>설명

레코드 집합의 이름은 문자로 시작 해야 하며 최대 40 자를 포함할 수 있습니다. 숫자 및 밑줄 문자를 포함할 수 있지만 문장 부호 또는 공백을 포함할 수 없습니다.

관련 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetparamvalue"></a><a name="getparamvalue"></a> CDaoRecordset:: GetParamValue

이 멤버 함수를 호출 하 여 기본 DAOParameter 개체에 저장 된 지정 된 매개 변수의 현재 값을 검색 합니다.

```cpp
virtual COleVariant GetParamValue(int nIndex);
virtual COleVariant GetParamValue(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
기본 DAOParameter 개체에 있는 매개 변수의 숫자 위치입니다.

*lpszName*<br/>
원하는 값을 가진 매개 변수의 이름입니다.

### <a name="return-value"></a>반환 값

매개 변수의 값을 포함 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 클래스의 개체입니다.

### <a name="remarks"></a>설명

이름 또는 컬렉션의 숫자 위치를 사용 하 여 매개 변수에 액세스할 수 있습니다.

관련 정보는 DAO 도움말의 "매개 변수 개체" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetpercentposition"></a><a name="getpercentposition"></a> CDaoRecordset:: GetPercentPosition

다이너셋 형식 또는 스냅숏 형식 레코드 집합으로 작업 하는 경우 레코드 집합을 완전히 채우기 전에를 호출 하는 경우 `GetPercentPosition` 이동 양은 [getrecordcount](#getrecordcount)를 호출 하 여 표시 된 것 처럼 액세스 한 레코드 수를 기준으로 합니다.

```cpp
float GetPercentPosition();
```

### <a name="return-value"></a>반환 값

레코드 집합의 레코드에 대 한 백분율을 기준으로 레코드 집합 개체에서 현재 레코드의 대략적인 위치를 나타내는 0에서 100 사이의 숫자입니다.

### <a name="remarks"></a>설명

[MoveLast](#movelast) 를 호출 하 여 마지막 레코드로 이동 하 여 모든 레코드 집합의 채우기를 완료할 수 있지만이 경우에는 상당한 시간이 걸릴 수 있습니다.

`GetPercentPosition`인덱스가 없는 테이블을 포함 하 여 세 가지 유형의 레코드 집합 개체에 대해를 호출할 수 있습니다. 그러나 `GetPercentPosition` 전달 전용 스크롤 스냅숏이 나 외부 데이터베이스에 대 한 통과 쿼리에서 열린 레코드 집합에 대해를 호출할 수 없습니다. 현재 레코드가 없거나 현재 레코드가 삭제 된 경우 `CDaoException` 이 throw 됩니다.

관련 내용은 DAO 도움말의 "PercentPosition 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetrecordcount"></a><a name="getrecordcount"></a> CDaoRecordset:: GetRecordCount

이 멤버 함수를 호출 하 여 액세스 한 레코드 집합의 레코드 수를 확인 합니다.

```cpp
long GetRecordCount();
```

### <a name="return-value"></a>반환 값

레코드 집합 개체에서 액세스 한 레코드 수를 반환 합니다.

### <a name="remarks"></a>설명

`GetRecordCount` 모든 레코드에 액세스할 때까지 다이너셋 형식 또는 스냅숏 형식 레코드 집합에 포함 된 레코드 수를 나타내지 않습니다. 이 멤버 함수 호출은 완료 하는 데 상당한 시간이 걸릴 수 있습니다.

마지막 레코드에 액세스 한 후에는 반환 값이 레코드 집합에서 삭제 취소 된 레코드의 총 수를 나타냅니다. 마지막 레코드를 강제로 액세스 하려면 `MoveLast` `FindLast` 레코드 집합에 대 한 또는 멤버 함수를 호출 합니다. SQL 카운트를 사용 하 여 쿼리에서 반환할 대략적인 레코드 수를 결정할 수도 있습니다.

응용 프로그램이 다이너셋 형식의 레코드 집합에서 레코드를 삭제 하면의 반환 값이 `GetRecordCount` 감소 합니다. 그러나 다른 사용자가 삭제 한 레코드는 `GetRecordCount` 현재 레코드가 삭제 된 레코드에 배치 될 때까지 반영 되지 않습니다. 레코드 수에 영향을 주는 트랜잭션을 실행 한 후 트랜잭션을 롤백하는 경우 `GetRecordCount` 는 남은 레코드의 실제 수를 반영 하지 않습니다.

`GetRecordCount`스냅숏 형식 레코드 집합에서의 값은 기본 테이블의 변경 내용에 의해 영향을 받지 않습니다.

테이블 `GetRecordCount` 형식 레코드 집합에서의 값은 테이블에 있는 대략적인 레코드 수를 반영 하며 테이블 레코드를 추가 및 삭제 하는 즉시 영향을 받습니다.

레코드가 없는 레코드 집합은 값 0을 반환 합니다. 연결 된 테이블 또는 ODBC 데이터베이스로 작업할 때는 `GetRecordCount` 항상-1을 반환 합니다. `Requery`레코드 집합에서 멤버 함수를 호출 하면 `GetRecordCount` 쿼리를 다시 실행 한 것 처럼의 값이 다시 설정 됩니다.

관련 정보는 DAO 도움말의 "RecordCount 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetsql"></a><a name="getsql"></a> CDaoRecordset:: GetSQL

이 멤버 함수를 호출 하 여 레코드를 열 때 레코드 집합의 레코드를 선택 하는 데 사용 된 SQL 문을 가져옵니다.

```cpp
CString GetSQL() const;
```

### <a name="return-value"></a>반환 값

`CString`SQL 문을 포함 하는입니다.

### <a name="remarks"></a>설명

이는 일반적으로 SQL **SELECT** 문입니다.

에서 반환 되는 문자열은 `GetSQL` 일반적으로 *lpszSQL* 매개 변수에서 레코드 집합에 전달 했을 때 [Open](#open) 멤버 함수에 전달 했을 수 있는 문자열과 다릅니다. 이는 레코드 집합이 전달 된 항목을 기반으로 전체 SQL 문을 생성 하는 것입니다. 여기서는 `Open` 클래스 마법사를 사용 하 여 지정한 내용, [m_strFilter](#m_strfilter) 및 [m_strSort](#m_strsort) 데이터 멤버에서 지정 했을 수 있습니다.

> [!NOTE]
> 를 호출한 후에만이 멤버 함수 `Open` 를 호출 합니다.

관련 내용은 DAO 도움말의 "SQL 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgettype"></a><a name="gettype"></a> CDaoRecordset:: GetType

레코드 집합 개체의 형식을 확인 하기 위해 레코드 집합을 연 후이 멤버 함수를 호출 합니다.

```cpp
short GetType();
```

### <a name="return-value"></a>반환 값

레코드 집합의 유형을 나타내는 다음 값 중 하나입니다.

- `dbOpenTable` 테이블 형식 레코드 집합

- `dbOpenDynaset` 다이너셋 형식 레코드 집합

- `dbOpenSnapshot` 스냅숏 형식 레코드 집합

### <a name="remarks"></a>설명

관련 내용은 DAO 도움말의 "형식 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetvalidationrule"></a><a name="getvalidationrule"></a> CDaoRecordset:: GetValidationRule

이 멤버 함수를 호출 하 여 데이터 유효성 검사에 사용 되는 규칙을 결정 합니다.

```cpp
CString GetValidationRule();
```

### <a name="return-value"></a>반환 값

`CString`테이블에 변경 되거나 추가 될 때 레코드의 데이터에 대 한 유효성을 검사 하는 값을 포함 하는 개체입니다.

### <a name="remarks"></a>설명

이 규칙은 텍스트 기반 이며 기본 테이블이 변경 될 때마다 적용 됩니다. 데이터가 유효 하지 않은 경우 MFC는 예외를 throw 합니다. 반환 된 오류 메시지는 기본 필드 개체의 ValidationText 속성 (지정 된 경우) 또는 기본 필드 개체의 ValidationRule 속성으로 지정 된 식의 텍스트입니다. [GetValidationText](#getvalidationtext) 를 호출 하 여 오류 메시지의 텍스트를 가져올 수 있습니다.

예를 들어 일이 필요한 레코드의 필드에는 "DAY BETWEEN 1에서 31"과 같은 유효성 검사 규칙이 있을 수 있습니다.

관련 내용은 DAO 도움말의 "ValidationRule 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetgetvalidationtext"></a><a name="getvalidationtext"></a> CDaoRecordset:: GetValidationText

기본 필드 개체의 ValidationText 속성 텍스트를 검색 하려면이 멤버 함수를 호출 합니다.

```cpp
CString GetValidationText();
```

### <a name="return-value"></a>반환 값

`CString`필드 값이 내부 필드 개체의 유효성 검사 규칙을 충족 하지 않는 경우 표시 되는 메시지의 텍스트를 포함 하는 개체입니다.

### <a name="remarks"></a>설명

관련 내용은 DAO 도움말의 "ValidationText 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetisbof"></a><a name="isbof"></a> CDaoRecordset:: IsBOF

레코드에서 레코드로 이동 하기 전에이 멤버 함수를 호출 하 여 레코드 집합의 첫 번째 레코드 앞에 있는지 알아보세요.

```cpp
BOOL IsBOF() const;
```

### <a name="return-value"></a>반환 값

레코드 집합이 레코드를 포함 하지 않거나 첫 번째 레코드 앞으로 스크롤한 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

와 함께를 호출 `IsBOF` 하 여 레코드 `IsEOF` 집합에 레코드가 포함 되어 있는지 아니면 비어 있는지 확인할 수도 있습니다. 를 호출한 후 즉시 `Open` 레코드 집합에 레코드가 없는 경우는 `IsBOF` 0이 아닌 값을 반환 합니다. 하나 이상의 레코드를 포함 하는 레코드 집합을 열 때 첫 번째 레코드는 현재 레코드이 고 `IsBOF` 0을 반환 합니다.

첫 번째 레코드가 현재 레코드이 고를 호출 하는 경우는 `MovePrev` `IsBOF` 0이 아닌 값을 반환 합니다. `IsBOF`가 0이 아닌 값을 반환 하 고를 호출 하면 `MovePrev` 예외가 throw 됩니다. 가 `IsBOF` 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않으며 현재 레코드를 필요로 하는 모든 작업에서 예외가 발생 합니다.

및 설정에 대 한 특정 메서드의 효과 `IsBOF` `IsEOF` :

- 를 `Open*` 내부적으로 호출 하면을 호출 하 여 레코드 집합의 첫 번째 레코드를 현재 레코드로 만듭니다 `MoveFirst` . 따라서 `Open` 빈 레코드 집합에 대해를 호출 하면 `IsBOF` 및에서 `IsEOF` 0이 아닌 값이 반환 됩니다. 실패 하거나 호출 하는 동작은 다음 표를 참조 `MoveFirst` `MoveLast` 하세요.

- 레코드를 성공적으로 찾은 모든 이동 작업은 `IsBOF` 및 `IsEOF` 를 모두 0으로 반환 합니다.

- 호출 `AddNew` 후에 `Update` 새 레코드를 삽입 하는 호출이 발생 하면 `IsBOF` 가 0을 반환 하지만가 이미 0이 아닌 경우에만이 반환 됩니다 `IsEOF` . 상태는 `IsEOF` 항상 변경 되지 않은 상태로 유지 됩니다. Microsoft Jet 데이터베이스 엔진에서 정의한 대로 빈 레코드 집합의 현재 레코드 포인터는 파일의 끝에 있으므로 현재 레코드 뒤에 새 레코드가 삽입 됩니다.

- 모든 `Delete` 호출은 레코드 집합에서 남은 레코드만 제거 하더라도 또는의 값은 변경 하지 않습니다 `IsBOF` `IsEOF` .

다음 표에서는 다양 한 조합을 사용 하 여 허용 되는 이동 작업을 보여 줍니다 `IsBOF` /  `IsEOF` .

|시스템 상태|MoveFirst, MoveLast|MovePrev<br /><br /> Move < 0|0 이동|MoveNext<br /><br /> Move > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 0이 아닌 경우<br /><br /> `IsEOF`=0|허용|예외|예외|허용|
|`IsBOF`=0,<br /><br /> `IsEOF`= 0이 아닌 값|허용됨|허용됨|예외|예외|
|둘 다 0이 아닙니다.|예외|예외|예외|예외|
|0 모두|허용됨|허용됨|허용됨|허용됨|

이동 작업을 허용 하는 것은 작업에서 레코드를 성공적으로 찾으려고 한다는 의미는 아닙니다. 단지 지정 된 이동 작업을 수행 하려는 시도가 허용 되 고 예외를 생성 하지 않음을 나타냅니다. `IsBOF`및 멤버 함수 값은 `IsEOF` 시도한 이동의 결과로 변경 될 수 있습니다.

및 설정 값에서 레코드를 찾을 수 없는 이동 작업의 효과는 `IsBOF` `IsEOF` 다음 표에 나와 있습니다.

|작업|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|0이 아닌|0이 아닌|
|`Move` 0|변경 내용 없음|변경 내용 없음|
|`MovePrev`, `Move` < 0|0이 아닌|변경 내용 없음|
|`MoveNext`, `Move` > 0|변경 내용 없음|0이 아닌|

관련 내용은 DAO 도움말의 "BOF, EOF 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetisdeleted"></a><a name="isdeleted"></a> CDaoRecordset:: IsDeleted

현재 레코드가 삭제 되었는지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```cpp
BOOL IsDeleted() const;
```

### <a name="return-value"></a>반환 값

레코드 집합을 삭제 된 레코드에 배치 하는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

레코드로 스크롤하고 `IsDeleted` TRUE (0이 아닌 값)를 반환 하는 경우 다른 레코드 집합 작업을 수행 하기 전에 다른 레코드로 스크롤해야 합니다.

> [!NOTE]
> 스냅숏 또는 테이블 형식 레코드 집합에서 레코드에 대 한 삭제 된 상태를 확인할 필요가 없습니다. 레코드는 스냅숏에서 삭제할 수 없으므로를 호출할 필요가 없습니다 `IsDeleted` . 테이블 형식 레코드 집합의 경우 삭제 된 레코드는 실제로 레코드 집합에서 제거 됩니다. 사용자, 다른 사용자 또는 다른 레코드 집합에서 레코드를 삭제 한 후에는 해당 레코드로 다시 스크롤할 수 없습니다. 따라서를 호출할 필요가 없습니다 `IsDeleted` .

다이너셋에서 레코드를 삭제 하면 해당 레코드는 레코드 집합에서 제거 되 고 해당 레코드로 다시 스크롤할 수 없습니다. 그러나 다이너셋의 레코드가 동일한 테이블을 기반으로 하는 다른 사용자 또는 다른 레코드 집합에서 삭제 되는 경우 나중에 `IsDeleted` 해당 레코드로 스크롤하면에서 TRUE를 반환 합니다.

관련 정보는 DAO 도움말의 "Delete 메서드", "LastModified 속성" 및 "EditMode 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetiseof"></a><a name="iseof"></a> CDaoRecordset:: IsEOF

레코드에서 레코드로 스크롤할 때이 멤버 함수를 호출 하 여 레코드 집합의 마지막 레코드를 벗어났는지 여부를 알아보세요.

```cpp
BOOL IsEOF() const;
```

### <a name="return-value"></a>반환 값

레코드 집합이 레코드를 포함 하지 않거나 마지막 레코드를 넘어 스크롤 된 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

을 호출 하 여 레코드 `IsEOF` 집합이 레코드를 포함 하거나 비어 있는지 확인할 수도 있습니다. 를 호출한 후 즉시 `Open` 레코드 집합에 레코드가 없는 경우는 `IsEOF` 0이 아닌 값을 반환 합니다. 하나 이상의 레코드를 포함 하는 레코드 집합을 열 때 첫 번째 레코드는 현재 레코드이 고 `IsEOF` 0을 반환 합니다.

를 호출할 때 마지막 레코드가 현재 레코드 이면는 `MoveNext` `IsEOF` 이후에 0이 아닌 값을 반환 합니다. `IsEOF`가 0이 아닌 값을 반환 하 고를 호출 하면 `MoveNext` 예외가 throw 됩니다. 가 `IsEOF` 0이 아닌 값을 반환 하는 경우 현재 레코드는 정의 되지 않으며 현재 레코드를 필요로 하는 모든 작업에서 예외가 발생 합니다.

및 설정에 대 한 특정 메서드의 효과 `IsBOF` `IsEOF` :

- 를 `Open` 내부적으로 호출 하면을 호출 하 여 레코드 집합의 첫 번째 레코드를 현재 레코드로 만듭니다 `MoveFirst` . 따라서 `Open` 빈 레코드 집합에 대해를 호출 하면 `IsBOF` 및에서 `IsEOF` 0이 아닌 값이 반환 됩니다. 실패 한 호출의 동작은 다음 표를 참조 `MoveFirst` 하세요.

- 레코드를 성공적으로 찾은 모든 이동 작업은 `IsBOF` 및 `IsEOF` 를 모두 0으로 반환 합니다.

- 호출 `AddNew` 후에 `Update` 새 레코드를 삽입 하는 호출이 발생 하면 `IsBOF` 가 0을 반환 하지만가 이미 0이 아닌 경우에만이 반환 됩니다 `IsEOF` . 상태는 `IsEOF` 항상 변경 되지 않은 상태로 유지 됩니다. Microsoft Jet 데이터베이스 엔진에서 정의한 대로 빈 레코드 집합의 현재 레코드 포인터는 파일의 끝에 있으므로 현재 레코드 뒤에 새 레코드가 삽입 됩니다.

- 모든 `Delete` 호출은 레코드 집합에서 남은 레코드만 제거 하더라도 또는의 값은 변경 하지 않습니다 `IsBOF` `IsEOF` .

다음 표에서는 다양 한 조합을 사용 하 여 허용 되는 이동 작업을 보여 줍니다 `IsBOF` /  `IsEOF` .

|시스템 상태|MoveFirst, MoveLast|MovePrev<br /><br /> Move < 0|0 이동|MoveNext<br /><br /> Move > 0|
|------|-------------------------|-----------------------------|------------|-----------------------------|
|`IsBOF`= 0이 아닌 경우<br /><br /> `IsEOF`=0|허용|예외|예외|허용|
|`IsBOF`=0,<br /><br /> `IsEOF`= 0이 아닌 값|허용됨|허용됨|예외|예외|
|둘 다 0이 아닙니다.|예외|예외|예외|예외|
|0 모두|허용됨|허용됨|허용됨|허용됨|

이동 작업을 허용 하는 것은 작업에서 레코드를 성공적으로 찾으려고 한다는 의미는 아닙니다. 단지 지정 된 이동 작업을 수행 하려는 시도가 허용 되 고 예외를 생성 하지 않음을 나타냅니다. `IsBOF`및 멤버 함수 값은 `IsEOF` 시도한 이동의 결과로 변경 될 수 있습니다.

및 설정 값에서 레코드를 찾을 수 없는 이동 작업의 효과는 `IsBOF` `IsEOF` 다음 표에 나와 있습니다.

|작업|IsBOF|IsEOF|
|------|-----------|-----------|
|`MoveFirst`, `MoveLast`|0이 아닌|0이 아닌|
|`Move` 0|변경 내용 없음|변경 내용 없음|
|`MovePrev`, `Move` < 0|0이 아닌|변경 내용 없음|
|`MoveNext`, `Move` > 0|변경 내용 없음|0이 아닌|

관련 내용은 DAO 도움말의 "BOF, EOF 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetisfielddirty"></a><a name="isfielddirty"></a> CDaoRecordset:: IsFieldDirty

이 멤버 함수를 호출 하 여 다이너셋의 지정 된 필드 데이터 멤버가 "더티" (변경 됨)로 플래그가 지정 되었는지 여부를 확인 합니다.

```cpp
BOOL IsFieldDirty(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
상태를 확인할 필드 데이터 멤버에 대 한 포인터 이거나, 필드가 커밋되지 않았는지 여부를 확인 하는 NULL입니다.

### <a name="return-value"></a>반환 값

지정 된 필드 데이터 멤버가 커밋되지 않은 것으로 플래그가 지정 되 면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

또는를 호출 하 여 현재 레코드가의 멤버 함수에 대 한 호출로 업데이트 되는 경우 모든 더티 필드 데이터 멤버의 데이터는 데이터 원본에 대 한 레코드에 전송 됩니다 `Update` `CDaoRecordset` `Edit` `AddNew` . 이 정보를 사용 하 여 필드 데이터 멤버에 플래그를 추가 하 여 데이터 원본에 기록 되지 않도록 열을 표시 하는 등의 추가 단계를 수행할 수 있습니다.

`IsFieldDirty` 는를 통해 구현 됩니다 `DoFieldExchange` .

## <a name="cdaorecordsetisfieldnull"></a><a name="isfieldnull"></a> CDaoRecordset:: IsFieldNull

이 멤버 함수를 호출 하 여 레코드 집합의 지정 된 필드 데이터 멤버에 Null로 플래그가 지정 되었는지 여부를 확인 합니다.

```cpp
BOOL IsFieldNull(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
상태를 확인할 필드 데이터 멤버에 대 한 포인터 이거나, 필드가 Null 인지 여부를 확인 하는 NULL입니다.

### <a name="return-value"></a>반환 값

지정 된 필드 데이터 멤버가 Null로 플래그가 지정 된 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

(데이터베이스 용어에서 Null은 "값을 갖지 않음"을 의미 하 고 c + +의 경우 NULL과 같지 않습니다.) 필드 데이터 멤버가 Null로 플래그가 지정 된 경우 값이 없는 현재 레코드의 열로 해석 됩니다.

> [!NOTE]
> 특정 상황에서는 `IsFieldNull` 다음 코드 예제와 같이를 사용 하는 것이 비효율적 일 수 있습니다.

[!code-cpp[NVC_MFCDatabase#5](../../mfc/codesnippet/cpp/cdaorecordset-class_5.cpp)]

> [!NOTE]
> 에서 파생 하지 않고 동적 레코드 바인딩을 사용 하는 경우 `CDaoRecordset` 예제에 표시 된 대로 VT_NULL를 사용 해야 합니다.

## <a name="cdaorecordsetisfieldnullable"></a><a name="isfieldnullable"></a> CDaoRecordset:: IsFieldNullable

지정 된 필드 데이터 멤버가 "nullable" (Null 값으로 설정할 수 있음) 인지 여부를 확인 하려면이 멤버 함수를 호출 합니다. C + + NULL은 Null과 같지 않습니다 .이는 데이터베이스 용어에서 "값이 없습니다."를 의미 합니다.

```cpp
BOOL IsFieldNullable(void* pv);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
상태를 확인할 필드 데이터 멤버에 대 한 포인터 이거나, 필드가 Null 인지 여부를 확인 하는 NULL입니다.

### <a name="return-value"></a>반환 값

지정 된 필드 데이터 멤버를 Null로 설정할 수 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

Null 일 수 없는 필드에는 값이 있어야 합니다. 레코드를 추가 하거나 업데이트할 때 이러한 필드를 Null로 설정 하려고 하면 데이터 원본에서 추가 또는 업데이트를 거부 하 고 `Update` 예외가 throw 됩니다. 는 `Update` 를 호출할 때가 아니라를 호출할 때 예외가 발생 합니다 `SetFieldNull` .

## <a name="cdaorecordsetisopen"></a><a name="isopen"></a> CDaoRecordset:: IsOpen

이 멤버 함수를 호출 하 여 레코드 집합이 열려 있는지 확인 합니다.

```cpp
BOOL IsOpen() const;
```

### <a name="return-value"></a>반환 값

레코드 집합 개체의 `Open` 또는 `Requery` 멤버 함수를 이전에 호출 하 고 레코드 집합을 닫지 않은 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

## <a name="cdaorecordsetm_bcheckcachefordirtyfields"></a><a name="m_bcheckcachefordirtyfields"></a> CDaoRecordset:: m_bCheckCacheForDirtyFields

캐시 된 필드가 더티 (변경 됨) 및 Null로 자동으로 표시 되는지 여부를 나타내는 플래그를 포함 합니다.

### <a name="remarks"></a>설명

플래그의 기본값은 TRUE입니다. 이 데이터 멤버의 설정은 전체 이중 버퍼링 메커니즘을 제어 합니다. 플래그를 TRUE로 설정 하면 DFX 메커니즘을 사용 하 여 필드 별로 캐싱을 해제할 수 있습니다. 플래그를 FALSE로 설정한 경우에는를 직접 호출 해야 합니다 `SetFieldDirty` `SetFieldNull` .

을 호출 하기 전에이 데이터 멤버 `Open` 를 설정 합니다. 이 메커니즘은 사용 편의성을 위해 주로 사용 됩니다. 변경이 수행 되 면 필드의 이중 버퍼링 때문에 성능이 느릴 수 있습니다.

## <a name="cdaorecordsetm_nfields"></a><a name="m_nfields"></a> CDaoRecordset:: m_nFields

레코드 집합 클래스의 필드 데이터 멤버 수와 데이터 원본의 레코드 집합에서 선택한 열 수를 포함 합니다.

### <a name="remarks"></a>설명

레코드 집합 클래스의 생성자는 `m_nFields` 올바른 수의 정적 바인딩 필드를 사용 하 여 초기화 해야 합니다. 클래스 마법사는이 초기화를 사용 하 여 레코드 집합 클래스를 선언할 때이 초기화를 작성 합니다. 수동으로 작성할 수도 있습니다.

프레임 워크는이 숫자를 사용 하 여 필드 데이터 멤버와 데이터 소스에 있는 현재 레코드의 해당 열 간의 상호 작용을 관리 합니다.

> [!NOTE]
> 이 숫자는 `DoFieldExchange` 매개 변수를 사용 하 여를 호출한 후에 등록 된 출력 열의 수와 일치 해야 합니다 `SetFieldType` `CDaoFieldExchange::outputColumn` .

및를 통해 열을 동적으로 바인딩할 수 있습니다 `CDaoRecordset::GetFieldValue` `CDaoRecordset::SetFieldValue` . 이렇게 하면 `m_nFields` 멤버 함수의 DFX 함수 호출 수를 반영 하기 위해의 수를 증가 시킬 필요가 없습니다 `DoFieldExchange` .

## <a name="cdaorecordsetm_nparams"></a><a name="m_nparams"></a> CDaoRecordset:: m_nParams

레코드 집합의 쿼리와 함께 전달 되는 매개 변수의 수와 같은 레코드 집합 클래스의 매개 변수 데이터 멤버 수를 포함 합니다.

### <a name="remarks"></a>설명

레코드 집합 클래스에 매개 변수 데이터 멤버가 있는 경우 클래스의 생성자는 올바른 수를 사용 하 여 *m_nParams* 을 초기화 해야 합니다. *M_nParams* 기본값은 0입니다. 수동으로 수행 해야 하는 매개 변수 데이터 멤버를 추가 하는 경우에는 매개 변수 수를 반영 하도록 클래스 생성자에서 초기화를 수동으로 추가 해야 합니다 .이 값은 적어도 *m_strFilter* 또는 *m_strSort* 문자열의 ' ' 자리 표시자 수 만큼 커야 합니다.

프레임 워크는이 숫자를 사용 하 여 레코드 집합의 쿼리를 매개 변수화 합니다.

> [!NOTE]
> 이 숫자는 `DoFieldExchange` 매개 변수를 사용 하 여를 호출한 후에 등록 된 "params"의 수와 일치 해야 합니다 `SetFieldType` `CFieldExchange::param` .

관련 정보는 DAO 도움말의 "매개 변수 개체" 항목을 참조 하십시오.

## <a name="cdaorecordsetm_pdaorecordset"></a><a name="m_pdaorecordset"></a> CDaoRecordset:: m_pDAORecordset

개체를 기반으로 하는 DAO 레코드 집합 개체의 OLE 인터페이스에 대 한 포인터를 포함 `CDaoRecordset` 합니다.

### <a name="remarks"></a>설명

DAO 인터페이스에 직접 액세스 해야 하는 경우이 포인터를 사용 합니다.

관련 내용은 DAO 도움말의 "레코드 집합 개체" 항목을 참조 하십시오.

## <a name="cdaorecordsetm_pdatabase"></a><a name="m_pdatabase"></a> CDaoRecordset:: m_pDatabase

`CDaoDatabase`레코드 집합을 데이터 소스에 연결 하는 데 사용할 개체에 대 한 포인터를 포함 합니다.

### <a name="remarks"></a>설명

이 변수는 두 가지 방법으로 설정 됩니다. 일반적으로 레코드 집합 개체를 생성할 때 이미 열려 있는 개체에 대 한 포인터를 전달 `CDaoDatabase` 합니다. 대신 NULL을 전달 하면에서 `CDaoRecordset` 개체를 만들어 `CDaoDatabase` 엽니다. 두 경우 모두 `CDaoRecordset` 이 변수에 포인터를 저장 합니다.

일반적으로에 저장 된 포인터를 직접 사용 하지 않아도 됩니다 `m_pDatabase` . 그러나에 대 한 고유한 확장을 작성 하 `CDaoRecordset` 는 경우 포인터를 사용 해야 할 수 있습니다. 예를 들어 사용자 고유의를 throw 하는 경우 포인터가 필요할 수 있습니다 `CDaoException` .

관련 내용은 DAO 도움말의 "데이터베이스 개체" 항목을 참조 하십시오.

## <a name="cdaorecordsetm_strfilter"></a><a name="m_strfilter"></a> CDaoRecordset:: m_strFilter

SQL 문의 **WHERE** 절을 생성 하는 데 사용 되는 문자열을 포함 합니다.

### <a name="remarks"></a>설명

여기에는 레코드 집합을 필터링 할 예약 **된 단어가 포함** 되지 않습니다. 테이블 형식 레코드 집합에는이 데이터 멤버를 사용할 수 없습니다. 를 사용 하면 `m_strFilter` 포인터를 사용 하 여 레코드 집합을 열 때 아무런 효과가 없습니다 `CDaoQueryDef` .

미국 버전의 Microsoft Jet 데이터베이스 엔진을 사용 하지 않는 경우에도 날짜를 포함 하는 필드를 필터링 할 때 미국 날짜 형식 (월-일-연도)을 사용 합니다. 그렇지 않으면 데이터가 원하는 대로 필터링 되지 않을 수 있습니다.

관련 내용은 DAO 도움말의 "필터 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetm_strsort"></a><a name="m_strsort"></a> CDaoRecordset:: m_strSort

예약 된 단어 **orderby** 를 사용 하지 않고 SQL 문의 **orderby** 절을 포함 하는 문자열을 포함 합니다.

### <a name="remarks"></a>설명

다이너셋 및 스냅숏 형식의 레코드 집합 개체를 기준으로 정렬할 수 있습니다.

테이블 형식 레코드 집합 개체는 정렬할 수 없습니다. 테이블 형식 레코드 집합의 정렬 순서를 확인 하려면 [SetCurrentIndex](#setcurrentindex)를 호출 합니다.

포인터를 사용 하 여 레코드 집합을 열 때 *m_strSort* 을 사용 해도 아무런 효과가 없습니다 `CDaoQueryDef` .

관련 내용은 DAO 도움말의 "Sort Property" 항목을 참조 하십시오.

## <a name="cdaorecordsetmove"></a><a name="move"></a> CDaoRecordset:: Move

현재 레코드에서 레코드 집합 *Lrows* 레코드를 배치 하려면이 멤버 함수를 호출 합니다.

```cpp
virtual void Move(long lRows);
```

### <a name="parameters"></a>매개 변수

*lRows*<br/>
앞으로 또는 뒤로 이동할 레코드 수입니다. 양수 값은 레코드 집합의 끝 부분으로 앞으로 이동 합니다. 음수 값은 시작 부분을 향해 뒤로 이동 합니다.

### <a name="remarks"></a>설명

앞으로 또는 뒤로 이동할 수 있습니다. `Move( 1 )` 는와 같으며 `MoveNext` 와 `Move( -1 )` 동일 `MovePrev` 합니다.

> [!CAUTION]
> 레코드 `Move` 집합에 레코드가 없으면 함수를 호출 하면 예외가 throw 됩니다. 일반적으로 `IsBOF` 이동 작업 전에 및를 모두 호출 하 여 레코드 `IsEOF` 집합에 레코드가 있는지 여부를 확인 합니다. 또는를 호출한 후에 `Open` `Requery` 는 또는를 호출 `IsBOF` `IsEOF` 합니다.

> [!NOTE]
> 레코드 집합의 시작 또는 끝을 지나서 스크롤 했거나 `IsBOF` `IsEOF` 0이 아닌 값을 반환 하는 경우에 대 한 호출은를 `Move` throw `CDaoException` 합니다.

> [!NOTE]
> `Move`현재 레코드를 업데이트 하거나 추가 하는 동안 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

`Move`앞 으로만 이동 가능한 스크롤 스냅숏에서를 호출 하는 경우 *lrows* 매개 변수는 양의 정수 여야 하며 책갈피는 허용 되지 않으므로 앞 으로만 이동 하면 됩니다.

레코드 집합의 first, last, next 또는 previous 레코드를 현재 레코드로 만들려면, `MoveFirst` `MoveLast` , `MoveNext` 또는 `MovePrev` 멤버 함수를 호출 합니다.

관련 정보는 DAO 도움말의 "Move Method" 및 "MoveFirst, MoveLast, MoveNext, MovePrevious 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetmovefirst"></a><a name="movefirst"></a> CDaoRecordset:: MoveFirst

이 멤버 함수를 호출 하 여 레코드 집합의 첫 번째 레코드 (있는 경우)를 현재 레코드로 만듭니다.

```cpp
void MoveFirst();
```

### <a name="remarks"></a>설명

`MoveFirst`레코드 집합을 연 후 즉시를 호출할 필요가 없습니다. 이때 첫 번째 레코드 (있는 경우)가 자동으로 현재 레코드가 됩니다.

> [!CAUTION]
> 레코드 `Move` 집합에 레코드가 없으면 함수를 호출 하면 예외가 throw 됩니다. 일반적으로 `IsBOF` 이동 작업 전에 및를 모두 호출 하 여 레코드 `IsEOF` 집합에 레코드가 있는지 여부를 확인 합니다. 또는를 호출한 후에 `Open` `Requery` 는 또는를 호출 `IsBOF` `IsEOF` 합니다.

> [!NOTE]
> `Move`현재 레코드를 업데이트 하거나 추가 하는 동안 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

`Move`조건을 적용 하지 않고 레코드에서 레코드로 이동 하려면 함수를 사용 합니다. 찾기 작업을 사용 하 여 특정 조건에 맞는 다이너셋 형식 또는 스냅숏 형식 recordset 개체에서 레코드를 찾을 수 있습니다. 테이블 형식 recordset 개체에서 레코드를 찾으려면를 호출 `Seek` 합니다.

레코드 집합이 테이블 형식 레코드 집합을 참조 하는 경우 이동은 테이블의 현재 인덱스를 따릅니다. 기본 DAO 개체의 인덱스 속성을 사용 하 여 현재 인덱스를 설정할 수 있습니다. 현재 인덱스를 설정 하지 않은 경우 반환 되는 레코드의 순서는 정의 되지 않습니다.

`MoveLast`SQL 쿼리 또는 쿼리 정의를 기반으로 하는 레코드 집합 개체에 대해를 호출 하면 쿼리가 강제로 완료 되 고 레코드 집합 개체가 완전히 채워집니다.

`MoveFirst` `MovePrev` 앞 으로만 이동 가능한 스크롤 스냅숏으로 또는 멤버 함수를 호출할 수 없습니다.

레코드 집합 개체에서 현재 레코드의 위치를 특정 개수의 레코드를 앞 이나 뒤로 이동 하려면를 호출 `Move` 합니다.

관련 정보는 DAO 도움말의 "Move Method" 및 "MoveFirst, MoveLast, MoveNext, MovePrevious 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetmovelast"></a><a name="movelast"></a> CDaoRecordset:: MoveLast

이 멤버 함수를 호출 하 여 레코드 집합의 마지막 레코드 (있는 경우)를 현재 레코드로 만듭니다.

```cpp
void MoveLast();
```

### <a name="remarks"></a>설명

> [!CAUTION]
> 레코드 `Move` 집합에 레코드가 없으면 함수를 호출 하면 예외가 throw 됩니다. 일반적으로 `IsBOF` 이동 작업 전에 및를 모두 호출 하 여 레코드 `IsEOF` 집합에 레코드가 있는지 여부를 확인 합니다. 또는를 호출한 후에 `Open` `Requery` 는 또는를 호출 `IsBOF` `IsEOF` 합니다.

> [!NOTE]
> `Move`현재 레코드를 업데이트 하거나 추가 하는 동안 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

`Move`조건을 적용 하지 않고 레코드에서 레코드로 이동 하려면 함수를 사용 합니다. 찾기 작업을 사용 하 여 특정 조건에 맞는 다이너셋 형식 또는 스냅숏 형식 recordset 개체에서 레코드를 찾을 수 있습니다. 테이블 형식 recordset 개체에서 레코드를 찾으려면를 호출 `Seek` 합니다.

레코드 집합이 테이블 형식 레코드 집합을 참조 하는 경우 이동은 테이블의 현재 인덱스를 따릅니다. 기본 DAO 개체의 인덱스 속성을 사용 하 여 현재 인덱스를 설정할 수 있습니다. 현재 인덱스를 설정 하지 않은 경우 반환 되는 레코드의 순서는 정의 되지 않습니다.

`MoveLast`SQL 쿼리 또는 쿼리 정의를 기반으로 하는 레코드 집합 개체에 대해를 호출 하면 쿼리가 강제로 완료 되 고 레코드 집합 개체가 완전히 채워집니다.

레코드 집합 개체에서 현재 레코드의 위치를 특정 개수의 레코드를 앞 이나 뒤로 이동 하려면를 호출 `Move` 합니다.

관련 정보는 DAO 도움말의 "Move Method" 및 "MoveFirst, MoveLast, MoveNext, MovePrevious 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetmovenext"></a><a name="movenext"></a> CDaoRecordset:: MoveNext

이 멤버 함수를 호출 하 여 레코드 집합의 다음 레코드를 현재 레코드로 만듭니다.

```cpp
void MoveNext();
```

### <a name="remarks"></a>설명

이전 레코드로 이동 하기 전에를 호출 하는 것이 좋습니다 `IsBOF` . 가 0을 `MovePrev` 반환 하면가 `CDaoException` `IsBOF` 0을 반환 하 고, 첫 번째 레코드 이전에 이미 스크롤 했거나 레코드 집합에서 레코드를 선택 하지 않았음을 나타내는을 호출 합니다.

> [!CAUTION]
> 레코드 `Move` 집합에 레코드가 없으면 함수를 호출 하면 예외가 throw 됩니다. 일반적으로 `IsBOF` 이동 작업 전에 및를 모두 호출 하 여 레코드 `IsEOF` 집합에 레코드가 있는지 여부를 확인 합니다. 또는를 호출한 후에 `Open` `Requery` 는 또는를 호출 `IsBOF` `IsEOF` 합니다.

> [!NOTE]
> `Move`현재 레코드를 업데이트 하거나 추가 하는 동안 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

`Move`조건을 적용 하지 않고 레코드에서 레코드로 이동 하려면 함수를 사용 합니다. 찾기 작업을 사용 하 여 특정 조건에 맞는 다이너셋 형식 또는 스냅숏 형식 recordset 개체에서 레코드를 찾을 수 있습니다. 테이블 형식 recordset 개체에서 레코드를 찾으려면를 호출 `Seek` 합니다.

레코드 집합이 테이블 형식 레코드 집합을 참조 하는 경우 이동은 테이블의 현재 인덱스를 따릅니다. 기본 DAO 개체의 인덱스 속성을 사용 하 여 현재 인덱스를 설정할 수 있습니다. 현재 인덱스를 설정 하지 않은 경우 반환 되는 레코드의 순서는 정의 되지 않습니다.

레코드 집합 개체에서 현재 레코드의 위치를 특정 개수의 레코드를 앞 이나 뒤로 이동 하려면를 호출 `Move` 합니다.

관련 정보는 DAO 도움말의 "Move Method" 및 "MoveFirst, MoveLast, MoveNext, MovePrevious 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetmoveprev"></a><a name="moveprev"></a> CDaoRecordset:: MovePrev

이 멤버 함수를 호출 하 여 레코드 집합의 이전 레코드를 현재 레코드로 만듭니다.

```cpp
void MovePrev();
```

### <a name="remarks"></a>설명

이전 레코드로 이동 하기 전에를 호출 하는 것이 좋습니다 `IsBOF` . 가 0을 `MovePrev` 반환 하면가 `CDaoException` `IsBOF` 0을 반환 하 고, 첫 번째 레코드 이전에 이미 스크롤 했거나 레코드 집합에서 레코드를 선택 하지 않았음을 나타내는을 호출 합니다.

> [!CAUTION]
> 레코드 `Move` 집합에 레코드가 없으면 함수를 호출 하면 예외가 throw 됩니다. 일반적으로 `IsBOF` 이동 작업 전에 및를 모두 호출 하 여 레코드 `IsEOF` 집합에 레코드가 있는지 여부를 확인 합니다. 또는를 호출한 후에 `Open` `Requery` 는 또는를 호출 `IsBOF` `IsEOF` 합니다.

> [!NOTE]
> `Move`현재 레코드를 업데이트 하거나 추가 하는 동안 함수를 호출 하면 경고가 발생 하지 않고 업데이트가 손실 됩니다.

`Move`조건을 적용 하지 않고 레코드에서 레코드로 이동 하려면 함수를 사용 합니다. 찾기 작업을 사용 하 여 특정 조건에 맞는 다이너셋 형식 또는 스냅숏 형식 recordset 개체에서 레코드를 찾을 수 있습니다. 테이블 형식 recordset 개체에서 레코드를 찾으려면를 호출 `Seek` 합니다.

레코드 집합이 테이블 형식 레코드 집합을 참조 하는 경우 이동은 테이블의 현재 인덱스를 따릅니다. 기본 DAO 개체의 인덱스 속성을 사용 하 여 현재 인덱스를 설정할 수 있습니다. 현재 인덱스를 설정 하지 않은 경우 반환 되는 레코드의 순서는 정의 되지 않습니다.

`MoveFirst` `MovePrev` 앞 으로만 이동 가능한 스크롤 스냅숏으로 또는 멤버 함수를 호출할 수 없습니다.

레코드 집합 개체에서 현재 레코드의 위치를 특정 개수의 레코드를 앞 이나 뒤로 이동 하려면를 호출 `Move` 합니다.

관련 정보는 DAO 도움말의 "Move Method" 및 "MoveFirst, MoveLast, MoveNext, MovePrevious 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetopen"></a><a name="open"></a> CDaoRecordset:: Open

이 멤버 함수를 호출 하 여 레코드 집합에 대 한 레코드를 검색 해야 합니다.

```cpp
virtual void Open(
    int nOpenType = AFX_DAO_USE_DEFAULT_TYPE,
    LPCTSTR lpszSQL = NULL,
    int nOptions = 0);

virtual void Open(
    CDaoTableDef* pTableDef,
    int nOpenType = dbOpenTable,
    int nOptions = 0);

virtual void Open(
    CDaoQueryDef* pQueryDef,
    int nOpenType = dbOpenDynaset,
    int nOptions = 0);
```

### <a name="parameters"></a>매개 변수

*nOpenType*<br/>
다음 값 중 하나입니다.

- `dbOpenDynaset` 양방향 스크롤이 포함 된 다이너셋 형식의 레코드 집합입니다. 이것이 기본값입니다.

- `dbOpenTable` 양방향 스크롤이 있는 테이블 형식 레코드 집합입니다.

- `dbOpenSnapshot` 양방향 스크롤이 있는 스냅숏 형식 레코드 집합입니다.

*lpszSQL*<br/>
다음 중 하나를 포함 하는 문자열 포인터입니다.

- NULL 포인터입니다.

- 하나 이상의 테이블 및/또는 쿼리 테이블 이름 (쉼표로 구분)입니다.

- SQL **SELECT** 문 (선택적으로 sql **WHERE** 또는 **ORDERBY** 절)

- 통과 쿼리입니다.

*nOptions*<br/>
아래에 나열 된 하나 이상의 옵션입니다. 기본값은 0입니다. 가능한 값은 다음과 같습니다.

- `dbAppendOnly` 새 레코드 (다이너셋 형식 레코드 집합만)만 추가할 수 있습니다. 이 옵션은 레코드를 추가 하는 것만을 의미 합니다. MFC ODBC 데이터베이스 클래스에는 레코드를 검색 하 고 추가할 수 있는 추가 전용 옵션이 있습니다.

- `dbForwardOnly` 레코드 집합은 앞 으로만 이동 가능한 스크롤 스냅숏입니다.

- `dbSeeChanges` 다른 사용자가 편집 중인 데이터를 변경 하는 경우 예외를 생성 합니다.

- `dbDenyWrite` 다른 사용자는 레코드를 수정 하거나 추가할 수 없습니다.

- `dbDenyRead` 다른 사용자는 레코드를 볼 수 없습니다 (테이블 형식 레코드 집합에만 해당).

- `dbReadOnly` 레코드를 볼 수만 있습니다. 다른 사용자는이를 수정할 수 있습니다.

- `dbInconsistent` 일관 되지 않은 업데이트가 허용 됩니다 (다이너셋 형식 레코드 집합에만 해당).

- `dbConsistent` 일관 된 업데이트만 허용 됩니다 (다이너셋 형식 레코드 집합에만 해당).

> [!NOTE]
> 상수 `dbConsistent` 와는 `dbInconsistent` 함께 사용할 수 없습니다. 지정 된 인스턴스 중 하나를 사용할 수 있지만 둘 다 사용할 수는 없습니다 `Open` .

*pTableDef*<br/>
[CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 개체에 대 한 포인터입니다. 이 버전은 테이블 형식 레코드 집합에 대해서만 유효 합니다. 이 옵션을 사용 하는 경우를 `CDaoDatabase` 생성 하는 데 사용 되는 포인터가 `CDaoRecordset` 사용 되지 않고 테이블 정의가 있는 데이터베이스가 사용 됩니다.

*pQueryDef*<br/>
[CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) 개체에 대 한 포인터입니다. 이 버전은 다이너셋 형식 및 스냅숏 형식 레코드 집합에 대해서만 유효 합니다. 이 옵션을 사용 하는 경우를 `CDaoDatabase` 생성 하는 데 사용 되는 포인터가 `CDaoRecordset` 사용 되지 않습니다. 대신 querydef가 있는 데이터베이스가 사용 됩니다.

### <a name="remarks"></a>설명

을 호출 하기 전에 `Open` 레코드 집합 개체를 생성 해야 합니다. 다음과 같은 여러 가지 방법으로 이 작업을 수행할 수 있습니다.

- 레코드 집합 개체를 생성할 때 이미 열려 있는 개체에 대 한 포인터를 전달 `CDaoDatabase` 합니다.

- 레코드 집합 개체를 생성 하는 경우 열려 있지 않은 개체에 대 한 포인터를 전달 `CDaoDatabase` 합니다. 레코드 집합에서 `CDaoDatabase` 개체를 열 수 있지만 레코드 집합 개체가 닫히면 해당 개체는 닫히지 않습니다.

- 레코드 집합 개체를 생성 하는 경우 NULL 포인터를 전달 합니다. 레코드 집합 개체는 `GetDefaultDBName` 를 호출 하 여 Microsoft Access의 이름을 가져옵니다. 열려는 MDB 파일입니다. 그러면 레코드 집합에서 `CDaoDatabase` 개체가 열리고 레코드 집합이 열려 있는 동안 열린 상태로 유지 됩니다. `Close`레코드 집합에 대해를 호출 하면 `CDaoDatabase` 개체도 닫힙니다.

    > [!NOTE]
    >  레코드 집합에서 개체가 열리면 `CDaoDatabase` 비독점적 access를 사용 하 여 데이터 원본을 엽니다.

`Open` *LpszSQL* 매개 변수를 사용 하는 버전의 경우 레코드 집합이 열리면 여러 가지 방법 중 하나로 레코드를 검색할 수 있습니다. 첫 번째 옵션은에 DFX 함수를 포함 하는 것입니다 `DoFieldExchange` . 두 번째 옵션은 멤버 함수를 호출 하 여 동적 바인딩을 사용 하는 것입니다 `GetFieldValue` . 이러한 옵션은 개별적으로 또는 함께 구현할 수 있습니다. 결합 된 경우에는에 대 한 호출에 대해 직접 SQL 문을 전달 해야 `Open` 합니다.

개체를 전달 하는 두 번째 버전의를 사용 하는 경우 `Open` `CDaoTableDef` 결과 열을 및 DFX 메커니즘을 통해 바인딩할 수 있으며를 `DoFieldExchange` 통해 동적으로 바인딩할 수 있습니다 `GetFieldValue` .

> [!NOTE]
> `Open` `CDaoTableDef` 테이블 형식 레코드 집합에 대해서만 개체를 사용 하 여를 호출할 수 있습니다.

개체를 전달 하는 세 번째 버전의를 사용 하는 경우 `Open` `CDaoQueryDef` 해당 쿼리가 실행 되 고 결과 열은 `DoFieldExchange` 및 DFX 메커니즘을 통해 바인딩 및/또는을 통해 동적으로 바인딩할 수 있습니다 `GetFieldValue` .

> [!NOTE]
> `Open` `CDaoQueryDef` 다이너셋 형식 및 스냅숏 형식 레코드 집합에 대해서만 개체를 사용 하 여를 호출할 수 있습니다.

매개 변수를 사용 하는 첫 번째 버전의 경우 `Open` `lpszSQL` 다음 표에 표시 된 조건에 따라 레코드가 선택 됩니다.

|`lpszSQL` 매개 변수의 값|선택한 레코드는 다음에 의해 결정 됩니다.|예제|
|--------------------------------------|----------------------------------------|-------------|
|NULL|에서 반환 된 문자열 `GetDefaultSQL` 입니다.||
|하나 이상의 테이블 및/또는 쿼리 정의 이름에 대 한 쉼표로 구분 된 목록입니다.|`DoFieldExchange`에 표시 된 모든 열|`"Customer"`|
|테이블 목록 **에서** 열 목록 **선택**|지정 된 테이블 정의 및/또는 쿼리 정의의 지정 된 열입니다.|`"SELECT CustId, CustName`<br /><br /> `FROM Customer"`|

일반적인 절차는에 NULL을 전달 하는 것입니다 `Open` .이 경우는 `Open` `GetDefaultSQL` 파생 클래스를 만들 때 클래스 마법사가 생성 하는 재정의 가능한 멤버 함수를 호출 `CDaoRecordset` 합니다. 이 값은 클래스 마법사에서 지정한 테이블 및/또는 쿼리 정의 이름을 제공 합니다. 대신 *lpszSQL* 매개 변수에서 다른 정보를 지정할 수 있습니다.

전달 하는 것과 관계 없이 `Open` 쿼리에 대 한 최종 SQL 문자열을 생성 합니다. 문자열에는 전달 된 *lpszSQL* 문자열에 추가 된 Sql **WHERE** 및 **ORDERBY** 절이 포함 될 수 있습니다. 그런 다음 쿼리를 실행 합니다. 를 호출한 후를 호출 하 여 생성 된 문자열을 검사할 수 있습니다 `GetSQL` `Open` .

레코드 집합 클래스의 필드 데이터 멤버는 선택한 데이터의 열에 바인딩됩니다. 레코드가 반환 되 면 첫 번째 레코드가 현재 레코드가 됩니다.

필터 또는 정렬 등의 레코드 집합에 대 한 옵션을 설정 하려는 경우에는 `m_strSort` `m_strFilter` 레코드 집합 개체를 구성한 후를 호출 하기 전에를 설정 합니다 `Open` . 레코드 집합이 이미 열려 있는 후 레코드 집합의 레코드를 새로 고치려면를 호출 `Requery` 합니다.

`Open`다이너셋 형식 또는 스냅숏 형식 레코드 집합에서를 호출 하거나 데이터 원본이 SQL 문 또는 연결 된 테이블을 나타내는 tabledef를 참조 하는 경우 형식 인수에를 사용할 수 없습니다 `dbOpenTable` . 이렇게 하면 MFC에서 예외를 throw 합니다. 테이블 정의 개체가 연결 된 테이블을 나타내는지 여부를 확인 하려면 [CDaoTableDef](../../mfc/reference/cdaotabledef-class.md) 개체를 만들고 해당 [getconnect](../../mfc/reference/cdaotabledef-class.md#getconnect) 멤버 함수를 호출 합니다.

`dbSeeChanges`동일한 레코드를 편집 하거나 삭제 하는 경우 다른 사용자 또는 컴퓨터의 다른 프로그램에서 변경한 내용을 트래핑 하려면 플래그를 사용 합니다. 예를 들어 두 사용자가 같은 레코드를 편집 하기 시작 하면 멤버 함수를 호출 하는 첫 번째 사용자가 `Update` 성공 합니다. `Update`두 번째 사용자가를 호출 하면 `CDaoException` 이 throw 됩니다. 마찬가지로 두 번째 사용자가를 호출 하 여 `Delete` 레코드를 삭제 하 고 첫 번째 사용자가 이미 변경한 경우이 `CDaoException` 발생 합니다.

일반적으로 `CDaoException` 업데이트 하는 동안 사용자가이를 가져오는 경우 코드에서 필드의 내용을 새로 고치고 새로 수정 된 값을 검색 해야 합니다. 삭제 하는 동안 예외가 발생 하는 경우 코드에서 사용자에 게 새 레코드 데이터를 표시 하 고 데이터가 최근에 변경 되었음을 나타내는 메시지를 표시할 수 있습니다. 이 시점에서 코드는 사용자가 여전히 레코드를 삭제 하려고 한다는 확인을 요청할 수 있습니다.

> [!TIP]
> 앞 으로만 이동 가능한 스크롤 옵션 ( `dbForwardOnly` )을 사용 하 여 응용 프로그램이 ODBC 데이터 원본에서 연 레코드 집합을 통해 단일 패스를 만들 때 성능을 향상 시킬 수 있습니다.

관련 내용은 DAO 도움말의 "OpenRecordset 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetrequery"></a><a name="requery"></a> CDaoRecordset:: Requery

이 멤버 함수를 호출 하 여 레코드 집합을 다시 작성 (새로 고침) 합니다.

```cpp
virtual void Requery();
```

### <a name="remarks"></a>설명

레코드가 반환 되 면 첫 번째 레코드가 현재 레코드가 됩니다.

사용자 또는 다른 사용자가 데이터 원본에 만드는 추가 및 삭제를 레코드 집합에 반영 하려면를 호출 하 여 레코드 집합을 다시 빌드해야 합니다 `Requery` . 레코드 집합이 다이너셋 인 경우 사용자 또는 다른 사용자가 기존 레코드에 대해 수행 하는 업데이트 (추가는 제외)가 자동으로 반영 됩니다. 레코드 집합이 스냅숏이 면 `Requery` 를 호출 하 여 추가 및 삭제 뿐만 아니라 다른 사용자의 편집 내용을 반영 해야 합니다.

다이너셋 또는 스냅숏의 경우 `Requery` 매개 변수 값을 사용 하 여 레코드 집합을 다시 작성 하려는 경우 언제 든 지를 호출 합니다. 를 호출 하기 전에 [m_strFilter](#m_strfilter) 및 [m_strSort](#m_strsort) 설정 하 여 새 필터나 정렬을 설정 `Requery` 합니다. 를 호출 하기 전에 매개 변수 데이터 멤버에 새 값을 할당 하 여 새 매개 변수를 설정 `Requery` 합니다.

레코드 집합을 다시 작성 하려는 시도가 실패 하면 레코드 집합은 닫힙니다. 를 호출 하기 전에 `Requery` [canrestart](#canrestart) 멤버 함수를 호출 하 여 레코드 집합을 다시 검색할 수 있는지 여부를 확인할 수 있습니다. `CanRestart` 는이 성공할 것임을 보장 하지 않습니다 `Requery` .

> [!CAUTION]
> `Requery`를 호출한 후에만를 호출 `Open` 합니다.

> [!NOTE]
> [Requery](#requery) 를 호출 하면 DAO 책갈피가 변경 됩니다.

`Requery`호출 `CanRestart` 에서 0을 반환 하거나 테이블 형식 레코드 집합에서 사용할 수 없는 경우에는 다이너셋 형식 또는 스냅숏 형식 레코드 집합에 대해를 호출할 수 없습니다.

를 `IsBOF` `IsEOF` 호출한 후와 모두 0이 아닌 값을 반환 하 `Requery` 는 경우 쿼리는 레코드를 반환 하지 않고 레코드 집합에 데이터가 포함 되지 않습니다.

관련 내용은 DAO 도움말의 "Requery 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetseek"></a><a name="seek"></a> CDaoRecordset:: Seek

이 멤버 함수를 호출 하 여 현재 인덱스에 대 한 지정 된 조건을 충족 하는 인덱싱된 테이블 형식 recordset 개체에서 레코드를 찾고이 레코드를 현재 레코드로 설정 합니다.

```cpp
BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKey1,
    COleVariant* pKey2 = NULL,
    COleVariant* pKey3 = NULL);

BOOL Seek(
    LPCTSTR lpszComparison,
    COleVariant* pKeyArray,
    WORD nKeys);
```

### <a name="parameters"></a>매개 변수

*lpszComparison*<br/>
"<", " \<=", "=", "> =" 또는 ">" 문자열 식 중 하나입니다.

*pKey1*<br/>
인덱스의 첫 번째 필드에 해당 하는 값을 갖는 [COleVariant](../../mfc/reference/colevariant-class.md) 에 대 한 포인터입니다. 필수 요소.

*pKey2*<br/>
`COleVariant`인덱스의 두 번째 필드 (있는 경우)에 해당 하는 값을 갖는에 대 한 포인터입니다. 기본값은 NULL입니다.

*pKey3*<br/>
`COleVariant`인덱스의 세 번째 필드 (있는 경우)에 해당 하는 값이 있는에 대 한 포인터입니다. 기본값은 NULL입니다.

*pKeyArray*<br/>
변형 배열에 대 한 포인터입니다. 배열 크기는 인덱스의 필드 수에 해당 합니다.

*nKeys*<br/>
배열의 크기에 해당 하는 정수입니다 .이 정수는 인덱스의 필드 수입니다.

> [!NOTE]
> 키에 와일드 카드를 지정 하지 마십시오. 와일드 카드는 `Seek` 와 일치 하는 레코드를 반환 하지 않습니다.

### <a name="return-value"></a>반환 값

일치 하는 레코드가 있는 경우 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

의 두 번째 (array) 버전을 사용 `Seek` 하 여 4 개 이상의 필드 인덱스를 처리 합니다.

`Seek` 테이블 형식 레코드 집합에서 고성능 인덱스 검색을 사용 하도록 설정 합니다. 를 호출 하기 전에를 호출 하 여 현재 인덱스를 설정 해야 합니다 `SetCurrentIndex` `Seek` . 인덱스가 고유 하지 않은 키 필드를 식별 하는 경우는 `Seek` 조건을 충족 하는 첫 번째 레코드를 찾습니다. 인덱스를 설정 하지 않으면 예외가 throw 됩니다.

유니코드 레코드 집합을 만들지 않는 경우 `COleVariant` 개체를 명시적으로 ANSI로 선언 해야 합니다. 이 작업을 수행 하려면 *vtSrc* 가 (ANSI)로 설정 된 생성자의 [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** `VT_BSTRT` 또는 `COleVariant` *lpszSrc* 가로 설정 된 [setstring](../../mfc/reference/colevariant-class.md#setstring)**(** *vtSrc* **,** *vtSrc* **)** 함수를 사용 합니다 `VT_BSTRT` .

를 호출 하 `Seek` 는 경우 하나 이상의 키 값과 비교 연산자 ("<", " \<=", "=", "> =" 또는 ">")를 전달 합니다. `Seek` 지정 된 키 필드를 검색 하 고 *lpszComparison* 및 *pKey1* 에 지정 된 조건을 충족 하는 첫 번째 레코드를 찾습니다. 이 항목이 발견 되 면 `Seek` 0이 아닌 값을 반환 하 고 해당 레코드를 current로 만듭니다. `Seek`에서 일치 하는 항목을 찾지 못하면는 `Seek` 0을 반환 하 고 현재 레코드는 정의 되지 않습니다. DAO를 직접 사용 하는 경우 NoMatch 속성을 명시적으로 확인 해야 합니다.

`lpszComparison`가 "=", ">=" 또는 ">" 이면 `Seek` 인덱스의 시작 부분에서 시작 합니다. *LpszComparison* 이 "<" 또는 "<=" 이면는 `Seek` 인덱스 끝에서 시작 하 고 끝에 중복 된 인덱스 항목이 없으면 뒤로 검색 합니다. 이 경우는 `Seek` 인덱스 끝의 중복 인덱스 항목 중 임의의 항목에서 시작 합니다.

를 사용 하는 경우 현재 레코드가 될 필요는 없습니다 `Seek` .

특정 조건을 충족 하는 다이너셋 형식 또는 스냅숏 형식 레코드 집합에서 레코드를 찾으려면 찾기 작업을 사용 합니다. 특정 조건을 만족 하는 레코드 뿐만 아니라 모든 레코드를 포함 하려면 이동 작업을 사용 하 여 레코드에서 레코드로 이동 합니다.

`Seek`연결 된 테이블은 다이너셋 형식 또는 스냅숏 형식 레코드 집합으로 열어야 하므로 모든 형식의 연결 된 테이블에 대해를 호출할 수 없습니다. 그러나 `CDaoDatabase::Open` 를 호출 하 여 설치 가능한 ISAM 데이터베이스를 직접 열면 `Seek` 성능이 느릴 수 있지만 해당 데이터베이스의 테이블에 대해를 호출할 수 있습니다.

관련 내용은 DAO 도움말의 "Seek 메서드" 항목을 참조 하십시오.

## <a name="cdaorecordsetsetabsoluteposition"></a><a name="setabsoluteposition"></a> CDaoRecordset:: SetAbsolutePosition

레코드 집합 개체의 현재 레코드에 대 한 상대 레코드 번호를 설정 합니다.

```cpp
void SetAbsolutePosition(long lPosition);
```

### <a name="parameters"></a>매개 변수

*lPosition*<br/>
레코드 집합에서 현재 레코드의 서 수 위치에 해당 합니다.

### <a name="remarks"></a>설명

를 호출 하면 `SetAbsolutePosition` 다이너셋 형식 또는 스냅숏 형식 레코드 집합의 서 수 위치에 따라 특정 레코드에 현재 레코드 포인터를 배치할 수 있습니다. [GetAbsolutePosition](#getabsoluteposition)를 호출 하 여 현재 레코드 번호를 확인할 수도 있습니다.

> [!NOTE]
> 이 멤버 함수는 다이너셋 형식 및 스냅숏 형식 레코드 집합에 대해서만 유효 합니다.

기본 DAO 개체의 AbsolutePosition 속성 값은 0부터 시작 합니다. 0의 설정은 레코드 집합의 첫 번째 레코드를 참조 합니다. 채워진 레코드 수보다 큰 값을 설정 하면 MFC에서 예외가 throw 됩니다. 멤버 함수를 호출 하 여 레코드 집합에서 채워진 레코드 수를 확인할 수 있습니다 `GetRecordCount` .

현재 레코드를 삭제 하면 AbsolutePosition 속성 값이 정의 되지 않고 MFC가 참조 되는 경우 예외를 throw 합니다. 새 레코드는 시퀀스의 끝에 추가 됩니다.

> [!NOTE]
> 이 속성은 서로게이트 레코드 번호로 사용 하기 위한 것이 아닙니다. 책갈피는 지정 된 위치를 유지 하 고 반환 하는 데 권장 되는 방법 이지만 책갈피를 지 원하는 모든 형식의 레코드 집합 개체에 현재 레코드를 배치할 수 있는 유일한 방법입니다. 특히, 앞의 레코드가 삭제 될 때 지정 된 레코드의 위치가 변경 됩니다. 또한 레코드 집합에 있는 개별 레코드의 순서는 **ORDERBY** 절을 사용 하 여 SQL 문을 사용 하 여 생성 된 경우를 제외 하 고는 다시 생성 될 경우 지정 된 레코드는 동일한 절대 위치를 갖게 됩니다.

관련 내용은 DAO 도움말의 "AbsolutePosition 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetsetbookmark"></a><a name="setbookmark"></a> CDaoRecordset:: SetBookmark

이 멤버 함수를 호출 하 여 지정 된 책갈피를 포함 하는 레코드에 레코드 집합을 배치 합니다.

```cpp
void SetBookmark(COleVariant varBookmark);
```

### <a name="parameters"></a>매개 변수

*varBookmark*<br/>
특정 레코드의 책갈피 값을 포함 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 개체입니다.

### <a name="remarks"></a>설명

레코드 집합 개체를 만들거나 열 때 각 레코드에는 이미 고유한 책갈피가 있습니다. 을 호출 하 `GetBookmark` 고 값을 개체에 저장 하 여 현재 레코드에 대 한 책갈피를 검색할 수 있습니다 `COleVariant` . 나중에 `SetBookmark` 저장 된 책갈피 값을 사용 하 여를 호출 하 여 해당 레코드로 돌아갈 수 있습니다.

> [!NOTE]
> [Requery](#requery) 를 호출 하면 DAO 책갈피가 변경 됩니다.

유니코드 레코드 집합을 만들지 않는 경우 `COleVariant` 개체는 ANSI로 명시적으로 선언 되어야 합니다. 이 작업을 수행 하려면 *vtSrc* 가 (ANSI)로 설정 된 생성자의 [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** `VT_BSTRT` 또는 `COleVariant` *lpszSrc* 가로 설정 된 [setstring](../../mfc/reference/colevariant-class.md#setstring)**(** *vtSrc* **,** *vtSrc* **)** 함수를 사용 합니다 `VT_BSTRT` .

관련 내용은 DAO 도움말의 "책갈피 속성" 및 책갈피를 사용할 수 있는 속성 "항목을 참조 하십시오.

## <a name="cdaorecordsetsetcachesize"></a><a name="setcachesize"></a> CDaoRecordset:: SetCacheSize

캐시 될 레코드 수를 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetCacheSize(long lSize);
```

### <a name="parameters"></a>매개 변수

*lSize*<br/>
레코드 수를 지정 합니다. 일반적인 값은 100입니다. 0을 설정 하면 캐싱이 해제 됩니다. 설정은 5에서 1200 사이 여야 합니다. 캐시는 상당한 양의 메모리를 사용할 수 있습니다.

### <a name="remarks"></a>설명

캐시는 응용 프로그램이 실행 되는 동안 데이터를 다시 요청 하는 경우 서버에서 가장 최근에 검색 된 데이터를 보관 하는 로컬 메모리의 공간입니다. 데이터 캐싱은 다이너셋 형식의 레코드 집합 개체를 통해 원격 서버에서 데이터를 검색 하는 응용 프로그램의 성능을 향상 시킵니다. 데이터가 요청 될 때 Microsoft Jet 데이터베이스 엔진은 서버에서 검색 하는 대신 요청 된 데이터에 대 한 캐시를 먼저 확인 하 여 더 많은 시간을 사용 합니다. ODBC 데이터 원본에서 가져오지 않은 데이터는 캐시에 저장 되지 않습니다.

모든 ODBC 데이터 원본 (예: 연결 된 테이블)에는 로컬 캐시를 사용할 수 있습니다. 캐시를 만들려면 원격 데이터 원본에서 레코드 집합 개체를 열고 `SetCacheSize` 및 `SetCacheStart` 멤버 함수를 호출한 다음 멤버 함수를 호출 `FillCache` 하거나 이동 작업 중 하나를 사용 하 여 레코드를 단계별로 실행 합니다. 멤버 함수의 *Lsize* 매개 변수는 `SetCacheSize` 응용 프로그램에서 한 번에 사용할 수 있는 레코드 수를 기반으로 할 수 있습니다. 예를 들어 화면에 표시할 데이터의 원본으로 레코드 집합을 사용 하는 경우 `SetCacheSize` *lsize* 매개 변수를 20으로 전달 하 여 20 개의 레코드를 한 번에 표시할 수 있습니다.

관련 내용은 DAO 도움말의 "CacheSize, CacheStart 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetsetcachestart"></a><a name="setcachestart"></a> CDaoRecordset:: SetCacheStart

캐시 될 레코드 집합의 첫 번째 레코드에 대 한 책갈피를 지정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetCacheStart(COleVariant varBookmark);
```

### <a name="parameters"></a>매개 변수

*varBookmark*<br/>
캐시 될 레코드 집합에서 첫 번째 레코드의 책갈피를 지정 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 입니다.

### <a name="remarks"></a>설명

멤버 함수의 *varbookmark* 매개 변수에 대 한 모든 레코드의 책갈피 값을 사용할 수 있습니다 `SetCacheStart` . 현재 레코드를 사용 하 여 캐시를 시작 하려는 레코드를 만들고, [Setbookmark](#setbookmark)를 사용 하 여 해당 레코드에 대 한 책갈피를 설정 하 고, 책갈피 값을 멤버 함수에 대 한 매개 변수로 전달 합니다 `SetCacheStart` .

Microsoft Jet 데이터베이스 엔진은 캐시 범위 내에서 레코드를 요청 하 고 서버에서 캐시 범위를 벗어난 레코드를 요청 합니다.

캐시에서 검색 된 레코드는 다른 사용자가 원본 데이터에 대해 동시에 변경한 내용을 반영 하지 않습니다.

모든 캐시 된 데이터를 강제로 업데이트 하려면의 *Lsize* 매개 변수를 0으로 전달 하 고 `SetCacheSize` `SetCacheSize` 원래 요청한 캐시 크기를 다시 호출한 다음 `FillCache` 멤버 함수를 호출 합니다.

유니코드 레코드 집합을 만들지 않는 경우 `COleVariant` 개체는 ANSI로 명시적으로 선언 되어야 합니다. 이 작업을 수행 하려면 *vtSrc* 가 (ANSI)로 설정 된 생성자의 [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** `VT_BSTRT` 또는 `COleVariant` *lpszSrc* 가로 설정 된 [setstring](../../mfc/reference/colevariant-class.md#setstring)**(** *vtSrc* **,** *vtSrc* **)** 함수를 사용 합니다 `VT_BSTRT` .

관련 내용은 DAO 도움말의 CacheSize, CacheStart Properties 항목을 참조 하십시오.

## <a name="cdaorecordsetsetcurrentindex"></a><a name="setcurrentindex"></a> CDaoRecordset:: SetCurrentIndex

테이블 형식 레코드 집합에 인덱스를 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetCurrentIndex(LPCTSTR lpszIndex);
```

### <a name="parameters"></a>매개 변수

*lpszIndex*<br/>
설정할 인덱스의 이름을 포함 하는 포인터입니다.

### <a name="remarks"></a>설명

기본 테이블의 레코드는 특정 순서로 저장 되지 않습니다. 인덱스를 설정 하면 데이터베이스에서 반환 되는 레코드의 순서가 변경 되지만 레코드가 저장 되는 순서에는 영향을 주지 않습니다. 지정 된 인덱스가 이미 정의 되어 있어야 합니다. 존재 하지 않는 인덱스 개체를 사용 하려고 하거나 [Seek](#seek)를 호출할 때 인덱스를 설정 하지 않은 경우 MFC는 예외를 throw 합니다.

[CDaoTableDef:: CreateIndex](../../mfc/reference/cdaotabledef-class.md#createindex) 를 호출 하 고 [CDaoTableDef:: Append](../../mfc/reference/cdaotabledef-class.md#append)를 호출한 다음 레코드 집합을 다시 열어 기본 테이블 정의의 Indexes 컬렉션에 새 인덱스를 추가 하 여 테이블에 대 한 새 인덱스를 만들 수 있습니다.

테이블 형식 레코드 집합에서 반환 된 레코드는 기본 테이블 정의에 대해 정의 된 인덱스만 정렬할 수 있습니다. 다른 순서로 레코드를 정렬 하기 위해 [CDaoRecordset:: m_strSort](#m_strsort)에 저장 된 SQL **ORDERBY** 절을 사용 하 여 다이너셋 형식 또는 스냅숏 형식 레코드 집합을 열 수 있습니다.

관련 정보는 DAO 도움말의 "인덱스 개체" 및 정의 "현재 인덱스" 항목을 참조 하십시오.

## <a name="cdaorecordsetsetfielddirty"></a><a name="setfielddirty"></a> CDaoRecordset:: SetFieldDirty

이 멤버 함수를 호출 하 여 레코드 집합의 필드 데이터 멤버에 변경 되거나 변경 되지 않은 것으로 플래그를 지정 합니다.

```cpp
void SetFieldDirty(
    void* pv,
    BOOL bDirty = TRUE);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
레코드 집합 또는 NULL에 있는 필드 데이터 멤버의 주소를 포함 합니다. NULL 인 경우 레코드 집합의 모든 필드 데이터 멤버에 플래그가 지정 됩니다. C + + NULL은 데이터베이스 용어에서 Null과 같지 않습니다 .이는 "값이 없습니다."를 의미 합니다.

*bDirty*<br/>
필드 데이터 멤버를 "더티" (변경 됨)로 플래그를 지정 하려면 TRUE입니다. 필드 데이터 멤버에 "clean" (변경 되지 않음)으로 플래그를 지정 하려면 FALSE로 설정 합니다.

### <a name="remarks"></a>설명

필드를 변경 되지 않은 것으로 표시 하면 필드가 업데이트 되지 않습니다.

이 프레임 워크는 변경 된 필드 데이터 멤버를 표시 하 여 DAO 레코드 필드 교환 (DFX) 메커니즘에 의해 데이터 원본의 레코드에 기록 되도록 합니다. 필드의 값을 변경 하면 일반적으로 필드가 자동으로 설정 되므로 직접 호출할 필요가 거의 `SetFieldDirty` 없지만 필드 데이터 멤버의 값에 관계 없이 열이 명시적으로 업데이트 되거나 삽입 되도록 할 수도 있습니다. 또한 DFX 메커니즘은 PSEUDONULL 사용을 사용 합니다. 자세한 내용은 [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)를 참조 하세요.

이중 버퍼링 메커니즘이 사용 되지 않는 경우 필드의 값을 변경 해도 필드가 더티로 자동 설정 되지 않습니다. 이 경우 필드를 더티로 명시적으로 설정 해야 합니다. [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) 에 포함 된 플래그는이 자동 필드 검사를 제어 합니다.

> [!NOTE]
> [Edit](#edit) 또는 [AddNew](#addnew)를 호출한 후에만이 멤버 함수를 호출 합니다.

함수의 첫 번째 인수에 NULL을 사용 하면 `outputColumn` 의 **param** 필드가 아닌 모든 필드에 함수가 적용 됩니다 `CDaoFieldExchange` . 예를 들어

[!code-cpp[NVC_MFCDatabase#6](../../mfc/codesnippet/cpp/cdaorecordset-class_6.cpp)]

`outputColumn`필드만 NULL로 설정 됩니다. **param** 필드는 영향을 받지 않습니다.

**매개 변수** 를 사용 하려면 작업할 개별 **매개** 변수의 실제 주소를 제공 해야 합니다. 예를 들어 다음과 같습니다.

[!code-cpp[NVC_MFCDatabase#7](../../mfc/codesnippet/cpp/cdaorecordset-class_7.cpp)]

즉, 필드를 사용할 수 있는 것 처럼 모든 **param** 필드를 NULL로 설정할 수 없습니다 `outputColumn` .

`SetFieldDirty` 는를 통해 구현 됩니다 `DoFieldExchange` .

## <a name="cdaorecordsetsetfieldnull"></a><a name="setfieldnull"></a> CDaoRecordset:: SetFieldNull

이 멤버 함수를 호출 하 여 레코드 집합의 필드 데이터 멤버에 Null (값 없음) 또는 Null이 아닌 값으로 플래그를 지정 합니다.

```cpp
void SetFieldNull(
    void* pv,
    BOOL bNull = TRUE);
```

### <a name="parameters"></a>매개 변수

*pv*<br/>
레코드 집합 또는 NULL에 있는 필드 데이터 멤버의 주소를 포함 합니다. NULL 인 경우 레코드 집합의 모든 필드 데이터 멤버에 플래그가 지정 됩니다. C + + NULL은 데이터베이스 용어에서 Null과 같지 않습니다 .이는 "값이 없습니다."를 의미 합니다.

*bNull*<br/>
필드 데이터 멤버에 값이 없는 것으로 플래그가 지정 되는 경우 0이 아닌 값 (Null)입니다. 필드 데이터 멤버가 Null이 아닌 것으로 플래그가 지정 되 면 0이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

`SetFieldNull` 는 메커니즘에서 바인딩된 필드에 사용 됩니다 `DoFieldExchange` .

레코드 집합에 새 레코드를 추가 하면 처음에는 모든 필드 데이터 멤버가 Null 값으로 설정 되 고 "더티" (변경 됨)로 플래그가 지정 됩니다. 데이터 원본에서 레코드를 검색 하는 경우 해당 열의 열 값이 이미 있거나 Null입니다. 필드를 Null로 설정 하는 것이 적절 하지 않은 경우 [CDaoException](../../mfc/reference/cdaoexception-class.md) 이 throw 됩니다.

예를 들어, 이중 버퍼링 메커니즘을 사용 하는 경우, 예를 들어 현재 레코드의 필드를 값이 없는 것으로 지정 하려는 경우에는 `SetFieldNull` *BNULL* 을 TRUE로 설정 하 여를 호출 하 여 Null로 플래그를 지정 합니다. 이전에 Null로 표시 된 필드에 값을 지정 하려면 새 값을 설정 하기만 하면 됩니다. 을 사용 하 여 Null 플래그를 제거할 필요는 없습니다 `SetFieldNull` . 필드가 Null 일 수 있는지 여부를 확인 하려면 [IsFieldNullable](#isfieldnullable)를 호출 합니다.

이중 버퍼링 메커니즘을 사용 하지 않는 경우 필드의 값을 변경 해도 필드가 더티로 자동 설정 되 고 Null이 아닌 값으로 설정 됩니다. 필드를 변경 하 고 Null이 아닌 필드를 구체적으로 설정 해야 합니다. [M_bCheckCacheForDirtyFields](#m_bcheckcachefordirtyfields) 에 포함 된 플래그는이 자동 필드 검사를 제어 합니다.

DFX 메커니즘에서는 PSEUDONULL 사용을 사용 합니다. 자세한 내용은 [CDaoFieldExchange:: m_nOperation](../../mfc/reference/cdaofieldexchange-class.md#m_noperation)를 참조 하세요.

> [!NOTE]
> [Edit](#edit) 또는 [AddNew](#addnew)를 호출한 후에만이 멤버 함수를 호출 합니다.

함수의 첫 번째 인수에 NULL을 사용 하면 함수는 `outputColumn` 의 **param** 필드가 아닌 필드에만 적용 됩니다 `CDaoFieldExchange` . 예를 들어

[!code-cpp[NVC_MFCDatabase#8](../../mfc/codesnippet/cpp/cdaorecordset-class_8.cpp)]

`outputColumn`필드만 NULL로 설정 됩니다. **param** 필드는 영향을 받지 않습니다.

## <a name="cdaorecordsetsetfieldvalue"></a><a name="setfieldvalue"></a> CDaoRecordset:: SetFieldValue

이 멤버 함수를 호출 하 여 필드 값을 서 수 위치로 설정 하거나 문자열의 값을 변경 하 여 설정 합니다.

```cpp
virtual void SetFieldValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);

virtual void SetFieldValue(
    int nIndex,
    const COleVariant& varValue);

void SetFieldValue(
    LPCTSTR lpszName,
    LPCTSTR lpszValue);

void SetFieldValue(
    int nIndex,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
필드 이름을 포함 하는 문자열에 대 한 포인터입니다.

*varValue*<br/>
필드 내용의 값을 포함 하는 [COleVariant](../../mfc/reference/colevariant-class.md) 개체에 대 한 참조입니다.

*nIndex*<br/>
레코드 집합의 Fields 컬렉션에 있는 필드의 서 수 위치 (0부터 시작)를 나타내는 정수입니다.

*lpszValue*<br/>
필드 내용의 값을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`SetFieldValue`및 [GetFieldValue](#getfieldvalue) 를 사용 하 여 [DoFieldExchange](#dofieldexchange) 메커니즘을 사용 하 여 열을 정적으로 바인딩하지 않고 런타임에 필드를 동적으로 바인딩합니다.

유니코드 레코드 집합을 만들지 않는 경우 매개 변수를 포함 하지 않는 형식을 사용 해야 합니다 `SetFieldValue` `COleVariant` . 그렇지 않으면 `COleVariant` 개체를 명시적으로 ANSI로 선언 해야 합니다. 이 작업을 수행 하려면 *vtSrc* 가 (ANSI)로 설정 된 생성자의 [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** `VT_BSTRT` 또는 `COleVariant` *lpszSrc* 가로 설정 된 [setstring](../../mfc/reference/colevariant-class.md#setstring)**(** *vtSrc* **,** *vtSrc* **)** 함수를 사용 합니다 `VT_BSTRT` .

관련 내용은 DAO 도움말의 "Field Object" 및 "Value Property" 항목을 참조 하십시오.

## <a name="cdaorecordsetsetfieldvaluenull"></a><a name="setfieldvaluenull"></a> CDaoRecordset:: SetFieldValueNull

이 멤버 함수를 호출 하 여 필드를 Null 값으로 설정 합니다.

```cpp
void SetFieldValueNull(int nIndex);
void SetFieldValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0부터 시작 하는 인덱스 조회를 위해 레코드 집합에 있는 필드의 인덱스입니다.

*lpszName*<br/>
이름으로 조회 하기 위한 레코드 집합의 필드 이름입니다.

### <a name="remarks"></a>설명

C + + NULL은 Null과 같지 않습니다 .이는 데이터베이스 용어에서 "값을 갖지 않습니다."를 의미 합니다.

관련 내용은 DAO 도움말의 "Field Object" 및 "Value Property" 항목을 참조 하십시오.

## <a name="cdaorecordsetsetlockingmode"></a><a name="setlockingmode"></a> CDaoRecordset:: SetLockingMode

이 멤버 함수를 호출 하 여 레코드 집합의 잠금 유형을 설정 합니다.

```cpp
void SetLockingMode(BOOL bPessimistic);
```

### <a name="parameters"></a>매개 변수

*bPessimistic*<br/>
잠금 유형을 나타내는 플래그입니다.

### <a name="remarks"></a>설명

비관적 잠금이 적용 되 면 멤버 함수를 호출 하는 즉시 편집 중인 레코드를 포함 하는 2K 페이지가 잠깁니다 `Edit` . `Update`또는 `Close` 멤버 함수 또는 이동 또는 찾기 작업 중 하나를 호출 하면 페이지 잠금이 해제 됩니다.

낙관적 잠금이 적용 되 면 레코드를 포함 하는 2K 페이지가 멤버 함수를 사용 하 여 레코드를 업데이트 하는 동안에만 잠깁니다 `Update` .

페이지가 잠겨 있는 경우 다른 사용자가 동일한 페이지에서 레코드를 편집할 수 없습니다. 를 호출 하 `SetLockingMode` 고 0이 아닌 값을 전달 하 고 다른 사용자에 게 이미 잠긴 페이지가 있으면를 호출할 때 예외가 throw 됩니다 `Edit` . 다른 사용자는 잠긴 페이지에서 데이터를 읽을 수 있습니다.

`SetLockingMode`0 값을 사용 하 여를 호출 하 고 `Update` 페이지가 다른 사용자에 의해 잠겨 있는 동안 나중에를 호출 하는 경우 예외가 발생 합니다. 다른 사용자가 변경한 레코드를 확인 하 고 변경 내용을 잃지 `SetBookmark` 않기 위해 현재 레코드의 책갈피 값을 사용 하 여 멤버 함수를 호출 합니다.

ODBC 데이터 원본으로 작업할 때 잠금 모드는 항상 낙관적입니다.

## <a name="cdaorecordsetsetparamvalue"></a><a name="setparamvalue"></a> CDaoRecordset:: SetParamValue

런타임에 레코드 집합에서 매개 변수의 값을 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
virtual void SetParamValue(
    int nIndex,
    const COleVariant& varValue);

virtual void SetParamValue(
    LPCTSTR lpszName,
    const COleVariant& varValue);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
Querydef의 Parameters 컬렉션에 있는 매개 변수의 숫자 위치입니다.

*var*<br/>
설정할 값입니다. 설명을 참조 하세요.

*lpszName*<br/>
값을 설정 하려는 매개 변수의 이름입니다.

### <a name="remarks"></a>설명

매개 변수는 레코드 집합의 SQL 문자열의 일부로 이미 설정 되어 있어야 합니다. 이름 또는 컬렉션의 인덱스 위치를 사용 하 여 매개 변수에 액세스할 수 있습니다.

개체로 설정할 값을 지정 합니다 `COleVariant` . 개체에서 원하는 값 및 형식을 설정 하는 방법에 대 한 자세한 내용은 `COleVariant` 클래스 [COleVariant](../../mfc/reference/colevariant-class.md)를 참조 하세요. 유니코드 레코드 집합을 만들지 않는 경우 `COleVariant` 개체는 ANSI로 명시적으로 선언 되어야 합니다. 이 작업을 수행 하려면 *vtSrc* 가 (ANSI)로 설정 된 생성자의 [COleVariant:: COleVariant](../../mfc/reference/colevariant-class.md#colevariant)**(** *lpszSrc* **,** *vtSrc* **)** `VT_BSTRT` 또는 `COleVariant` *lpszSrc* 가로 설정 된 [setstring](../../mfc/reference/colevariant-class.md#setstring)**(** *vtSrc* **,** *vtSrc* **)** 함수를 사용 합니다 `VT_BSTRT` .

## <a name="cdaorecordsetsetparamvaluenull"></a><a name="setparamvaluenull"></a> CDaoRecordset:: SetParamValueNull

이 멤버 함수를 호출 하 여 매개 변수를 Null 값으로 설정 합니다.

```cpp
void SetParamValueNull(int nIndex);
void SetParamValueNull(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
0부터 시작 하는 인덱스 조회를 위해 레코드 집합에 있는 필드의 인덱스입니다.

*lpszName*<br/>
이름으로 조회 하기 위한 레코드 집합의 필드 이름입니다.

### <a name="remarks"></a>설명

C + + NULL은 Null과 같지 않습니다 .이는 데이터베이스 용어에서 "값을 갖지 않습니다."를 의미 합니다.

## <a name="cdaorecordsetsetpercentposition"></a><a name="setpercentposition"></a> CDaoRecordset:: SetPercentPosition

이 멤버 함수를 호출 하 여 레코드 집합의 레코드에 대 한 백분율을 기준으로 레코드 집합 개체에서 현재 레코드의 대략적인 위치를 변경 하는 값을 설정 합니다.

```cpp
void SetPercentPosition(float fPosition);
```

### <a name="parameters"></a>매개 변수

*fPosition*<br/>
0부터 100까지의 숫자입니다.

### <a name="remarks"></a>설명

다이너셋 형식 또는 스냅숏 형식 레코드 집합으로 작업 하는 경우 먼저를 호출 하기 전에 마지막 레코드로 이동 하 여 레코드 집합을 채웁니다 `SetPercentPosition` . 레코드 집합을 완전히 채우기 전에를 호출 하는 경우 `SetPercentPosition` 이동 양은 [getrecordcount](#getrecordcount)의 값으로 표시 되는 액세스 되는 레코드 수를 기준으로 합니다. 을 호출 하 여 마지막 레코드로 이동할 수 있습니다 `MoveLast` .

를 호출 하면 해당 `SetPercentPosition` 값에 해당 하는 대략적인 위치에 있는 레코드가 최신 상태가 됩니다.

> [!NOTE]
> `SetPercentPosition`현재 레코드를 레코드 집합의 특정 레코드로 이동 하기 위해를 호출 하는 것은 권장 되지 않습니다. 대신 [Setbookmark](#setbookmark) 멤버 함수를 호출 합니다.

관련 내용은 DAO 도움말의 "PercentPosition 속성" 항목을 참조 하십시오.

## <a name="cdaorecordsetupdate"></a><a name="update"></a> CDaoRecordset:: Update

또는 멤버 함수를 호출한 후이 멤버 함수를 호출 `AddNew` `Edit` 합니다.

```cpp
virtual void Update();
```

### <a name="remarks"></a>설명

이 호출은 또는 작업을 완료 하는 데 필요 `AddNew` `Edit` 합니다.

및는 모두 `AddNew` `Edit` 데이터 원본에 저장 하기 위해 추가 되거나 편집 된 데이터를 저장 하는 편집 버퍼를 준비 합니다. `Update` 데이터를 저장 합니다. 변경 된 것으로 표시 되거나 검색 된 필드만 업데이트 됩니다.

데이터 원본에서 트랜잭션을 지 원하는 경우 `Update` 트랜잭션에 대 한 호출 및 해당 또는 호출을 수행할 수 있습니다 `AddNew` `Edit` .

> [!CAUTION]
> `Update`또는 중 하나를 먼저 호출 하지 않고를 호출 하면 `AddNew` `Edit` 이 `Update` throw `CDaoException` 됩니다. `AddNew`또는를 호출 하 `Edit` 는 경우 MoveNext를 `Update` 호출 하기 전에 [](#movenext) 를 호출 하거나 레코드 집합 또는 데이터 원본 연결을 닫아야 합니다. 그렇지 않으면 알림 없이 변경 내용이 손실 됩니다.

다중 사용자 환경에서 레코드 집합 개체가 pessimistically 되 면 `Edit` 업데이트가 완료 될 때까지 해당 레코드는 해당 시점에서 잠긴 상태로 유지 됩니다. 레코드 집합이 낙관적으로 잠겨 있으면 레코드는 잠기고 데이터베이스에서 업데이트 되기 직전에 미리 편집 된 레코드와 비교 됩니다. 를 호출한 후에 레코드가 변경 된 경우 `Edit` `Update` 작업이 실패 하 고 MFC에서 예외가 throw 됩니다. 를 사용 하 여 잠금 모드를 변경할 수 있습니다 `SetLockingMode` .

> [!NOTE]
> 낙관적 잠금은 ODBC 및 설치 가능 ISAM과 같은 외부 데이터베이스 형식에서 항상 사용 됩니다.

관련 정보는 DAO 도움말의 "AddNew 메서드", "CancelUpdate 메서드", "Delete 메서드", "LastModified 속성", "업데이트 방법" 및 "EditMode 속성" 항목을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDaoTableDef 클래스](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoWorkspace 클래스](../../mfc/reference/cdaoworkspace-class.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoQueryDef 클래스](../../mfc/reference/cdaoquerydef-class.md)<br/>
