---
description: '자세한 정보: 컴파일러 경고 (수준 2 및 3) C4008'
title: 컴파일러 경고(수준 2 및 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 6f13ef60efabeaffe549189431aa04c65a12cbe5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97234425"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>컴파일러 경고(수준 2 및 3) C4008

'identifier': 'attribute' 특성이 무시됩니다.

컴파일러가 **`__fastcall`** **`static`** **`inline`** 함수 (수준 3 경고) 또는 데이터 (수준 2 경고)에 대 한, 또는 특성을 무시 했습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. **`__fastcall`** 데이터가 있는 특성입니다.

1. **`static`****`inline`** **main** 함수를 사용 하는 또는 특성입니다.
