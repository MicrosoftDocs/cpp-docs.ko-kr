---
description: '자세한 정보: CBindStatusCallback 클래스'
title: CBindStatusCallback 클래스
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 8c57328be0cb2678e671f68ac5bb44471056f457
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97146980"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback 클래스

이 클래스는 `IBindStatusCallback` 인터페이스를 구현합니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
데이터를 받을 때 호출 되는 함수를 포함 하는 클래스입니다.

*nBindFlags*<br/>
[Getbindinfo](#getbindinfo)에서 반환 하는 바인딩 플래그를 지정 합니다. 기본 구현에서는 바인딩이 비동기로 설정 되 고, 최신 버전의 데이터/개체를 검색 하며, 검색 된 데이터를 디스크 캐시에 저장 하지 않습니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CBindStatusCallback:: CBindStatusCallback](#cbindstatuscallback)|생성자입니다.|
|[CBindStatusCallback::~CBindStatusCallback](#dtor)|소멸자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CBindStatusCallback::D o)](#download)|다운로드 프로세스를 시작 하 고, 개체를 만들고,를 호출 하는 정적 메서드입니다 `CBindStatusCallback` `StartAsyncDownload` .|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|만들 바인딩 형식에 대 한 정보를 요청 하기 위해 비동기 모니커에 의해 호출 됩니다.|
|[CBindStatusCallback:: GetPriority](#getpriority)|바인딩 작업의 우선 순위를 가져오기 위해 비동기 모니커에 의해 호출 됩니다. ATL 구현은을 반환 합니다 `E_NOTIMPL` .|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|데이터를 사용할 수 있게 되 면 응용 프로그램에 데이터를 제공 하기 위해 호출 됩니다. 데이터를 읽은 다음 데이터를 사용 하기 위해 전달 된 함수를 호출 합니다.|
|[CBindStatusCallback::OnLowResource](#onlowresource)|리소스가 부족 하면 호출 됩니다. ATL 구현은 S_OK 반환 합니다.|
|[CBindStatusCallback:: OnObjectAvailable](#onobjectavailable)|응용 프로그램에 개체 인터페이스 포인터를 전달 하기 위해 비동기 모니커에 의해 호출 됩니다. ATL 구현은 S_OK 반환 합니다.|
|[CBindStatusCallback::OnProgress](#onprogress)|데이터 다운로드 프로세스의 진행 상황을 나타내기 위해 호출 됩니다. ATL 구현은 S_OK 반환 합니다.|
|[CBindStatusCallback:: OnStartBinding](#onstartbinding)|바인딩이 시작 되 면 호출 됩니다.|
|[CBindStatusCallback:: OnStopBinding](#onstopbinding)|비동기 데이터 전송이 중지 될 때 호출 됩니다.|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|사용 가능한 바이트 및 읽은 바이트를 0으로 초기화 하 고, URL에서 푸시 형식 스트림 개체를 만들며, `OnDataAvailable` 데이터를 사용할 수 있을 때마다를 호출 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CBindStatusCallback:: m_dwAvailableToRead](#m_dwavailabletoread)|읽을 수 있는 바이트 수입니다.|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|읽은 총 바이트 수입니다.|
|[CBindStatusCallback:: m_pFunc](#m_pfunc)|데이터를 사용할 수 있을 때 호출 되는 함수에 대 한 포인터입니다.|
|[CBindStatusCallback::m_pT](#m_pt)|비동기 데이터 전송을 요청 하는 개체에 대 한 포인터입니다.|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|현재 바인딩 작업의 [ibindctx interface](/windows/win32/api/objidl/nn-objidl-ibindctx) 인터페이스에 대 한 포인터입니다.|
|[CBindStatusCallback:: m_spBinding](#m_spbinding)|`IBinding`현재 바인딩 작업의 인터페이스에 대 한 포인터입니다.|
|[CBindStatusCallback:: m_spMoniker](#m_spmoniker)|사용할 URL에 대 한 [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) 인터페이스에 대 한 포인터입니다.|
|[CBindStatusCallback::m_spStream](#m_spstream)|데이터 전송에 대 한 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 인터페이스에 대 한 포인터입니다.|

## <a name="remarks"></a>설명

`CBindStatusCallback` 클래스가 `IBindStatusCallback` 인터페이스를 구현합니다. `IBindStatusCallback` 는 비동기 데이터 전송에서 알림을 받을 수 있도록 응용 프로그램에서 구현 해야 합니다. 시스템에서 제공 하는 비동기 모니커는 `IBindStatusCallback` 메서드를 사용 하 여 개체와의 비동기 데이터 전송에 대 한 정보를 보내고 받습니다.

일반적으로 `CBindStatusCallback` 개체는 특정 바인드 작업과 연결 됩니다. 예를 들어 [ASYNC](../../overview/visual-cpp-samples.md) 샘플에서 URL 속성을 설정 하면 `CBindStatusCallback` 에 대 한 호출에서 개체를 만듭니다 `Download` .

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

비동기 모니커는 콜백 함수를 사용 하 여 `OnData` 데이터가 있을 때 응용 프로그램을 호출 합니다. 비동기 모니커는 시스템에서 제공 됩니다.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>요구 사항

**헤더:** 없음 ctl. h

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="cbindstatuscallback"></a> CBindStatusCallback:: CBindStatusCallback

생성자입니다.

```
CBindStatusCallback();
```

### <a name="remarks"></a>설명

비동기 데이터 전송과 관련 된 알림을 수신 하는 개체를 만듭니다. 일반적으로 각 바인드 작업에 대해 하나의 개체가 만들어집니다.

생성자는 또한 [m_pT](#m_pt) 를 초기화 하 고 NULL로 [m_pFunc](#m_pfunc) 합니다.

## <a name="cbindstatuscallbackcbindstatuscallback"></a><a name="dtor"></a> CBindStatusCallback:: ~ CBindStatusCallback

소멸자입니다.

```
~CBindStatusCallback();
```

### <a name="remarks"></a>설명

할당 된 리소스를 모두 해제 합니다.

## <a name="cbindstatuscallbackdownload"></a><a name="download"></a> CBindStatusCallback::D o)

개체를 만들고 `CBindStatusCallback` 를 호출 `StartAsyncDownload` 하 여 지정 된 URL에서 비동기적으로 데이터를 다운로드 하기 시작 합니다.

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>매개 변수

*P t*<br/>
진행 비동기 데이터 전송을 요청 하는 개체에 대 한 포인터입니다. `CBindStatusCallback`개체는이 개체의 클래스에서 템플릿 화 됩니다.

*pFunc*<br/>
진행 읽은 데이터를 수신 하는 함수에 대 한 포인터입니다. 함수는 개체의 형식 클래스의 멤버입니다 `T` . 구문 및 예제는 [StartAsyncDownload](#startasyncdownload) 을 참조 하세요.

*bstrURL*<br/>
진행 데이터를 가져올 URL입니다. 유효한 모든 URL 또는 파일 이름일 수 있습니다. NULL이 될 수 없습니다. 예를 들어:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
진행 `IUnknown` 컨테이너의입니다. 기본값은 NULL입니다.

*bRelative*<br/>
진행 URL이 상대 경로 인지 아니면 절대 URL 인지를 나타내는 플래그입니다. 기본적으로 FALSE로 설정 됩니다. 즉, URL은 절대 URL입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

데이터를 사용할 수 있을 때마다를 통해 개체에 전송 됩니다 `OnDataAvailable` . `OnDataAvailable` 데이터를 읽고 *Pfunc* 가 가리키는 함수를 호출 합니다. 예를 들어 데이터를 저장 하거나 화면에 출력 합니다.

## <a name="cbindstatuscallbackgetbindinfo"></a><a name="getbindinfo"></a> CBindStatusCallback:: GetBindInfo

모니커에 바인딩하는 방법을 알리기 위해 호출 됩니다.

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>매개 변수

*pgrfBSCF*<br/>
제한이 바인딩 작업을 수행 하는 방법을 지정 하는 BINDF 열거형 값에 대 한 포인터입니다. 기본적으로는 다음 열거형 값을 사용 하 여 설정 합니다.

비동기 다운로드를 BINDF_ASYNCHRONOUS 합니다.

데이터를 `OnDataAvailable` 사용할 수 있을 때까지 데이터를 차단 하지 않고 데이터를 아직 사용할 수 없는 경우 BINDF_ASYNCSTORAGE E_PENDING 반환 됩니다.

BINDF_GETNEWESTVERSION 바인딩 작업에서 최신 버전의 데이터를 검색 해야 합니다.

BINDF_NOWRITECACHE 바인딩 작업은 검색 된 데이터를 디스크 캐시에 저장 하지 않아야 합니다.

*pbindinfo*<br/>
[in, out] `BINDINFO` 개체의 바인딩을 원하는 방법에 대 한 자세한 정보를 제공 하는 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

기본 구현에서는 바인딩이 비동기로 설정 되 고 데이터 푸시 모델을 사용 합니다. 데이터 푸시 모델에서 모니커는 비동기 바인딩 작업을 구동 하 고 새 데이터를 사용할 수 있을 때마다 클라이언트에 지속적으로 알립니다.

## <a name="cbindstatuscallbackgetpriority"></a><a name="getpriority"></a> CBindStatusCallback:: GetPriority

바인딩 작업의 우선 순위를 가져오기 위해 비동기 모니커에 의해 호출 됩니다.

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>매개 변수

*pnPriority*<br/>
제한이 성공 시 우선 순위를 받는 **LONG** 변수의 주소입니다.

### <a name="return-value"></a>반환 값

E_NOTIMPL을 반환합니다.

## <a name="cbindstatuscallbackm_dwavailabletoread"></a><a name="m_dwavailabletoread"></a> CBindStatusCallback:: m_dwAvailableToRead

읽을 수 있는 바이트 수를 저장 하는 데 사용할 수 있습니다.

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>설명

에서 0으로 초기화 `StartAsyncDownload` 됩니다.

## <a name="cbindstatuscallbackm_dwtotalread"></a><a name="m_dwtotalread"></a> CBindStatusCallback:: m_dwTotalRead

비동기 데이터 전송에서 읽은 총 바이트 수입니다.

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>설명

`OnDataAvailable`실제로 읽은 바이트 수에 의해 매번 증가 합니다. 에서 0으로 초기화 `StartAsyncDownload` 됩니다.

## <a name="cbindstatuscallbackm_pfunc"></a><a name="m_pfunc"></a> CBindStatusCallback:: m_pFunc

에서 가리키는 함수는 `m_pFunc` `OnDataAvailable` 사용 가능한 데이터를 읽은 후에 호출 됩니다. 예를 들어 데이터를 저장 하거나 화면에 출력 합니다.

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>설명

가 가리키는 함수는 `m_pFunc` 개체 클래스의 멤버 이며 다음 구문을 갖습니다.

```cpp
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

## <a name="cbindstatuscallbackm_pt"></a><a name="m_pt"></a> CBindStatusCallback:: m_pT

비동기 데이터 전송을 요청 하는 개체에 대 한 포인터입니다.

```
T* m_pT;
```

### <a name="remarks"></a>설명

`CBindStatusCallback`개체는이 개체의 클래스에서 템플릿 화 됩니다.

## <a name="cbindstatuscallbackm_spbindctx"></a><a name="m_spbindctx"></a> CBindStatusCallback:: m_spBindCtx

바인딩 컨텍스트 (특정 모니커 바인딩 작업에 대 한 정보를 저장 하는 개체)에 대 한 액세스를 제공 하는 [ibindctx interface](/windows/win32/api/objidl/nn-objidl-ibindctx) 인터페이스에 대 한 포인터입니다.

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>설명

에서 초기화 `StartAsyncDownload` 됩니다.

## <a name="cbindstatuscallbackm_spbinding"></a><a name="m_spbinding"></a> CBindStatusCallback:: m_spBinding

`IBinding`현재 바인딩 작업의 인터페이스에 대 한 포인터입니다.

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>설명

에서 초기화 되 `OnStartBinding` 고에서 릴리스 `OnStopBinding` 되었습니다.

## <a name="cbindstatuscallbackm_spmoniker"></a><a name="m_spmoniker"></a> CBindStatusCallback:: m_spMoniker

사용할 URL에 대 한 [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker) 인터페이스에 대 한 포인터입니다.

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>설명

에서 초기화 `StartAsyncDownload` 됩니다.

## <a name="cbindstatuscallbackm_spstream"></a><a name="m_spstream"></a> CBindStatusCallback:: m_spStream

현재 바인딩 작업의 [IStream](/windows/win32/api/objidl/nn-objidl-istream) 인터페이스에 대 한 포인터입니다.

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>설명

Bcsf 플래그가 `OnDataAvailable` `STGMEDIUM` BCSF_FIRSTDATANOTIFICATION 되 면 구조에서 초기화 되 고 bcsf 플래그가 BCSF_LASTDATANOTIFICATION 되 면 해제 됩니다.

## <a name="cbindstatuscallbackondataavailable"></a><a name="ondataavailable"></a> CBindStatusCallback:: OnDataAvailable 사용 가능

시스템이 제공 하는 비동기 모니커는 `OnDataAvailable` 를 호출 하 여 개체를 사용할 수 있게 되 면 해당 개체에 데이터를 제공 합니다.

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>매개 변수

*grfBSCF*<br/>
진행 BSCF 열거형 값입니다. BSCF_FIRSTDATANOTIFICATION, BSCF_INTERMEDIARYDATANOTIFICATION 또는 BSCF_LASTDATANOTIFICATION 중 하나 이상입니다.

*dwSize*<br/>
진행 바인딩이 시작 된 이후에 사용할 수 있는 데이터의 누적 크기 (바이트)입니다. 은 (는) 0 일 수 있습니다. 즉, 데이터의 양이 관련이 없거나 특정 크기를 사용할 수 없음을 나타냅니다.

*pformatetc*<br/>
진행 사용 가능한 데이터의 형식을 포함 하는 [FORMATETC](/windows/win32/com/the-formatetc-structure) 구조체에 대 한 포인터입니다. 형식이 없는 경우 CF_NULL 수 있습니다.

*pstgmed*<br/>
진행 현재 사용할 수 있는 실제 데이터를 보유 하는 [STGMEDIUM](/windows/win32/com/the-stgmedium-structure) 구조에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

`OnDataAvailable` 데이터를 읽은 다음 개체 클래스의 메서드를 호출 합니다. 예를 들어 데이터를 저장 하거나 화면에 출력 합니다. 자세한 내용은 [Cbindstatuscallback:: StartAsyncDownload](#startasyncdownload) 를 참조 하세요.

## <a name="cbindstatuscallbackonlowresource"></a><a name="onlowresource"></a> CBindStatusCallback:: OnLowResource

리소스가 부족 하면 호출 됩니다.

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>매개 변수

*dwReserved*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="cbindstatuscallbackonobjectavailable"></a><a name="onobjectavailable"></a> CBindStatusCallback:: OnObjectAvailable

응용 프로그램에 개체 인터페이스 포인터를 전달 하기 위해 비동기 모니커에 의해 호출 됩니다.

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
요청 된 인터페이스의 인터페이스 식별자입니다. 사용되지 않습니다.

*punk*<br/>
IUnknown 인터페이스의 주소입니다. 사용되지 않습니다.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="cbindstatuscallbackonprogress"></a><a name="onprogress"></a> CBindStatusCallback:: OnProgress

데이터 다운로드 프로세스의 진행 상황을 나타내기 위해 호출 됩니다.

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>매개 변수

*ulProgress*<br/>
부호 없는 정수 (long)입니다. 사용되지 않습니다.

*ulProgressMax*<br/>
부호 없는 정수 (long)를 사용 하지 않습니다.

*ulStatusCode*<br/>
부호 없는 정수 (long)입니다. 사용되지 않습니다.

*szStatusText*<br/>
문자열 값의 주소입니다. 사용되지 않습니다.

### <a name="return-value"></a>반환 값

S_OK를 반환 합니다.

## <a name="cbindstatuscallbackonstartbinding"></a><a name="onstartbinding"></a> CBindStatusCallback:: OnStartBinding

[M_spBinding](#m_spbinding) 데이터 멤버를 *pbinding* 의 `IBinding`포인터로 설정합니다.

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>매개 변수

*dwReserved*<br/>
다음에 사용하도록 예약됩니다.

*pBinding*<br/>
진행 현재 바인딩 작업의 IBinding 인터페이스 주소입니다. NULL 일 수 없습니다. 클라이언트는이 포인터에서 AddRef를 호출 하 여 바인딩 개체에 대 한 참조를 유지 해야 합니다.

## <a name="cbindstatuscallbackonstopbinding"></a><a name="onstopbinding"></a> CBindStatusCallback:: OnStopBinding

`IBinding`데이터 멤버 [m_spBinding](#m_spbinding)에서 포인터를 해제 합니다.

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>매개 변수

*hresult*<br/>
바인딩 작업에서 반환 된 상태 코드입니다.

*szError*<br/>
문자열 값의 주소입니다. 사용되지 않습니다.

### <a name="remarks"></a>설명

바인드 작업의 끝을 나타내기 위해 시스템에서 제공 하는 비동기 모니커에 의해 호출 됩니다.

## <a name="cbindstatuscallbackstartasyncdownload"></a><a name="startasyncdownload"></a> CBindStatusCallback:: StartAsyncDownload

지정 된 URL에서 비동기적으로 데이터를 다운로드 하기 시작 합니다.

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>매개 변수

*P t*<br/>
진행 비동기 데이터 전송을 요청 하는 개체에 대 한 포인터입니다. `CBindStatusCallback`개체는이 개체의 클래스에서 템플릿 화 됩니다.

*pFunc*<br/>
진행 읽고 있는 데이터를 수신 하는 함수에 대 한 포인터입니다. 함수는 개체의 형식 클래스의 멤버입니다 `T` . 구문 및 예제는 **설명** 을 참조 하세요.

*bstrURL*<br/>
진행 데이터를 가져올 URL입니다. 유효한 모든 URL 또는 파일 이름일 수 있습니다. NULL이 될 수 없습니다. 예를 들어:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
진행 `IUnknown` 컨테이너의입니다. 기본값은 NULL입니다.

*bRelative*<br/>
진행 URL이 상대 경로 인지 아니면 절대 URL 인지를 나타내는 플래그입니다. 기본적으로 FALSE로 설정 됩니다. 즉, URL은 절대 URL입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값 중 하나입니다.

### <a name="remarks"></a>설명

데이터를 사용할 수 있을 때마다를 통해 개체에 전송 됩니다 `OnDataAvailable` . `OnDataAvailable` 데이터를 읽고 *Pfunc* 가 가리키는 함수를 호출 합니다. 예를 들어 데이터를 저장 하거나 화면에 출력 합니다.

*Pfunc* 에서 가리키는 함수는 개체 클래스의 멤버 이며 다음 구문을 갖습니다.

```cpp
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

[비동기](../../overview/visual-cpp-samples.md) 샘플에서 가져온 다음 예제에서 함수는 `OnData` 받은 데이터를 텍스트 상자에 씁니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>참고 항목

[클래스 개요](../../atl/atl-class-overview.md)
