---
description: '자세히 알아보기: FtmBase 클래스'
title: FtmBase 클래스
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
- ftm/Microsoft::WRL::FtmBaseCreateGlobalInterfaceTable
- ftm/Microsoft::WRL::FtmBase::DisconnectObject
- ftm/Microsoft::WRL::FtmBase::FtmBase
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
- ftm/Microsoft::WRL::FtmBase::marshaller_
- ftm/Microsoft::WRL::FtmBase::ReleaseMarshalData
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
helpviewer_keywords:
- Microsoft::WRL::FtmBase class
- Microsoft::WRL::FtmBase::CreateGlobalInterfaceTable method
- Microsoft::WRL::FtmBase::DisconnectObject method
- Microsoft::WRL::FtmBase::FtmBase, constructor
- Microsoft::WRL::FtmBase::GetMarshalSizeMax method
- Microsoft::WRL::FtmBase::GetUnmarshalClass method
- Microsoft::WRL::FtmBase::MarshalInterface method
- Microsoft::WRL::FtmBase::marshaller_ data member
- Microsoft::WRL::FtmBase::ReleaseMarshalData method
- Microsoft::WRL::FtmBase::UnmarshalInterface method
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
ms.openlocfilehash: dc7ae3768233dd51d34b48da8c12a2d4b6bed773
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250090"
---
# <a name="ftmbase-class"></a>FtmBase 클래스

자유 스레드된 마샬러 개체를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
class FtmBase :
    public Microsoft::WRL::Implements<
        Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,
        Microsoft::WRL::CloakedIid<IMarshal>
    >;
```

## <a name="remarks"></a>설명

자세한 내용은 [RuntimeClass 클래스](runtimeclass-class.md)를 참조 하세요.

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

| 이름                         | 설명                                        |
| ---------------------------- | -------------------------------------------------- |
| [FtmBase:: FtmBase](#ftmbase) | `FtmBase` 클래스의 새 인스턴스를 초기화합니다. |

### <a name="public-methods"></a>Public 메서드

| 이름                                                               | 설명                                                                                                                                                          |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [FtmBase:: CreateGlobalInterfaceTable](#createglobalinterfacetable) | GIT (전역 인터페이스 테이블)을 만듭니다.                                                                                                                              |
| [FtmBase::D isconnectObject](#disconnectobject)                     | 개체에 대 한 모든 외부 연결을 강제로 해제 합니다. 개체의 서버는를 종료 하기 전에 개체의이 메서드 구현을 호출 합니다.                |
| [FtmBase:: GetMarshalSizeMax](#getmarshalsizemax)                   | 지정 된 개체에서 지정 된 인터페이스 포인터를 마샬링하는 데 필요한 바이트 수에 대 한 상한을 가져옵니다.                                                |
| [FtmBase:: GetUnmarshalClass](#getunmarshalclass)                   | COM이 해당 프록시에 대 한 코드를 포함 하는 DLL을 찾기 위해 사용 하는 CLSID를 가져옵니다. COM은이 DLL을 로드 하 여 프록시의 초기화 되지 않은 인스턴스를 만듭니다. |
| [FtmBase:: MarshalInterface](#marshalinterface)                     | 일부 클라이언트 프로세스에서 프록시 개체를 초기화 하는 데 필요한 데이터를 스트림에 씁니다.                                                                          |
| [FtmBase:: ReleaseMarshalData](#releasemarshaldata)                 | 마샬링된 데이터 패킷을 소멸 시킵니다.                                                                                                                                    |
| [FtmBase:: UnmarshalInterface](#unmarshalinterface)                 | 새로 만든 프록시를 초기화 하 고 해당 프록시에 대 한 인터페이스 포인터를 반환 합니다.                                                                                    |

### <a name="public-data-members"></a>공용 데이터 멤버

| Name                                | 설명                                       |
| ----------------------------------- | ------------------------------------------------- |
| [FtmBase:: marshaller_](#marshaller) | 자유 스레드된 마샬러에 대 한 참조를 보유 합니다. |

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`FtmBase`

## <a name="requirements"></a>요구 사항

**헤더:** ftm

**네임스페이스:** Microsoft::WRL

## <a name="ftmbasecreateglobalinterfacetable"></a><a name="createglobalinterfacetable"></a> FtmBase:: CreateGlobalInterfaceTable

GIT (전역 인터페이스 테이블)을 만듭니다.

```cpp
static HRESULT CreateGlobalInterfaceTable(
   __out IGlobalInterfaceTable **git
);
```

### <a name="parameters"></a>매개 변수

*git*<br/>
이 작업이 완료 되 면 전역 인터페이스 테이블에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

자세한 내용은 [`IGlobalInterfaceTable`](/windows/win32/api/objidl/nn-objidl-iglobalinterfacetable)를 참조하세요.

## <a name="ftmbasedisconnectobject"></a><a name="disconnectobject"></a> FtmBase::D isconnectObject

개체에 대 한 모든 외부 연결을 강제로 해제 합니다. 개체의 서버는를 종료 하기 전에 개체의이 메서드 구현을 호출 합니다.

```cpp
STDMETHODIMP DisconnectObject(
   __in DWORD dwReserved
) override;
```

### <a name="parameters"></a>매개 변수

*dwReserved*<br/>
나중에 사용하도록 예약되어 있습니다. 0이어야 합니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="ftmbaseftmbase"></a><a name="ftmbase"></a> FtmBase:: FtmBase

`FtmBase` 클래스의 새 인스턴스를 초기화합니다.

```cpp
FtmBase();
```

## <a name="ftmbasegetmarshalsizemax"></a><a name="getmarshalsizemax"></a> FtmBase:: GetMarshalSizeMax

지정 된 개체에서 지정 된 인터페이스 포인터를 마샬링하는 데 필요한 바이트 수에 대 한 상한을 가져옵니다.

```cpp
STDMETHODIMP GetMarshalSizeMax(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out DWORD *pSize
) override;
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
마샬링할 인터페이스의 식별자에 대 한 참조입니다.

