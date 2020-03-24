---
title: 컴파일러 경고(수준 1) C4651
ms.date: 11/04/2016
f1_keywords:
- C4651
helpviewer_keywords:
- C4651
ms.assetid: f1ea82aa-4dc1-4972-b55a-57fdb962f0dd
ms.openlocfilehash: bc8131665c970c3b86bb1e84e39636ae8f93897b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80199544"
---
# <a name="compiler-warning-level-1-c4651"></a>컴파일러 경고(수준 1) C4651

미리 컴파일된 헤더에 대해 ' 정의 '가 지정 되었지만 현재 컴파일에는 지정 되지 않았습니다.

미리 컴파일된 헤더를 생성할 때 정의가 지정 되었지만이 컴파일에서는 지정 되지 않았습니다.

이 정의는 미리 컴파일된 헤더 내에서 적용 되지만 나머지 코드에는 적용 되지 않습니다.

/DSYMBOL를 사용 하 여 미리 컴파일된 헤더를 빌드한 경우/Yu 컴파일에/DSYMBOL.가 없는 경우 컴파일러에서이 경고를 생성 합니다.  /Yu 명령줄에/DSYMBOL를 추가 하면이 경고가 해결 됩니다.
