---
description: '다음에 대 한 자세한 정보: cpp_quote'
title: cpp_quote (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: fe8424fd16cb75e320f8c1a1f8e3e444cf2185ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333169"
---
# <a name="cpp_quote"></a>cpp_quote

지정 된 문자열을 인용 문자 없이 생성 된 .idl 파일로 내보냅니다.

## <a name="syntax"></a>구문

```cpp
[ cpp_quote("statement") ];
```

### <a name="parameters"></a>매개 변수

*statement*<br/>
C 명령입니다.

## <a name="remarks"></a>설명

**Cpp_quote** c + + 특성은 .idl 파일에 전처리기 지시문을 추가 하려는 경우에 유용 합니다.

**Cpp_quote** 를 사용 하 고 MIDL 컴파일의 일부로 .h 파일을 생성할 수도 있습니다. 예를 들어 c + + IDL 특성을 사용 하지만 일부 작업에이 파일을 사용할 수 없는 c + + 헤더 파일이 있는 경우이 파일을 컴파일하여 MIDL에서 생성 된 .h 파일을 만들 수 있습니다 .이 파일은 사용할 수 있습니다.

**Cpp_quote** 특성에는 [cpp_quote](/windows/win32/Midl/cpp-quote) MIDL 특성과 동일한 기능이 있습니다.

## <a name="example"></a>예제

예제를 보려면 예제를 사용 하는 방법 [예제를 참조](dual.md) 하십시오. **cpp_quote** 를 사용 하는 방법을 사용 합니다.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|원하는 위치|
|**불가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[IDL 특성](idl-attributes.md)<br/>
[독립형 특성](stand-alone-attributes.md)
