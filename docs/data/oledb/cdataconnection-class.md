---
title: CDataConnection 클래스
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: c456f4bf5891f550fcd9523fa376333d66e079a6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509100"
---
# <a name="cdataconnection-class"></a>CDataConnection 클래스

데이터 원본에 대 한 연결을 관리 합니다.

## <a name="syntax"></a>구문

```cpp
class CDataConnection
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[CDataConnection](#cdataconnection)|생성자입니다. 개체를 인스턴스화하고 초기화 `CDataConnection` 합니다.|
|[복사](#copy)|기존 데이터 연결의 복사본을 만듭니다.|
|[열기](#open)|초기화 문자열을 사용 하 여 데이터 원본에 대 한 연결을 엽니다.|
|[OpenNewSession](#opennewsession)|현재 연결에 대 한 새 세션을 엽니다.|

### <a name="operators"></a>연산자

| 속성 | 설명 |
|-|-|
|[연산자 BOOL](#op_bool)|현재 세션이 열려 있는지 여부를 확인 합니다.|
|[연산자 bool](#op_bool_ole)|현재 세션이 열려 있는지 여부를 확인 합니다.|
|[operator CDataSource&](#op_cdata_amp)|포함 된 개체에 대 한 참조를 반환 합니다 `CDataSource` .|
|[연산자 CDataSource *](#op_cdata_star)|포함된 `CDataSource` 개체에 대한 포인터를 반환합니다.|
|[연산자 CSession&](#op_csession_amp)|포함 된 개체에 대 한 참조를 반환 합니다 `CSession` .|
|[연산자 CSession*](#op_csession_star)|포함된 `CSession` 개체에 대한 포인터를 반환합니다.|

## <a name="remarks"></a>설명

`CDataConnection` 는 필요한 개체 (데이터 소스 및 세션)와 데이터 소스에 연결할 때 수행 해야 하는 작업의 일부를 캡슐화 하기 때문에 클라이언트를 만드는 데 유용한 클래스입니다.

를 사용 하지 않는 `CDataConnection` 경우 개체를 만들고 `CDataSource` [OpenFromInitializationString](./cdatasource-class.md#openfrominitializationstring) 메서드를 호출한 다음, [Open](./csession-class.md#open) 메서드를 호출한 다음 [CCommand](../../data/oledb/ccommand-class.md) 개체를 만들고 해당 * 메서드를 호출 해야 [CSession](../../data/oledb/csession-class.md) `Open` 합니다.

`CDataConnection`에서는 연결 개체를 만들고 초기화 문자열을 전달한 다음 해당 연결을 사용 하 여 명령을 열어야 합니다. 데이터베이스에 대 한 연결을 반복 해 서 사용 하려는 경우에는 연결을 열어 두는 것이 좋습니다 .이 `CDataConnection` 작업을 수행 하는 편리한 방법을 제공 합니다.

> [!NOTE]
> 여러 세션을 처리 해야 하는 데이터베이스 응용 프로그램을 만드는 경우 [Opennewsession](#opennewsession)을 사용 해야 합니다.

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a> CDataConnection:: CDataConnection

개체를 인스턴스화하고 초기화 `CDataConnection` 합니다.

### <a name="syntax"></a>구문

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>매개 변수

*gid*<br/>
진행 기존 데이터 연결에 대 한 참조입니다.

### <a name="remarks"></a>설명

첫 번째 재정의는 `CDataConnection` 기본 설정을 사용 하 여 새 개체를 만듭니다.

두 번째 재정의는 `CDataConnection` 지정한 데이터 연결 개체와 동일한 설정을 사용 하 여 새 개체를 만듭니다.

## <a name="cdataconnectioncopy"></a><a name="copy"></a> CDataConnection:: Copy

기존 데이터 연결의 복사본을 만듭니다.

### <a name="syntax"></a>구문

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>매개 변수

*gid*<br/>
진행 복사할 기존 데이터 연결에 대 한 참조입니다.

## <a name="cdataconnectionopen"></a><a name="open"></a> CDataConnection:: Open

초기화 문자열을 사용 하 여 데이터 원본에 대 한 연결을 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>매개 변수

*szInitString*<br/>
진행 데이터 원본에 대 한 초기화 문자열입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a> CDataConnection:: OpenNewSession

현재 연결 개체의 데이터 원본을 사용 하 여 새 세션을 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>매개 변수

*세션별*<br/>
[in/out] 새 세션 개체에 대 한 참조입니다.

### <a name="remarks"></a>설명

새 세션은 현재 연결 개체의 포함 된 데이터 원본 개체를 부모로 사용 하 고 데이터 원본과 동일한 모든 정보에 액세스할 수 있습니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a> CDataConnection:: operator BOOL

현재 세션이 열려 있는지 여부를 확인 합니다.

### <a name="syntax"></a>구문

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>설명

**BOOL** (MFC typedef) 값을 반환 합니다. **TRUE** 는 현재 세션이 열려 있음을 의미 합니다. **FALSE** 는 현재 세션이 닫 혔 음을 의미 합니다.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a> CDataConnection:: operator bool (OLE DB)

현재 세션이 열려 있는지 여부를 확인 합니다.

### <a name="syntax"></a>구문

```cpp
operator bool() throw();
```

### <a name="remarks"></a>설명

**`bool`**(C + + 데이터 형식) 값을 반환 합니다. **`true`** 현재 세션이 열려 있음을 의미 합니다. **`false`** 현재 세션이 닫 혔 음을 의미 합니다.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a> CDataConnection:: operator CDataSource&amp;

포함 된 개체에 대 한 참조를 반환 합니다 `CDataSource` .

### <a name="syntax"></a>구문

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>설명

이 연산자는 `CDataSource` `CDataConnection` 참조가 필요한 개체를 전달할 수 있도록 포함 된 개체에 대 한 참조를 반환 합니다 `CDataSource` .

### <a name="example"></a>예제

참조를 사용 하는 함수 (예: 아래)가 있는 경우 `func` `CDataSource` 를 사용 하 여 `CDataSource&` 개체를 전달할 수 있습니다 `CDataConnection` .

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a> CDataConnection:: operator CDataSource *

포함된 `CDataSource` 개체에 대한 포인터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>설명

이 연산자는 `CDataSource` 포인터가 예상되는 위치에 `CDataConnection` 개체를 전달할 수 있게 해주는, 포함된 `CDataSource` 개체에 대한 포인터를 반환합니다.

사용 예는 [Operator CDataSource&](#op_cdata_amp) 를 참조 하세요.

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a> CDataConnection:: operator CSession&amp;

포함 된 개체에 대 한 참조를 반환 합니다 `CSession` .

### <a name="syntax"></a>구문

```cpp
operator const CSession&();
```

### <a name="remarks"></a>설명

이 연산자는 `CSession` `CDataConnection` 참조가 필요한 개체를 전달할 수 있도록 포함 된 개체에 대 한 참조를 반환 합니다 `CSession` .

### <a name="example"></a>예제

참조를 사용 하는 함수 (예: 아래)가 있는 경우 `func` `CSession` 를 사용 하 여 `CSession&` 개체를 전달할 수 있습니다 `CDataConnection` .

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a> CDataConnection:: operator CSession *

포함된 `CSession` 개체에 대한 포인터를 반환합니다.

### <a name="syntax"></a>구문

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>설명

이 연산자는 `CSession` 포인터가 예상되는 위치에 `CDataConnection` 개체를 전달할 수 있게 해주는, 포함된 `CSession` 개체에 대한 포인터를 반환합니다.

### <a name="example"></a>예제

사용 예는 [Operator CSession&](#op_csession_amp) 를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
