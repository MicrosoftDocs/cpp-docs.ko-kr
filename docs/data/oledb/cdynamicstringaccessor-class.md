---
description: '자세한 정보: CDynamicStringAccessor 클래스'
title: CDynamicStringAccessor 클래스
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: 89ad306242c5fa0a01b0f14673382fade8df128c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97170713"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor 클래스

데이터베이스 스키마(데이터베이스의 내부 구조)에 대해 모를 때 데이터 소스에 액세스할 수 있습니다.

## <a name="syntax"></a>Syntax

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>요구 사항

**헤더**: atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[GetString](#getstring)|지정된 열 데이터를 문자열로 검색합니다.|
|[SetString](#setstring)|지정된 열 데이터를 문자열로 설정합니다.|

## <a name="remarks"></a>설명

[Cdynamicaccessor](../../data/oledb/cdynamicaccessor-class.md) 는 공급자가 보고 하는 네이티브 형식으로 데이터를 요청 하지만 `CDynamicStringAccessor` 은 공급자가 데이터 저장소에서 액세스 하는 모든 데이터를 문자열 데이터로 인출 하도록 요청 합니다. 데이터 저장소의 내용 표시 또는 인쇄와 같이 데이터 저장소의 값을 계산 하지 않아도 되는 간단한 작업에 특히 유용 합니다.

데이터 저장소에 있는 열 데이터의 네이티브 형식은 중요하지 않습니다. 공급자가 데이터 변환을 지원할 수 있는 한 데이터를 문자열 형식으로 제공합니다. 드문 경우지만 공급자가 네이티브 데이터 형식에서 문자열로의 변환을 지원하지 않을 경우에는 요청 호출이 성공 값 DB_S_ERRORSOCCURED를 반환하고, 해당 열의 상태는 DBSTATUS_E_CANTCONVERTVALUE로 변환 문제가 있음을 나타냅니다.

`CDynamicStringAccessor`메서드를 사용 하 여 열 정보를 가져올 수 있습니다. 이 열 정보를 사용 하 여 런타임에 동적으로 접근자를 만들 수 있습니다.

열 정보는이 클래스에서 만들고 관리 하는 버퍼에 저장 됩니다. [GetString](#getstring)를 사용 하 여 버퍼에서 데이터를 가져오거나 [setstring](#setstring)을 사용 하 여 버퍼에 저장 합니다.

동적 접근자 클래스 사용에 대 한 설명 및 예제는 [동적 접근자 사용](../../data/oledb/using-dynamic-accessors.md)을 참조 하세요.

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a> CDynamicStringAccessor:: GetString

지정된 열 데이터를 문자열로 검색합니다.

### <a name="syntax"></a>구문

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 열에서 검색 된 문자열 값에 대 한 포인터입니다. 값은 형식입니다 `BaseType` . _UNICODE 정의 여부에 따라 **CHAR** 또는 **WCHAR** 가 됩니다. 지정 된 열을 찾을 수 없는 경우 NULL을 반환 합니다.

### <a name="remarks"></a>설명

두 번째 재정의 폼은 열 이름을 ANSI 문자열로 사용 합니다. 세 번째 재정의 폼은 열 이름을 유니코드 문자열로 사용 합니다.

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a> CDynamicStringAccessor:: SetString

지정된 열 데이터를 문자열로 설정합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>매개 변수

*nColumn*<br/>
[in] 열 번호입니다. 열 번호는 1로 시작 합니다. 특수 값 0은 책갈피 열 (있는 경우)을 참조 합니다.

*pColumnName*<br/>
진행 열 이름을 포함 하는 문자열에 대 한 포인터입니다.

*data*<br/>
진행 지정 된 열에 쓸 문자열 데이터에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

지정 된 열을 설정할 문자열 값에 대 한 포인터입니다. 값은 형식입니다 `BaseType` . _UNICODE 정의 여부에 따라 **CHAR** 또는 **WCHAR** 가 됩니다.

### <a name="remarks"></a>설명

두 번째 재정의 폼은 열 이름을 ANSI 문자열로 사용 하 고 세 번째 재정의 폼은 열 이름을 유니코드 문자열로 사용 합니다.

0이 아닌 값을 포함 하도록 _SECURE_ATL 정의 된 경우 입력 *데이터* 문자열이 참조 된 데이터 열의 최대 허용 길이 보다 길면 런타임 어설션 오류가 생성 됩니다. 그렇지 않으면 입력 문자열이 허용 되는 최대 길이 보다 길면 입력 문자열이 잘립니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 클래스](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 클래스](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 클래스](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 클래스](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA 클래스](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW 클래스](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor 클래스](../../data/oledb/cxmlaccessor-class.md)
