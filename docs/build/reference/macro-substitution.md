---
description: '자세히 알아보기: 매크로 대체'
title: 매크로 대체
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: 5e1531afb210b4671632bca2540bfc7562653139
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199183"
---
# <a name="macro-substitution"></a>매크로 대체

*Macroname* 이 호출 되 면 해당 정의 문자열 *에 있는 문자열 1* 의 각 항목이 문자열 *2* 로 바뀝니다.

## <a name="syntax"></a>구문

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>설명

매크로 대체는 대/소문자를 구분 하며 literal입니다. *문자열* 1과 *문자열 2* 는 매크로를 호출할 수 없습니다. 대체는 원래 정의를 수정 하지 않습니다. 을 제외한 모든 미리 정의 된 매크로에서 텍스트를 대체할 수 있습니다 [$$@](filename-macros.md) .

콜론 앞에 공백 또는 탭이 없습니다. 콜론 뒤의 any는 리터럴로 해석 됩니다. 문자열이 null 인 경우 매크로의 정의 문자열에서 *string1* 의 모든 항목이 *삭제 됩니다.*

## <a name="see-also"></a>참고 항목

[NMAKE 매크로 사용](using-an-nmake-macro.md)
