---
description: '자세한 정보: 이름 (C/c + +)'
title: NAME(C/C++)
ms.date: 11/04/2016
f1_keywords:
- name
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
ms.openlocfilehash: 7444aa20539b47b1f04d17a266a0b65a552af3f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97137776"
---
# <a name="name-cc"></a>NAME(C/C++)

주 출력 파일의 이름을 지정 합니다.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>설명

출력 파일 이름을 지정 하는 동일한 방법은 [/out](out-output-file-name.md) 링커 옵션을 사용 하 고, 기본 주소를 설정 하는 것과 같은 방법은 [/base](base-base-address.md) 링커 옵션을 사용 하는 것입니다. 둘 다 지정 하면/OUT은 **NAME** 을 재정의 합니다.

DLL을 빌드하면 NAME은 DLL 이름에만 영향을 줍니다.

## <a name="see-also"></a>참고 항목

[Module-Definition 문에 대 한 규칙](rules-for-module-definition-statements.md)
