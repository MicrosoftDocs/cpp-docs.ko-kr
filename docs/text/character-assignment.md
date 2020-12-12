---
description: '자세한 정보: 문자 할당'
title: 문자 할당
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], assignments
- MBCS [C++], character assignments
ms.assetid: dcc329cd-92df-4e20-817d-364be62ff28f
ms.openlocfilehash: d0db79acb8732404016f4a20579aff78ff996c17
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187548"
---
# <a name="character-assignment"></a>문자 할당

**`while`** 루프에서 문자열을 검색 하 고 ' X '를 제외한 모든 문자를 다른 문자열로 복사 하는 다음 예제를 살펴보십시오.

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
        *sz1++ = *sz2++;
    else
        sz2++;
}
```

이 코드는에서 가리키는 위치로 바이트를 복사 `sz2` `sz1` `sz1` 하 고 다음 바이트를 받도록 증분 합니다. 그러나의 다음 문자가 `sz2` 더블 바이트 문자인 경우 할당을 통해 `sz1` 첫 번째 바이트만 복사 됩니다. 다음 코드에서는 이식 가능한 함수를 사용 하 여 문자를 안전 하 게 복사 하 고을 증분 `sz1` 및 올바르게 복사 합니다 `sz2` .

```cpp
while( *sz2 )
{
    if( *sz2 != 'X' )
    {
        _mbscpy_s( sz1, 1, sz2 );
        sz1 = _mbsinc( sz1 );
        sz2 = _mbsinc( sz2 );
    }
    else
        sz2 = _mbsinc( sz2 );
}
```

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)<br/>
[문자 비교](../text/character-comparison.md)
