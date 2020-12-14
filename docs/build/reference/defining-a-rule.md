---
description: '자세히 알아보기: 규칙 정의'
title: 규칙 정의
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
ms.openlocfilehash: 89a5db90162ede02743aa469ac4f9e3d75c5e147
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201679"
---
# <a name="defining-a-rule"></a>규칙 정의

*Fromext* 는 종속 파일의 확장을 나타내며 *toext* 는 대상 파일의 확장을 나타냅니다.

```
.fromext.toext:
   commands
```

## <a name="remarks"></a>설명

확장은 대/소문자를 구분 하지 않습니다. 매크로를 호출 하 여 *fromext* 및 *toext* 를 나타낼 수 있습니다. 전처리 하는 동안 매크로가 확장 됩니다. *Fromext* 앞에 오는 마침표 (.)는 줄의 시작 부분에 있어야 합니다. 콜론 (:) 앞에 0 개 이상의 공백이 나 탭이 있습니다. 공백, 탭, 세미콜론 (;) 명령을 지정 하려면 숫자 기호 (#)를 지정 하 여 주석을 지정 하거나 줄 바꿈 문자를 지정 합니다. 다른 공백은 허용 되지 않습니다. 명령은 설명 블록으로 지정 됩니다.

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

[규칙에서 경로 검색](search-paths-in-rules.md)

## <a name="see-also"></a>참고 항목

[유추 규칙](inference-rules.md)
