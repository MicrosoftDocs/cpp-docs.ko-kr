---
description: '자세히 알아보기: local (c + +)'
title: local (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.local
helpviewer_keywords:
- local attribute
ms.assetid: 35cdd668-bd8e-492a-b7b8-263e7b662437
ms.openlocfilehash: 7fa1366b78576224f8fcc0d91392fe1fc6cb8af9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327513"
---
# <a name="local-c"></a>local(C++)

인터페이스 헤더에서 사용 하는 경우에서 MIDL 컴파일러를 헤더 생성기로 사용할 수 있습니다. 개별 함수에서 사용 하는 경우 스텁이 생성 되지 않는 지역 프로시저를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
[local]
```

## <a name="remarks"></a>설명

**로컬** c + + 특성에는 [로컬](/windows/win32/Midl/local) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

**Local** 을 사용 하는 방법에 대 한 예제는 [call_as](call-as.md) 를 참조 하세요.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**interface**, interface 메서드|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|`dispinterface`|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[인터페이스 특성](interface-attributes.md)<br/>
[메서드 특성](method-attributes.md)<br/>
[call_as](call-as.md)
