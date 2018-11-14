---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: 983fbc190fb83b81534e3888c748c0bf9c235638
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524666"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

포함 된 `iostreams` 표준 헤더 \<iomanip > 여러 조작자를 정의 하는 단일 인수입니다.

## <a name="syntax"></a>구문

```cpp
#include <iomanip>
```

## <a name="remarks"></a>설명

호출 하는 지정 되지 않은 형식, 반환 각 이러한 조작자 `T1` 를 통해 `T10`를 둘 다 오버 로드는 `basic_istream` \< **Elem**, **Tr** > `::` [연산자 >>](../standard-library/istream-operators.md#op_gt_gt) 하 고 `basic_ostream` \< **Elem**하십시오 **Tr** > `::` [연산자 <<](../standard-library/ostream-operators.md#op_lt_lt)합니다.

### <a name="manipulators"></a>조작자

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|통화 금액을 필요에 따라 국가별 형식으로 가져옵니다.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|지정된 형식으로 사용하여 시간 구조의 시간을 가져옵니다.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|통화 금액을 필요에 따라 국가별 형식으로 제공합니다.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|시간 구조의 시간 및 사용할 형식 문자열을 제공합니다.|
|[quoted](../standard-library/iomanip-functions.md#quoted)|삽입 및 추출 연산자를 사용하여 문자열의 편리한 라운드트립을 사용하도록 설정합니다.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|지정된 플래그를 지웁니다.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|정수의 밑을 설정합니다.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|오른쪽 맞춤된 디스플레이에서 공백을 채우는데 사용할 문자를 설정합니다.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|지정된 플래그를 설정합니다.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|부동 소수점 값의 전체 자릿수를 설정합니다.|
|[setw](../standard-library/iomanip-functions.md#setw)|표시 필드의 너비를 지정합니다.|

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 프로그래밍](../standard-library/iostream-programming.md)<br/>
[iostreams 규칙](../standard-library/iostreams-conventions.md)<br/>
