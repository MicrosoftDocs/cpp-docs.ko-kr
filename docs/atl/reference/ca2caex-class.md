---
description: '자세히 알아보기: CA2CAEX 클래스'
title: CA2CAEX 클래스
ms.date: 11/04/2016
f1_keywords:
- CA2CAEX
- ATLCONV/ATL::CA2CAEX
- ATLCONV/ATL::CA2CAEX::CA2CAEX
- ATLCONV/ATL::CA2CAEX::m_psz
helpviewer_keywords:
- CA2CAEX class
ms.assetid: 388e7c1d-a144-474c-a182-b15f69a74bd8
ms.openlocfilehash: 89709280e94e07c549d179dc9a9863bd4bf2cbaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97158597"
---
# <a name="ca2caex-class"></a>CA2CAEX 클래스

이 클래스는 문자열 변환 매크로 CA2CTEX 및 CT2CAEX 및 typedef CA2CA에 사용 됩니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```cpp
template<int t_nBufferLength = 128>
class CA2CAEX
```

### <a name="parameters"></a>매개 변수

*t_nBufferLength*<br/>
변환 프로세스에 사용 되는 버퍼의 크기입니다. 기본 길이는 128 바이트입니다.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CA2CAEX::CA2CAEX](#ca2caex)|생성자입니다.|
|[CA2CAEX:: ~ CA2CAEX](#dtor)|소멸자입니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CA2CAEX:: operator LPCSTR](#operator_lpcstr)|변환 연산자입니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CA2CAEX:: m_psz](#m_psz)|원본 문자열을 저장 하는 데이터 멤버입니다.|

## <a name="remarks"></a>설명

추가 기능이 필요 하지 않은 경우 CA2CTEX, CT2CAEX 또는 CA2CA를 고유한 코드에 사용 합니다.

이 클래스는 루프에서 사용 하기 안전 하며 스택을 오버플로 하지 않습니다. 기본적으로 ATL 변환 클래스와 매크로는 현재 스레드의 ANSI 코드 페이지를 변환에 사용합니다.

다음 매크로는이 클래스를 기반으로 합니다.

- CA2CTEX

- CT2CAEX

다음 typedef는이 클래스를 기반으로 합니다.

- CA2CA

이러한 텍스트 변환 매크로에 대 한 설명은 [ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md)를 참조 하세요.

## <a name="example"></a>예제

이러한 문자열 변환 매크로를 사용 하는 예제는 [ATL 및 MFC 문자열 변환 매크로](string-conversion-macros.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

**헤더:**

## <a name="ca2caexca2caex"></a><a name="ca2caex"></a> CA2CAEX::CA2CAEX

생성자입니다.

```cpp
CA2CAEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2CAEX(LPCSTR psz) throw(...);
```

### <a name="parameters"></a>매개 변수

*psz*<br/>
변환할 텍스트 문자열입니다.

*nCodePage*<br/>
이 클래스에서 사용 되지 않습니다.

### <a name="remarks"></a>설명

변환에 필요한 버퍼를 만듭니다.

## <a name="ca2caexca2caex"></a><a name="dtor"></a> CA2CAEX:: ~ CA2CAEX

소멸자입니다.

```cpp
~CA2CAEX() throw();
```

### <a name="remarks"></a>설명

할당 된 버퍼를 해제 합니다.

## <a name="ca2caexm_psz"></a><a name="m_psz"></a> CA2CAEX:: m_psz

원본 문자열을 저장 하는 데이터 멤버입니다.

```cpp
LPCSTR m_psz;
```

## <a name="ca2caexoperator-lpcstr"></a><a name="operator_lpcstr"></a> CA2CAEX:: operator LPCSTR

변환 연산자입니다.

```cpp
operator LPCSTR() const throw();
```

### <a name="return-value"></a>반환 값

텍스트 문자열을 LPCSTR 형식으로 반환 합니다.

## <a name="see-also"></a>참고 항목

[CA2AEX 클래스](../../atl/reference/ca2aex-class.md)<br/>
[CA2WEX 클래스](../../atl/reference/ca2wex-class.md)<br/>
[CW2AEX 클래스](../../atl/reference/cw2aex-class.md)<br/>
[CW2CWEX 클래스](../../atl/reference/cw2cwex-class.md)<br/>
[CW2WEX 클래스](../../atl/reference/cw2wex-class.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)