*pv*<br/>
마샬링할 인터페이스 포인터입니다. NULL 일 수 있습니다.

*dwDestContext*<br/>
지정 된 인터페이스가 역마샬링 될 대상 컨텍스트입니다.

MSHCTX 열거 값을 하나 이상 지정 하십시오.

현재는 현재 프로세스 (MSHCTX_INPROC)의 다른 아파트 또는 현재 프로세스와 동일한 컴퓨터의 다른 프로세스 (MSHCTX_LOCAL)에서 역마샬링 될 수 있습니다.

*pvDestContext*<br/>
나중에 사용 하도록 예약 되어 있습니다. NULL 이어야 합니다.

*mshlflags*<br/>
마샬링될 데이터를 클라이언트 프로세스로 다시 전송할지 (일반적인 경우), 여러 클라이언트에서 검색할 수 있는 전역 테이블에 쓸지를 나타내는 플래그입니다. MSHLFLAGS 열거 값을 하나 이상 지정 하십시오.

*pSize*<br/>
이 작업이 완료 되 면 마샬링 스트림에 쓸 데이터 양의 상한에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_FAIL 또는 E_NOINTERFACE 합니다.

## <a name="ftmbasegetunmarshalclass"></a><a name="getunmarshalclass"></a> FtmBase:: GetUnmarshalClass

COM이 해당 프록시에 대 한 코드를 포함 하는 DLL을 찾기 위해 사용 하는 CLSID를 가져옵니다. COM은이 DLL을 로드 하 여 프록시의 초기화 되지 않은 인스턴스를 만듭니다.

