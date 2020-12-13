---
description: '자세한 정보: IRegistrar 인터페이스'
title: IRegistrar 인터페이스
ms.date: 02/01/2017
f1_keywords:
- IRegistrar
- ATLIFASE/ATL::IRegistrar
- ATLIFASE/ATL::IRegistrar::ResourceRegisterSz
- ATLIFASE/ATL::IRegistrar::ResourceUnregisterSz
- ATLIFASE/ATL::IRegistrar::FileRegister
- ATLIFASE/ATL::IRegistrar::FileUnregister
- ATLIFASE/ATL::IRegistrar::StringRegister
- ATLIFASE/ATL::IRegistrar::StringUnregister
- ATLIFASE/ATL::IRegistrar::ResourceRegister
- ATLIFASE/ATL::IRegistrar::ResourceUnregister
helpviewer_keywords:
- Iregistrar Interface
ms.assetid: e88c04b7-0c93-4ae8-aeb9-ecd78f87421e
ms.openlocfilehash: 9a138468ccbf21594c4e9d88d1ed2387a4c1052a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97139167"
---
# <a name="iregistrar-interface"></a>IRegistrar 인터페이스

이 인터페이스는 atliface. h에서 정의 되며 [UpdateRegistryFromResourceD](catlmodule-class.md#updateregistryfromresourced)와 같은 CAtlModule 멤버 함수에서 내부적으로 사용 됩니다.

## <a name="syntax"></a>구문

```
typedef interface IRegistrar IRegistrar;
```

## <a name="remarks"></a>설명

자세한 내용은 [대체 가능한 매개 변수 (등록자의 전처리기) 사용](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md) 항목을 참조 하세요.

## <a name="members"></a>멤버

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[IRegistrar:: ResourceRegisterSz](#resourceregistersz)|리소스를 등록 합니다. |
|[IRegistrar:: ResourceUnregisterSz](#resourceunregistersz)| 리소스 등록을 취소 합니다.|
|[IRegistrar:: FileRegister](#fileregister)|파일을 등록 합니다.|
|[IRegistrar:: FileUnregister 취소](#fileunregister)|파일의 등록을 취소 합니다.|
|[IRegistrar:: StringRegister](#stringregister)|문자열을 등록 합니다.|
|[IRegistrar:: StringUnregister 취소](#stringunregister)|문자열 등록 취소|
|[IRegistrar:: ResourceRegister](#resourceregister)|리소스를 등록 합니다.|
|[IRegistrar:: ResourceUnregister 취소](#resourceunregister)|리소스 등록을 취소 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** atlifase

## <a name="iregistrarresourceregistersz"></a><a name="resourceregistersz"></a> IRegistrar:: ResourceRegisterSz

리소스를 등록 합니다.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregistersz"></a><a name="resourceunregistersz"></a> IRegistrar:: ResourceUnregisterSz

리소스 등록을 취소 합니다.

```
virtual HRESULT STDMETHODCALLTYPE ResourceUnregisterSz(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_z_ LPCOLESTR szID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarfileregister"></a><a name="fileregister"></a> IRegistrar:: FileRegister

파일을 등록 합니다.

```
virtual HRESULT STDMETHODCALLTYPE FileRegister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarfileunregister"></a><a name="fileunregister"></a> IRegistrar:: FileUnregister 취소

파일의 등록을 취소 합니다.

```
virtual HRESULT STDMETHODCALLTYPE FileUnregister(
    /* [in] */ _In_z_ LPCOLESTR fileName) = 0;
```

## <a name="iregistrarstringregister"></a><a name="stringregister"></a> IRegistrar:: StringRegister

지정 된 문자열 데이터를 등록 합니다.

```
virtual HRESULT STDMETHODCALLTYPE StringRegister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarstringunregister"></a><a name="stringunregister"></a> IRegistrar:: StringUnregister 취소

지정 된 문자열 데이터의 등록을 취소 합니다.

```
virtualHRESULT STDMETHODCALLTYPE StringUnregister(
    /* [in] */ _In_z_ LPCOLESTR data) = 0;
```

## <a name="iregistrarresourceregister"></a><a name="resourceregister"></a> IRegistrar:: ResourceRegister

리소스를 등록 합니다.

```
virtual HRESULT STDMETHODCALLTYPE ResourceRegister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="iregistrarresourceunregister"></a><a name="resourceunregister"></a> IRegistrar:: ResourceUnregister 취소

리소스 등록을 취소 합니다.

```
virtualHRESULT STDMETHODCALLTYPE ResourceUnregister(
    /* [in] */ _In_z_ LPCOLESTR resFileName,
    /* [in] */ _In_ UINT nID,
    /* [in] */ _In_z_ LPCOLESTR szType) = 0;
```

## <a name="see-also"></a>참고 항목

[대체 가능 매개 변수 사용 (등록자의 전처리기)](../../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)<br/>
[클래스 개요](../../atl/atl-class-overview.md)<br/>
[모듈 클래스](../../atl/atl-module-classes.md)<br/>
[레지스트리 구성 요소(등록자)](../../atl/atl-registry-component-registrar.md)
