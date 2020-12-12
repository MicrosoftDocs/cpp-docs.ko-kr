---
description: '자세히 알아보기: 포인터 증가 및 감소'
title: 포인터 증가 및 감소
ms.date: 11/04/2016
helpviewer_keywords:
- incrementing pointers
- MBCS [C++], pointers
- pointers [C++], multibyte characters
- decrementing pointers
ms.assetid: 0872b4a0-e2bd-4004-8319-070efb76f2fd
ms.openlocfilehash: 3c333c11c5a0b68bf013dbd374eb1cc4e5f00abc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97207321"
---
# <a name="incrementing-and-decrementing-pointers"></a>포인터 증가 및 감소

다음 팁을 사용 합니다.

- 후행 바이트를 가리킵니다. 일반적으로 트레일 바이트에 대 한 포인터를 포함 하는 것은 안전 하지 않습니다. 일반적으로 역방향이 아닌 문자열을 앞으로 검색 하는 것이 더 안전 합니다.

- 전체 문자를 이동 하는 포인터 증가/감소 함수 및 매크로를 사용할 수 있습니다.

    ```cpp
    sz1++;
    ```

   다음과 같이 사용하십시오.

    ```cpp
    sz1 = _mbsinc( sz1 );
    ```

   `_mbsinc`및 `_mbsdec` 함수는 `character` 문자 크기에 관계 없이 단위를 올바르게 증가 및 감소 시킵니다.

- 감소의 경우 다음과 같이 문자열의 헤드에 대 한 포인터가 필요 합니다.

    ```cpp
    sz2--;
    ```

   다음과 같이 사용하십시오.

    ```cpp
    sz2 = _mbsdec( sz2Head, sz2 );
    ```

   또는 다음과 같이 head 포인터가 문자열의 올바른 문자에 대 한 것일 수 있습니다.

    ```cpp
    sz2Head < sz2
    ```

   알려진 유효한 선행 바이트에 대 한 포인터가 있어야 합니다.

- 보다 빠른 호출을 위해 이전 문자에 대 한 포인터를 유지 관리 하려고 할 수 있습니다 `_mbsdec` .

## <a name="see-also"></a>참고 항목

[MBCS 프로그래밍 팁](../text/mbcs-programming-tips.md)<br/>
[바이트 인덱스](../text/byte-indices.md)
