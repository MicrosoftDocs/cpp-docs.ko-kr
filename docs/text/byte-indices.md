---
description: '자세한 정보: 바이트 인덱스'
title: 바이트 인덱스
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], byte indices
- byte indices [C++]
ms.assetid: f6e7774a-86c6-41c2-89e3-74fd46432e47
ms.openlocfilehash: 5ee4b2cb8611893c71f5c6597e619cc73e2848ef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187561"
---
# <a name="byte-indices"></a>바이트 인덱스

다음 팁을 사용 합니다.

- 문자열에 bytewise 인덱스를 사용 하면 포인터 조작에 의해 발생 하는 것과 유사한 문제가 발생 합니다. 문자열에서 백슬래시 문자를 검색 하는 다음 예제를 살펴보십시오.

    ```cpp
    while ( rgch[ i ] != '\\' )
        i++;
    ```

   이는 선행 바이트가 아닌 후행 바이트를 인덱싱할 수 있으므로를 가리키지 않을 수 있습니다 `character` .

- [_Mbclen](../c-runtime-library/reference/mbclen-mblen-mblen-l.md) 함수를 사용 하 여 위의 문제를 해결 합니다.

    ```cpp
    while ( rgch[ i ] != '\\' )
        i += _mbclen ( rgch + i );
    ```

   따라서 선행 바이트를 올바르게 인덱싱합니다 `character` . `_mbclen`함수는 문자 크기 (1 바이트 또는 2 바이트)를 결정 합니다.

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)<br/>
[문자열의 마지막 문자](../text/last-character-in-a-string.md)
