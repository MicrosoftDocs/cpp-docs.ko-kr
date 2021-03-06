---
description: '다음에 대 한 자세한 정보: &lt; 실행&gt;'
title: '&lt;문제점&gt;'
ms.date: 01/15/2021
f1_keywords:
- <execution>
- execution/std::execution
- std::execution
helpviewer_keywords:
- execution header
ms.openlocfilehash: 2ffba3ad8620092676588c2a67e36cf8956413ba
ms.sourcegitcommit: 3d9cfde85df33002e3b3d7f3509ff6a8dc4c0a21
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98667487"
---
# `<execution>`

병렬 알고리즘에 대 한 실행 정책에 대해 설명 합니다.

## <a name="syntax"></a>Syntax

```cpp
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```

### <a name="classes-and-structs"></a>클래스 및 구조체

|속성|Description|
|-|-|
|[`is_execution_policy` 구조체](is-execution-policy-struct.md)|다른 방법으로는 모호한 오버 로드 확인 참여를 제외 하는 실행 정책을 검색 합니다.|
|[`parallel_policy` 클래스](parallel-policy-class.md)|병렬 알고리즘 오버 로드를 명확 하 게 구분 하기 위해 고유한 형식으로 사용 됩니다. 병렬 알고리즘의 실행이 병렬화 될 수 있음을 나타냅니다.|
|[`parallel_unsequenced_policy` 클래스](parallel-unsequenced-policy-class.md)|병렬 알고리즘 오버 로드를 명확 하 게 구분 하기 위해 고유한 형식으로 사용 됩니다. 병렬 알고리즘의 실행이 병렬화 되어 벡터화 수 있음을 나타냅니다.|
|[`sequenced_policy` 클래스](sequenced-policy-class.md)|병렬 알고리즘 오버 로드를 명확 하 게 구분 하기 위해 고유한 형식으로 사용 됩니다. 병렬 알고리즘의 실행이 병렬화 되지 않을 수 있음을 지정 합니다.|

## <a name="requirements"></a>요구 사항

**헤더:**\<execution>

**네임스페이스:** stdext

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](thread-safety-in-the-cpp-standard-library.md)\
[C++ 표준 라이브러리 참조](cpp-standard-library-reference.md)
