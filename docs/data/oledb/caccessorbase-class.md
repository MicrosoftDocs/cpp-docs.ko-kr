---
title: CAccessorBase 클래스
ms.date: 11/04/2016
f1_keywords:
- CAccessorBase
- CAccessorBase.Close
- CAccessorBase::Close
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
- CAccessorBase::GetNumAccessors
- GetNumAccessors
- CAccessorBase.GetNumAccessors
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
- CAccessorBase::ReleaseAccessors
- CAccessorBase.ReleaseAccessors
- ReleaseAccessors
helpviewer_keywords:
- CAccessorBase class
- Close method
- GetHAccessor method
- GetNumAccessors method
- IsAutoAccessor method
- ReleaseAccessors method
ms.assetid: 389b65be-11ca-4ae0-9290-60c621c4982b
ms.openlocfilehash: 81b0ecd8ded7acb0c0e376d0869decb2bfcb590e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509117"
---
# <a name="caccessorbase-class"></a>CAccessorBase 클래스

OLE DB 템플릿의 모든 접근자는이 클래스에서 파생 됩니다. `CAccessorBase` 한 행 집합에서 여러 접근자를 관리할 수 있습니다. 또한 매개 변수 및 출력 열 모두에 대 한 바인딩을 제공 합니다.

## <a name="syntax"></a>구문

```cpp
// Replace with syntax
```

## <a name="members"></a>멤버

### <a name="methods"></a>메서드

| 속성 | 설명 |
|--|--|
| [닫기](#close) | 접근자를 닫습니다. |
| [GetHAccessor](#geth) | 접근자 핸들을 검색 합니다. |
| [GetNumAccessors](#getnum) | 클래스에서 만든 접근자 수를 검색 합니다. |
| [IsAutoAccessor](#isauto) | 지정 된 접근자가 autoaccessor 인지 여부를 테스트 합니다. |
| [ReleaseAccessors](#release) | 접근자를 해제 합니다. |

## <a name="requirements"></a>요구 사항

**헤더:** atldbcli.h

## <a name="caccessorbaseclose"></a><a name="close"></a> CAccessorBase:: Close

접근자를 닫습니다.

### <a name="syntax"></a>구문

```cpp
void Close();
```

### <a name="remarks"></a>설명

[Releaseaccessors](#release) 를 먼저 호출 해야 합니다.

## <a name="caccessorbasegethaccessor"></a><a name="geth"></a> CAccessorBase:: GetHAccessor

지정된 접근자의 접근자 핸들을 검색합니다.

### <a name="syntax"></a>구문

```cpp
HACCESSOR GetHAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>매개 변수

*nAccessor*<br/>
[in] 접근자에 대한 0 오프셋의 수입니다.

### <a name="return-value"></a>반환 값

접근자 핸들입니다.

## <a name="caccessorbasegetnumaccessors"></a><a name="getnum"></a> CAccessorBase:: GetNumAccessors

클래스에서 만든 접근자 수를 검색 합니다.

### <a name="syntax"></a>구문

```cpp
ULONG GetNumAccessors() const;
```

### <a name="return-value"></a>Return Value

클래스에서 만든 접근자의 수입니다.

## <a name="caccessorbaseisautoaccessor"></a><a name="isauto"></a> CAccessorBase:: IsAutoAccessor

이동 작업 중 접근자에 대 한 데이터가 자동으로 검색 되 면 true를 반환 합니다.

### <a name="syntax"></a>구문

```cpp
bool IsAutoAccessor(ULONG nAccessor) const;
```

#### <a name="parameters"></a>매개 변수

*nAccessor*<br/>
[in] 접근자에 대한 0 오프셋의 수입니다.

### <a name="return-value"></a>반환 값

**`true`** 접근자가 autoaccessor 이면를 반환 합니다. 그렇지 않으면를 반환 **`false`** 합니다.

## <a name="caccessorbasereleaseaccessors"></a><a name="release"></a> CAccessorBase:: ReleaseAccessors

클래스에서 만든 접근자를 해제 합니다.

### <a name="syntax"></a>구문

```cpp
HRESULT ReleaseAccessors(IUnknown* pUnk);
```

#### <a name="parameters"></a>매개 변수

*pUnk*<br/>
진행 `IUnknown` 접근자를 만든 COM 개체의 인터페이스에 대 한 포인터입니다.

### <a name="return-value"></a>반환 값

표준 HRESULT입니다.

### <a name="remarks"></a>설명

[CAccessorRowset:: Close](./caccessorrowset-class.md#close)에서 호출 됩니다.

## <a name="see-also"></a>참고 항목

[OLE DB 소비자 템플릿](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 소비자 템플릿 참조](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessorBase 클래스](../../data/oledb/caccessorbase-class.md)
