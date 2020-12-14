---
description: '자세한 정보: 매크로의 특수 문자'
title: 매크로의 특수 문자
ms.date: 11/04/2016
helpviewer_keywords:
- special characters, in NMAKE macros
ms.assetid: c0a06cfc-7103-4ee2-a585-e8f6e85dccd7
ms.openlocfilehash: 569aedbc474f660894b723f9356355e2360a4e61
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224662"
---
# <a name="special-characters-in-macros"></a>매크로의 특수 문자

정의 뒤에 오는 숫자 기호 (#)는 주석을 지정 합니다. 매크로에 리터럴 숫자 기호를 지정 하려면 ^ #와 같이 캐럿 (^)을 사용 합니다.

달러 기호 ($)는 매크로 호출을 지정 합니다. $ $를 지정 하려면 $ $를 사용 합니다.

정의를 새 줄로 확장 하려면 줄을 백슬래시 ()로 종료 \\ 합니다. 매크로가 호출 될 때 백슬래시와 줄 바꿈 문자가 공백으로 바뀝니다. 줄의 끝에 리터럴 백슬래시를 지정 하려면 캐럿 (^) 앞에 백슬래시를 추가 하거나 주석 지정자 (#)를 사용 하 여 뒤에 추가 합니다.

리터럴 줄 바꿈 문자를 지정 하려면 다음과 같이 캐럿 (^)을 사용 하 여 줄을 종료 합니다.

```
CMDS = cls^
dir
```

## <a name="see-also"></a>참고 항목

[NMAKE 매크로 정의](defining-an-nmake-macro.md)
