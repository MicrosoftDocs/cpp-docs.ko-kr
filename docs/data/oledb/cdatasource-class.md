---
title: CDataSource 클래스
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: f94cd631f1c6febdc07d53f84803b1203f4116bc
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502538"
---
# <a name="cdatasource-class"></a>CDataSource 클래스

공급자를 통해 데이터 원본에 대 한 연결을 나타내는 OLE DB 데이터 소스 개체에 해당 합니다.

## <a name="syntax"></a>구문

```cpp
class CDataSource
```

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|-|-|
|[닫기](#close)|연결을 닫습니다.|
|[GetInitializationString](#getinitializationstring)|현재 열려 있는 데이터 원본의 초기화 문자열을 검색 합니다.|
|[GetProperties](#getproperties)|연결 된 데이터 원본에 대해 현재 설정 된 속성 값을 가져옵니다.|
|[GetProperty](#getproperty)|연결 된 데이터 소스에 대해 현재 설정 된 단일 속성의 값을 가져옵니다.|
|[열기](#open)|`CLSID`, `ProgID` 또는 `CEnumerator` 호출자가 제공한 모니커를 사용 하 여 공급자 (데이터 원본)에 대 한 연결을 만듭니다.|
|[OpenFromFileName](#openfromfilename)|사용자가 제공한 파일 이름으로 지정된 파일에서 데이터 소스를 엽니다.|
|[OpenFromInitializationString](#openfrominitializationstring)|초기화 문자열로 지정 된 데이터 소스를 엽니다.|
|[OpenWithPromptFileName](#openwithpromptfilename)|사용자가 이전에 만든 데이터 연결 파일을 선택 하 여 해당 데이터 원본을 열 수 있도록 허용 합니다.|
|[OpenWithServiceComponents](#openwithservicecomponents)|데이터 연결 대화 상자를 사용 하 여 데이터 원본 개체를 엽니다.|

## <a name="remarks"></a>설명

단일 연결에 대해 하나 이상의 데이터베이스 세션을 만들 수 있습니다. 이러한 세션은로 표시 됩니다 `CSession` . 를 사용 하 여 세션을 만들기 전에 연결을 열려면 [Cdatasource:: Open](#open) 을 호출 해야 합니다 `CSession::Open` .

를 사용 하는 방법에 대 한 예제는 `CDataSource` [CatDB](../../overview/visual-cpp-samples.md) 샘플을 참조 하세요.

## <a name="cdatasourceclose"></a><a name="close"></a> CDataSource:: Close

포인터를 해제 하 여 연결을 닫습니다 `m_spInit` .

### <a name="syntax"></a>구문

```cpp
void Close() throw();
```

## <a name="cdatasourcegetinitializationstring"></a><a name="getinitializationstring"></a> CDataSource:: GetInitializationString

현재 열려 있는 데이터 원본의 초기화 문자열을 검색 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>매개 변수

*pInitializationString*<br/>
제한이 초기화 문자열에 대 한 포인터입니다.

*bIncludePassword*<br/>
[in] **`true`** 문자열에 암호가 포함 된 경우 그렇지 않으면 **`false`** 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

결과 초기화 문자열을 사용 하 여 나중에이 데이터 원본 연결을 다시 열 수 있습니다.

## <a name="cdatasourcegetproperties"></a><a name="getproperties"></a> CDataSource:: GetProperties

연결 된 데이터 원본 개체에 대해 요청 된 속성 정보를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>매개 변수

Windows SDK *OLE DB 프로그래머 참조* 에서 [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

단일 속성을 가져오려면 [GetProperty](#getproperty)를 사용 합니다.

## <a name="cdatasourcegetproperty"></a><a name="getproperty"></a> CDataSource:: GetProperty

연결 된 데이터 원본 개체에 대해 지정 된 속성의 값을 반환 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>매개 변수

*guid*<br/>
진행 속성을 반환할 속성 집합을 식별 하는 GUID입니다.

*propid*<br/>
진행 반환할 속성의 속성 ID입니다.

*pVariant*<br/>
제한이 에서 속성의 값을 반환 하는 variant에 대 한 포인터 `GetProperty` 입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

여러 속성을 얻으려면 [GetProperties](#getproperties)를 사용 합니다.

## <a name="cdatasourceopen"></a><a name="open"></a> CDataSource:: Open

, 또는 모니커를 사용 하 여 데이터 원본에 대 한 연결을 열거나 `CLSID` `ProgID` `CEnumerator` 사용자에 게 로케이터 대화 상자를 표시 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,
   LPCTSTR pName,LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>매개 변수

*가*<br/>
진행 `CLSID` 데이터 공급자의입니다.

*pPropSet*<br/>
진행 설정할 속성 및 값을 포함 하는 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열에 대 한 포인터입니다. Windows SDK에서 *OLE DB 프로그래머 참조* 의 [속성 집합 및 속성 그룹](/previous-versions/windows/desktop/ms713696(v=vs.85)) 을 참조 하세요.

*nPropertySets*<br/>
진행 *PPropSet* 인수에 전달 된 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 수입니다.

*pName*<br/>
[in] 연결할 데이터베이스의 이름입니다.

*pUserName*<br/>
[in] 사용자의 이름입니다.

*pPassword*<br/>
[in] 사용자의 암호입니다.

*nInitMode*<br/>
[in] 데이터베이스 초기화 모드입니다. 유효한 초기화 모드 목록은 Windows SDK에서 *OLE DB 프로그래머 참조* 의 [초기화 속성](/previous-versions/windows/desktop/ms723127(v=vs.85))을 참조 하세요. *Ninitmode* 가 0 이면 연결을 여는 데 사용 되는 속성 집합에 초기화 모드가 포함 되지 않습니다.

*szProgID*<br/>
[in] 프로그램 식별자입니다.

*열거*<br/>
진행 호출자가를 지정 하지 않을 때 연결을 열기 위한 모니커를 가져오는 데 사용 되는 [CEnumerator](../../data/oledb/cenumerator-class.md) 개체 `CLSID` 입니다.

*hWnd*<br/>
[in] 대화 상자의 부모가 될 창의 핸들입니다. *HWnd* 매개 변수를 사용 하는 함수 오버 로드를 사용 하면 서비스 구성 요소가 자동으로 호출 됩니다. 자세한 내용은 설명 부분을 참조 하십시오.

*dwPromptOptions*<br/>
[in] 표시할 로케이터 대화 상자의 스타일을 결정합니다. 가능한 값은 Msdasc.h를 참조하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

*HWnd* 매개 변수를 사용 하는 메서드 오버 로드는 oledb32.dll의 서비스 구성 요소를 사용 하 여 데이터 소스 개체를 엽니다. 이 DLL에는 리소스 풀링, 자동 트랜잭션 참여 등과 같은 서비스 구성 요소 기능의 구현이 포함 되어 있습니다. 자세한 내용은 [OLE DB 프로그래머 가이드](/previous-versions/windows/desktop/ms713643(v=vs.85))에서 OLE DB 참조를 참조 하세요.

*HWnd* 매개 변수를 사용 하지 않는 메서드 오버 로드는 oledb32.dll의 서비스 구성 요소를 사용 하지 않고 데이터 소스 개체를 엽니다. 이러한 함수 오버 로드를 사용 하 여 연 [Cdatasource](../../data/oledb/cdatasource-class.md) 개체는 서비스 구성 요소의 기능을 활용할 수 없습니다.

### <a name="example"></a>예제

다음 코드에서는 OLE DB 템플릿을 사용하여 Jet 4.0 데이터 소스를 여는 방법을 보여 줍니다. Jet 데이터 소스를 OLE DB 데이터 소스로 처리합니다. 그러나에 대 한 호출에는 `Open` 두 개의 속성 집합이 필요 합니다. 하나는 DBPROPSET_DBINIT이 고 다른 하나는 DBPROPSET_JETOLEDB_DBINIT에 대해 설정 되므로 DBPROP_JETOLEDB_DATABASEPASSWORD를 설정할 수 있습니다.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="cdatasourceopenfromfilename"></a><a name="openfromfilename"></a> CDataSource:: OpenFromFileName

사용자가 제공한 파일 이름으로 지정된 파일에서 데이터 소스를 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>매개 변수

*szFileName*<br/>
[in] 일반적으로 데이터 소스 연결(.UDL) 파일의 이름입니다.

데이터 연결 파일 (.udl 파일)에 대 한 자세한 내용은 Windows SDK의 [데이터 연결 API 개요](/previous-versions/windows/desktop/ms718102(v=vs.85)) 를 참조 하세요.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 oledb32.dll에 있는 서비스 구성 요소를 사용하여 데이터 원본 개체를 엽니다. 이 DLL에는 리소스 풀링, 자동 트랜잭션 참여 등과 같은 서비스 구성 요소 기능의 구현이 들어 있습니다. 자세한 내용은 [OLE DB 프로그래머 가이드](/previous-versions/windows/desktop/ms713643(v=vs.85))에서 OLE DB 참조를 참조 하세요.

## <a name="cdatasourceopenfrominitializationstring"></a><a name="openfrominitializationstring"></a> CDataSource:: OpenFromInitializationString

사용자가 제공한 초기화 문자열로 지정 된 데이터 원본을 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>매개 변수

*szInitializationString*<br/>
진행 초기화 문자열입니다.

*fPromptForInfo*<br/>
진행 이 인수를로 설정 하면 **`true`** `OpenFromInitializationString` DBPROP_INIT_PROMPT 속성이 DBPROMPT_COMPLETEREQUIRED로 설정 되며,이는 추가 정보가 필요한 경우에만 사용자에 게 메시지를 표시 하도록 지정 합니다. 이는 초기화 문자열이 암호를 필요로 하는 데이터베이스를 지정 하지만 해당 문자열에 암호가 포함 되지 않는 경우에 유용 합니다. 데이터베이스에 연결 하려고 할 때 사용자에 게 암호 (또는 다른 누락 된 정보)를 입력 하 라는 메시지가 표시 됩니다.

기본값은입니다 .이 값은 **`false`** 사용자에 게 메시지가 표시 되지 않도록 지정 합니다 (DBPROMPT_NOPROMPT DBPROP_INIT_PROMPT 설정).

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 oledb32.dll에 있는 서비스 구성 요소를 사용하여 데이터 원본 개체를 엽니다. 이 DLL에는 리소스 풀링, 자동 트랜잭션 참여 등과 같은 서비스 구성 요소 기능의 구현이 들어 있습니다.

## <a name="cdatasourceopenwithpromptfilename"></a><a name="openwithpromptfilename"></a> CDataSource:: OpenWithPromptFileName

이 메서드는 사용자에게 대화 상자를 표시한 다음 사용자가 지정한 파일을 사용하여 데이터 원본을 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>매개 변수

*hWnd*<br/>
[in] 대화 상자의 부모가 될 창의 핸들입니다.

*dwPromptOptions*<br/>
[in] 표시할 로케이터 대화 상자의 스타일을 결정합니다. 가능한 값은 Msdasc.h를 참조하세요.

*szInitialDirectory*<br/>
[in] 로케이터 대화 상자에 표시할 초기 디렉터리입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 oledb32.dll에 있는 서비스 구성 요소를 사용하여 데이터 원본 개체를 엽니다. 이 DLL에는 리소스 풀링, 자동 트랜잭션 참여 등과 같은 서비스 구성 요소 기능의 구현이 들어 있습니다. 자세한 내용은 [OLE DB 프로그래머 가이드](/previous-versions/windows/desktop/ms713643(v=vs.85))에서 OLE DB 참조를 참조 하세요.

## <a name="cdatasourceopenwithservicecomponents"></a><a name="openwithservicecomponents"></a> CDataSource:: OpenWithServiceComponents

oledb32.dll에서 서비스 구성 요소를 사용하여 데이터 원본 개체를 엽니다.

### <a name="syntax"></a>구문

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>매개 변수

*가*<br/>
진행 `CLSID` 데이터 공급자의입니다.

*szProgID*<br/>
[in] 데이터 공급자의 프로그램 ID입니다.

*pPropset*<br/>
진행 설정할 속성 및 값을 포함 하는 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 배열에 대 한 포인터입니다. Windows SDK에서 *OLE DB 프로그래머 참조* 의 [속성 집합 및 속성 그룹](/previous-versions/windows/desktop/ms713696(v=vs.85)) 을 참조 하세요. 데이터 원본 개체가 초기화되면 속성은 데이터 원본 속성 그룹에 속해야 합니다. *PPropset*에서 동일한 속성이 두 번 이상 지정 된 경우 사용 되는 값은 공급자별로 다릅니다. *Ulpropsets* 가 0 이면이 매개 변수는 무시 됩니다.

*ulPropSets*<br/>
진행 *PPropSet* 인수에 전달 된 [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) 구조체의 수입니다. 이 값이 0 이면 공급자는 *pPropset*를 무시 합니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

이 메서드는 oledb32.dll에 있는 서비스 구성 요소를 사용하여 데이터 원본 개체를 엽니다. 이 DLL에는 리소스 풀링, 자동 트랜잭션 참여 등과 같은 서비스 구성 요소 기능의 구현이 들어 있습니다. 자세한 내용은 [OLE DB 프로그래머 가이드](/previous-versions/windows/desktop/ms713643(v=vs.85))에서 OLE DB 참조를 참조 하세요.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)
