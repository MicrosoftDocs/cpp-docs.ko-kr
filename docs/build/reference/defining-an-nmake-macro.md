---
description: '자세한 정보: NMAKE 매크로 정의'
title: NMake 매크로 정의
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
ms.openlocfilehash: 133e05cac2a236a38f6b2d1e719f1b66fd73760d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201640"
---
# <a name="defining-an-nmake-macro"></a>NMake 매크로 정의

## <a name="syntax"></a>구문

```

macroname=string
```

## <a name="remarks"></a>설명

*Macroname* 은 문자, 숫자 및 밑줄 (_)이 최대 1024 자인 조합 이며 대/소문자를 구분 합니다. *Macroname* 은 호출 된 매크로를 포함할 수 있습니다. *Macroname* 이 모두 호출 된 매크로로 구성 된 경우에는 호출 되는 매크로가 null 이거나 정의 되지 않은 상태일 수 없습니다.

는 `string` 0 개 이상의 문자 시퀀스 일 수 있습니다. Null 문자열은 문자를 포함 하지 않거나 공백 또는 탭만 포함 합니다. 에는 `string` 매크로 호출이 포함 될 수 있습니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[매크로의 특수 문자](special-characters-in-macros.md)

[null 및 정의되지 않은 매크로](null-and-undefined-macros.md)

[매크로를 정의할 위치](where-to-define-macros.md)

[매크로 정의의 우선 순위](precedence-in-macro-definitions.md)

## <a name="see-also"></a>참고 항목

[매크로와 NMake](macros-and-nmake.md)
