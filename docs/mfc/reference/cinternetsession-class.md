---
title: CInternetSession 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
dev_langs:
- C++
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c0f885ad5ef8202e7826a8f53dc5df832eecc372
ms.sourcegitcommit: 05075fce8a0ed7fddb99f50f3931db966a91450d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2018
ms.locfileid: "36271336"
---
# <a name="cinternetsession-class"></a>CInternetSession 클래스
한 개 또는 여러 개의 동시 인터넷 세션을 만들어 초기화하며, 필요한 경우 프록시 서버에 대한 연결을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```  
class CInternetSession : public CObject  
```  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CInternetSession::CInternetSession](#cinternetsession)|`CInternetSession` 개체를 생성합니다.|  
  
### <a name="public-methods"></a>Public 메서드  
  
|이름|설명|  
|----------|-----------------|  
|[CInternetSession::Close](#close)|인터넷 세션이 종료 될 때 인터넷 연결을 닫습니다.|  
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|상태 콜백 루틴을 설정합니다.|  
|[CInternetSession::GetContext](#getcontext)|인터넷 세션이 종료 될 때 인터넷 연결을 닫습니다.|  
|[CInternetSession::GetCookie](#getcookie)|Url 지정 된 URL과 모든 부모에 대 한 쿠키를 반환합니다.|  
|[CInternetSession::GetCookieLength](#getcookielength)|버퍼에 저장 하는 쿠키의 길이 지정 하는 변수를 검색 합니다.|  
|[Cinternetsession:: Getftpconnection](#getftpconnection)|서버와 FTP 세션을 엽니다. 사용자가 로그온합니다.|  
|[CInternetSession::GetGopherConnection](#getgopherconnection)|Gopher 서버 연결을 시도 하는 응용 프로그램을 엽니다.|  
|[CInternetSession::GetHttpConnection](#gethttpconnection)|연결을 시도 하는 응용 프로그램에 대 한 HTTP 서버를 엽니다.|  
|[Cinternetsession:: Onstatuscallback](#onstatuscallback)|상태 콜백이 활성화 된 경우 작업의 상태를 업데이트 합니다.|  
|[CInternetSession::OpenURL](#openurl)|구문 분석 하 고 URL을 엽니다.|  
|[CInternetSession::SetCookie](#setcookie)|지정된 된 URL에 대 한 쿠키를 설정 합니다.|  
|[CInternetSession::SetOption](#setoption)|인터넷 세션에 대 한 옵션을 설정합니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CInternetSession::operator HINTERNET](#operator_hinternet)|현재 인터넷 세션에 대 한 핸들입니다.|  
  
## <a name="remarks"></a>설명  
 인터넷 연결 응용 프로그램의 기간에 대 한 존재 해야 하는 경우 만들 수 있습니다는 `CInternetSession` 클래스의 멤버 [CWinApp](../../mfc/reference/cwinapp-class.md)합니다.  
  
 호출할 수 인터넷 세션을 설정 하 고 나면 [OpenURL](#openurl)합니다. `CInternetSession` 다음 전역 함수를 호출 하 여 사용자에 대 한 URL을 구문 분석 [AfxParseURL](internet-url-parsing-globals.md#afxparseurl)합니다. 해당 프로토콜 종류에 관계 없이 `CInternetSession` URL을 해석 하 고를 관리 합니다. 지정 된 "file://" URL 리소스를 식별 하는 로컬 파일에 대 한 요청을 처리할 수입니다. `OpenURL` 에 대 한 포인터를 반환 합니다는 [CStdioFile](../../mfc/reference/cstdiofile-class.md) 개체를 전달 하는 경우 이름을 로컬 파일입니다.  
  
 사용 하 여 인터넷 서버에서 URL을 열면 `OpenURL`, 사이트에서 정보를 읽을 수 있습니다. 서버에 있는 파일에서 (예: HTTP, FTP, 또는 gopher) 용 서비스 관련 작업을 수행 하려는 경우 해당 서버에서 적절 한 연결을 설정 해야 합니다. 특정 종류의 특정 서비스에 직접 연결을 열려면 다음 멤버 함수 중 하나를 사용 합니다.  
  
- [GetGopherConnection](#getgopherconnection) gopher 서비스에 연결 합니다.  
  
- [GetHttpConnection](#gethttpconnection) 를 HTTP 서비스의 연결을 엽니다.  
  
- [GetFtpConnection](#getftpconnection) 를 FTP 서비스의 연결을 엽니다.  
  
 [SetOption](#setoption) 횟수, 제한 시간 값과 같은 세션의 쿼리 옵션을 설정할 수 있습니다.  
  
 `CInternetSession` 멤버 함수 [SetCookie](#setcookie), [GetCookie](#getcookie), 및 [GetCookieLength](#getcookielength) Win32 쿠키 데이터베이스를 통해 서버와 스크립트 유지 관리 하는 방법을 제공 합니다. 클라이언트 워크스테이션에 대 한 상태 정보입니다.  
  
 기본 인터넷 프로그래밍 작업에 대 한 자세한 내용은 문서 참조 [인터넷 첫 번째 단계: WinInet](../../mfc/wininet-basics.md)합니다. MFC WinInet 클래스를 사용 하는 방법에 대 한 일반 정보에 대 한 문서를 참조 [인터넷 WinInet를 사용한 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)합니다.  
  
> [!NOTE]
> `CInternetSession` throw 합니다는 [AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception) 지원 되지 않는 서비스 형식에 대 한 합니다. 다음 서비스 유형에 현재 지원: FTP, HTTP, gopher, 및 파일입니다.  
  
## <a name="inheritance-hierarchy"></a>상속 계층  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CInternetSession`  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** afxinet.h  
  
##  <a name="cinternetsession"></a>  CInternetSession::CInternetSession  
 이 멤버 함수를 호출 하는 경우는 `CInternetSession` 개체가 만들어집니다.  
  
```  
CInternetSession(
    LPCTSTR pstrAgent = NULL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,  
    LPCTSTR pstrProxyName = NULL,  
    LPCTSTR pstrProxyBypass = NULL,  
    DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrAgent`  
 응용 프로그램이 나 인터넷 함수 (예를 들어 "Microsoft 인터넷 브라우저")를 호출 하는 엔터티 이름을 식별 하는 문자열에 대 한 포인터입니다. 경우 `pstrAgent` 은 **NULL** 프레임 워크 (기본값), 전역 함수를 호출 [AfxGetAppName](application-information-and-management.md#afxgetappname), 응용 프로그램의 이름을 포함 하는 null로 끝나는 문자열을 반환 하는 합니다. 일부 프로토콜이이 문자열을 사용 하 여 서버에 응용 프로그램을 식별 합니다.  
  
 `dwContext`  
 작업에 대 한 컨텍스트 식별자입니다. `dwContext` 반환한 작업의 상태 정보를 식별 [cinternetsession:: Onstatuscallback](#onstatuscallback)합니다. 기본값은 1로 설정 그러나 작업에 대 한 특정 컨텍스트 ID를 명시적으로 할당할 수 있습니다. 개체와 수행 하는 작업 컨텍스트 ID와 가진 연결 됩니다.  
  
 `dwAccessType`  
 필요한 액세스의 형식입니다. 다음은 유효한 값을는 정확히 하나의 제공 될 수 있습니다.  
  
- **INTERNET_OPEN_TYPE_PRECONFIG** 레지스트리에서 미리 구성 된 설정을 사용 하 여 연결 합니다. 이 액세스 형식은 기본값으로 설정 됩니다. TIS 프록시를 통해 연결할 설정 `dwAccessType` ;이 값으로 설정한 레지스트리에 적절 하 게 합니다.  
  
- `INTERNET_OPEN_TYPE_DIRECT` 인터넷에 직접 연결 합니다.  
  
- `INTERNET_OPEN_TYPE_PROXY` CERN 프록시를 통해 연결 합니다.  
  
 다양 한 유형의 프록시를 사용 하 여 연결에 대 한 자세한 내용은 참조 [일반적인 FTP 클라이언트 응용 프로그램의 단계를](../../mfc/steps-in-a-typical-ftp-client-application.md)합니다.  
  
 *pstrProxyName*  
 기본 설정 CERN 프록시의 이름을 경우 `dwAccessType` 로 설정 되어 `INTERNET_OPEN_TYPE_PROXY`합니다. 기본값은 **NULL**합니다.  
  
 *pstrProxyBypass*  
 서버 주소는 선택적 목록을 포함 하는 문자열에 대 한 포인터입니다. 프록시 액세스를 사용 하는 경우 이러한 주소를 건너뛸 수 있습니다. 경우는 **NULL** 값이 제공, 바이패스 목록 레지스트리에서 읽을 수는 있습니다. 이 매개 변수는 의미 있는 경우에만 `dwAccessType` 로 설정 된 `INTERNET_OPEN_TYPE_PROXY`합니다.  
  
 `dwFlags`  
 다양 한 캐싱 옵션을 나타냅니다. 기본값은 0으로 설정 됩니다. 가능한 값은 다음과 같습니다.  
  
- `INTERNET_FLAG_DONT_CACHE` 로컬 또는 게이트웨이 서버를 모두에서 데이터를 캐시 하지 마십시오.  
  
- `INTERNET_FLAG_OFFLINE` 다운로드 작업은 영구 캐시를 통해 도달 됩니다. 항목이 캐시에 없는 경우 적절 한 오류 코드가 반환 됩니다. 이 플래그의 비트와 함께 `OR` ( **&#124;**) 연산자.  
  
### <a name="remarks"></a>설명  
 **CInternetSession** 함수인는 첫 번째 인터넷 응용 프로그램에서 호출 합니다. 내부 데이터 구조를 초기화 하 고 응용 프로그램의 이후 호출에 대해 준비 합니다.  
  
 인터넷 연결을 열 수 있는, `CInternetSession` throw 한 [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)합니다.  
  
### <a name="example"></a>예  
  예를 참조 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)합니다.  
  
##  <a name="close"></a>  CInternetSession::Close  
 응용 프로그램 사용 하 여 완료 되 면이 함수를 호출는 `CInternetSession` 개체입니다.  
  
```  
virtual void Close();
```  
  
### <a name="example"></a>예  
  예를 참조 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)합니다.  
  
##  <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback  
 상태 콜백을 사용 하도록 설정 하려면이 함수를 호출 합니다.  
  
```  
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```  
  
### <a name="parameters"></a>매개 변수  
 `bEnable`  
 콜백 사용 되는지 여부를 지정 합니다. 기본값은 **TRUE**합니다.  
  
### <a name="return-value"></a>반환 값  
 성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출이 실패 한 경우 throw 되는 검사 하 여 오류의 원인을 결정 [CInternetException](../../mfc/reference/cinternetexception-class.md) 개체입니다.  
  
### <a name="remarks"></a>설명  
 상태 콜백이 처리할 때는 응용 프로그램의 상태 표시줄에 (예: 이름 확인, 서버 및 기타 등등에 연결) 작업의 진행률에 대 한 상태를 제공할 수 있습니다. 장기 작업 하는 동안 작업 상태 표시는 특히이 좋습니다.  
  
 콜백을 요청의 처리 중에 발생 하기 때문에 응용 프로그램 네트워크에 데이터 처리량의 성능 저하를 방지 하기 위해 콜백에서 가능한 최소한의 시간을 할애 해야 합니다. 예를 들어 콜백에서 대화 상자를 배치 이러한 긴 작업 서버 종료 요청을 수 있습니다.  
  
 상태 콜백 콜백은 보류 중인으로 제거할 수 없습니다.  
  
 모든 작업을 비동기적으로 처리 하려면 고유한 스레드를 만들거나 MFC 없이 WinInet 함수를 사용 해야 합니다.  
  
##  <a name="getcontext"></a>  CInternetSession::GetContext  
 특정 응용 프로그램 세션에 대 한 상황에 맞는 값을 가져오려면이 함수를 호출 합니다.  
  
```  
DWORD_PTR GetContext() const;  
```  
  
### <a name="return-value"></a>반환 값  
 응용 프로그램 정의 컨텍스트 식별자입니다.  
  
### <a name="remarks"></a>설명  
 [OnStatusCallback](#onstatuscallback) 에서 반환 된 컨텍스트 ID를 사용 하 여 **GetContext** 특정 응용 프로그램의 상태를 보고 합니다. 예를 들어, 사용자 상태 정보를 반환 하는 인터넷 요청을 활성화할 때 상태 콜백이 해당 특정 요청에서 상태 보고 컨텍스트 ID를 사용 합니다. 사용자가 두 개의 별도 활성화 하는 경우 인터넷 요청 상태 정보를 반환 둘 다 포함 `OnStatusCallback` 컨텍스트 식별자를 사용 하 여 해당 요청에 대 한 상태를 반환 합니다. 따라서 모든 상태 콜백 작업에 대 한 컨텍스트 식별자를 사용 하 고 세션은 세션이 종료 될 때까지 연관 된 합니다.  
  
 비동기 작업에 대 한 자세한 내용은 문서 참조 [인터넷 첫 번째 단계: WinInet](../../mfc/wininet-basics.md)합니다.  
  
##  <a name="getcookie"></a>  CInternetSession::GetCookie  
 이 멤버 함수는 Win32 함수의 동작을 구현 [InternetGetCookie](http://msdn.microsoft.com/library/windows/desktop/aa384710)Windows SDK에 설명 된 대로 합니다.  
  
```  
static BOOL GetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    LPTSTR pstrCookieData,  
    DWORD dwBufLen);

 
static BOOL GetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    CString& strCookieData);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrUrl`  
 URL을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrCookieName`  
 지정된 된 URL에 대 한 쿠키의 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrCookieData`  
 첫 번째 오버 로드에서 쿠키 데이터를 수신 하는 버퍼의 주소를 포함 하는 문자열에 대 한 포인터입니다. 이 값 **NULL**합니다. 두 번째 오버 로드에 대 한 참조는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 쿠키 데이터를 받을 개체입니다.  
  
 `dwBufLen`  
 크기를 지정 하는 변수는 `pstrCookieData` 버퍼입니다. 버퍼에 복사 하는 데이터의 양을 수신 함수가 성공 하면는 `pstrCookieData` 버퍼입니다. 경우 `pstrCookieData` 은 **NULL**,이 매개 변수는 모든 쿠키 데이터를 복사 하는 데 필요한 버퍼의 크기를 지정 하는 값을 받습니다.  
  
### <a name="return-value"></a>반환 값  
 반환 **TRUE** 성공 하면 또는 **FALSE** 그렇지 않은 경우. 호출이 실패 한 경우 Win32 함수 호출 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) 오류의 원인을 확인 합니다. 다음 오류 값이 적용 됩니다.  
  
- **ERROR_NO_MORE_ITEMS** 지정된 된 URL에 대 한 쿠키가 없는 모든 부모입니다.  
  
- **ERROR_INSUFFICIENT_BUFFER** 전달 된 값 `dwBufLen` 모든 쿠키 데이터를 복사 하기에 부족 합니다. 반환 된 값 `dwBufLen` 버퍼의 크기를 모든 데이터를 사용 하는 데 필요한입니다.  
  
### <a name="remarks"></a>설명  
 두 번째 오버 로드에서 MFC에 제공 된 쿠키 데이터를 검색 `CString` 개체입니다.  
  
##  <a name="getcookielength"></a>  CInternetSession::GetCookieLength  
 이 버퍼에 저장 하는 쿠키의 길이를 가져오는 함수를 호출 합니다.  
  
```  
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrUrl`  
 URL을 포함 하는 문자열에 대 한 포인터  
  
 `pstrCookieName`  
 쿠키의 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 A `DWORD` 버퍼에 저장 하는 쿠키의 길이 나타내는 값입니다. 표시 이름으로 0 이면 쿠키가 없는 `pstrCookieName` 존재 합니다.  
  
### <a name="remarks"></a>설명  
 이 값은 사용 하 여 [GetCookie](#getcookie)합니다.  
  
##  <a name="getftpconnection"></a>  Cinternetsession:: Getftpconnection  
 FTP 연결을 설정 및 가져오기에 대 한 포인터를이 멤버 함수 호출을 `CFtpConnection` 개체입니다.  
  
```  
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    BOOL bPassive = FALSE);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrServer`  
 FTP 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrUserName`  
 사용자가 로그인의 이름을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. 경우 **NULL**, 기본값은 익명입니다.  
  
 `pstrPassword`  
 로그인에 사용할 암호를 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다. 두 `pstrPassword` 및 `pstrUserName` 는 **NULL**, 기본 익명 암호는 사용자의 전자 메일 이름입니다. 경우 `pstrPassword` 은 **NULL** (또는 빈 문자열) 하지만 `pstrUserName` 않습니다 **NULL**, 빈 암호가 사용 됩니다. 다음 표에서 설명의 가능한 네 가지 설정에 대 한 동작 `pstrUserName` 및 `pstrPassword`:  
  
|`pstrUserName`|`pstrPassword`|FTP 서버에 전송 하는 사용자 이름|FTP 서버에 전송 하는 암호|  
|--------------------|--------------------|---------------------------------|---------------------------------|  
|**NULL** 또는 ""|**NULL** 또는 ""|"anonymous"|사용자의 전자 메일 이름|  
|비- **NULL** 문자열|**NULL** 또는 ""|`pstrUserName`|" "|  
|**NULL** 비- **NULL** 문자열|**오류**|**오류**||  
|비- **NULL** 문자열|비- **NULL** 문자열|`pstrUserName`|`pstrPassword`|  
  
 `nPort`  
 서버에서 사용 하는 TCP/IP 포트를 식별 하는 번호입니다.  
  
 `bPassive`  
 이 FTP 세션에 대 한 passive 또는 active 모드를 지정합니다. 경우로 설정 **TRUE**, Win32 API 설정 `dwFlag` 를 **INTERNET_FLAG_PASSIVE**합니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 [CFtpConnection](../../mfc/reference/cftpconnection-class.md) 개체입니다. 호출이 실패 한 경우 throw 되는 검사 하 여 오류의 원인을 결정 [CInternetException](../../mfc/reference/cinternetexception-class.md) 개체입니다.  
  
### <a name="remarks"></a>설명  
 `GetFtpConnection` FTP 서버에 연결 하 고 만들고 반환에 대 한 포인터는 **CFTPConnection** 개체입니다. 서버에 대해 특정 작업을 수행 하지는 않습니다. 파일에 쓰거나 읽을 하려는 별도 단계로 이러한 작업을 수행 해야 예를 들어 있습니다. 클래스를 참조 하십시오. [CFtpConnection](../../mfc/reference/cftpconnection-class.md) 및 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md) 파일을 검색 하는 방법에 대 한 정보에 대 한 파일을 열을 읽거나 파일에 쓸 수 있습니다. 문서를 참조 [인터넷 WinInet를 사용한 프로그래밍](../../mfc/win32-internet-extensions-wininet.md) 단계에서 일반적인 FTP 연결 작업을 수행 합니다.  
  
### <a name="example"></a>예  
  예를 참조 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)합니다.  
  
##  <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection  
 호출에 대 한 포인터를 가져와서 새 gopher 연결을 설정 하려면이 함수는 `CGopherConnection` 개체입니다.  
  
```  
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrServer`  
 Gopher 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrUserName`  
 사용자 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrPassword`  
 액세스 암호를 포함 하는 문자열에 대 한 포인터입니다.  
  
 `nPort`  
 서버에서 사용 하는 TCP/IP 포트를 식별 하는 번호입니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md) 개체입니다. 호출이 실패 한 경우 throw 되는 검사 하 여 오류의 원인을 결정 [CInternetException](../../mfc/reference/cinternetexception-class.md) 개체입니다.  
  
### <a name="remarks"></a>설명  
 `GetGopherConnection` gopher 서버에 연결 하 고 만들고 반환에 대 한 포인터는 `CGopherConnection` 개체입니다. 서버에 대해 특정 작업을 수행 하지는 않습니다. 데이터를 읽거나 하려는 별도 단계로 이러한 작업을 수행 해야 예를 들어 있습니다. 클래스를 참조 하십시오. [CGopherConnection](../../mfc/reference/cgopherconnection-class.md), [CGopherFile](../../mfc/reference/cgopherfile-class.md), 및 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md) 파일을 검색 하는 방법에 대 한 정보에 대 한 파일을 열을 읽거나 파일에 쓸 수 있습니다. FTP 사이트를 탐색 하는 방법에 대 한 정보를 멤버 함수를 참조 하십시오. [OpenURL](#openurl)합니다. 문서 참조 [인터넷 WinInet를 사용한 프로그래밍](../../mfc/win32-internet-extensions-wininet.md) 단계에서 일반적인 gopher 연결 작업을 수행 합니다.  
  
##  <a name="gethttpconnection"></a>  CInternetSession::GetHttpConnection  
 이 멤버 함수에 대 한 포인터를 HTTP 연결을 설정할 호출는 `CHttpConnection` 개체입니다.  
  
```  
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL);

 
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,  
    DWORD dwFlags,  
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,  
    LPCTSTR pstrUserName = NULL,  
    LPCTSTR pstrPassword = NULL);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrServer`  
 HTTP 서버 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `nPort`  
 서버에서 사용 하는 TCP/IP 포트를 식별 하는 번호입니다.  
  
 `pstrUserName`  
 사용자 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrPassword`  
 액세스 암호를 포함 하는 문자열에 대 한 포인터입니다.  
  
 *dwflags*  
 어떠한 조합의 **INTERNET_ FLAG_\***  플래그입니다. 표를 참조는 **주의** 섹션 [CHttpConnection::OpenRequest](../../mfc/reference/chttpconnection-class.md#openrequest) 에 대 한 설명은 `dwFlags` 값입니다.  
  
### <a name="return-value"></a>반환 값  
 에 대 한 포인터는 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 개체입니다. 호출이 실패 한 경우 throw 되는 검사 하 여 오류의 원인을 결정 [CInternetException](../../mfc/reference/cinternetexception-class.md) 개체입니다.  
  
### <a name="remarks"></a>설명  
 `GetHttpConnection` HTTP 서버에 연결 하 고 만들고 반환에 대 한 포인터는 `CHttpConnection` 개체입니다. 서버에 대해 특정 작업을 수행 하지는 않습니다. HTTP 헤더를 쿼리 하려는 경우 별도 단계로이 작업을 수행 해야 예를 들어 있습니다. 클래스를 참조 하십시오. [CHttpConnection](../../mfc/reference/chttpconnection-class.md) 및 [CHttpFile](../../mfc/reference/chttpfile-class.md) 작업 대 한 정보는 HTTP 서버에 연결을 사용 하 여 수행할 수 있습니다. HTTP 사이트를 탐색 하는 방법에 대 한 정보를 멤버 함수를 참조 하십시오. [OpenURL](#openurl)합니다. 문서를 참조 [인터넷 WinInet를 사용한 프로그래밍](../../mfc/win32-internet-extensions-wininet.md) 단계에서 일반적인 HTTP 연결 작업을 수행 합니다.  
  
##  <a name="onstatuscallback"></a>  Cinternetsession:: Onstatuscallback  
 이 멤버 함수는 상태 콜백이 활성화 되어 있고 작업이 보류 중인 상태를 업데이트 하기 위해 프레임 워크에 의해 호출 됩니다.  
  
```  
virtual void OnStatusCallback(
    DWORD_PTR dwContext,  
    DWORD dwInternetStatus,  
    LPVOID lpvStatusInformation,  
    DWORD dwStatusInformationLength);
```  
  
### <a name="parameters"></a>매개 변수  
 `dwContext`  
 응용 프로그램에서 제공 된 컨텍스트 값입니다.  
  
 `dwInternetStatus`  
 콜백이 수행 되는 이유를 나타내는 상태 코드입니다. 참조 **주의** 가능한 값의 테이블에 대 한 합니다.  
  
 `lpvStatusInformation`  
 이 콜백은 관련 된 정보를 포함 하는 버퍼에 대 한 포인터입니다.  
  
 `dwStatusInformationLength`  
 `lpvStatusInformation`의 크기입니다.  
  
### <a name="remarks"></a>설명  
 호출 해야 [EnableStatusCallback](#enablestatuscallback) 상태 콜백 기능을 활용할 수 있습니다.  
  
 `dwInternetStatus` 매개 변수 수행 되는 작업을 나타내며의 내용을 결정 `lpvStatusInformation` 됩니다. `dwStatusInformationLength` 에 포함 된 데이터의 길이 나타냅니다 `lpvStatusInformation`합니다. 다음 상태에 대 한 값 `dwInternetStatus` ´ ï ´ ù.  
  
|값|의미|  
|-----------|-------------|  
|`INTERNET_STATUS_RESOLVING_NAME`|에 포함 된 이름의 IP 주소를 찾는 `lpvStatusInformation`합니다.|  
|`INTERNET_STATUS_NAME_RESOLVED`|에 포함 된 이름의 IP 주소를 찾았습니다 `lpvStatusInformation`합니다.|  
|`INTERNET_STATUS_CONNECTING_TO_SERVER`|소켓 주소에 연결 ( [SOCKADDR](../../mfc/reference/sockaddr-structure.md))로 가리키는 `lpvStatusInformation`합니다.|  
|`INTERNET_STATUS_CONNECTED_TO_SERVER`|소켓 주소에 연결 했습니다. ( `SOCKADDR`)로 가리키는 `lpvStatusInformation`합니다.|  
|`INTERNET_STATUS_SENDING_REQUEST`|서버에 정보 요청을 전송 합니다. `lpvStatusInformation` 매개 변수는 **NULL**합니다.|  
|**INTERNET_STATUS_ REQUEST_SENT**|서버에 정보 요청을 보냈습니다. `lpvStatusInformation` 매개 변수는 **NULL**합니다.|  
|`INTERNET_STATUS_RECEIVING_RESPONSE`|서버 요청에 응답을 기다리는 중입니다. `lpvStatusInformation` 매개 변수는 **NULL**합니다.|  
|`INTERNET_STATUS_RESPONSE_RECEIVED`|서버에서 성공적으로 응답을 받았습니다. `lpvStatusInformation` 매개 변수는 **NULL**합니다.|  
|`INTERNET_STATUS_CLOSING_CONNECTION`|서버에 연결을 닫는 중입니다. `lpvStatusInformation` 매개 변수는 **NULL**합니다.|  
|`INTERNET_STATUS_CONNECTION_CLOSED`|서버에 연결을 성공적으로 종료 합니다. `lpvStatusInformation` 매개 변수는 **NULL**합니다.|  
|`INTERNET_STATUS_HANDLE_CREATED`|Win32 API 함수에 의해 사용 [InternetConnect](http://msdn.microsoft.com/library/windows/desktop/aa384363) 새 핸들 만들었음을 나타냅니다. 이렇게 하면 응용 프로그램 호출 Win32 함수 [InternetCloseHandle](http://msdn.microsoft.com/library/windows/desktop/aa384350) 다른 스레드에서 너무 오래 걸리면 연결 합니다. 이러한 함수에 대 한 자세한 내용은 Windows SDKfor를 참조 하십시오.|  
|`INTERNET_STATUS_HANDLE_CLOSING`|핸들 값이 성공적으로 종료 되었습니다.|  
  
 상태 콜백 루틴을 수행 하기 전에 특별 한 조치를 요구 하려면이 멤버 함수를 재정의 합니다.  
  
> [!NOTE]
>  상태 콜백 스레드 상태 보호가 필요 합니다. MFC 공유 라이브러리를 사용 하는 경우 재정의의 시작 부분에 다음 줄을 추가 합니다.  
  
 [!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]  
  
 비동기 작업에 대 한 자세한 내용은 문서 참조 [인터넷 첫 번째 단계: WinInet](../../mfc/wininet-basics.md)합니다.  
  
##  <a name="openurl"></a>  CInternetSession::OpenURL  
 HTTP 서버에 지정 된 요청을 보내고 MIME 클라이언트 추가 RFC822 지정을 허용 하는 함수 또는 요청과 함께 보낼 HTTP 헤더에는이 멤버를 호출 합니다.  
  
```  
CStdioFile* OpenURL(
    LPCTSTR pstrURL,  
    DWORD_PTR dwContext = 1,  
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,  
    LPCTSTR pstrHeaders = NULL,  
    DWORD dwHeadersLength = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 *pstrURL*  
 읽기를 시작할 URL의 이름에 대 한 포인터입니다. Url만 파일 부터는:, ftp:, gopher:, 또는 http: 지원 됩니다. **ASSERT** 경우 *pszURL* 은 **NULL**합니다.  
  
 `dwContext`  
 응용 프로그램 정의 값 콜백에서 반환된 된 핸들을 전달.  
  
 `dwFlags`  
 이 연결을 처리 하는 방법을 설명 하는 플래그입니다. 참조 **주의** 유효한 플래그에 대 한 자세한 내용은 합니다. 유효한 플래그는:  
  
- **INTERNET_FLAG_TRANSFER_ASCII** 기본값입니다. ASCII 텍스트 파일을 전송 합니다.  
  
- **INTERNET_FLAG_TRANSFER_BINARY** 이진 파일로 파일을 전송 합니다.  
  
- `INTERNET_FLAG_RELOAD` 로컬로 캐시 된 경우에 데이터를 통신에서 가져옵니다.  
  
- `INTERNET_FLAG_DONT_CACHE` 로컬 또는 게이트웨이 모두에서 데이터를 캐시 하지 마십시오.  
  
- `INTERNET_FLAG_SECURE` 이 플래그는 HTTP 요청에 적용할 수 있습니다. Secure Sockets Layer 또는 PCT. 통신 중에 보안 트랜잭션을 요청합니다  
  
- **INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT** 에 의해 생성 된 새 요청에 대 한 서버에 대 한 기존 연결 다시 사용 가능한 경우 **OpenUrl** 각 연결 요청에 대 한 새 세션을 만드는 대신 합니다.  
  
- **INTERNET_FLAG_PASSIVE** FTP 사이트에 사용 합니다. 수동 FTP 의미 체계를 사용 합니다. 함께 사용할 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) 의 `OpenURL`합니다.  
  
 `pstrHeaders`  
 HTTP 서버에 보내야 하는 헤더를 포함 하는 문자열에 대 한 포인터입니다.  
  
 *dwHeadersLength*  
 추가 헤더의 문자 길이입니다. -1l 이것이 및 `pstrHeaders` 이 아닌 **NULL**, 다음 `pstrHeaders` 0으로 종료 되 고 길이 계산 간주 됩니다.  
  
### <a name="return-value"></a>반환 값  
 FTP, GOPHER, HTTP 및 파일 형식 인터넷 서비스에 대 한 파일 핸들을 반환합니다. 반환 **NULL** 실패 한 경우 구문 분석 합니다.  
  
 포인터는 `OpenURL` 반환에 따라 달라 집니다 *pszURL*의 서비스의 유형입니다. 아래 표에서 가능한 포인터를 보여 줍니다. `OpenURL` 반환할 수 있습니다.  
  
|URL 형식|반환 값|  
|--------------|-------------|  
|file://|**CStdioFile\\\***|  
|http://|**CHttpFile\\\***|  
|gopher://|**CGopherFile\\\***|  
|ftp: / /|**CInternetFile\\\***|  
  
### <a name="remarks"></a>설명  
 매개 변수 `dwFlags` 하나를 포함 해야 **INTERNET_FLAG_TRANSFER_ASCII** 또는 **INTERNET_FLAG_TRANSFER_BINARY**, 둘 중 하나입니다. 나머지 플래그 비트와 결합할 수 있습니다 `OR` 연산자 ( **&#124;**).  
  
 `OpenURL`Win32 함수를 래핑하는 **InternetOpenURL**만 다운로드, 검색 및 인터넷 서버에서 데이터 읽기를 허용 합니다. `OpenURL` no 필요 없는 파일 조작 원격 위치에서 허용 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md) 개체입니다.  
  
 특정 연결을 사용 하려면 (즉, 프로토콜 관련) 함수, 파일에 쓰기 등 세션을 열고, 다음 특정 종류의 연결을 열고 다음 해야 해당 연결을 사용 하 여 원하는 모드에서 한 파일을 엽니다. 참조 `CInternetConnection` 연결에 대 한 함수에 대 한 자세한 내용은 합니다.  
  
##  <a name="operator_hinternet"></a>  CInternetSession::operator HINTERNET  
 이 연산자를 사용 하 여 현재 인터넷 세션에 대 한 Windows 핸들을 가져올 수 있습니다.  
  
```  
operator HINTERNET() const;  
```  
  
##  <a name="setcookie"></a>  CInternetSession::SetCookie  
 지정된 된 URL에 대 한 쿠키를 설정 합니다.  
  
```  
static BOOL SetCookie(
    LPCTSTR pstrUrl,  
    LPCTSTR pstrCookieName,  
    LPCTSTR pstrCookieData);
```  
  
### <a name="parameters"></a>매개 변수  
 `pstrUrl`  
 쿠키를 설정 해야 하는 URL을 지정 하는 null로 끝나는 문자열에 대 한 포인터입니다.  
  
 `pstrCookieName`  
 쿠키의 이름을 포함 하는 문자열에 대 한 포인터입니다.  
  
 `pstrCookieData`  
 URL에 연결할 실제 문자열 데이터가 포함 된 문자열에 대 한 포인터입니다.  
  
### <a name="return-value"></a>반환 값  
 반환 **TRUE** 성공 하면 또는 **FALSE** 그렇지 않은 경우. 특정 오류 코드를 가져오려면 호출 **GetLastError 합니다.**  
  
### <a name="remarks"></a>설명  
 이 멤버 함수는 Win32 메시지의 동작을 구현 [InternetSetCookie](http://msdn.microsoft.com/library/windows/desktop/aa385107)Windows SDK에 설명 된 대로 합니다.  
  
##  <a name="setoption"></a>  CInternetSession::SetOption  
 인터넷 세션에 대 한 옵션을 설정 하려면이 함수를 호출 합니다.  
  
```  
BOOL SetOption(
    DWORD dwOption,  
    LPVOID lpBuffer,  
    DWORD dwBufferLength,  
    DWORD dwFlags = 0);

 
BOOL SetOption(
    DWORD dwOption,  
    DWORD dwValue,  
    DWORD dwFlags = 0);
```  
  
### <a name="parameters"></a>매개 변수  
 `dwOption`  
 인터넷 옵션 설정입니다. 참조 [옵션 플래그](http://msdn.microsoft.com/library/windows/desktop/aa385328) Windows SDKfor 가능한 옵션 목록에에서 있습니다.  
  
 `lpBuffer`  
 옵션 설정을 포함 하는 버퍼입니다.  
  
 *dwBufferLength*  
 길이가 `lpBuffer` 의 크기 또는 `dwValue`합니다.  
  
 `dwValue`  
 A `DWORD` 옵션 설정이 들어 있는입니다.  
  
 `dwFlags`  
 다양 한 캐싱 옵션을 나타냅니다. 기본값은 0으로 설정 됩니다. 가능한 값은 다음과 같습니다.  
  
- `INTERNET_FLAG_DONT_CACHE` 로컬 또는 게이트웨이 서버를 모두에서 데이터를 캐시 하지 마십시오.  
  
- `INTERNET_FLAG_OFFLINE` 다운로드 작업은 영구 캐시를 통해 도달 됩니다. 항목이 캐시에 없는 경우 적절 한 오류 코드가 반환 됩니다. 이 플래그의 비트와 함께 `OR` ( **&#124;**) 연산자.  
  
### <a name="return-value"></a>반환 값  
 작업에 성공 하면 값이 **TRUE** 반환 됩니다. 오류가 발생 한 값 경우 **FALSE** 반환 됩니다. Win32 함수 호출이 실패 한 경우 [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360) 오류의 원인을 확인 하기 위해 호출할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [CObject 클래스](../../mfc/reference/cobject-class.md)   
 [계층 구조 차트](../../mfc/hierarchy-chart.md)   
 [CInternetConnection 클래스](../../mfc/reference/cinternetconnection-class.md)   
 [CHttpConnection 클래스](../../mfc/reference/chttpconnection-class.md)   
 [CFtpConnection 클래스](../../mfc/reference/cftpconnection-class.md)   
 [CGopherConnection 클래스](../../mfc/reference/cgopherconnection-class.md)
