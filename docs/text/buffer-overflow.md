---
description: '자세한 정보: 버퍼 오버플로'
title: 버퍼 오버플로
ms.date: 11/04/2016
helpviewer_keywords:
- buffers [C++], character sizes
- buffer overflows [C++]
- MBCS [C++], buffer overflow
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
ms.openlocfilehash: 17da102b9a48a34d9879c08f0470ced3852ed0ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97187600"
---
# <a name="buffer-overflow"></a>버퍼 오버플로

문자 크기를 변경 하면 문자를 버퍼에 넣을 때 문제가 발생할 수 있습니다. 문자열의 문자를 버퍼로 복사 하는 다음 코드를 고려 합니다 `sz` `rgch` .

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
    rgch[ cb++ ] = *sz++;
```

질문은: 마지막 바이트가 선행 바이트를 복사 했습니까? 다음은 버퍼를 잠재적으로 오버플로될 수 있으므로 문제를 해결 하지 않습니다.

```cpp
cb = 0;
while( cb < sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

`_mbccpy`이 호출은 올바른 작업을 수행 하려고 시도 합니다. 즉, 1 바이트 또는 2 바이트 인지에 관계 없이 전체 문자를 복사 합니다. 그러나 문자의 너비가 2 바이트 이면 복사 된 마지막 문자가 버퍼에 맞지 않을 수 있다는 것을 고려 하지 않습니다. 올바른 솔루션은 다음과 같습니다.

```cpp
cb = 0;
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )
{
    _mbccpy( rgch + cb, sz );
    cb += _mbclen( sz );
    sz = _mbsinc( sz );
}
```

이 코드는를 사용 하 여 `_mbclen` 가 가리키는 현재 문자의 크기를 테스트 하는 루프 테스트에서 가능한 버퍼 오버플로를 테스트 `sz` 합니다. 함수를 호출 하 여 `_mbsnbcpy` 루프의 코드를 **`while`** 한 줄의 코드로 바꿀 수 있습니다. 예를 들어:

```cpp
_mbsnbcpy( rgch, sz, sizeof( rgch ) );
```

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)
