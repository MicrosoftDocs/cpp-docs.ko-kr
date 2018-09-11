---
title: begin 함수 | Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::begin
dev_langs:
- C++
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ad73daba0bce57a19c512a53747cf8ac804e929d
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101757"
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
벡터의 컬렉션인\<T > 또는 VectorView\<T >를 IVector로 액세스할 수 있는 개체\<T > 또는 IVectorView\<T > 인터페이스입니다.

*i*<br/>
IIterable 액세스할 수 있는 임의의 Windows 런타임 개체의 컬렉션인\<T > 인터페이스입니다.

### <a name="return-value"></a>반환 값

컬렉션의 시작 부분을 가리키는 반복기입니다.

### <a name="remarks"></a>설명

처음 두 템플릿 함수는 반복기를 반환하고 세 번째 템플릿 함수는 입력 반복기를 반환합니다.

개체에서 반환 되는 시작 하는 VectorIterator가 VectorProxy 형식의 요소를 저장 하는 프록시 반복기\<T >입니다. 그러나 프록시 개체는 사용자 코드에 거의 표시되지 않습니다. 자세한 내용은 [컬렉션(C++/CX)](../cppcx/collections-c-cx.md)을 참조하세요.

### <a name="requirements"></a>요구 사항

**헤더:** collection.h

**네임스페이스:** Windows::Foundation::Collections

## <a name="see-also"></a>참고 항목

[Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)