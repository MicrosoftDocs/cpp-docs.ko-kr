---
description: '자세히 알아보기: CDaoWorkspace 클래스'
title: CDaoWorkspace 클래스
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: 73236019db3ecf4a79ef93e19a55d909e6e0d61d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247999"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace 클래스

단일 사용자가 로그인부터 로그인까지 암호로 보호되고 명명된 데이터베이스 세션을 관리합니다. DAO는 Office 2013을 통해 지원 됩니다. DAO 3.6은 최종 버전이 며 사용 되지 않는 것으로 간주 됩니다.

## <a name="syntax"></a>구문

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|작업 영역 개체를 생성 합니다. 그런 다음 또는를 호출 `Create` `Open` 합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|새로 만든 작업 영역을 데이터베이스 엔진의 작업 영역 컬렉션에 추가 합니다.|
|[CDaoWorkspace::BeginTrans](#begintrans)|작업 영역에 열려 있는 모든 데이터베이스에 적용 되는 새 트랜잭션을 시작 합니다.|
|[CDaoWorkspace::Close](#close)|작업 영역 및 작업 영역에 포함 된 모든 개체를 닫습니다. 보류 중인 트랜잭션을 롤백합니다.|
|[CDaoWorkspace::CommitTrans](#committrans)|현재 트랜잭션을 완료 하 고 변경 내용을 저장 합니다.|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|데이터베이스를 압축 하거나 복제 합니다.|
|[CDaoWorkspace:: Create](#create)|새 DAO 작업 영역 개체를 만듭니다.|
|[CDaoWorkspace:: GetDatabaseCount](#getdatabasecount)|작업 영역의 데이터베이스 컬렉션에 있는 DAO 데이터베이스 개체의 수를 반환 합니다.|
|[CDaoWorkspace::GetDatabaseInfo](#getdatabaseinfo)|작업 영역 데이터베이스 컬렉션에 정의 된 지정 된 DAO 데이터베이스에 대 한 정보를 반환 합니다.|
|[CDaoWorkspace::GetIniPath](#getinipath)|Windows 레지스트리에서 Microsoft Jet 데이터베이스 엔진 초기화 설정의 위치를 반환 합니다.|
|[CDaoWorkspace::GetIsolateODBCTrans](#getisolateodbctrans)|데이터 원본에 대 한 다중 연결을 통해 동일한 ODBC 데이터 원본을 포함 하는 여러 트랜잭션을 격리 하는지 여부를 나타내는 값을 반환 합니다.|
|[CDaoWorkspace::GetLoginTimeout](#getlogintimeout)|사용자가 ODBC 데이터베이스에 로그인 하려고 할 때 오류가 발생 하기 전 까지의 시간 (초)을 반환 합니다.|
|[CDaoWorkspace:: GetName](#getname)|작업 영역 개체에 대 한 사용자 정의 이름을 반환 합니다.|
|[CDaoWorkspace:: GetUserName](#getusername)|작업 영역을 만들 때 지정한 사용자 이름을 반환 합니다. 작업 영역 소유자의 이름입니다.|
|[CDaoWorkspace::GetVersion](#getversion)|작업 영역과 연결 된 데이터베이스 엔진의 버전을 포함 하는 문자열을 반환 합니다.|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|데이터베이스 엔진의 작업 영역 컬렉션에 있는 DAO 작업 영역 개체의 수를 반환 합니다.|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|데이터베이스 엔진의 작업 영역 컬렉션에 정의 된 지정 된 DAO 작업 영역에 대 한 정보를 반환 합니다.|
|[CDaoWorkspace::Idle](#idle)|데이터베이스 엔진이 백그라운드 작업을 수행할 수 있도록 합니다.|
|[CDaoWorkspace::IsOpen](#isopen)|작업 영역이 열려 있으면 0이 아닌 값을 반환 합니다.|
|[CDaoWorkspace::Open](#open)|DAO의 기본 작업 영역에 연결 된 작업 영역 개체를 명시적으로 엽니다.|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|손상 된 데이터베이스를 복구 하려고 시도 합니다.|
|[CDaoWorkspace:: Rollback](#rollback)|현재 트랜잭션을 종료 하 고 변경 내용을 저장 하지 않습니다.|
|[CDaoWorkspace::SetDefaultPassword](#setdefaultpassword)|작업 영역 개체가 특정 암호 없이 생성 될 때 데이터베이스 엔진에서 사용 하는 암호를 설정 합니다.|
|[CDaoWorkspace::SetDefaultUser](#setdefaultuser)|작업 영역 개체가 특정 사용자 이름 없이 생성 될 때 데이터베이스 엔진에서 사용 하는 사용자 이름을 설정 합니다.|
|[CDaoWorkspace::SetIniPath](#setinipath)|Windows 레지스트리에서 Microsoft Jet 데이터베이스 엔진 초기화 설정의 위치를 설정 합니다.|
|[CDaoWorkspace::SetIsolateODBCTrans](#setisolateodbctrans)|데이터 원본에 대 한 여러 연결을 강제 적용 하 여 동일한 ODBC 데이터 원본을 포함 하는 여러 트랜잭션을 격리 하는지 여부를 지정 합니다.|
|[CDaoWorkspace::SetLoginTimeout](#setlogintimeout)|사용자가 ODBC 데이터 원본에 로그인 할 때 오류가 발생 하기 전 까지의 시간 (초)을 설정 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CDaoWorkspace::m_pDAOWorkspace](#m_pdaoworkspace)|기본 DAO 작업 영역 개체를 가리킵니다.|

## <a name="remarks"></a>설명

대부분의 경우에는 여러 작업 영역이 필요 하지 않으며 명시적 작업 영역 개체를 만들 필요가 없습니다. 데이터베이스 및 레코드 집합 개체를 열면 DAO의 기본 작업 영역을 사용 합니다. 그러나 필요한 경우 추가 작업 영역 개체를 만들어 한 번에 여러 세션을 실행할 수 있습니다. 각 작업 영역 개체는 자체 데이터베이스 컬렉션에 여러 개의 열려 있는 데이터베이스 개체를 포함할 수 있습니다. MFC에서 작업 영역은 주로 트랜잭션 관리자 이며, 같은 "트랜잭션 공간"에 열려 있는 데이터베이스 집합을 모두 지정 합니다.

> [!NOTE]
> DAO 데이터베이스 클래스는 ODBC (Open Database Connectivity)를 기반으로 하는 MFC 데이터베이스 클래스와는 다릅니다. 모든 DAO 데이터베이스 클래스 이름에는 "CDao" 접두사가 있습니다. 일반적으로 DAO 기반의 MFC 클래스는 ODBC를 기반으로 하는 MFC 클래스 보다 더 사용할 수 있습니다. DAO 기반 클래스는 ODBC 드라이버를 포함 하 여 Microsoft Jet 데이터베이스 엔진을 통해 데이터에 액세스 합니다. 또한 DAO를 직접 호출할 필요 없이 데이터베이스를 만들고 클래스를 통해 테이블 및 필드를 추가 하는 등의 DDL (데이터 정의 언어) 작업을 지원 합니다.

## <a name="capabilities"></a>기능

클래스 `CDaoWorkspace` 는 다음을 제공 합니다.

- 필요한 경우 데이터베이스 엔진을 초기화 하 여 만든 기본 작업 영역에 명시적으로 액세스 합니다. 일반적으로 데이터베이스 및 레코드 집합 개체를 만들어 DAO의 기본 작업 영역을 암시적으로 사용 합니다.

- 작업 영역에 열려 있는 모든 데이터베이스에 트랜잭션을 적용 하는 트랜잭션 공간. 별도의 트랜잭션 공간을 관리 하는 추가 작업 영역을 만들 수 있습니다.

- 기본 Microsoft Jet 데이터베이스 엔진의 다양 한 속성에 대 한 인터페이스입니다 (정적 멤버 함수 참조). 작업 영역 열기 또는 만들기 또는 열기 또는 만들기 전에 정적 멤버 함수 호출에서 데이터베이스 엔진을 초기화 합니다.

- 추가 된 모든 활성 작업 영역을 저장 하는 데이터베이스 엔진의 작업 영역 컬렉션에 대 한 액세스입니다. 또한 작업 영역을 만들고 컬렉션에 추가 하지 않고도 작업 영역을 만들 수 있습니다.

## <a name="security"></a>보안

MFC는 보안 제어에 사용 되는 DAO의 사용자 및 그룹 컬렉션을 구현 하지 않습니다. DAO의 이러한 측면이 필요한 경우 DAO 인터페이스에 대 한 직접 호출을 통해 직접 프로그래밍 해야 합니다. 자세한 내용은 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)을 참조 하세요.

## <a name="usage"></a>사용

클래스를 사용 하 여 다음을 수행할 수 있습니다 `CDaoWorkspace` .

- 기본 작업 영역을 명시적으로 엽니다.

   일반적으로 기본 작업 영역을 사용 하는 것은 암시적 이며, new [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 또는 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 열 때입니다. 그러나 데이터베이스 엔진 속성이 나 작업 영역 컬렉션에 액세스 하기 위해 명시적으로 액세스 해야 할 수도 있습니다. 아래의 "기본 작업 영역의 암시적 사용"을 참조 하세요.

- 새 작업 영역을 만듭니다. 작업 영역 컬렉션에 추가 하려면 [Append](#append) 를 호출 합니다.

- 작업 영역 컬렉션에서 기존 작업 영역을 엽니다.

작업 영역 컬렉션에 없는 새 작업 영역을 만드는 작업은 [Create](#create) member 함수 아래에 설명 되어 있습니다. 작업 영역 개체는 tso 엔진 세션 사이에서 지속 되지 않습니다. 응용 프로그램이 정적으로 MFC를 연결 하는 경우 응용 프로그램을 종료 하면 데이터베이스 엔진이 초기화 하지 않습니다. 응용 프로그램이 MFC에 동적으로 연결 되는 경우에는 MFC DLL이 언로드될 때 데이터베이스 엔진이 초기화 되지 않습니다.

기본 작업 영역을 명시적으로 열거나 작업 영역 컬렉션에서 기존 작업 영역을 여는 것은 [Open](#open) 멤버 함수 아래에 설명 되어 있습니다.

[Close](#close) 멤버 함수를 사용 하 여 작업 영역을 닫아 작업 영역 세션을 종료 합니다. `Close` 이전에 닫지 않은 데이터베이스를 모두 닫고 커밋되지 않은 트랜잭션을 롤백합니다.

## <a name="transactions"></a>트랜잭션

DAO는 작업 영역 수준에서 트랜잭션을 관리 합니다. 따라서 열려 있는 여러 데이터베이스가 있는 작업 영역에서 트랜잭션은 모든 데이터베이스에 적용 됩니다. 예를 들어 두 데이터베이스에 커밋되지 않은 업데이트가 있고 [CommitTrans](#committrans)를 호출 하면 모든 업데이트가 커밋됩니다. 트랜잭션을 단일 데이터베이스로 제한 하려는 경우이에 대 한 별도의 작업 영역 개체가 필요 합니다.

## <a name="implicit-use-of-the-default-workspace"></a>기본 작업 영역의 암시적 사용

MFC는 다음과 같은 상황에서 암시적으로 DAO의 기본 작업 영역을 사용 합니다.

- 새 `CDaoDatabase` 개체를 만들었지만 기존 개체를 통해이를 수행 하지 않는 경우 `CDaoWorkspace` MFC는 DAO의 기본 작업 영역에 해당 하는 임시 작업 영역 개체를 만듭니다. 여러 데이터베이스에 대해이 작업을 수행 하는 경우 모든 데이터베이스 개체가 기본 작업 영역에 연결 됩니다. 데이터 멤버를 통해 데이터베이스의 작업 영역에 액세스할 수 있습니다 `CDaoDatabase` .

- 마찬가지로 `CDaoRecordset` 개체에 대 한 포인터를 제공 하지 않고 개체를 만드는 경우에는 `CDaoDatabase` MFC에서 임시 데이터베이스 개체 및 임시 작업 영역 개체를 확장 하 여 만듭니다. 데이터 멤버를 통해 레코드 집합의 데이터베이스 및 간접적으로 작업 영역에 액세스할 수 있습니다 `CDaoRecordset` .

## <a name="other-operations"></a>기타 작업

또한 손상 된 데이터베이스를 복구 하거나 데이터베이스를 압축 하는 등의 다른 데이터베이스 작업도 제공 됩니다.

DAO를 직접 호출 하는 방법과 DAO 보안에 대 한 자세한 내용은 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)을 참조 하십시오.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>요구 사항

**헤더:** afxdao

## <a name="cdaoworkspaceappend"></a><a name="append"></a> CDaoWorkspace:: Append

[Create](#create)를 호출한 후이 멤버 함수를 호출 합니다.

```
virtual void Append();
```

### <a name="remarks"></a>설명

`Append` 새로 만든 작업 영역 개체를 데이터베이스 엔진의 작업 영역 컬렉션에 추가 합니다. 작업 영역은 데이터베이스 엔진 세션 간에 지속 되지 않습니다. 메모리에만 저장 되 고 디스크에는 저장 되지 않습니다. 작업 영역을 추가할 필요는 없습니다. 그렇지 않은 경우에는 계속 사용할 수 있습니다.

추가 된 작업 영역은 [Close](#close) 멤버 함수를 호출할 때까지 작업 영역 컬렉션에서 활성 상태의 활성 상태로 유지 됩니다.

관련 내용은 DAO 도움말의 "Append 메서드" 항목을 참조 하십시오.

## <a name="cdaoworkspacebegintrans"></a><a name="begintrans"></a> CDaoWorkspace:: BeginTrans

이 멤버 함수를 호출 하 여 트랜잭션을 시작 합니다.

```cpp
void BeginTrans();
```

### <a name="remarks"></a>설명

를 호출한 후에 `BeginTrans` 는 트랜잭션을 커밋할 때 데이터 또는 데이터베이스 구조에 대 한 업데이트를 적용 합니다. 작업 영역에서 단일 트랜잭션 공간을 정의 하기 때문에 트랜잭션은 작업 영역에서 열려 있는 모든 데이터베이스에 적용 됩니다. 트랜잭션을 완료 하는 방법에는 두 가지가 있습니다.

- [CommitTrans](#committrans) 멤버 함수를 호출 하 여 트랜잭션을 커밋하고 데이터 원본에 변경 내용을 저장 합니다.

- 또는 [Rollback](#rollback) 멤버 함수를 호출 하 여 트랜잭션을 취소 합니다.

트랜잭션이 보류 중인 동안 작업 영역 개체 또는 데이터베이스 개체를 닫아도 보류 중인 모든 트랜잭션이 롤백됩니다.

한 ODBC 데이터 원본에서 다른 ODBC 데이터 원본의 트랜잭션을 격리 해야 하는 경우 [SetIsolateODBCTrans](#setisolateodbctrans) 멤버 함수를 참조 하세요.

## <a name="cdaoworkspacecdaoworkspace"></a><a name="cdaoworkspace"></a> CDaoWorkspace::CDaoWorkspace

`CDaoWorkspace` 개체를 생성합니다.

```
CDaoWorkspace();
```

### <a name="remarks"></a>설명

C + + 개체를 생성 한 후에는 두 가지 옵션이 있습니다.

- 개체의 [Open](#open) 멤버 함수를 호출 하 여 기본 작업 영역을 열거나 작업 영역 컬렉션에서 기존 개체를 엽니다.

- 또는 개체의 [create](#create) member 함수를 호출 하 여 새 DAO 작업 영역 개체를 만듭니다. 이렇게 하면 개체를 통해 참조할 수 있는 새 작업 영역 세션이 명시적으로 시작 됩니다 `CDaoWorkspace` . 를 호출한 후 `Create` 작업 영역을 데이터베이스 엔진의 작업 영역 컬렉션에 추가 하려면 [추가](#append) 를 호출할 수 있습니다.

개체를 명시적으로 만들어야 하는 경우에 대 한 자세한 내용은 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md) 의 클래스 개요를 참조 하세요 `CDaoWorkspace` . 일반적으로 작업 영역을 지정 하지 않고 [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) 개체를 열 때 또는 데이터베이스 개체를 지정 하지 않고 [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) 개체를 열 때 생성 된 작업 영역을 암시적으로 사용 합니다. 이러한 방식으로 만들어진 MFC DAO 개체는 DAO의 기본 작업 영역을 사용 하며 한 번 생성 되 고 다시 사용 됩니다.

작업 영역 및 포함 된 개체를 해제 하려면 작업 영역 개체의 [Close](#close) 멤버 함수를 호출 합니다.

## <a name="cdaoworkspaceclose"></a><a name="close"></a> CDaoWorkspace:: Close

이 멤버 함수를 호출 하 여 작업 영역 개체를 닫습니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

열려 있는 작업 영역 개체를 닫으면 기본 DAO 개체가 해제 되 고 작업 영역이 작업 영역 컬렉션의 멤버인 경우 컬렉션에서 제거 됩니다. 호출은 `Close` 바람직한 프로그래밍 습관입니다.

> [!CAUTION]
> 작업 영역 개체를 닫으면 작업 영역에서 열려 있는 데이터베이스를 닫습니다. 이로 인해 데이터베이스에 열려 있는 모든 레코드 집합이 닫히고 보류 중인 편집 내용 또는 업데이트가 롤백됩니다. 관련 내용은 [CDaoDatabase:: close](../../mfc/reference/cdaodatabase-class.md#close), [CDaoRecordset:: close](../../mfc/reference/cdaorecordset-class.md#close), [CDaoTableDef:: Close](../../mfc/reference/cdaotabledef-class.md#close)및 [CDaoQueryDef:: close](../../mfc/reference/cdaoquerydef-class.md#close) 멤버 함수를 참조 하세요.

작업 영역 개체가 영구적이 지 않습니다. 이러한 항목에 대 한 참조가 존재 하는 경우에만 존재 합니다. 즉, 데이터베이스 엔진 세션이 종료 되 면 작업 영역 및 해당 데이터베이스 컬렉션이 지속 되지 않습니다. 작업 영역 및 데이터베이스를 다시 열어 다음 세션을 위해 다시 만들어야 합니다.

관련 정보는 DAO 도움말의 "Close 메서드" 항목을 참조 하십시오.

## <a name="cdaoworkspacecommittrans"></a><a name="committrans"></a> CDaoWorkspace:: CommitTrans

이 멤버 함수를 호출 하 여 트랜잭션을 커밋합니다.-작업 영역에서 하나 이상의 데이터베이스에 대 한 편집 및 업데이트 그룹을 저장 합니다.

```cpp
void CommitTrans();
```

### <a name="remarks"></a>설명

트랜잭션은 [BeginTrans](#begintrans)를 호출 하 여 데이터베이스의 데이터 또는 구조에 대 한 일련의 변경 내용으로 구성 됩니다. 트랜잭션을 완료 하면 커밋하거나 [롤백하여 롤백합니다 (](#rollback)변경 취소) 합니다. 기본적으로 트랜잭션을 사용 하지 않으면 레코드 업데이트가 즉시 커밋됩니다. 를 호출 `BeginTrans` 하면가 호출 될 때까지 업데이트 커밋이 지연 됩니다 `CommitTrans` .

> [!CAUTION]
> 단일 작업 영역 내에서 트랜잭션은 항상 작업 영역에 대해 전역적 이며 하나의 데이터베이스 또는 레코드 집합으로 제한 되지 않습니다. 작업 영역 트랜잭션 내에서 둘 이상의 데이터베이스 또는 레코드 집합에 대 한 작업을 수행 하는 경우는 `CommitTrans` 보류 중인 모든 업데이트를 커밋하고 `Rollback` 해당 데이터베이스 및 레코드 집합에 대 한 모든 작업을 복원 합니다.

보류 중인 트랜잭션이 있는 데이터베이스 또는 작업 영역을 닫으면 트랜잭션이 모두 롤백됩니다.

> [!NOTE]
> 이는 2 단계 커밋 메커니즘이 아닙니다. 하나의 업데이트가 커밋에 실패 하는 경우 다른 업데이트가 계속 커밋됩니다.

## <a name="cdaoworkspacecompactdatabase"></a><a name="compactdatabase"></a> CDaoWorkspace::CompactDatabase

지정 된 Microsoft Jet를 압축 하려면이 멤버 함수를 호출 합니다. MDB) 데이터베이스입니다.

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>매개 변수

*lpszSrcName*<br/>
기존에 닫힌 데이터베이스의 이름입니다. 전체 경로와 파일 이름을 사용할 수 있습니다 (예: "C: \\ \MYDB. MDB ". 파일 이름에 확장명이 있으면 지정 해야 합니다. 네트워크에서 UNC (uniform 명명 규칙)를 지 원하는 경우 " \\ \\ \\ \myserver \\ \MYSHARE \\ \MYDIR \\ \MYDB.와 같은 네트워크 경로를 지정할 수도 있습니다. MDB ". " \\ "은 c + + 이스케이프 문자 이므로 경로 문자열에 이중 백슬래시가 필요 합니다.

*lpszDestName*<br/>
만들고 있는 압축 된 데이터베이스의 전체 경로입니다. *LpszSrcName* 와 함께 네트워크 경로를 지정할 수도 있습니다. *LpszDestName* 인수를 사용 하 여 *lpszSrcName* 와 동일한 데이터베이스 파일을 지정할 수 없습니다.

*lpszPassword*<br/>
암호로 보호 된 데이터베이스를 압축 하려고 할 때 사용 되는 암호입니다. 암호를 사용 하는 버전을 사용 하는 경우 `CompactDatabase` 모든 매개 변수를 제공 해야 합니다. 또한이 매개 변수는 connect 매개 변수 이므로 다음과 같이 특별 한 서식 지정이 필요 합니다. PWD = *lpszPassword*. 예:; PWD = "행복". (선행 세미콜론이 필요 합니다.)

*lpszLocale*<br/>
*LpszDestName* 을 만들기 위한 정렬 순서를 지정 하는 데 사용 되는 문자열 식입니다. (아래 참조)의 기본값을 적용 하 여이 인수를 생략 하는 경우 `dbLangGeneral` 새 데이터베이스의 로캘은 이전 데이터베이스의 로캘과 동일 합니다. 가능한 값은 다음과 같습니다.

- `dbLangGeneral` 영어, 독일어, 프랑스어, 포르투갈어, 이탈리아어 및 현대 스페인어

- `dbLangArabic` 아랍어

- `dbLangCyrillic` 러시아어

- `dbLangCzech` 체코어

- `dbLangDutch` 네덜란드어

- `dbLangGreek` 그리스어

- `dbLangHebrew` 히브리어

- `dbLangHungarian` 헝가리어

- `dbLangIcelandic` 아이슬란드어

- `dbLangNordic` 북유럽어 언어 (Microsoft Jet 데이터베이스 엔진 버전 1.0에만 해당)

- `dbLangNorwdan` 노르웨이어 및 덴마크어

- `dbLangPolish` 폴란드어

- `dbLangSpanish` 전통 스페인어

- `dbLangSwedfin` 스웨덴어 및 핀란드어

- `dbLangTurkish` 터키어

*nOptions*<br/>
대상 데이터베이스 *lpszDestName* 에 대 한 옵션을 하나 이상 나타냅니다. 기본값을 적용 하 여이 인수를 생략 하는 경우 *lpszDestName* 는 *lpszSrcName* 와 동일한 암호화와 동일한 버전을 갖게 됩니다. `dbEncrypt`또는 옵션을 비트 or `dbDecrypt` 연산자를 사용 하는 버전 옵션 중 하 나와 결합할 수 있습니다. 데이터베이스 엔진 버전이 아닌 데이터베이스 형식을 지정 하는 가능한 값은 다음과 같습니다.

- `dbEncrypt` 압축 하는 동안 데이터베이스를 암호화 합니다.

- `dbDecrypt` 압축 하는 동안 데이터베이스의 암호를 해독 합니다.

- `dbVersion10` 압축 하는 동안 Microsoft Jet 데이터베이스 엔진 버전 1.0을 사용 하는 데이터베이스를 만듭니다.

- `dbVersion11` 압축 하는 동안 Microsoft Jet 데이터베이스 엔진 버전 1.1을 사용 하는 데이터베이스를 만듭니다.

- `dbVersion20` 압축 하는 동안 Microsoft Jet 데이터베이스 엔진 버전 2.0을 사용 하는 데이터베이스를 만듭니다.

- `dbVersion30` 압축 하는 동안 Microsoft Jet 데이터베이스 엔진 버전 3.0을 사용 하는 데이터베이스를 만듭니다.

`dbEncrypt`옵션 인수에서 또는를 사용 하 여 `dbDecrypt` 압축 될 때 데이터베이스의 암호를 암호화할지 여부를 지정할 수 있습니다. 암호화 상수를 생략 하거나 및를 모두 포함 하는 `dbDecrypt` 경우 `dbEncrypt` *lpszDestName* 는 *lpszSrcName* 와 동일한 암호화를 갖게 됩니다. Options 인수에서 version 상수 중 하나를 사용 하 여 압축 된 데이터베이스에 대 한 데이터 형식의 버전을 지정할 수 있습니다. 이 상수는 *lpszDestName* 의 데이터 형식 버전에만 영향을 줍니다. 하나의 버전 상수만 지정할 수 있습니다. 버전 상수를 생략 하는 경우 *lpszDestName* 는 *lpszSrcName* 과 동일한 버전을 갖게 됩니다. *LpszDestName* 는 *lpszSrcName* 의 버전 보다 같거나 높은 버전 으로만 압축할 수 있습니다.

> [!CAUTION]
> 데이터베이스가 암호화 되지 않은 경우 사용자/암호 보안을 구현 하는 경우에도 데이터베이스를 구성 하는 이진 디스크 파일을 직접 읽을 수 있습니다.

### <a name="remarks"></a>설명

데이터베이스에서 데이터를 변경 하면 데이터베이스 파일이 조각화 될 수 있으며 필요한 것 보다 더 많은 디스크 공간을 사용할 수 있습니다. 데이터베이스 파일을 조각 모음 하려면 정기적으로 데이터베이스를 압축 해야 합니다. 압축 된 데이터베이스는 일반적으로 더 작습니다. 또한 데이터베이스를 복사 하 고 압축 하는 동안 데이터 형식의 데이터 정렬, 암호화 또는 버전을 변경 하도록 선택할 수 있습니다.

> [!CAUTION]
> `CompactDatabase`멤버 함수는 전체 Microsoft Access 데이터베이스를 한 버전에서 다른 버전으로 올바르게 변환 하지 않습니다. 데이터 형식만 변환 됩니다. 폼 및 보고서와 같은 Microsoft Access 정의 개체는 변환 되지 않습니다. 그러나 데이터는 올바르게 변환 됩니다.

> [!TIP]
> 를 사용 하 여 `CompactDatabase` 데이터베이스 파일을 복사할 수도 있습니다.

데이터베이스를 압축 하는 방법에 대 한 자세한 내용은 DAO 도움말의 "CompactDatabase 메서드" 항목을 참조 하십시오.

## <a name="cdaoworkspacecreate"></a><a name="create"></a> CDaoWorkspace:: Create

새 DAO 작업 영역 개체를 만들어 MFC 개체와 연결 하려면이 멤버 함수를 호출 `CDaoWorkspace` 합니다.

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
새 작업 영역 개체의 이름을 고유 하 게 설정 하는 최대 14 자의 문자열입니다. 이름을 제공 해야 합니다. 관련 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

*lpszUserName*<br/>
작업 영역 소유자의 사용자 이름입니다. 요구 사항은 *lpszDefaultUser* 매개 변수를 사용 하 여 [setdefaultuser](#setdefaultuser) 멤버 함수를 참조 하세요. 관련 정보는 DAO 도움말의 "UserName 속성" 항목을 참조 하십시오.

*lpszPassword*<br/>
새 작업 영역 개체에 대 한 암호입니다. 암호는 최대 14 자까지 가능 하며 ASCII 0 (null)을 제외한 모든 문자를 포함할 수 있습니다. 암호는 대소문자를 구분합니다. 관련 내용은 DAO 도움말에서 "Password 속성" 항목을 참조 하십시오.

### <a name="remarks"></a>설명

전반적인 생성 프로세스는 다음과 같습니다.

1. [CDaoWorkspace](#cdaoworkspace) 개체를 생성 합니다.

1. 개체의 `Create` 멤버 함수를 호출 하 여 기본 DAO 작업 영역을 만듭니다. 작업 영역 이름을 지정 해야 합니다.

1. 데이터베이스 엔진의 작업 영역 컬렉션에 작업 영역을 추가 하려면 필요에 따라 [Append](#append) 를 호출 합니다. 작업 영역을 추가 하지 않고 작업을 수행할 수 있습니다.

호출 후 `Create` 작업 영역 개체는 열린 상태 이며 사용할 준비가 되었습니다. 이후에를 호출 하지 `Open` 않습니다 `Create` . `Create`작업 영역이 이미 작업 영역 컬렉션에 있는 경우에는를 호출 하지 않습니다. `Create` 응용 프로그램에 대해 아직 초기화 되지 않은 경우 데이터베이스 엔진을 초기화 합니다.

## <a name="cdaoworkspacegetdatabasecount"></a><a name="getdatabasecount"></a> CDaoWorkspace:: GetDatabaseCount

이 멤버 함수를 호출 하 여 작업 영역의 데이터베이스 컬렉션에서 DAO 데이터베이스 개체의 수를 검색 합니다 (작업 영역에서 열려 있는 데이터베이스 수).

```
short GetDatabaseCount();
```

### <a name="return-value"></a>반환 값

작업 영역에 열려 있는 데이터베이스의 수입니다.

### <a name="remarks"></a>설명

`GetDatabaseCount` 는 작업 영역의 데이터베이스 컬렉션에 정의 된 모든 데이터베이스를 반복 해야 하는 경우에 유용 합니다. 컬렉션에서 지정 된 데이터베이스에 대 한 정보를 가져오려면 [Getdatabaseinfo](#getdatabaseinfo)를 참조 하세요. 일반적인 사용법은를 호출 하 여 `GetDatabaseCount` 에 대 한 반복 호출에 대 한 루프 인덱스로이 숫자를 사용 하는 것입니다 `GetDatabaseInfo` .

## <a name="cdaoworkspacegetdatabaseinfo"></a><a name="getdatabaseinfo"></a> CDaoWorkspace:: GetDatabaseInfo

작업 영역에 열려 있는 데이터베이스에 대 한 다양 한 종류의 정보를 얻으려면이 멤버 함수를 호출 합니다.

```cpp
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 작업 영역 데이터베이스 컬렉션에 있는 데이터베이스 개체의 인덱스 (0부터 시작)입니다.

*dbinfo*<br/>
요청 된 정보를 반환 하는 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 데이터베이스에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 작업과 함께 여기에 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름, 업데이트 가능, 트랜잭션

- AFX_DAO_SECONDARY_INFO 기본 정보 plus: 버전, 데이터 정렬 순서, 쿼리 제한 시간

- 기본 및 보조 정보 및: 연결 AFX_DAO_ALL_INFO

*lpszName*<br/>
이름으로 조회 하기 위한 데이터베이스 개체의 이름입니다. 이름은 새 작업 영역 개체의 이름을 고유 하 게 하는 최대 14 자의 문자열입니다.

### <a name="remarks"></a>설명

한 버전의 함수를 사용 하 여 인덱스를 기준으로 데이터베이스를 조회할 수 있습니다. 다른 버전에서는 이름을 기준으로 데이터베이스를 조회할 수 있습니다.

*Dbinfo* 에 반환 되는 정보에 대 한 설명은 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하는 경우 모든 이전 수준에 대 한 정보도 얻을 수 있습니다.

## <a name="cdaoworkspacegetinipath"></a><a name="getinipath"></a> CDaoWorkspace::GetIniPath

이 멤버 함수를 호출 하 여 Windows 레지스트리에서 Microsoft Jet 데이터베이스 엔진 초기화 설정의 위치를 가져옵니다.

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>반환 값

레지스트리 위치를 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

이 위치를 사용 하 여 데이터베이스 엔진의 설정에 대 한 정보를 가져올 수 있습니다. 반환 되는 정보는 실제로 레지스트리 하위 키의 이름입니다.

관련 정보는 DAO 도움말의 "IniPath 속성" 및 "데이터 액세스에 대 한 Windows 레지스트리 설정 사용자 지정" 항목을 참조 하십시오.

## <a name="cdaoworkspacegetisolateodbctrans"></a><a name="getisolateodbctrans"></a> CDaoWorkspace::GetIsolateODBCTrans

작업 영역에 대 한 DAO IsolateODBCTrans 속성의 현재 값을 가져오려면이 멤버 함수를 호출 합니다.

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>반환 값

ODBC 트랜잭션이 격리 된 경우 0이 아닌 경우 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

경우에 따라 동일한 ODBC 데이터베이스에서 여러 개의 동시 트랜잭션을 보류 해야 할 수도 있습니다. 이렇게 하려면 각 트랜잭션에 대해 별도의 작업 영역을 열어야 합니다. 각 작업 영역에는 데이터베이스에 대 한 자체 ODBC 연결이 있을 수 있지만이로 인해 시스템 성능이 저하 된다는 점에 유의 하세요. 트랜잭션 격리는 일반적으로 필요 하지 않기 때문에 동일한 사용자가 연 여러 작업 영역 개체의 ODBC 연결은 기본적으로 공유 됩니다.

Microsoft SQL Server와 같은 일부 ODBC 서버는 단일 연결에서 동시 트랜잭션을 허용 하지 않습니다. 이러한 데이터베이스에 대해 보류 중인 한 번에 둘 이상의 트랜잭션을 가져야 하는 경우에는 각 작업 영역에서 IsolateODBCTrans 속성을 열 때마다 TRUE로 설정 합니다. 이렇게 하면 각 작업 영역에 대해 별도의 ODBC 연결을 강제 적용 합니다.

관련 내용은 DAO 도움말의 "IsolateODBCTrans 속성" 항목을 참조 하십시오.

## <a name="cdaoworkspacegetlogintimeout"></a><a name="getlogintimeout"></a> CDaoWorkspace:: GetLoginTimeout

작업 영역에 대 한 DAO LoginTimeout 속성의 현재 값을 가져오려면이 멤버 함수를 호출 합니다.

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>반환 값

ODBC 데이터베이스에 로그인 하려고 할 때 오류가 발생 하기 전 까지의 시간 (초)입니다.

### <a name="remarks"></a>설명

이 값은 ODBC 데이터베이스에 로그인 하려고 할 때 오류가 발생 하기 전 까지의 시간 (초)을 나타냅니다. 기본 LoginTimeout 설정은 20 초입니다. LoginTimeout을 0으로 설정 하면 시간 제한이 발생 하지 않으며 데이터 원본과의 통신이 응답 하지 않을 수 있습니다.

Microsoft SQL Server와 같은 ODBC 데이터베이스에 로그인을 시도 하는 경우 네트워크 오류가 발생 하거나 서버가 실행 되 고 있지 않기 때문에 연결이 실패할 수 있습니다. 기본값 20 초 동안 연결을 대기 하는 대신 데이터베이스 엔진이 오류를 생성 하기 전까지 대기 하는 기간을 지정할 수 있습니다. 서버에 로그인 하는 것은 외부 서버 데이터베이스에서 쿼리를 실행 하는 것과 같은 여러 이벤트의 일부로 암시적으로 수행 됩니다.

관련 내용은 DAO 도움말의 "LoginTimeout 속성" 항목을 참조 하십시오.

## <a name="cdaoworkspacegetname"></a><a name="getname"></a> CDaoWorkspace:: GetName

이 멤버 함수를 호출 하 여 개체의 내부에 있는 DAO 작업 영역 개체의 사용자 정의 이름을 가져옵니다 `CDaoWorkspace` .

```
CString GetName();
```

### <a name="return-value"></a>반환 값

DAO 작업 영역 개체의 사용자 정의 이름을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

이름은 데이터베이스 엔진의 작업 영역 컬렉션에서 이름을 기준으로 DAO 작업 영역 개체에 액세스 하는 데 유용 합니다.

관련 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

## <a name="cdaoworkspacegetusername"></a><a name="getusername"></a> CDaoWorkspace:: GetUserName

이 멤버 함수를 호출 하 여 작업 영역의 소유자 이름을 가져옵니다.

```
CString GetUserName();
```

### <a name="return-value"></a>반환 값

작업 영역 개체의 소유자를 나타내는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

작업 영역 소유자에 대 한 사용 권한을 가져오거나 설정 하려면 DAO를 직접 호출 하 여 사용 권한 속성 설정을 확인 합니다. 사용자가 보유 한 사용 권한을 결정 합니다. 권한으로 작업 하려면 시스템이 필요 합니다. MDA 파일.

DAO를 직접 호출 하는 방법에 대 한 자세한 내용은 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)를 참조 하십시오. 관련 정보는 DAO 도움말의 "UserName 속성" 항목을 참조 하십시오.

## <a name="cdaoworkspacegetversion"></a><a name="getversion"></a> CDaoWorkspace:: GetVersion

사용 중인 Microsoft Jet 데이터베이스 엔진의 버전을 확인 하려면이 멤버 함수를 호출 합니다.

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>반환 값

개체와 연결 된 데이터베이스 엔진의 버전을 나타내는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 입니다.

### <a name="remarks"></a>설명

반환 되는 값은 "major. minor" 형식의 버전 번호를 나타냅니다. 예를 들면 "3.0"입니다. 제품 버전 번호 (예: 3.0)는 버전 번호 (3), 마침표 및 릴리스 번호 (0)로 구성 됩니다.

관련 내용은 DAO 도움말의 "버전 속성" 항목을 참조 하십시오.

## <a name="cdaoworkspacegetworkspacecount"></a><a name="getworkspacecount"></a> CDaoWorkspace::GetWorkspaceCount

이 멤버 함수를 호출 하 여 데이터베이스 엔진의 작업 영역 컬렉션에 있는 DAO 작업 영역 개체의 수를 검색 합니다.

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>반환 값

작업 영역 컬렉션에서 열린 작업 영역 수입니다.

### <a name="remarks"></a>설명

컬렉션에 추가 되지 않은 열려 있는 작업 영역은이 수에 포함 되지 않습니다. `GetWorkspaceCount` 는 작업 영역 컬렉션에 정의 된 모든 작업 영역을 반복 해야 하는 경우에 유용 합니다. 컬렉션에서 지정 된 작업 영역에 대 한 정보를 얻으려면 [GetWorkspaceInfo](#getworkspaceinfo)를 참조 하세요. 일반적인 사용법은를 호출 하 `GetWorkspaceCount` 여 열린 작업 영역 수를 호출한 다음에 대 한 반복 호출에 루프 인덱스로 해당 숫자를 사용 하는 것입니다 `GetWorkspaceInfo` .

## <a name="cdaoworkspacegetworkspaceinfo"></a><a name="getworkspaceinfo"></a> CDaoWorkspace::GetWorkspaceInfo

세션에 열려 있는 작업 영역에 대 한 다양 한 종류의 정보를 얻으려면이 멤버 함수를 호출 합니다.

```cpp
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>매개 변수

*nIndex*<br/>
인덱스를 기준으로 조회 하기 위해 작업 영역 컬렉션에 있는 데이터베이스 개체의 인덱스 (0부터 시작)입니다.

*wkspcinfo*<br/>
요청 된 정보를 반환 하는 [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) 개체에 대 한 참조입니다.

*dwInfoOptions*<br/>
검색할 작업 영역에 대 한 정보를 지정 하는 옵션입니다. 사용할 수 있는 옵션은 함수에서 반환 하는 작업과 함께 여기에 나열 됩니다.

- AFX_DAO_PRIMARY_INFO (기본값) 이름

- AFX_DAO_SECONDARY_INFO 기본 정보 plus: 사용자 이름

- 기본 및 보조 정보를 추가 하 고: ODBCTrans 격리 AFX_DAO_ALL_INFO

*lpszName*<br/>
이름으로 조회할 작업 영역 개체의 이름입니다. 이름은 새 작업 영역 개체의 이름을 고유 하 게 하는 최대 14 자의 문자열입니다.

### <a name="remarks"></a>설명

*Wkspcinfo* 에 반환 되는 정보에 대 한 설명은 [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md) 구조를 참조 하세요. 이 구조에는 위의 정보 항목에 해당 하는 멤버가 포함 되어 *있습니다.* 한 수준에서 정보를 요청 하면 이전 수준에 대 한 정보도 얻을 수 있습니다.

## <a name="cdaoworkspaceidle"></a><a name="idle"></a> CDaoWorkspace:: Idle

`Idle`을 호출 하 여 데이터베이스 엔진에 강력한 데이터 처리로 인해 최신 상태가 아닐 수 있는 백그라운드 작업을 수행할 수 있는 기회를 제공 합니다.

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>매개 변수

*nAction*<br/>
유휴 상태 처리 중에 수행할 작업입니다. 현재 유일 하 게 유효한 동작은 `dbFreeLocks` 입니다.

### <a name="remarks"></a>설명

이는 대부분의 경우에는 레코드 집합의 모든 레코드를 최신 상태로 유지 하는 백그라운드 처리 시간이 충분 하지 않은 다중 사용자, 멀티태스킹 환경에서 주로 적용 됩니다.

> [!NOTE]
> `Idle`Microsoft Jet 데이터베이스 엔진 버전 3.0을 사용 하 여 만든 데이터베이스에는를 호출할 필요가 없습니다. `Idle`이전 버전에서 만든 데이터베이스에만 사용 합니다.

일반적으로 읽기 잠금이 제거 되 고 로컬 다이너셋 형식 recordset 개체의 데이터는 다른 작업 (마우스 이동 포함)이 발생 하지 않는 경우에만 업데이트 됩니다. 정기적으로를 호출 하는 경우 `Idle` 불필요 한 읽기 잠금을 해제 하 여 백그라운드 처리 작업을 처리할 시간을 데이터베이스 엔진에 제공 합니다. 상수를 `dbFreeLocks` 인수로 지정 하면 모든 읽기 잠금이 해제 될 때까지 처리가 지연 됩니다.

응용 프로그램의 여러 인스턴스가 실행 되 고 있지 않으면 단일 사용자 환경에서이 멤버 함수가 필요 하지 않습니다. `Idle`멤버 함수는 데이터베이스 엔진이 데이터를 디스크에 플러시하 며 메모리에 대 한 잠금을 해제 하도록 하 여 다중 사용자 환경에서 성능을 향상 시킬 수 있습니다. 트랜잭션 작업을 수행 하 여 읽기 잠금을 해제할 수도 있습니다.

관련 내용은 DAO 도움말의 "Idle 메서드" 항목을 참조 하십시오.

## <a name="cdaoworkspaceisopen"></a><a name="isopen"></a> CDaoWorkspace:: IsOpen

이 멤버 함수를 호출 하 여 `CDaoWorkspace` 개체가 열려 있는지 여부, 즉 [open](#open) 을 호출 하 여 MFC 개체를 초기화 했는지, 아니면 [Create](#create)를 호출 하 여 MFC 개체를 초기화 했는지 여부를 확인 합니다.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>반환 값

작업 영역 개체가 열려 있으면 0이 아닌 값이 고, 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

열려 있는 상태의 작업 영역에 대 한 멤버 함수를 호출할 수 있습니다.

## <a name="cdaoworkspacem_pdaoworkspace"></a><a name="m_pdaoworkspace"></a> CDaoWorkspace:: m_pDAOWorkspace

기본 DAO 작업 영역 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

기본 DAO 개체에 직접 액세스 해야 하는 경우이 데이터 멤버를 사용 합니다. 이 포인터를 통해 DAO 개체의 인터페이스를 호출할 수 있습니다.

DAO 개체에 직접 액세스 하는 방법에 대 한 자세한 내용은 [Technical Note 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)를 참조 하십시오.

## <a name="cdaoworkspaceopen"></a><a name="open"></a> CDaoWorkspace:: Open

DAO의 기본 작업 영역에 연결 된 작업 영역 개체를 명시적으로 엽니다.

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
열려는 DAO 작업 영역 개체의 이름 (작업 영역 이름을 고유 하 게 하는 최대 14 자의 문자열)입니다. 기본 작업 영역을 명시적으로 열려면 NULL 값을 그대로 적용 합니다. 이름 지정 요구 사항은 [Create](#create) *lpszName* 매개 변수를 참조 하세요. 관련 내용은 DAO 도움말의 "이름 속성" 항목을 참조 하십시오.

### <a name="remarks"></a>설명

개체를 생성 한 후 `CDaoWorkspace` 다음 중 하나를 수행 하려면이 멤버 함수를 호출 합니다.

- 기본 작업 영역을 명시적으로 엽니다. *LpszName* 에 대해 NULL을 전달 합니다.

- `CDaoWorkspace`작업 영역 컬렉션의 구성원 인 기존 개체를 이름으로 엽니다. 기존 작업 영역 개체에 대 한 올바른 이름을 전달 하세요.

`Open` 작업 영역 개체를 열린 상태로 전환 하 고 응용 프로그램에 대해 아직 초기화 되지 않은 경우에도 데이터베이스 엔진을 초기화 합니다.

`CDaoWorkspace`작업 영역을 연 후에는 많은 멤버 함수를 호출할 수 있지만, 데이터베이스 엔진에서 작동 하는 다음 멤버 함수는 c + + 개체를 생성 한 후에를 호출 하기 전에 사용할 수 있습니다 `Open` .

:::row:::
   :::column span="":::
      [만드십시오](#create)\
      [GetIniPath](#getinipath)\
      [GetLoginTimeout](#getlogintimeout)
   :::column-end:::
   :::column span="":::
      [가져오기](#getversion)\
      [유휴 상태](#idle)
   :::column-end:::
   :::column span="":::
      [SetDefaultPassword](#setdefaultpassword)\
      [SetDefaultUser](#setdefaultuser)
   :::column-end:::
   :::column span="":::
      [SetIniPath](#setinipath)\
      [SetLoginTimeout](#setlogintimeout)
   :::column-end:::
:::row-end:::

## <a name="cdaoworkspacerepairdatabase"></a><a name="repairdatabase"></a> CDaoWorkspace::RepairDatabase

Microsoft Jet 데이터베이스 엔진에 액세스 하는 손상 된 데이터베이스를 복구 해야 하는 경우이 멤버 함수를 호출 합니다.

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>매개 변수

*lpszName*<br/>
기존 Microsoft Jet 엔진 데이터베이스 파일의 경로 및 파일 이름입니다. 경로를 생략 하면 현재 디렉터리만 검색 됩니다. 시스템에서 UNC (uniform 명명 규칙)를 지 원하는 경우 " \\ \\ \\ \myserver \\ \MYSHARE \\ \MYDIR \\ \MYDB.와 같은 네트워크 경로를 지정할 수도 있습니다. MDB ". " \\ "은 c + + 이스케이프 문자 이므로 경로 문자열에 이중 백슬래시가 필요 합니다.

### <a name="remarks"></a>설명

복구 하기 전에 *lpszName* 에서 지정한 데이터베이스를 닫아야 합니다. 다중 사용자 환경에서 다른 사용자는 복구 하는 동안 *lpszName* 를 열 수 없습니다. *LpszName* 가 닫혀 있지 않거나 단독 사용에 사용할 수 없는 경우 오류가 발생 합니다.

이 멤버 함수는 불완전 한 쓰기 작업으로 인해 손상 되었을 수 있는 것으로 표시 된 데이터베이스를 복구 하려고 시도 합니다. 정전 또는 컴퓨터 하드웨어 문제로 인해 Microsoft Jet 데이터베이스 엔진을 사용 하는 응용 프로그램이 예기치 않게 닫히는 경우에 발생할 수 있습니다. 작업을 완료 하 고 [Close](../../mfc/reference/cdaodatabase-class.md#close) 멤버 함수를 호출 하거나 일반적인 방법으로 응용 프로그램을 종료 하는 경우 데이터베이스가 손상 되었을 수 있는 것으로 표시 되지 않습니다.

> [!NOTE]
> 데이터베이스를 복구한 후에는 [CompactDatabase](#compactdatabase) 멤버 함수를 사용 하 여 파일을 조각 모음 하 고 디스크 공간을 복구 하는 것도 좋습니다.

데이터베이스를 복구 하는 방법에 대 한 자세한 내용은 DAO 도움말의 "RepairDatabase 메서드" 항목을 참조 하십시오.

## <a name="cdaoworkspacerollback"></a><a name="rollback"></a> CDaoWorkspace:: Rollback

이 멤버 함수를 호출 하 여 현재 트랜잭션을 종료 하 고 작업 영역의 모든 데이터베이스를 트랜잭션이 시작 되기 전의 상태로 복원 합니다.

```cpp
void Rollback();
```

### <a name="remarks"></a>설명

> [!CAUTION]
> 단일 작업 영역 개체 내에서 트랜잭션은 항상 작업 영역에 대해 전역적 이며 하나의 데이터베이스 또는 레코드 집합으로 제한 되지 않습니다. 작업 영역 트랜잭션 내에서 둘 이상의 데이터베이스 또는 레코드 집합에 대 한 작업을 수행 하는 경우는 `Rollback` 해당 데이터베이스 및 레코드 집합에 대 한 모든 작업을 복원 합니다.

보류 중인 트랜잭션을 저장 하거나 롤백하지 않고 작업 영역 개체를 닫으면 트랜잭션이 자동으로 롤백됩니다. [BeginTrans](#begintrans)를 먼저 호출하지 않고 [CommitTrans](#committrans) 및 `Rollback`를 호출하면 오류가 발생합니다.

> [!NOTE]
> 트랜잭션을 시작할 때 데이터베이스 엔진은 워크스테이션의 TEMP 환경 변수로 지정 된 디렉터리에 저장 된 파일에 해당 작업을 기록 합니다. 트랜잭션 로그 파일에서 임시 드라이브의 사용 가능한 저장소를 모두 사용 하는 경우 데이터베이스 엔진을 사용 하면 MFC에서 `CDaoException` (DAO 오류 2004)이 throw 됩니다. 이 시점에서를 호출 하면 결정 되지 않은 `CommitTrans` 작업 수가 커밋되지 않지만 남은 완료 되지 않은 작업이 손실 되며 작업을 다시 시작 해야 합니다. `Rollback`를 호출 하면 트랜잭션 로그가 해제 되 고 트랜잭션의 모든 작업이 롤백됩니다.

## <a name="cdaoworkspacesetdefaultpassword"></a><a name="setdefaultpassword"></a> CDaoWorkspace:: SetDefaultPassword

특정 암호를 사용 하지 않고 작업 영역 개체를 만들 때 데이터베이스 엔진에서 사용 하는 기본 암호를 설정 하려면이 멤버 함수를 호출 합니다.

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>매개 변수

*lpszPassword*<br/>
기본 암호입니다. 암호는 최대 14 자까지 가능 하며 ASCII 0 (null)을 제외한 모든 문자를 포함할 수 있습니다. 암호는 대소문자를 구분합니다.

### <a name="remarks"></a>설명

설정 하는 기본 암호는 호출 후 만든 새 작업 영역에 적용 됩니다. 후속 작업 영역을 만들 때 [만들기](#create) 호출에서 암호를 지정할 필요가 없습니다.

이 멤버 함수를 사용 하려면 다음을 수행 합니다.

1. 개체를 생성 `CDaoWorkspace` 하지만는 호출 하지 않습니다 `Create` .

1. 을 호출 하 `SetDefaultPassword` 고, 원하는 경우 [Setdefaultuser](#setdefaultuser)를 호출 합니다.

1. `Create`암호를 지정 하지 않고이 작업 영역 개체 또는 후속 작업에 대해를 호출 합니다.

기본적으로 DefaultUser 속성은 "admin"으로 설정 되 고 Defaultuser 속성은 빈 문자열 ("")로 설정 됩니다.

보안에 대 한 자세한 내용은 DAO 도움말의 "사용 권한 속성" 항목을 참조 하십시오. 관련 내용은 DAO 도움말의 "DefaultPassword Property" 및 "Defaultpassword Property" 항목을 참조 하십시오.

## <a name="cdaoworkspacesetdefaultuser"></a><a name="setdefaultuser"></a> CDaoWorkspace:: SetDefaultUser

특정 사용자 이름 없이 작업 영역 개체를 만들 때 데이터베이스 엔진에서 사용 하는 기본 사용자 이름을 설정 하려면이 멤버 함수를 호출 합니다.

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>매개 변수

*lpszDefaultUser*<br/>
기본 사용자 이름입니다. 사용자 이름은 1-20 자까지 가능 하며, 영문자, 악센트가 있는 문자, 숫자, 공백, 기호 (예: "(따옴표),/(슬래시), \ (백슬래시), \[ \] (대괄호),: (콜론), &#124; (파이프), \< (less-than sign), > (보다 큼 부호), + (더하기 기호), = (등호))를 포함할 수 있습니다. (세미콜론),, (쉼표), (물음표), \* (별표), 선행 공백 및 제어 문자 (ascii 00 ~ ascii 31). 관련 정보는 DAO 도움말의 "UserName 속성" 항목을 참조 하십시오.

### <a name="remarks"></a>설명

설정한 기본 사용자 이름은 호출 후 만든 새 작업 영역에 적용 됩니다. 후속 작업 영역을 만들 때 [만들기](#create) 호출에서 사용자 이름을 지정할 필요가 없습니다.

이 멤버 함수를 사용 하려면 다음을 수행 합니다.

1. 개체를 생성 `CDaoWorkspace` 하지만는 호출 하지 않습니다 `Create` .

1. 을 호출 하 `SetDefaultUser` 고, 원하는 경우 [Setdefaultpassword](#setdefaultpassword)를 호출 합니다.

1. `Create`사용자 이름을 지정 하지 않고이 작업 영역 개체 또는 후속 작업 영역에 대해를 호출 합니다.

기본적으로 DefaultUser 속성은 "admin"으로 설정 되 고 Defaultuser 속성은 빈 문자열 ("")로 설정 됩니다.

관련 내용은 DAO 도움말의 "DefaultUser Property" 및 "Defaultuser Property" 항목을 참조 하십시오.

## <a name="cdaoworkspacesetinipath"></a><a name="setinipath"></a> CDaoWorkspace::SetIniPath

Microsoft Jet 데이터베이스 엔진에 대 한 Windows 레지스트리 설정의 위치를 지정 하려면이 멤버 함수를 호출 합니다.

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>매개 변수

*lpszRegistrySubkey*<br/>
설치 가능한 ISAM 데이터베이스에 필요한 Microsoft Jet 데이터베이스 엔진 설정 또는 매개 변수의 위치에 대 한 Windows 레지스트리 하위 키의 이름을 포함 하는 문자열입니다.

### <a name="remarks"></a>설명

`SetIniPath`특수 설정을 지정 해야 하는 경우에만를 호출 합니다. 자세한 내용은 DAO 도움말의 "IniPath 속성" 항목을 참조 하십시오.

> [!NOTE]
> 응용 `SetIniPath` 프로그램을 실행할 때가 아닌 응용 프로그램 설치 중에를 호출 합니다. `SetIniPath` 작업 영역, 데이터베이스 또는 레코드 집합을 열기 전에를 호출 해야 합니다. 그렇지 않으면 MFC는 예외를 throw 합니다.

이 메커니즘을 사용 하 여 사용자 제공 레지스트리 설정을 사용 하 여 데이터베이스 엔진을 구성할 수 있습니다. 이 특성의 범위는 응용 프로그램으로 제한 되며 응용 프로그램을 다시 시작 하지 않으면 변경할 수 없습니다.

## <a name="cdaoworkspacesetisolateodbctrans"></a><a name="setisolateodbctrans"></a> CDaoWorkspace::SetIsolateODBCTrans

작업 영역에 대 한 DAO IsolateODBCTrans 속성의 값을 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>매개 변수

*bIsolateODBCTrans*<br/>
ODBC 트랜잭션 격리를 시작 하려면 TRUE를 전달 합니다. ODBC 트랜잭션 격리를 중지 하려면 FALSE를 전달 합니다.

### <a name="remarks"></a>설명

경우에 따라 동일한 ODBC 데이터베이스에서 여러 개의 동시 트랜잭션을 보류 해야 할 수도 있습니다. 이렇게 하려면 각 트랜잭션에 대해 별도의 작업 영역을 열어야 합니다. 각 작업 영역에는 데이터베이스에 대 한 자체 ODBC 연결이 있을 수 있지만이로 인해 시스템 성능이 저하 됩니다. 트랜잭션 격리는 일반적으로 필요 하지 않기 때문에 동일한 사용자가 연 여러 작업 영역 개체의 ODBC 연결은 기본적으로 공유 됩니다.

Microsoft SQL Server와 같은 일부 ODBC 서버는 단일 연결에서 동시 트랜잭션을 허용 하지 않습니다. 이러한 데이터베이스에 대해 보류 중인 한 번에 둘 이상의 트랜잭션을 가져야 하는 경우에는 각 작업 영역에서 IsolateODBCTrans 속성을 열 때마다 TRUE로 설정 합니다. 이렇게 하면 각 작업 영역에 대해 별도의 ODBC 연결을 강제 적용 합니다.

## <a name="cdaoworkspacesetlogintimeout"></a><a name="setlogintimeout"></a> CDaoWorkspace:: SetLoginTimeout

작업 영역에 대 한 DAO LoginTimeout 속성의 값을 설정 하려면이 멤버 함수를 호출 합니다.

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>매개 변수

*nSeconds*<br/>
ODBC 데이터베이스에 로그인 하려고 할 때 오류가 발생 하기 전 까지의 시간 (초)입니다.

### <a name="remarks"></a>설명

이 값은 ODBC 데이터베이스에 로그인 하려고 할 때 오류가 발생 하기 전 까지의 시간 (초)을 나타냅니다. 기본 LoginTimeout 설정은 20 초입니다. LoginTimeout을 0으로 설정 하면 시간 제한이 발생 하지 않으며 데이터 원본과의 통신이 응답 하지 않을 수 있습니다.

Microsoft SQL Server와 같은 ODBC 데이터베이스에 로그인을 시도 하는 경우 네트워크 오류가 발생 하거나 서버가 실행 되 고 있지 않기 때문에 연결이 실패할 수 있습니다. 기본값 20 초 동안 연결을 대기 하는 대신 데이터베이스 엔진이 오류를 생성 하기 전까지 대기 하는 기간을 지정할 수 있습니다. 서버에 대 한 로그온은 외부 서버 데이터베이스에서 쿼리를 실행 하는 것과 같은 여러 이벤트의 일부로 암시적으로 수행 됩니다. 시간 제한 값은 LoginTimeout 속성의 현재 설정에 따라 결정 됩니다.

관련 내용은 DAO 도움말의 "LoginTimeout 속성" 항목을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase 클래스](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset 클래스](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef 클래스](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef 클래스](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException 클래스](../../mfc/reference/cdaoexception-class.md)
