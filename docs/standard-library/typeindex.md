---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 189fb7cd3757a3f71a50badc682b7b4db611b4e0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33855112"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

[type_info](../cpp/type-info-class.md) 클래스의 개체 인덱싱을 지원하는 클래스와 함수를 정의하기 위한 표준 헤더 \<typeindex>를 포함합니다.

## <a name="syntax"></a>구문

```cpp
#include <typeindex>
```

## <a name="remarks"></a>설명

[hash 구조체](../standard-library/hash-structure.md)는 [type_index](../standard-library/type-index-class.md) 형식의 값을 인덱스 값 분포에 매핑하는 데 적합한 `hash function`을 정의합니다.

`type_index` 클래스는 인덱싱을 지원하기 위해 포인터를 `type_info` 개체에 래핑합니다.

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
