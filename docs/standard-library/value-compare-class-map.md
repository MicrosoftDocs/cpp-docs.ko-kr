---
description: '자세한 정보: value_compare 클래스 ( &lt; map &gt; )'
title: value_compare 클래스(&lt;map&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: c5b7ba865606e0bc5a5c8238de72824f9061c1b5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97312815"
---
# <a name="value_compare-class-ltmapgt"></a>value_compare 클래스(&lt;map&gt;)

키 값 비교를 통해 맵의 요소를 비교하여 map 내의 상대 순서를 확인할 수 있는 함수 개체를 제공합니다.

## <a name="syntax"></a>구문

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>설명

맵에 포함 된 전체 요소 중에서 제공 하는 비교 기준은 `value_compare` `value_types` 보조 클래스 생성에의 한 개별 요소의 키 간 비교에서 발생 합니다. 멤버 함수 연산자는 `comp` 에서 제공 하는 함수 개체에 저장 된 형식의 개체를 사용 하 여 `key_compare` `value_compare` 두 요소의 정렬 키 구성 요소를 비교 합니다.

키 값이 요소 값과 동일한 단순 컨테이너인 sets 및 multisets의 경우 `value_compare`는 `key_compare`와 동일합니다. 반면 maps 및 multimaps의 경우에는 `pair` 형식 요소의 값이 요소 키의 값과 동일하지 않으므로 value_compare가 key_compare와 동일하지 않습니다.

## <a name="example"></a>예제

`value_compare`를 선언하고 사용하는 방법의 예제는 [value_comp](../standard-library/map-class.md#value_comp)의 예제를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:**\<map>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[binary_function 구조체](../standard-library/binary-function-struct.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
