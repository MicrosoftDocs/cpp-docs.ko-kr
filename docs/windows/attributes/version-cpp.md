---
description: '자세한 정보: 버전 (c + +)'
title: version (c + + COM 특성)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: 5b6d13e59b36fe37d71c9e2cca6fe7d75587f77b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118305"
---
# <a name="version-c"></a>version(C++)

클래스의 여러 버전에서 특정 버전을 식별 합니다.

## <a name="syntax"></a>구문

```cpp
[ version("version") ]
```

### <a name="parameters"></a>매개 변수

*version*<br/>
`coclass`의 버전 번호입니다. 지정 하지 않으면 1.0가 .idl 파일에 배치 됩니다.

## <a name="remarks"></a>설명

**버전** c + + 특성은 [버전](/windows/win32/Midl/version) MIDL 특성과 동일한 기능을 포함 하며 생성 된 .idl 파일로 전달 됩니다.

## <a name="example"></a>예제

**버전** 의 샘플 사용에 대 한 [바인딩](bindable.md) 가능한 예제를 참조 하십시오.

## <a name="requirements"></a>요구 사항

| 특성 컨텍스트 | 값 |
|-|-|
|**적용 대상**|**`class`**, **`struct`**|
|**불가능**|아니요|
|**필수 특성**|**coclass**|
|**잘못된 특성**|없음|

특성 컨텍스트에 대한 자세한 내용은 [특성 컨텍스트](cpp-attributes-com-net.md#contexts)를 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 특성](compiler-attributes.md)<br/>
[클래스 특성](class-attributes.md)
