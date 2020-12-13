---
description: '다음에 대 한 자세한 정보: output_iterator_tag 구조체'
title: output_iterator_tag 구조체
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 1bd97f88dc7ae68976920cf006cd10115b16b2f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340907"
---
# <a name="output_iterator_tag-struct"></a>output_iterator_tag 구조체

출력 반복기를 나타내는 함수의 반환 형식을 제공 하는 클래스입니다 `iterator_category` .

## <a name="syntax"></a>Syntax

구조체 output_iterator_tag {} ;

## <a name="remarks"></a>설명

범주 태그 클래스는 알고리즘 선택을 위한 컴파일 태그로 사용됩니다. 템플릿 함수는 컴파일 시간에서 가장 효율적인 알고리즘을 사용할 수 있도록 해당 반복기 인수의 가장 구체적인 범주를 찾아야 합니다. `Iterator` 형식의 모든 반복기에 대해 `iterator_traits`< `Iterator`> **::iterator_category** 는 반복기 동작을 설명하는 가장 구체적인 범주 태그로 정의되어야 합니다.

형식은  \< **Iter**> 출력 반복기로 사용 될 수 있는 개체를 설명 하는 경우 반복기 **:: iterator_category** 와 동일 합니다 `Iter` .

이 태그는 다른 반복기 태그처럼 반복기에 대해 `value_type` 또는 `difference_type`에서 매개 변수화되지 않습니다. 출력 반복기에는 `value_type` 또는 `difference_type`이 없기 때문입니다.

## <a name="example"></a>예제

`iterator_tag` S를 사용하는 방법에 대한 예제는 [iterator_traits](../standard-library/iterator-traits-struct.md) 또는 [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:**\<iterator>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C + + 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)
