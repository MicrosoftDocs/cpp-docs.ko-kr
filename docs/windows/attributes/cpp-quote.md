---
title: cpp_quote (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.cpp_quote
helpviewer_keywords:
- cpp_quote attribute
ms.assetid: f75327ff-42bd-498b-9177-7ffa25427e1f
ms.openlocfilehash: 905c9fc41b1b42dffe9c7b39fae0b096cdc24950
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501759"
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

**Cpp_quote** C++ 특성은 .idl 파일에 전처리기 지시문을 추가 하려는 경우에 유용 합니다.

**Cpp_quote** 를 사용 하 고 MIDL 컴파일의 일부로 .h 파일을 생성할 수도 있습니다. 예를 들어 IDL 특성을 사용 C++ C++ 하지만 일부 작업에이 파일을 사용할 수 없는 헤더 파일이 있는 경우이 파일을 컴파일하여 MIDL에서 생성 된 .h 파일을 만들 수 있습니다 .이 파일은 사용할 수 있습니다.

**Cpp_quote** 특성은 [cpp_quote](/windows/win32/Midl/cpp-quote) MIDL 특성과 동일한 기능을 포함 합니다.

## <a name="example"></a>예제

예제 [에 대 한](dual.md) 예제는 **cpp_quote**를 사용 하는 방법을 참조 하세요.

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|원하는 위치|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[IDL 특성](idl-attributes.md)<br/>
[독립 실행형 특성](stand-alone-attributes.md)