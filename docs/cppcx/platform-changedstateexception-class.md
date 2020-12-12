---
description: '자세한 정보: Platform:: ChangedStateException 클래스'
title: Platform::ChangedStateException 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: baabf54cacfc4dd03256b569fb868c402ea98a97
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97284033"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException 클래스

개체의 내부 상태가 변경되어 메서드의 결과가 무효화될 때 throw됩니다.

## <a name="syntax"></a>구문

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>설명

부모 컬렉션이 변경된 후 컬렉션 반복기 또는 컬렉션 뷰의 메서드가 호출되어 메서드 결과가 무효화되는 경우가 이 예외가 throw되는 한 가지 예입니다.

자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타 데이터:** platform.object

## <a name="see-also"></a>참고 항목

[Platform:: COMException 클래스](../cppcx/platform-comexception-class.md)
