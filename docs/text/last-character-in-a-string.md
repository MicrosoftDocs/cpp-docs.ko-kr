---
description: '자세한 정보: 문자열의 마지막 문자'
title: 문자열의 마지막 문자
ms.date: 11/04/2016
helpviewer_keywords:
- last character in string
- MBCS [C++], last character in string
ms.assetid: 0a180376-4e55-41e8-9c64-539c7b6d8047
ms.openlocfilehash: 10ab90614509508b9667c29ccf166ddaf784a92e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207243"
---
# <a name="last-character-in-a-string"></a>문자열의 마지막 문자

다음 팁을 사용 합니다.

- 대부분의 경우 트레일 바이트 범위는 ASCII 문자 집합과 겹칩니다. 제어 문자 (32 미만)에 대해 bytewise 검색을 안전 하 게 사용할 수 있습니다.

- 문자열의 마지막 문자가 백슬래시 문자 인지 여부를 확인 하는 다음 코드 줄을 살펴보겠습니다.

    ```cpp
    if ( sz[ strlen( sz ) - 1 ] == '\\' )    // Is last character a '\'?
        // . . .
    ```

   `strlen`는 MBCS를 인식 하지 못하므로 멀티 바이트 문자열의 문자 수가 아닌 바이트 수를 반환 합니다. 또한 일부 코드 페이지 (예: 932)에서 ' \\ ' (0x5c)는 유효한 트레일 바이트 ( `sz` 는 C 문자열)입니다.

   가능한 한 가지 방법은 다음과 같이 코드를 다시 작성 하는 것입니다.

    ```cpp
    char *pLast;
    pLast = _mbsrchr( sz, '\\' );    // find last occurrence of '\' in sz
    if ( pLast && ( *_mbsinc( pLast ) == '\0' ) )
        // . . .
    ```

   이 코드는 MBCS 함수 및를 사용 합니다 `_mbsrchr` `_mbsinc` . 이러한 함수는 MBCS를 인식 하므로 ' ' \\ 문자와 후행 바이트 ' '를 구분할 수 있습니다 \\ . 문자열의 마지막 문자가 null (' \ 0 ') 이면 코드에서 일부 작업을 수행 합니다.

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)<br/>
[문자 할당](../text/character-assignment.md)
