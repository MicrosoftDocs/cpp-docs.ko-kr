---
title: export (C++ COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.export
helpviewer_keywords:
- export attribute
ms.assetid: 70b3e848-fad6-4e09-8c72-be60ca72a4df
ms.openlocfilehash: 771bfdfe4eab2acf31e97a606795066e8938a8a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501612"
---
# <a name="export"></a>내보내기

데이터 구조가 .idl 파일에 배치 되도록 합니다.

## <a name="syntax"></a>구문

```cpp
[export]
```

## <a name="remarks"></a>설명

**Export** C++ 특성을 사용 하면 데이터 구조가 .idl 파일에 배치 된 다음 모든 언어에서 사용할 수 있도록 하는 이진 호환 형식으로 형식 라이브러리에서 사용할 수 있습니다.

클래스에 public 멤버만 있는 경우에도 ( **구조체**에 해당) **내보내기** 특성을 클래스에 적용할 수 없습니다.

명명 되지 않은 **열거형** 또는 **구조체**를 내보내는 경우 **__unnamed**<em>x</em>로 시작 하는 이름이 지정 됩니다. 여기서 *x* 는 일련 번호입니다.

내보내기에 유효한 typedef는 기본 형식, 구조체, 공용 구조체, 열거형 또는 형식 식별자입니다.  자세한 내용은 [typedef](/windows/win32/Midl/typedef) 를 참조 하십시오.

## <a name="example"></a>예제

다음 코드에서는 **export** 특성을 사용 하는 방법을 보여 줍니다.

```cpp
// cpp_attr_ref_export.cpp
// compile with: /LD
[module(name="MyLibrary")];

[export]
struct MyStruct {
   int i;
};
```

## <a name="requirements"></a>요구 사항

### <a name="attribute-context"></a>특성 컨텍스트

|||
|-|-|
|**적용 대상**|**union**, **typedef**, **enum**, **struct**또는 **interface**|
|**반복 가능**|아니요|
|**필수 특성**|없음|
|**잘못된 특성**|없음|

자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고자료

[컴파일러 특성](compiler-attributes.md)<br/>
[Typedef, Enum, Union 및 Struct 특성](typedef-enum-union-and-struct-attributes.md)