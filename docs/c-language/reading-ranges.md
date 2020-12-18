---
description: '자세한 정보: 범위 읽기'
title: 범위 읽기
ms.date: 11/04/2016
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
ms.openlocfilehash: afb1ff0f25360de7c47663279bf6f54dd7ca6a48
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97309123"
---
# <a name="reading-ranges"></a>범위 읽기

**ANSI 4.9.6.2**`fscanf` 함수에서 % [ 변환을 위한 scanlist의 첫 번째 문자도 아니고 마지막 문자도 아닌 대시(–) 문자의 해석

다음 줄

```
fscanf( fileptr, "%[A-Z]", strptr);
```

에서는 A–Z 범위에 속한 문자의 개수를 `strptr`이 가리키는 문자열로 읽습니다.

## <a name="see-also"></a>참조

[라이브러리 함수](../c-language/library-functions.md)
