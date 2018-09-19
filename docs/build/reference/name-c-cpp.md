---
title: 이름 (C/C + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- name
dev_langs:
- C++
helpviewer_keywords:
- NAME .def file statement
ms.assetid: 5c9b6bd8-9275-46a5-afba-f17a5936dc26
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc37a96e50c6cd5bae2cc60661db04f3b92d162b
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715756"
---
# <a name="name-cc"></a>NAME(C/C++)

기본 출력 파일의 이름을 지정합니다.

```
NAME [application][BASE=address]
```

## <a name="remarks"></a>설명

출력 파일 이름을 지정 하는 해당 하는 방법은 된를 [/out](../../build/reference/out-output-file-name.md) 링커 옵션 및 기본 주소를 설정 하는 동일한 방법을 사용 하 여는 [/base](../../build/reference/base-base-address.md) 링커 옵션. 모두 지정 하면 / 아웃 재정의 **이름을**입니다.

DLL을 빌드하는 경우 이름을 DLL 이름에만 적용 됩니다.

## <a name="see-also"></a>참고 항목

[모듈 정의 문의 규칙](../../build/reference/rules-for-module-definition-statements.md)