---
description: '자세한 정보: 컴파일러 경고 (수준 1) C4041'
title: 컴파일러 경고(수준 1) C4041
ms.date: 11/04/2016
f1_keywords:
- C4041
helpviewer_keywords:
- C4041
ms.assetid: 107ee9fd-4b88-4f22-a18f-a20726831095
ms.openlocfilehash: d3473be35182f6c99541aa2a0fc79de79dee4a07
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97160716"
---
# <a name="compiler-warning-level-1-c4041"></a>컴파일러 경고(수준 1) C4041

컴파일러 한계 : 브라우저 출력을 종료하고 있습니다.

브라우저 정보가 컴파일러 한계를 초과했습니다.

[/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) (지역 변수를 포함하는 브라우저 정보)을 사용하여 컴파일하면 이 경고가 발생할 수 있습니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. /Fr(지역 변수 없는 브라우저 정보)을 사용하여 컴파일합니다.

1. 브라우저 출력을 사용하지 않도록 설정합니다(/FR 또는 /Fr 없이 컴파일).
