---
description: '자세한 정보: 구조체 구현'
title: Implements 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Implements
- implements/Microsoft::WRL::Implements::CanCastTo
- implements/Microsoft::WRL::Implements::CastToUnknown
- implements/Microsoft::WRL::Implements::FillArrayWithIid
- implements/Microsoft::WRL::Implements::IidCount
helpviewer_keywords:
- Microsoft::WRL::Implements structure
- Microsoft::WRL::Implements::CanCastTo method
- Microsoft::WRL::Implements::CastToUnknown method
- Microsoft::WRL::Implements::FillArrayWithIid method
- Microsoft::WRL::Implements::IidCount method
ms.assetid: 29b13e90-34d4-4a0b-babd-5187c9eb0c36
ms.openlocfilehash: b438e012b23e34b08956c969ffe604878d3065fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97249830"
---
# <a name="implements-structure"></a>Implements 구조체

`QueryInterface` `GetIid` 지정 된 인터페이스에 대해 및을 구현 합니다.

## <a name="syntax"></a>구문

```cpp
template <
    typename I0,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct __declspec(novtable) Implements :
    Details::ImplementsHelper<
        RuntimeClassFlags<WinRt>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8, I9
        >::TypeT
    >,
    Details::ImplementsBase;

template <
    int flags,
    typename I0,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8
>
struct __declspec(novtable) Implements<
        RuntimeClassFlags<flags>,
        I0, I1, I2, I3, I4, I5, I6, I7, I8> :
    Details::ImplementsHelper<
        RuntimeClassFlags<flags>,
        typename Details::InterfaceListHelper<
            I0, I1, I2, I3, I4, I5, I6, I7, I8
        >::TypeT
    >,
    Details::ImplementsBase;
```

### <a name="parameters"></a>매개 변수

*I0*<br/>
0 번째 인터페이스 ID입니다. 필수 사항입니다.

*I1*<br/>
첫 번째 인터페이스 ID입니다. (선택 사항)

*I2*<br/>
두 번째 인터페이스 ID입니다. (선택 사항)

*I3*<br/>
세 번째 인터페이스 ID입니다. (선택 사항)

*I4*<br/>
네 번째 인터페이스 ID입니다. (선택 사항)

*I5*<br/>
다섯 번째 인터페이스 ID입니다. (선택 사항)

*I6*<br/>
여섯 번째 인터페이스 ID입니다. (선택 사항)

*I7*<br/>
일곱 번째 인터페이스 ID입니다. (선택 사항)

*I8*<br/>
여덟 번째 인터페이스 ID입니다. (선택 사항)

*I9*<br/>
아홉 번째 인터페이스 ID입니다. (선택 사항)

*flags*<br/>
클래스에 대 한 구성 플래그입니다. [RuntimeClassFlags](runtimeclassflags-structure.md) 구조체에 지정 된 하나 이상의 [RuntimeClassType](runtimeclasstype-enumeration.md) 열거형입니다.

## <a name="remarks"></a>설명

지정 된 인터페이스 목록에서 파생 되 고 및에 대 한 도우미 템플릿을 구현 `QueryInterface` `GetIid` 합니다.

*I9* interface 매개 변수를 통해 각 *I0* 는 `IUnknown` , `IInspectable` 또는 [ChainInterfaces](chaininterfaces-structure.md) 템플릿 중 하나에서 파생 되어야 합니다. *Flags* 매개 변수는 또는에 대해 지원이 생성 되는지 여부를 결정 합니다 `IUnknown` `IInspectable` .

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

| Name        | 설명                               |
| ----------- | ----------------------------------------- |
| `ClassFlags`| `RuntimeClassFlags<WinRt>`의 동의어입니다. |

### <a name="protected-methods"></a>Protected 메서드

| Name                                              | 설명                                                                                                   |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Implements:: CanCastTo](#cancastto)               | 지정 된 인터페이스에 대 한 포인터를 가져옵니다.                                                                    |
| [Implements:: CastToUnknown](#casttounknown)       | 기본 인터페이스에 대 한 포인터를 가져옵니다 `IUnknown` .                                                        |
| [Implements:: FillArrayWithIid](#fillarraywithiid) | 현재 0 번째 template 매개 변수에 지정 된 인터페이스 ID를 지정 된 배열 요소에 삽입 합니다. |

### <a name="protected-constants"></a>Protected 상수

| Name                              | 설명                                    |
| --------------------------------- | ---------------------------------------------- |
| [Implements:: IidCount](#iidcount) | 구현 된 인터페이스 Id의 수를 포함 합니다. |

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`I0`

`ChainInterfaces`

`I0`

`ImplementsBase`

`ImplementsHelper`

`Implements`

## <a name="requirements"></a>요구 사항

**헤더:** .h를 구현 합니다.

**네임스페이스:** Microsoft::WRL

## <a name="implementscancastto"></a><a name="cancastto"></a> Implements:: CanCastTo

지정 된 인터페이스에 대 한 포인터를 가져옵니다.

```cpp
__forceinline HRESULT CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>매개 변수

*riid*<br/>
인터페이스 ID에 대 한 참조입니다.

*ppv*<br/>
성공 하는 경우 *riid* 에서 지정 된 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

성공 하면 S_OK 합니다. 그렇지 않으면 E_NOINTERFACE와 같은 오류를 나타내는 HRESULT입니다.

### <a name="remarks"></a>설명

이는 QueryInterface 작업을 수행 하는 내부 도우미 함수입니다.

## <a name="implementscasttounknown"></a><a name="casttounknown"></a> Implements:: CastToUnknown

기본 인터페이스에 대 한 포인터를 가져옵니다 `IUnknown` .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>반환 값

이 작업은 항상 성공 하 고 포인터를 반환 합니다 `IUnknown` .

### <a name="remarks"></a>설명

내부 도우미 함수입니다.

## <a name="implementsfillarraywithiid"></a><a name="fillarraywithiid"></a> Implements:: FillArrayWithIid

현재 0 번째 template 매개 변수에 지정 된 인터페이스 ID를 지정 된 배열 요소에 삽입 합니다.

```cpp
__forceinline static void FillArrayWithIid(
   unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>매개 변수

*index*<br/>
이 작업의 시작 배열 요소를 나타내는 인덱스 (0부터 시작)입니다. 이 작업이 완료 되 면 *인덱스* 는 1 씩 증가 합니다.

*iid*<br/>
IID 형식의 배열입니다.

### <a name="remarks"></a>설명

내부 도우미 함수입니다.

## <a name="implementsiidcount"></a><a name="iidcount"></a> Implements:: IidCount

구현 된 인터페이스 Id의 수를 포함 합니다.

```cpp
static const unsigned long IidCount;
```
