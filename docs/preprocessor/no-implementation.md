---
title: no_implementation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f169b30394e3fdf893475a49946266143772eb7
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50078065"
---
# <a name="noimplementation"></a>no_implementation
**C + + 전용**

래퍼 멤버 함수의 구현이 포함된 .tli 헤더를 생성하지 않습니다.

## <a name="syntax"></a>구문

```
no_implementation
```

## <a name="remarks"></a>설명

이 특성이 지정된 경우 형식 라이브러리 항목을 노출하는 선언이 포함된 .tlh 헤더가 .tli 헤더 파일을 포함하는 `#include` 문 없이 생성됩니다.

이 특성은 함께에서 사용 [implementation_only](../preprocessor/implementation-only.md)합니다.

**C + + 전용 종료**

## <a name="see-also"></a>참고 항목

[#import 특성](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import 지시문](../preprocessor/hash-import-directive-cpp.md)