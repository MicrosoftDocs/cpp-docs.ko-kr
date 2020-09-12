---
title: '&lt;bit&gt;'
description: 개별 비트 및 비트 시퀀스를 액세스, 조작 및 처리 하는 함수입니다.
ms.date: 08/28/2020
f1_keywords:
- <bit>
helpviewer_keywords:
- bit header
ms.openlocfilehash: 5652d0af767520710ee08b1827e0df27c477ee6d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040056"
---
# <a name="ltbitgt"></a>&lt;bit&gt;

개별 비트 및 비트 시퀀스를 액세스, 조작 및 처리 하는 함수를 정의 합니다.

예를 들어 비트를 회전 하 고, 연속 설정 또는 선택이 취소 된 비트 수를 찾거나, 숫자가 2의 정수 거듭제곱 인지 확인 하 고, 숫자를 나타낼 최소 비트 수를 찾는 등의 함수를 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

**헤더:**\<bit>

**네임스페이스:** std

[/std: c + + 최신](../build/reference/std-specify-language-standard-version.md) 항목이 필요 합니다.

## <a name="members"></a>멤버

### <a name="types"></a>유형

| Type | Description |
|--------|----------|
| [endian](bit-enum.md) | 스칼라 형식의 endian 지정 합니다. |

### <a name="functions"></a>Functions

| 함수 | Description |
|-----|-----|
|[bit_cast](bit-functions.md#bit_cast) | 개체 표현을 한 형식에서 다른 형식으로 다시 해석 합니다. |
|[bit_ceil](bit-functions.md#bit_ceil) | 값 보다 크거나 같은 2의 가장 작은 거듭제곱을 찾습니다. |
|[bit_floor](bit-functions.md#bit_floor) | 값 보다 크지 않은 2의 가장 큰 정수 거듭제곱을 찾습니다. |
|[bit_width](bit-functions.md#bit_width) | 값을 나타내는 데 필요한 최소 비트 수를 찾습니다. |
|[countl_zero](bit-functions.md#countl_zero) | 가장 중요 한 비트에서 시작 하 여 0으로 설정 된 연속 비트 수를 계산 합니다. |
|[countl_one](bit-functions.md#countl_one) | 가장 중요 한 비트에서 시작 하 여 1로 설정 된 연속 비트 수를 계산 합니다. |
|[countr_zero](bit-functions.md#countr_zero) | 최하위 비트에서 시작 하 여 0으로 설정 된 연속 비트 수를 계산 합니다. |
|[countr_one](bit-functions.md#countl_one) | 최하위 비트에서 시작 하 여 1로 설정 된 연속 비트 수를 계산 합니다. |
|[has_single_bit](bit-functions.md#has_single_bit) | 값에 1 비트만 설정 되어 있는지 확인 합니다. 이는 값이 2의 거듭제곱 인지 여부를 테스트 하는 것과 같습니다. |
|[popcount](bit-functions.md#popcount) | 1로 설정 된 비트 수를 계산 합니다. |
|[rotl](bit-functions.md#rotl) | 비트 왼쪽 회전의 결과를 계산 합니다. |
|[rotr](bit-functions.md#rotr) | 비트 오른쪽 회전의 결과를 계산 합니다. |

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](cpp-standard-library-header-files.md)