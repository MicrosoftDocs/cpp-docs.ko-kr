---
description: '자세한 정보: 리소스 컴파일러 오류 RW2001'
title: 리소스 컴파일러 오류 RW2001
ms.date: 11/04/2016
f1_keywords:
- RW2001
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
ms.openlocfilehash: e550854af4d504e484b722050f0274887956f2c6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337253"
---
# <a name="resource-compiler-error-rw2001"></a>리소스 컴파일러 오류 RW2001

전처리 된 RC 파일의 지시문이 잘못 되었습니다.

RC 파일에 **#pragma** 지시문이 포함 되어 있습니다.

리소스 컴파일러가 포함 파일을 처리할 때 정의 하는 **RC_INVOKED** 상수를 사용 하 여 **#ifndef** 전처리기 지시문을 사용 합니다. **RC_INVOKED** 상수가 정의 될 때 처리 되지 않은 코드 블록 안에 **#pragma** 지시문을 추가 합니다. 블록의 코드는 리소스 컴파일러가 아니라 C/c + + 컴파일러에 의해서만 처리 됩니다. 다음 샘플 코드에서는이 기법을 보여 줍니다.

```
#ifndef RC_INVOKED
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler
#endif
```

**#Pragma** 전처리기 지시문은에서 의미가 없습니다. RC 파일. **#Include** 전처리기 지시문은에서 자주 사용 됩니다. 헤더 파일 (프로젝트 기반 사용자 지정 헤더 파일 또는 제품 중 하나를 사용 하 여 Microsoft에서 제공 하는 표준 헤더 파일)을 포함 하는 RC 파일 이러한 포함 파일 중 일부에는 **#pragma** 지시문이 포함 되어 있습니다. 헤더 파일에는 하나 이상의 다른 헤더 파일이 포함 될 수 있기 때문에 잘못 된 **#pragma** 지시어를 포함 하는 파일은 바로 명확 하지 않을 수 있습니다.

**#Ifndef RC_INVOKED** 기술은 프로젝트 기반 헤더 파일의 헤더 파일을 포함 하 여 제어할 수 있습니다.
