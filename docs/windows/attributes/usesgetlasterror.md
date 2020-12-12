---
description: '자세히 알아보기: # getlasterror'
title: '# getlasterror (c + + COM 특성)'
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: f43ae005e2f888f4318900cbde58f449011bd15e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329516"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

호출자가 해당 함수를 호출할 때 오류가 발생 하면 호출자가를 호출 하 여 오류 코드를 검색할 수 있음을 호출자에 `GetLastError` 게 알립니다.

## <a name="syntax"></a>구문

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>설명

**usesgetlasterror** C++ 특성은 [usesgetlasterror](/windows/win32/Midl/usesgetlasterror) MIDL 기능을 포함합니다.

## <a name="example"></a>예제

사용 방법에 대 한 샘플은 [idl_module](idl-module.md) 예제를 참조 **하십시오.**

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**module** 특성|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)
