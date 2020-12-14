---
description: '다음에 대 한 자세한 정보: begin 함수'
title: begin 함수
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: ae59a4b4344da520d86c216f4c9979953e16753c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97302766"
---
# <a name="begin-function"></a>begin 함수

지정된 인터페이스 매개 변수로 액세스되는 컬렉션 시작 부분을 가리키는 반복자를 반환합니다.

## <a name="syntax"></a>구문

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>매개 변수

*T*<br/>
템플릿 형식 매개 변수입니다.

*v*<br/>
\<T> \<T> IVector \<T> 또는 IVectorView 인터페이스에서 액세스 하는 Vector 또는 VectorView 개체의 컬렉션입니다 \<T> .

*i*<br/>
Iiterable<t> 인터페이스를 통해 액세스 되는 임의의 Windows 런타임 개체의 컬렉션입니다 \<T> .

### <a name="return-value"></a>반환 값

컬렉션의 시작 부분을 가리키는 반복기입니다.

### <a name="remarks"></a>설명

처음 두 템플릿 함수는 반복기를 반환하고 세 번째 템플릿 함수는 입력 반복기를 반환합니다.

Begin에 의해 반환 되는 VectorIterator 개체는 VectorProxy 형식의 요소를 저장 하는 프록시 반복기입니다 \<T> . 그러나 프록시 개체는 사용자 코드에 거의 표시되지 않습니다. 자세한 내용은 [컬렉션(C++/CX)](../cppcx/collections-c-cx.md)을 참조하세요.

### <a name="requirements"></a>요구 사항

**헤더:** collection .h

**네임스페이스:** Windows::Foundation::Collections

## <a name="see-also"></a>참고 항목

[Windows:: Foundation:: Collections 네임 스페이스](../cppcx/windows-foundation-collections-namespace-c-cx.md)
