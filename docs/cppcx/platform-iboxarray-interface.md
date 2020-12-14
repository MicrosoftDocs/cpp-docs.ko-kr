---
description: '자세한 정보: Platform:: IBoxArray 인터페이스'
title: Platform::IBoxArray 인터페이스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IBoxArray
- VCCORLIB/Platform::IBoxArray::Value
helpviewer_keywords:
- Platform::IBoxArray
ms.assetid: 6cd82c9e-4230-4147-9edb-7a652875dbf1
ms.openlocfilehash: 8b87a00d709bec8af016de4532c7c4ec759d72fc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195146"
---
# <a name="platformiboxarray-interface"></a>Platform::IBoxArray 인터페이스

`IBoxArray` 는 XAML 컨트롤의 요소와 같은 `Platform::Object^` 요소의 컬렉션에 저장되거나 ABI(애플리케이션 이진 인터페이스)를 통해 전달되는 값 형식의 배열에 대한 래퍼입니다.

## <a name="syntax"></a>구문

```cpp
template <typename T>
interface class IBoxArray
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
각 배열 요소의 boxed 값 형식입니다.

### <a name="remarks"></a>설명

`IBoxArray` 는에 대 한 c + +/CX 이름입니다 `Windows::Foundation::IReferenceArray` .

### <a name="members"></a>멤버

`IBoxArray` 인터페이스는 `IValueType` 인터페이스에서 상속됩니다. `IBoxArray` 에도 다음과 같은 멤버가 포함됩니다.

|메서드|설명|
|------------|-----------------|
|[값](#value)|이 `IBoxArray` 인스턴스에 이전에 저장된 unboxed 배열을 반환합니다.|

## <a name="iboxarrayvalue-property"></a><a name="value"></a> IBoxArray:: Value 속성

이 개체에 원래 저장된 값을 반환합니다.

### <a name="syntax"></a>구문

```cpp
property T Value {T get();}
```

### <a name="parameters"></a>매개 변수

*T*<br/>
boxed 값의 형식입니다.

### <a name="property-valuereturn-value"></a>속성 값/반환 값

이 개체에 원래 저장된 값을 반환합니다.

### <a name="remarks"></a>설명

예제를 보려면 [Boxing](../cppcx/boxing-c-cx.md)을 참조 하십시오.

## <a name="see-also"></a>참고 항목

[Array 및 WriteOnlyArray](../cppcx/array-and-writeonlyarray-c-cx.md)