```cpp
STDMETHODIMP GetUnmarshalClass(
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags,
   __out CLSID *pCid
) override;
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
마샬링할 인터페이스의 식별자에 대 한 참조입니다.

*pv*<br/>
마샬링할 인터페이스에 대 한 포인터입니다. 호출자에 게 원하는 인터페이스에 대 한 포인터가 없는 경우 NULL 일 수 있습니다.

*dwDestContext*<br/>
지정 된 인터페이스가 역마샬링 될 대상 컨텍스트입니다.

MSHCTX 열거 값을 하나 이상 지정 하십시오.

역마샬링은 현재 프로세스의 다른 아파트 (MSHCTX_INPROC) 나 현재 프로세스와 동일한 컴퓨터의 다른 프로세스 (MSHCTX_LOCAL)에서 발생할 수 있습니다.

*pvDestContext*<br/>
나중에 사용 하도록 예약 되어 있습니다. NULL 이어야 합니다.

*mshlflags*<br/>
이 작업이 완료 되 면 클라이언트 프로세스에서 프록시를 만드는 데 사용할 CLSID에 대 한 포인터입니다.

*pCid*

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 S_FALSE 합니다.

## <a name="ftmbasemarshalinterface"></a><a name="marshalinterface"></a> FtmBase:: MarshalInterface

일부 클라이언트 프로세스에서 프록시 개체를 초기화 하는 데 필요한 데이터를 스트림에 씁니다.

```cpp
STDMETHODIMP MarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __in_opt void *pv,
   __in DWORD dwDestContext,
   __reserved void *pvDestContext,
   __in DWORD mshlflags
) override;
```

### <a name="parameters"></a>매개 변수

*pStm*<br/>
마샬링을 수행 하는 동안 사용할 스트림에 대 한 포인터입니다.

*riid*<br/>
마샬링할 인터페이스의 식별자에 대 한 참조입니다. 이 인터페이스는 `IUnknown` 인터페이스에서 파생되어야 합니다.

*pv*<br/>
마샬링할 인터페이스 포인터에 대 한 포인터입니다. 호출자에 게 원하는 인터페이스에 대 한 포인터가 없는 경우 NULL 일 수 있습니다.

*dwDestContext*<br/>
지정 된 인터페이스가 역마샬링 될 대상 컨텍스트입니다.

MSHCTX 열거 값을 하나 이상 지정 하십시오.

역마샬링은 현재 프로세스의 다른 아파트 (MSHCTX_INPROC) 나 현재 프로세스와 동일한 컴퓨터의 다른 프로세스 (MSHCTX_LOCAL)에서 발생할 수 있습니다.

*pvDestContext*<br/>
나중에 사용하도록 예약되어 있습니다. 0이어야 합니다.

*mshlflags*<br/>
마샬링될 데이터를 클라이언트 프로세스로 다시 전송할지 (일반적인 경우), 여러 클라이언트에서 검색할 수 있는 전역 테이블에 쓸지 여부를 지정 합니다.

### <a name="return-value"></a>반환 값

인터페이스 포인터가 성공적으로 마샬링되 S_OK 합니다.

지정 된 인터페이스가 지원 되지 E_NOINTERFACE.

스트림이 꽉 찬 STG_E_MEDIUMFULL입니다.

E_FAIL 작업이 실패 했습니다.

## <a name="ftmbasemarshaller_"></a><a name="marshaller"></a> FtmBase:: marshaller_

자유 스레드된 마샬러에 대 한 참조를 보유 합니다.

```cpp
Microsoft::WRL::ComPtr<IMarshal> marshaller_; ;
```

## <a name="ftmbasereleasemarshaldata"></a><a name="releasemarshaldata"></a> FtmBase:: ReleaseMarshalData

마샬링된 데이터 패킷을 소멸 시킵니다.

```cpp
STDMETHODIMP ReleaseMarshalData(
   __in IStream *pStm
) override;
```

### <a name="parameters"></a>매개 변수

*pStm*<br/>
제거할 데이터 패킷을 포함 하는 스트림에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공하면 S_OK이고, 그렇지 않으면 오류를 나타내는 HRESULT입니다.

## <a name="ftmbaseunmarshalinterface"></a><a name="unmarshalinterface"></a> FtmBase:: UnmarshalInterface

새로 만든 프록시를 초기화 하 고 해당 프록시에 대 한 인터페이스 포인터를 반환 합니다.

```cpp
STDMETHODIMP UnmarshalInterface(
   __in IStream *pStm,
   __in REFIID riid,
   __deref_out void **ppv
) override;
```

### <a name="parameters"></a>매개 변수

*pStm*<br/>
인터페이스 포인터가 역마샬링 될 스트림에 대 한 포인터입니다.

*riid*<br/>
역마샬링 할 인터페이스의 식별자에 대 한 참조입니다.

*ppv*<br/>
이 작업이 완료 되 면 *riid* 에서 요청 된 인터페이스 포인터를 받는 포인터 변수의 주소입니다. 이 작업이 성공적으로 수행 되 면 **ppv* 는 역마샬링 될 인터페이스의 요청 된 인터페이스 포인터를 포함 합니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_NOINTERFACE 또는 E_FAIL 합니다.
