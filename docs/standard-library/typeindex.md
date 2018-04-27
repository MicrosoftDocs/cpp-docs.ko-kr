---
title: '&lt;typeindex&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <typeindex>
dev_langs:
- C++
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 63eae51554003a2c12caf2522a912adc9b96ec02
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2018
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
