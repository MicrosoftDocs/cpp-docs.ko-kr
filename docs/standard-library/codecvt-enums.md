---
description: '&lt;Codecvt 열거형에 대해 자세히 알아보세요. &gt;'
title: '&lt;codecvt&gt; 열거형'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bcd40f72f563b3ecf91125f7167f206d4b1b6517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234061"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; 열거형

## <a name="codecvt_mode-enumeration"></a><a name="codecvt_mode"></a> codecvt_mode 열거형

[로캘](../standard-library/locale-class.md) 패싯에 대 한 구성 정보를 지정 합니다.

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>설명

열거형은에 선언 된 로캘 패싯에 구성 정보를 제공 하는 세 개의 상수를 정의 합니다 [\<codecvt>](../standard-library/codecvt.md) . 고유 값은 다음과 같습니다.

- `consume_header` - 멀티바이트 시퀀스를 읽을 때 초기 헤더 시퀀스를 사용하고, 읽을 후속 멀티바이트 시퀀스의 엔디언(Endianness)을 결정할 경우

- `generate_header` - 멀티바이트 시퀀스를 작성할 때 초기 헤더 시퀀스를 생성하고, 작성할 후속 멀티바이트 시퀀스의 엔디언(Endianness)을 보급할 경우

- `little_endian` - 기본 big endian 순서와는 대조적으로 little endian 순서로 멀티바이트 시퀀스를 생성할 경우

이러한 상수는 임의 조합에서 함께 OR 처리될 수 있습니다.

## <a name="see-also"></a>참고 항목

[\<codecvt>](../standard-library/codecvt.md)
