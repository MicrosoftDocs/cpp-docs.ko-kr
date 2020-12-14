---
description: '자세히 알아보기: CAsyncMonikerFile 클래스'
title: CAsyncMonikerFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: 559ffd5ed3a8b7100d9901dc70fe4f5349c05f7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97343531"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile 클래스

ActiveX 컨트롤(이전의 OLE 컨트롤)에서 비동기 모니커를 사용할 수 있도록 기능을 제공합니다.

## <a name="syntax"></a>구문

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CAsyncMonikerFile:: CAsyncMonikerFile](#casyncmonikerfile)|`CAsyncMonikerFile` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CAsyncMonikerFile:: Close](#close)|모든 리소스를 닫고 해제 합니다.|
|[CAsyncMonikerFile:: GetBinding](#getbinding)|비동기 전송 바인딩에 대 한 포인터를 검색 합니다.|
|[CAsyncMonikerFile:: GetFormatEtc](#getformatetc)|스트림에서 데이터의 형식을 검색 합니다.|
|[CAsyncMonikerFile:: Open](#open)|파일을 비동기적으로 엽니다.|

### <a name="protected-methods"></a>Protected 메서드

|Name|설명|
|----------|-----------------|
|[CAsyncMonikerFile:: CreateBindStatusCallback](#createbindstatuscallback)|을 구현 하는 COM 개체를 만듭니다 `IBindStatusCallback` .|
|[CAsyncMonikerFile:: GetBindInfo](#getbindinfo)|만들려는 바인딩 유형에 대 한 정보를 요청 하기 위해 OLE 시스템 라이브러리에서 호출 됩니다.|
|[CAsyncMonikerFile:: GetPriority](#getpriority)|바인딩의 우선 순위를 가져오기 위해 OLE 시스템 라이브러리에 의해 호출 됩니다.|
|[CAsyncMonikerFile:: OnDataAvailable](#ondataavailable)|비동기 바인딩 작업을 수행 하는 동안 클라이언트에서 사용할 수 있게 될 때 데이터를 제공 하기 위해 호출 됩니다.|
|[CAsyncMonikerFile:: OnLowResource](#onlowresource)|리소스가 부족 하면 호출 됩니다.|
|[CAsyncMonikerFile:: OnProgress](#onprogress)|데이터 다운로드 프로세스에 대 한 진행률을 나타내기 위해 호출 됩니다.|
|[CAsyncMonikerFile:: OnStartBinding](#onstartbinding)|바인딩이 시작 되 면 호출 됩니다.|
|[CAsyncMonikerFile:: OnStopBinding](#onstopbinding)|비동기 전송이 중지 될 때 호출 됩니다.|

## <a name="remarks"></a>설명

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)에서 파생 되며,이는 [Colestreamfile](../../mfc/reference/colestreamfile-class.md)에서 파생 되며, URL에서 비동기적으로 파일을 로드 하는 것을 포함 하 여 `CAsyncMonikerFile` [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) 인터페이스를 사용 하 여 데이터 스트림에 비동기적으로 액세스 합니다. 파일은 ActiveX 컨트롤의 데이터 경로 속성 일 수 있습니다.

비동기 모니커는 주로 인터넷 사용 응용 프로그램 및 ActiveX 컨트롤에서 파일을 전송 하는 동안 응답성이 뛰어난 사용자 인터페이스를 제공 하는 데 사용 됩니다. 이에 대 한 가장 대표적인 예는 ActiveX 컨트롤에 대 한 비동기 속성을 제공 하는 데 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md) 를 사용 하는 것입니다. `CDataPathProperty`개체는 긴 속성 교환 프로세스 중에 새 데이터의 가용성을 나타내는 콜백을 반복적으로 받습니다.

인터넷 응용 프로그램에서 비동기 모니커 및 ActiveX 컨트롤을 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [인터넷 우선 단계: 비동기 모니커](../../mfc/asynchronous-monikers-on-the-internet.md)

- [인터넷 우선 단계: ActiveX 컨트롤](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxole

## <a name="casyncmonikerfilecasyncmonikerfile"></a><a name="casyncmonikerfile"></a> CAsyncMonikerFile:: CAsyncMonikerFile

`CAsyncMonikerFile` 개체를 생성합니다.

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>설명

인터페이스를 만들지 않습니다 `IBindHost` . `IBindHost` 는 멤버 함수에서 제공 하는 경우에만 사용 됩니다 `Open` .

인터페이스에 대 한 설명은 `IBindHost` Windows SDK를 참조 하세요.

## <a name="casyncmonikerfileclose"></a><a name="close"></a> CAsyncMonikerFile:: Close

모든 리소스를 닫고 해제 하려면이 함수를 호출 합니다.

```
virtual void Close();
```

### <a name="remarks"></a>설명

는 열지 않았거나 이미 닫혀 있는 파일에서 호출할 수 있습니다.

## <a name="casyncmonikerfilecreatebindstatuscallback"></a><a name="createbindstatuscallback"></a> CAsyncMonikerFile:: CreateBindStatusCallback

을 구현 하는 COM 개체를 만듭니다 `IBindStatusCallback` .

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>매개 변수

*pUnkControlling*<br/>
Unknown (outer)을 제어 하는 포인터 `IUnknown` 이거나 집계가 사용 되지 않는 경우 NULL입니다.

### <a name="return-value"></a>반환 값

*PUnkControlling* 가 NULL이 아닌 경우이 함수는를 `IUnknown` 지 원하는 새 COM 개체의 내부에 대 한 포인터를 반환 합니다 `IBindStatusCallback` . `pUnkControlling`가 NULL 인 경우이 함수는를 `IUnknown` 지 원하는 새 COM 개체의에 대 한 포인터를 반환 합니다 `IBindStatusCallback` .

### <a name="remarks"></a>설명

`CAsyncMonikerFile` 을 구현 하는 COM 개체가 필요 `IBindStatusCallback` 합니다. MFC는 이러한 개체를 구현 하 고 집계할 수 있습니다. `CreateBindStatusCallback`를 재정의 하 여 사용자 고유의 COM 개체를 반환할 수 있습니다. COM 개체는 `CreateBindStatusCallback` com 개체의 알 수 없는 제어를 사용 하 여를 호출 하 여 MFC의 구현을 집계할 수 있습니다. Com 지원을 사용 하 여 구현 된 COM 개체 `CCmdTarget` 는를 사용 하 여 알 수 없는 제어를 검색할 수 있습니다 `CCmdTarget::GetControllingUnknown` .

또는 COM 개체가를 호출 하 여 MFC의 구현에 위임할 수 있습니다 `CreateBindStatusCallback( NULL )` .

[CAsyncMonikerFile:: Open](#open) 호출 `CreateBindStatusCallback`

비동기 모니커 및 비동기 바인딩에 대 한 자세한 내용은 [Ibindstatuscallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\)) 인터페이스 및 [비동기 바인딩 및 저장소의 작동 방식](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)을 참조 하세요. 집계에 대 한 설명은 [집계](/windows/win32/com/aggregation)를 참조 하세요. 이 세 항목은 모두 Windows SDK에 있습니다.

## <a name="casyncmonikerfilegetbindinfo"></a><a name="getbindinfo"></a> CAsyncMonikerFile:: GetBindInfo

비동기 모니커에 바인딩하려는 방식을 알리기 위해 비동기 모니커의 클라이언트에서 호출 됩니다.

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>반환 값

에 대 한 설정을 검색 `IBindStatusCallBack` 합니다. 인터페이스에 대 한 설명은 `IBindStatusCallback` Windows SDK를 참조 하세요.

### <a name="remarks"></a>설명

기본 구현에서는 바인딩이 비동기로 설정 되 고, 저장소 미디어 (스트림)를 사용 하 고, 데이터 푸시 모델을 사용 합니다. 바인딩의 동작을 변경 하려는 경우이 함수를 재정의 합니다.

이 작업을 수행 하는 한 가지 이유는 데이터 푸시 모델 대신 데이터 끌어오기 모델을 사용 하 여 바인딩하는 것입니다. 데이터 끌어오기 모델에서 클라이언트는 바인딩 작업을 수행 하 고, 모니커는 데이터를 읽을 때 클라이언트에만 데이터를 제공 합니다. 데이터 푸시 모델에서 모니커는 비동기 바인딩 작업을 구동 하 고 새 데이터를 사용할 수 있을 때마다 클라이언트에 지속적으로 알립니다.

## <a name="casyncmonikerfilegetbinding"></a><a name="getbinding"></a> CAsyncMonikerFile:: GetBinding

비동기 전송 바인딩에 대 한 포인터를 검색 하려면이 함수를 호출 합니다.

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>반환 값

`IBinding`비동기 전송이 시작 될 때 제공 되는 인터페이스에 대 한 포인터입니다. 어떤 이유로 든 비동기식으로 전송할 수 없는 경우 NULL을 반환 합니다.

### <a name="remarks"></a>설명

이를 통해 `IBinding` 인터페이스 (예:, 및)를 통해 데이터 전송 프로세스를 제어할 수 있습니다 `IBinding::Abort` `IBinding::Pause` `IBinding::Resume` .

인터페이스에 대 한 설명은 `IBinding` Windows SDK를 참조 하세요.

## <a name="casyncmonikerfilegetformatetc"></a><a name="getformatetc"></a> CAsyncMonikerFile:: GetFormatEtc

이 함수를 호출 하 여 스트림의 데이터 형식을 검색 합니다.

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>반환 값

현재 열려 있는 스트림의 Windows 구조 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 에 대 한 포인터입니다. 모니커가 바인딩되지 않았거나, 비동기가 아니거나, 비동기 작업이 시작 되지 않은 경우 NULL을 반환 합니다.

## <a name="casyncmonikerfilegetpriority"></a><a name="getpriority"></a> CAsyncMonikerFile:: GetPriority

바인딩 프로세스에서 바인딩 작업을 위해 스레드에 지정 된 우선 순위를 받기 시작 하므로 비동기 모니커의 클라이언트에서 호출 됩니다.

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>반환 값

비동기 전송이 발생 하는 우선 순위입니다. 표준 스레드 우선 순위 플래그 중 하나: THREAD_PRIORITY_ABOVE_NORMAL, THREAD_PRIORITY_BELOW_NORMAL, THREAD_PRIORITY_HIGHEST, THREAD_PRIORITY_IDLE, THREAD_PRIORITY_LOWEST, THREAD_PRIORITY_NORMAL 및 THREAD_PRIORITY_TIME_CRITICAL. 이러한 값에 대 한 설명은 Windows 함수 [Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 를 참조 하십시오.

### <a name="remarks"></a>설명

`GetPriority` 해야 하지 직접 호출할 수 있습니다. THREAD_PRIORITY_NORMAL은 기본 구현에 의해 반환 됩니다.

## <a name="casyncmonikerfileondataavailable"></a><a name="ondataavailable"></a> CAsyncMonikerFile:: OnDataAvailable

비동기 모니커는 `OnDataAvailable` 비동기 바인딩 작업을 수행 하는 동안 사용할 수 있게 되는 클라이언트에 데이터를 제공 하기 위해를 호출 합니다.

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>매개 변수

*dwSize*<br/>
바인딩이 시작 된 이후에 사용할 수 있는 데이터의 누적 크기 (바이트)입니다. 은 (는) 0 일 수 있습니다 .이 값은 데이터의 양이 작업과 관련이 없거나 특정 크기를 사용할 수 없음을 나타냅니다.

*bscfFlag*<br/>
BSCF 열거형 값입니다. 다음 값 중 하나 이상이 될 수 있습니다.

- BSCF_FIRSTDATANOTIFICATION는 `OnDataAvailable` 지정 된 바인드 작업에 대 한 첫 번째 호출을 식별 합니다.

- BSCF_INTERMEDIATEDATANOTIFICATION는 `OnDataAvailable` 바인딩 작업에 대 한 중간 호출을 식별 합니다.

- BSCF_LASTDATANOTIFICATION는 `OnDataAvailable` 바인딩 작업에 대 한 마지막 호출을 식별 합니다.

### <a name="remarks"></a>설명

이 함수의 기본 구현은 아무 작업도 수행하지 않습니다. 예제 구현은 다음 예제를 참조 하세요.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

## <a name="casyncmonikerfileonlowresource"></a><a name="onlowresource"></a> CAsyncMonikerFile:: OnLowResource

리소스가 부족할 때 모니커에 의해 호출 됩니다.

```
virtual void OnLowResource();
```

### <a name="remarks"></a>설명

기본 구현에서는를 호출 `GetBinding( )-> Abort( )` 합니다.

## <a name="casyncmonikerfileonprogress"></a><a name="onprogress"></a> CAsyncMonikerFile:: OnProgress

일반적으로 시간이 오래 걸리는 작업 중에이 바인딩 작업의 현재 진행률 (일반적으로 적절 한 간격)을 나타내기 위해 모니커에 의해 호출 됩니다.

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>매개 변수

*ulProgress*<br/>
*UlProgressMax* 에 표시 된 예상 최대값을 기준으로 바인딩 작업의 현재 진행률을 나타냅니다.

*ulProgressMax*<br/>
 `OnProgress` 이 작업에 대 한 호출 기간 동안 예상 되는 최대 진행률 값을 나타냅니다.

*ulStatusCode*<br/>
바인딩 작업의 진행률에 대 한 추가 정보를 제공 합니다. 유효한 값은 열거형에서 가져옵니다 `BINDSTATUS` . 가능한 값에 대해서는 설명을 참조 하세요.

*szStatusText*<br/>
*Ulstatuscode* 의 값에 따라 현재 진행에 대 한 정보입니다. 가능한 값에 대해서는 설명을 참조 하세요.

### <a name="remarks"></a>설명

*Ulstatuscode* (및 각 값에 대 한 *szStatusText* )의 가능한 값은 다음과 같습니다.

| 값 | 설명 |
|--|--|
| BINDSTATUS_FINDINGRESOURCE | 바인딩 작업에서 바인딩되는 개체 또는 저장소를 보유 하는 리소스를 찾는 중입니다. *SzStatusText* 는 검색 중인 리소스의 표시 이름 (예: "www.microsoft.com")을 제공 합니다. |
| BINDSTATUS_CONNECTING | 바인딩 작업은 바인딩되는 개체 또는 저장소를 보유 하는 리소스에 연결 하는 것입니다. *SzStatusText* 는 연결 되는 리소스의 표시 이름 (예: IP 주소)을 제공 합니다. |
| BINDSTATUS_SENDINGREQUEST | 바인딩 작업에서 바인딩되는 개체 또는 저장소를 요청 하는 중입니다. *SzStatusText* 는 개체의 표시 이름 (예: 파일 이름)을 제공 합니다. |
| BINDSTATUS_REDIRECTING | 바인딩 작업이 다른 데이터 위치로 리디렉션 되었습니다. *SzStatusText* 는 새 데이터 위치의 표시 이름을 제공 합니다. |
| BINDSTATUS_USINGCACHEDCOPY | 바인딩 작업이 캐시 된 복사본에서 요청 된 개체나 저장소를 검색 하는 중입니다. *SzStatusText* 가 NULL 인 경우 |
| BINDSTATUS_BEGINDOWNLOADDATA | 바인딩 작업에서 바인딩되는 개체 또는 저장소를 수신 하기 시작 했습니다. *SzStatusText* 는 데이터 위치의 표시 이름을 제공 합니다. |
| BINDSTATUS_DOWNLOADINGDATA | 바인딩 작업은 바인딩되는 개체 또는 저장소를 계속 받습니다. *SzStatusText* 는 데이터 위치의 표시 이름을 제공 합니다. |
| BINDSTATUS_ENDDOWNLOADDATA | 바인딩 작업에서 바인딩되는 개체 또는 저장소 수신을 완료 했습니다. *SzStatusText* 는 데이터 위치의 표시 이름을 제공 합니다. |
| BINDSTATUS_CLASSIDAVAILABLE | 바인딩되는 개체의 인스턴스가 생성 될 것입니다. *SzStatusText* 는 새 개체의 CLSID를 문자열 형식으로 제공 하 여 클라이언트에서 바인딩 작업을 취소할 수 있도록 합니다 (원하는 경우). |

## <a name="casyncmonikerfileonstartbinding"></a><a name="onstartbinding"></a> CAsyncMonikerFile:: OnStartBinding

바인딩이 시작 될 때 작업을 수행 하려면 파생 클래스에서이 함수를 재정의 합니다.

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>설명

이 함수는 모니커에 의해 다시 호출 됩니다. 기본 구현은 아무 작업도 수행하지 않습니다.

## <a name="casyncmonikerfileonstopbinding"></a><a name="onstopbinding"></a> CAsyncMonikerFile:: OnStopBinding

바인드 작업 끝의 모니커에 의해 호출 됩니다.

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>매개 변수

*hresult*<br/>
오류 또는 경고 값인 HRESULT입니다.

*szErrort*<br/>
오류를 설명 하는 문자열입니다.

### <a name="remarks"></a>설명

전송이 중지 될 때 작업을 수행 하려면이 함수를 재정의 합니다. 기본적으로 함수는를 해제 `IBinding` 합니다.

인터페이스에 대 한 설명은 `IBinding` Windows SDK를 참조 하세요.

## <a name="casyncmonikerfileopen"></a><a name="open"></a> CAsyncMonikerFile:: Open

이 멤버 함수를 호출 하 여 파일을 비동기적으로 엽니다.

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszURL*<br/>
비동기적으로 열 파일에 대 한 포인터입니다. 파일은 유효한 모든 URL 또는 파일 이름이 될 수 있습니다.

*pError*<br/>
파일 예외에 대 한 포인터입니다. 오류가 발생 하면 원인으로 설정 됩니다.

*pMoniker*<br/>
비동기 모니커 인터페이스에 대 한 포인터 `IMoniker` , 문서 자체 모니커 (를 사용 하 여 검색할 수 있음) `IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)` 및 경로 이름에서 만든 모니커를 조합한 정확한 모니커입니다. 컨트롤은이 모니커를 사용 하 여 바인딩할 수 있지만 컨트롤이 저장 해야 하는 모니커가 아닙니다.

*pBindHost*<br/>
`IBindHost`잠재적 상대 경로 이름에서 모니커를 만드는 데 사용 되는 인터페이스에 대 한 포인터입니다. 바인딩 호스트가 잘못 되었거나 모니커를 제공 하지 않는 경우 호출의 기본값은 `Open(lpszFileName,pError)` 입니다. 인터페이스에 대 한 설명은 `IBindHost` Windows SDK를 참조 하세요.

*pServiceProvider*<br/>
`IServiceProvider` 인터페이스에 대한 포인터입니다. 서비스 공급자가 잘못 되었거나 서비스를 제공할 수 없는 경우 `IBindHost` 호출의 기본값은 `Open(lpszFileName,pError)` 입니다.

*pUnknown*<br/>
`IUnknown` 인터페이스에 대한 포인터입니다. `IServiceProvider`이 있으면 함수는를 쿼리 `IBindHost` 합니다. 서비스 공급자가 잘못 되었거나 서비스를 제공할 수 없는 경우 `IBindHost` 호출의 기본값은 `Open(lpszFileName,pError)` 입니다.

### <a name="return-value"></a>반환 값

파일이 성공적으로 열리면 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 호출은 바인딩 프로세스를 시작 합니다.

*LpszURL* 매개 변수에 대 한 URL 또는 파일 이름을 사용할 수 있습니다. 예를 들어:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- 또는 -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>참고 항목

[CMonikerFile 클래스](../../mfc/reference/cmonikerfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile 클래스](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty 클래스](../../mfc/reference/cdatapathproperty-class.md)
