---
description: '자세한 정보: 레지스트리 데이터 교환 매크로'
title: 레지스트리 데이터 교환 매크로
ms.date: 11/04/2016
f1_keywords:
- atlplus/ATL::BEGIN_RDX_MAP
- atlplus/ATL::END_RDX_MAP
- atlplus/ATL::RDX_BINARY
- atlplus/ATL::RDX_CSTRING_TEXT
- atlplus/ATL::RDX_DWORD
- atlplus/ATL::RDX_TEXT
helpviewer_keywords:
- RegistryDataExchange function, macros
ms.assetid: c1bc5e79-2307-43d2-9d10-3a62ffadf473
ms.openlocfilehash: ecfc5617922fe0a1ec7b134f61093a4ed3962a54
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157778"
---
# <a name="registry-data-exchange-macros"></a>레지스트리 데이터 교환 매크로

이러한 매크로는 레지스트리 데이터 교환 작업을 수행 합니다.

|Name|설명|
|-|-|
|[BEGIN_RDX_MAP](#begin_rdx_map)|레지스트리 데이터 교환 맵의 시작을 표시 합니다.|
|[END_RDX_MAP](#end_rdx_map)|레지스트리 데이터 교환 맵의 끝을 표시 합니다.|
|[RDX_BINARY](#rdx_binary)|지정 된 레지스트리 항목을 바이트 형식의 지정 된 멤버 변수에 연결 합니다.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|지정 된 레지스트리 항목을 CString 형식의 지정 된 멤버 변수에 연결 합니다.|
|[RDX_DWORD](#rdx_dword)|지정 된 레지스트리 항목을 DWORD 형식의 지정 된 멤버 변수에 연결 합니다.|
|[RDX_TEXT](#rdx_text)|지정 된 레지스트리 항목을 TCHAR.H 형식의 지정 된 멤버 변수에 연결 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 이를 추가 합니다.

## <a name="begin_rdx_map"></a><a name="begin_rdx_map"></a> BEGIN_RDX_MAP

레지스트리 데이터 교환 맵의 시작을 표시 합니다.

```
BEGIN_RDX_MAP
```

### <a name="remarks"></a>설명

레지스트리 데이터 교환 맵 내에서 다음 매크로를 사용 하 여 시스템 레지스트리에서 항목을 읽고 씁니다.

|매크로|설명|
|-----------|-----------------|
|[RDX_BINARY](#rdx_binary)|지정 된 레지스트리 항목을 바이트 형식의 지정 된 멤버 변수에 연결 합니다.|
|[RDX_DWORD](#rdx_dword)|지정 된 레지스트리 항목을 DWORD 형식의 지정 된 멤버 변수에 연결 합니다.|
|[RDX_CSTRING_TEXT](#rdx_cstring_text)|지정 된 레지스트리 항목을 CString 형식의 지정 된 멤버 변수에 연결 합니다.|
|[RDX_TEXT](#rdx_text)|지정 된 레지스트리 항목을 TCHAR.H 형식의 지정 된 멤버 변수에 연결 합니다.|

코드에서 시스템 레지스트리와 RDX MAP에 지정 된 변수 간에 데이터를 교환 해야 할 때마다 BEGIN_RDX_MAP 전역 함수 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)또는 END_RDX_MAP 매크로를 사용 하 여 만든 것과 동일한 이름의 멤버 함수를 사용 해야 합니다.

## <a name="end_rdx_map"></a><a name="end_rdx_map"></a> END_RDX_MAP

레지스트리 데이터 교환 맵의 끝을 표시 합니다.

```
END_RDX_MAP
```

## <a name="rdx_binary"></a><a name="rdx_binary"></a> RDX_BINARY

지정 된 레지스트리 항목을 바이트 형식의 지정 된 멤버 변수에 연결 합니다.

```
RDX_BINARY(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>매개 변수

*rootkey*<br/>
레지스트리 키 루트입니다.

*가*<br/>
레지스트리 하위 키입니다.

*valuename*<br/>
레지스트리 키입니다.

*구성원과*<br/>
지정 된 레지스트리 항목과 연결할 멤버 변수입니다.

*member_size*<br/>
멤버 변수의 크기 (바이트)입니다.

### <a name="remarks"></a>설명

이 매크로는 BEGIN_RDX_MAP 및 END_RDX_MAP 매크로와 함께 사용 되어 멤버 변수를 지정 된 레지스트리 항목과 연결 합니다. 전역 함수 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)및 END_RDX_MAP 매크로를 사용 하 BEGIN_RDX_MAP 여 만든 것과 동일한 이름의 멤버 함수를 사용 하 여 시스템 레지스트리와 RDX MAP의 멤버 변수 간에 데이터 교환을 수행 해야 합니다.

## <a name="rdx_cstring_text"></a><a name="rdx_cstring_text"></a> RDX_CSTRING_TEXT

지정 된 레지스트리 항목을 CString 형식의 지정 된 멤버 변수에 연결 합니다.

```
RDX_CSTRING_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>매개 변수

*rootkey*<br/>
레지스트리 키 루트입니다.

*가*<br/>
레지스트리 하위 키입니다.

*valuename*<br/>
레지스트리 키입니다.

*구성원과*<br/>
지정 된 레지스트리 항목과 연결할 멤버 변수입니다.

*member_size*<br/>
멤버 변수의 크기 (바이트)입니다.

### <a name="remarks"></a>설명

이 매크로는 BEGIN_RDX_MAP 및 END_RDX_MAP 매크로와 함께 사용 되어 멤버 변수를 지정 된 레지스트리 항목과 연결 합니다. 전역 함수 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)및 END_RDX_MAP 매크로를 사용 하 BEGIN_RDX_MAP 여 만든 것과 동일한 이름의 멤버 함수를 사용 하 여 시스템 레지스트리와 RDX MAP의 멤버 변수 간에 데이터 교환을 수행 해야 합니다.

## <a name="rdx_dword"></a><a name="rdx_dword"></a> RDX_DWORD

지정 된 레지스트리 항목을 DWORD 형식의 지정 된 멤버 변수에 연결 합니다.

```
RDX_DWORD(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>매개 변수

*rootkey*<br/>
레지스트리 키 루트입니다.

*가*<br/>
레지스트리 하위 키입니다.

*valuename*<br/>
레지스트리 키입니다.

*구성원과*<br/>
지정 된 레지스트리 항목과 연결할 멤버 변수입니다.

*member_size*<br/>
멤버 변수의 크기 (바이트)입니다.

### <a name="remarks"></a>설명

이 매크로는 BEGIN_RDX_MAP 및 END_RDX_MAP 매크로와 함께 사용 되어 멤버 변수를 지정 된 레지스트리 항목과 연결 합니다. 전역 함수 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)및 END_RDX_MAP 매크로를 사용 하 BEGIN_RDX_MAP 여 만든 것과 동일한 이름의 멤버 함수를 사용 하 여 시스템 레지스트리와 RDX MAP의 멤버 변수 간에 데이터 교환을 수행 해야 합니다.

## <a name="rdx_text"></a><a name="rdx_text"></a> RDX_TEXT

지정 된 레지스트리 항목을 TCHAR.H 형식의 지정 된 멤버 변수에 연결 합니다.

```
RDX_TEXT(
    rootkey,
    subkey,
    valuename,
    member,
    member_size )
```

### <a name="parameters"></a>매개 변수

*rootkey*<br/>
레지스트리 키 루트입니다.

*가*<br/>
레지스트리 하위 키입니다.

*valuename*<br/>
레지스트리 키입니다.

*구성원과*<br/>
지정 된 레지스트리 항목과 연결할 멤버 변수입니다.

*member_size*<br/>
멤버 변수의 크기 (바이트)입니다.

### <a name="remarks"></a>설명

이 매크로는 BEGIN_RDX_MAP 및 END_RDX_MAP 매크로와 함께 사용 되어 멤버 변수를 지정 된 레지스트리 항목과 연결 합니다. 전역 함수 [RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)및 END_RDX_MAP 매크로를 사용 하 BEGIN_RDX_MAP 여 만든 것과 동일한 이름의 멤버 함수를 사용 하 여 시스템 레지스트리와 RDX MAP의 멤버 변수 간에 데이터 교환을 수행 해야 합니다.

## <a name="see-also"></a>참고 항목

[매크로](../../atl/reference/atl-macros.md)<br/>
[RegistryDataExchange](../../atl/reference/registry-and-typelib-global-functions.md#registrydataexchange)
