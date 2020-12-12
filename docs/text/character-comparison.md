---
description: '자세한 정보: 문자 비교'
title: 문자 비교
ms.date: 11/04/2016
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
ms.openlocfilehash: 0e00e087074a70145f1a73694293edc3c522d69f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297007"
---
# <a name="character-comparison"></a>문자 비교

다음 팁을 사용 합니다.

- 알려진 선행 바이트를 ASCII 문자와 비교 하는 것이 올바르게 작동 합니다.

    ```cpp
    if( *sz1 == 'A' )
    ```

- 두 개의 알 수 없는 문자를 비교 하려면 Mbstring에 정의 된 매크로 중 하나를 사용 해야 합니다.

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   이렇게 하면 더블 바이트 문자의 두 바이트를 같은지 비교할 수 있습니다.

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)<br/>
[버퍼 오버플로](../text/buffer-overflow.md)
