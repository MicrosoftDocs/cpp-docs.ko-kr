---
description: '자세히 알아보기: CW2AEX 클래스'
title: CW2AEX 클래스
ms.date: 11/04/2016
f1_keywords:
- CW2AEX
- ATLCONV/ATL::CW2AEX
- ATLCONV/ATL::CW2AEX::CW2AEX
- ATLCONV/ATL::CW2AEX::m_psz
- ATLCONV/ATL::CW2AEX::m_szBuffer
helpviewer_keywords:
- CW2AEX class
ms.assetid: 44dc2cf5-dd30-440b-a9b9-b21b43f49843
ms.openlocfilehash: dfb654c43f2549cc1cfe58be064b2e6b9621fc69
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97140285"
---
# <a name="cw2aex-class"></a>CW2AEX 클래스

이 클래스는 문자열 변환 매크로 CT2AEX, CW2TEX, CW2CTEX 및 CT2CAEX와 typedef CW2A에서 사용 됩니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template<int t_nBufferLength = 128>
class CW2AEX
```

#### <a name="parameters"></a>매개 변수

*t_nBufferLength*<br/>
변환 프로세스에 사용 되는 버퍼의 크기입니다. 기본 길이는 128 바이트입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CW2AEX::CW2AEX](#cw2aex)|생성자입니다.|
|[CW2AEX:: ~ CW2AEX](#dtor)|소멸자입니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CW2AEX:: operator LPSTR](#operator_lpstr)|변환 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CW2AEX:: m_psz](#m_psz)|원본 문자열을 저장 하는 데이터 멤버입니다.|
|[CW2AEX:: m_szBuffer](#m_szbuffer)|변환 된 문자열을 저장 하는 데 사용 되는 정적 버퍼입니다.|

## <a name="remarks"></a>설명

추가 기능이 필요 하지 않는 한 코드에서 CT2AEX, CW2TEX, CW2CTEX, CT2CAEX 또는 CW2A를 사용 합니다.

이 클래스는 변환 결과를 저장 하는 데 사용 되는 고정 크기 정적 버퍼를 포함 합니다. 결과가 너무 커서 정적 버퍼에 맞지 않는 경우 클래스는 **malloc** 를 사용 하 여 메모리를 할당 하 고 개체가 범위를 벗어나면 메모리를 비웁니다. 이렇게 하면 이전 버전의 ATL에서 사용할 수 있는 텍스트 변환 매크로와 달리이 클래스는 루프에서 사용 하 고 스택을 오버플로 하지 않습니다.

클래스가 힙에서 메모리를 할당 하려고 시도 하 고 실패 하는 경우 `AtlThrow` E_OUTOFMEMORY의 인수를 사용 하 여를 호출 합니다.

기본적으로 ATL 변환 클래스 및 매크로는 현재 스레드의 ANSI 코드 페이지를 사용 하 여 변환 합니다. 특정 변환에 대해이 동작을 재정의 하려면 코드 페이지를 클래스의 생성자에 대 한 두 번째 매개 변수로 지정 합니다.

다음 매크로는이 클래스를 기반으로 합니다.

- CT2AEX

- CW2TEX

- CW2CTEX

- CT2CAEX

다음 typedef는이 클래스를 기반으로 합니다.

- CW2A

이러한 텍스트 변환 매크로에 대 한 설명은 [ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md)를 참조 하세요.

## <a name="example"></a>예제

이러한 문자열 변환 매크로를 사용 하는 예제는 [ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="cw2aexcw2aex"></a><a name="cw2aex"></a> CW2AEX::CW2AEX

생성자입니다.

```
CW2AEX(LPCWSTR psz, UINT nCodePage) throw(...);
CW2AEX(LPCWSTR psz) throw(...);
```

### <a name="parameters"></a>매개 변수

*psz*<br/>
변환할 텍스트 문자열입니다.

*nCodePage*<br/>
변환을 수행 하는 데 사용 되는 코드 페이지입니다. 자세한 내용은 Windows SDK 함수 [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar) 에 대 한 코드 페이지 매개 변수 설명을 참조 하십시오.

### <a name="remarks"></a>설명

변환 프로세스에 사용 되는 버퍼를 할당 합니다.

## <a name="cw2aexcw2aex"></a><a name="dtor"></a> CW2AEX:: ~ CW2AEX

소멸자입니다.

```
~CW2AEX() throw();
```

### <a name="remarks"></a>설명

할당 된 버퍼를 해제 합니다.

## <a name="cw2aexm_psz"></a><a name="m_psz"></a> CW2AEX:: m_psz

원본 문자열을 저장 하는 데이터 멤버입니다.

```
LPSTR m_psz;
```

## <a name="cw2aexm_szbuffer"></a><a name="m_szbuffer"></a> CW2AEX:: m_szBuffer

변환 된 문자열을 저장 하는 데 사용 되는 정적 버퍼입니다.

```
char m_szBuffer[t_nBufferLength];
```

## <a name="cw2aexoperator-lpstr"></a><a name="operator_lpstr"></a> CW2AEX:: operator LPSTR

변환 연산자입니다.

```
operator LPSTR() const throw();
```

### <a name="return-value"></a>반환 값

텍스트 문자열을 LPSTR 형식으로 반환 합니다.

## <a name="see-also"></a>참고 항목

[CA2AEX 클래스](../../atl/reference/ca2aex-class.md)<br/>
[CA2CAEX 클래스](../../atl/reference/ca2caex-class.md)<br/>
[CA2WEX 클래스](../../atl/reference/ca2wex-class.md)<br/>
[CW2CWEX 클래스](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 클래스](../../atl/reference/cw2wex-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
