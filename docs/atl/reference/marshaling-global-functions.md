---
description: '자세한 정보: 전역 함수 마샬링'
title: 마샬링 전역 함수
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: 5652ccf89090ba1d0f00c03472e29da9158b781e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97157947"
---
# <a name="marshaling-global-functions"></a>마샬링 전역 함수

이러한 함수는 마샬링 데이터를 인터페이스 포인터로 마샬링 및 변환 하기 위한 지원을 제공 합니다.

> [!IMPORTANT]
> 다음 표에 나열 된 함수는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

|Name|설명|
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|마샬링 데이터와 포인터를 해제 합니다 `IStream` .|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|새 스트림 개체를 만들고 지정 된 인터페이스 포인터를 마샬링합니다.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|스트림의 마샬링 데이터를 인터페이스 포인터로 변환 합니다.|

## <a name="requirements"></a>요구 사항:

**헤더:** 서 기. h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a> AtlFreeMarshalStream

스트림에서 마샬링 데이터를 해제한 다음 스트림 포인터를 해제합니다.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
진행 `IStream` 마샬링에 사용 되는 스트림의 인터페이스에 대 한 포인터입니다.

### <a name="example"></a>예제

[AtlMarshalPtrInProc](#atlmarshalptrinproc)의 예제를 참조 하세요.

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a> AtlMarshalPtrInProc

새 스트림 개체를 만들고, 프록시의 CLSID를 스트림에 쓰고, 프록시를 스트림으로 초기화하는 데 필요한 데이터를 작성하여 제공된 인터페이스 포인터를 마샬링합니다.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 마샬링할 인터페이스에 대 한 포인터입니다.

*iid*<br/>
진행 마샬링되는 인터페이스의 GUID입니다.

*ppStream*<br/>
제한이 `IStream` 마샬링에 사용 되는 새 스트림 개체의 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="remarks"></a>설명

MSHLFLAGS_TABLESTRONG 플래그는 포인터를 여러 스트림으로 마샬링할 수 있도록 설정 됩니다. 포인터를 여러 번 역 마샬링할 수도 있습니다.

마샬링을 수행 하지 못하면 스트림 포인터가 해제 됩니다.

`AtlMarshalPtrInProc` in-process 개체에 대 한 포인터에만 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a> AtlUnmarshalPtr

스트림의 마샬링 데이터를 클라이언트에서 사용할 수 있는 인터페이스 포인터로 변환합니다.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>매개 변수

*pStream*<br/>
진행 역마샬링 되는 스트림에 대 한 포인터입니다.

*iid*<br/>
진행 역마샬링 되는 인터페이스의 GUID입니다.

*ppUnk*<br/>
제한이 역마샬링 된 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT 값입니다.

### <a name="example"></a>예제

[AtlMarshalPtrInProc](#atlmarshalptrinproc)의 예제를 참조 하세요.

## <a name="see-also"></a>참조

[함수](../../atl/reference/atl-functions.md)
