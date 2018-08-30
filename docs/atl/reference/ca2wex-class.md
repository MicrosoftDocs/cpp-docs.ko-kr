---
title: CA2WEX 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 095d0d74fe5ff6eb30866b619e201a029b754d38
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202178"
---
# <a name="ca2wex-class"></a>CA2WEX 클래스
이 클래스는 문자열 변환 매크로 CA2TEX, CA2CTEX, CT2WEX, 및 CT2CWEX와 CA2W typedef에서 사용 됩니다.  
  
> [!IMPORTANT]
>  이 클래스 및 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.  
  
## <a name="syntax"></a>구문  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>매개 변수  
 *t_nBufferLength*  
 변환 프로세스에서 사용 되는 버퍼의 크기입니다. 기본 길이 128 바이트입니다.  
  
## <a name="members"></a>멤버  
  
### <a name="public-constructors"></a>Public 생성자  
  
|이름|설명|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|생성자입니다.|  
|[CA2WEX:: ~ CA2WEX](#dtor)|소멸자입니다.|  
  
### <a name="public-operators"></a>Public 연산자  
  
|이름|설명|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|변환 연산자입니다.|  
  
### <a name="public-data-members"></a>공용 데이터 멤버  
  
|이름|설명|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|소스 문자열을 저장 하는 데이터 멤버입니다.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|변환된 된 문자열을 저장 하는 데 정적 버퍼입니다.|  
  
## <a name="remarks"></a>설명  
 추가 기능은 필요 하지 않으면 코드에서 CA2TEX "," CA2CTEX "," CT2WEX "," CT2CWEX, "또는" CA2W을 사용 합니다.  
  
 이 클래스는 변환의 결과 저장 하는 데 사용 되는 고정 크기 정적 버퍼를 포함 합니다. 클래스를 사용 하 여 메모리 할당 결과가 너무 커서 정적 버퍼에 맞지 않는 경우 **malloc**, 개체가 범위를 벗어나면 메모리를 해제 합니다. 이렇게 하면 텍스트와 달리이 클래스는 루프에서 사용 하기에 안전 하 고 스택이 오버플로되지 않습니다 하는 ATL의 이전 버전에서 사용할 수 있는 변환 매크로입니다.  
  
 클래스에 힙 및 실패에 대 한 메모리를 할당 하려고 하는 경우 호출 `AtlThrow` E_OUTOFMEMORY의 인수와 함께 합니다.  
  
 기본적으로 ATL 변환 클래스 및 매크로 변환에 대 한 현재 스레드의 ANSI 코드 페이지를 사용 합니다. 특정 변환에 대 한이 동작을 재정의 하려는 경우 코드 페이지 클래스의 생성자에 대 한 두 번째 매개 변수로 지정 합니다.  
  
 다음 매크로이 클래스를 기반으로 합니다.  
  
- CA2TEX  
  
- CA2CTEX  
  
- CT2WEX  
  
- CT2CWEX  
  
 다음 typedef는이 클래스를 기반으로 합니다.  
  
- CA2W  
  
 이러한 텍스트 변환 매크로의 논의 참조 하세요 [ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md)합니다.  
  
## <a name="example"></a>예제  
 참조 [ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md) 이러한 문자열 변환 매크로 사용의 예입니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** atlconv.h  
  
##  <a name="ca2wex"></a>  CA2WEX::CA2WEX  
 생성자입니다.  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>매개 변수  
 *psz*  
 변환할 텍스트 문자열입니다.  
  
 *nCodePage*  
 코드 페이지 변환을 수행 하는 데 사용 합니다. Windows SDK 함수에 대 한 코드 페이지 매개 변수 설명을 참조 하세요 [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar) 대 한 자세한 내용은 합니다.  
  
### <a name="remarks"></a>설명  
 변환 프로세스에서 사용 되는 버퍼를 할당 합니다.  
  
##  <a name="dtor"></a>  CA2WEX:: ~ CA2WEX  
 소멸자입니다.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>설명  
 할당된 된 버퍼를 해제합니다.  
  
##  <a name="m_psz"></a>  CA2WEX::m_psz  
 소스 문자열을 저장 하는 데이터 멤버입니다.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>  CA2WEX::m_szBuffer  
 변환된 된 문자열을 저장 하는 데 정적 버퍼입니다.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>  CA2WEX::operator LPWSTR  
 변환 연산자입니다.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>반환 값  
 LPWSTR 입력할 텍스트 문자열을 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [CA2AEX 클래스](../../atl/reference/ca2aex-class.md)   
 [CA2CAEX 클래스](../../atl/reference/ca2caex-class.md)   
 [CW2AEX 클래스](../../atl/reference/cw2aex-class.md)   
 [CW2CWEX 클래스](../../atl/reference/cw2cwex-class.md)   
 [CW2WEX 클래스](../../atl/reference/cw2wex-class.md)   
 [클래스 개요](../../atl/atl-class-overview.md)
