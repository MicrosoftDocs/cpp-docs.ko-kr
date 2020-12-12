---
description: '다음에 대 한 자세한 정보: stdext 네임 스페이스'
title: stdext 네임스페이스
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: bb81dde22014ec91f7212ce4313c21a8410f30a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153787"
---
# <a name="stdext-namespace"></a>stdext 네임스페이스

[\<hash_map>](../standard-library/hash-map.md)및 [\<hash_set>](../standard-library/hash-set.md) 헤더 파일의 멤버는 현재 ISO c + + 표준에 포함 되어 있지 않습니다. 따라서 C++ 표준을 계속 준수하기 위해 이러한 형식 및 멤버를 `std` 네임스페이스에서 `stdext`네임스페이스로 이동했습니다.

기본값인 [/ze](../build/reference/za-ze-disable-language-extensions.md)로 컴파일하는 경우 컴파일러는 `std` \<hash_map> 및 헤더 파일의 멤버에 대해를 사용할 때 경고를 표시 합니다 \<hash_set> . 이 경고를 사용하지 않도록 설정하려면 [경고](../preprocessor/warning.md) pragma를 사용합니다.

/Ze를 사용 하 여 및 헤더 파일의 멤버에 대해를 사용 하는 데 컴파일러에서 오류를 생성 하도록 하려면 `std` \<hash_map> \<hash_set>  `#include` c + + 표준 라이브러리 헤더 파일 앞에 다음 지시문을 추가 합니다.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

**/Za** 를 사용 하 여 컴파일하는 경우 컴파일러에서 오류를 생성 합니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)
