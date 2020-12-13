---
description: Type_index 클래스에 대해 자세히 알아보세요.
title: type_index 클래스
ms.date: 11/04/2016
f1_keywords:
- typeindex/std::type_index
helpviewer_keywords:
- type_index class
ms.assetid: db366119-74cb-43e8-aacf-9679e561fa2f
ms.openlocfilehash: 4e9156420811d2712a5b9331d0ece0e7847103e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142690"
---
# <a name="type_index-class"></a>type_index 클래스

`type_index` 클래스는 [type_info 클래스](../cpp/type-info-class.md)에 포인터를 래핑하여 해당 개체에 의한 인덱싱을 지원합니다.

클래스 type_index {public: type_index (const type_info& tinfo); const char * name () const; size_t hash_code () const; bool operator = = (const type_info& right) const; bool operator! = (const type_info& right) const; bool operator< (const type_info& right) const; bool operator \<=(const type_info& right) const;
   bool operator> (const type_info& right) const; bool operator>= (const type_info& right) const;};

생성자는 `ptr`을 `&tinfo`로 초기화합니다.

`name`는 `ptr->name()`을 반환합니다.

`hash_code``ptr->hash_code().`를 반환합니다

`operator==`가 `*ptr == right.ptr`를 반환하는 경우

`operator!=`가 `!(*this == right)`를 반환하는 경우

`operator<`는 `*ptr->before(*right.ptr)`을 반환합니다.

`operator<=``!(right < *this).`를 반환합니다

`operator>`가 `right < *this`를 반환하는 경우

`operator>=`가 `!(*this < right)`를 반환하는 경우

## <a name="see-also"></a>참고 항목

[런타임 형식 정보](../cpp/run-time-type-information.md)\
[\<typeindex>](../standard-library/typeindex.md)
