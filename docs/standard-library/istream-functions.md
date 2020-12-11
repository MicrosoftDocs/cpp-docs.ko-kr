---
description: '자세히 알아보기: &lt; istream &gt; 함수'
title: '&lt;istream&gt; 함수'
ms.date: 11/04/2016
f1_keywords:
- istream/std::swap
- istream/std::ws
ms.assetid: 0301ea0d-4ded-4841-83dd-4253b55b3188
ms.openlocfilehash: c71770d8c6e86829eb4e0153abc924d612d3eff6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97154177"
---
# <a name="ltistreamgt-functions"></a>&lt;istream&gt; 함수

[스왑을](#istream_swap)\
[ws](#ws)

## <a name="swap"></a><a name="istream_swap"></a> 스왑을

두 stream 개체의 요소를 교환합니다.

```cpp
template <class Elem, class Tr>
void swap(
    basic_istream<Elem, Tr>& left,
    basic_istream<Elem, Tr>& right);

template <class Elem, class Tr>
void swap(
    basic_iostream<Elem, Tr>& left,
    basic_iostream<Elem, Tr>& right);
```

### <a name="parameters"></a>매개 변수

*비어*\
스트림입니다.

*오른쪽*\
스트림입니다.

## <a name="ws"></a><a name="ws"></a> ws-trust

스트림의 공백을 건너뜁니다.

```cpp
template class<Elem, Tr> basic_istream<Elem, Tr>& ws(basic_istream<Elem, Tr>& _Istr);
```

### <a name="parameters"></a>매개 변수

*_Istr*\
스트림입니다.

### <a name="return-value"></a>반환 값

스트림입니다.

### <a name="remarks"></a>설명

조작자는 `ch` [](../standard-library/basic-filebuf-class.md#open) <  **ctype** \< **Elem**> > ( [getloc](../standard-library/ios-base-class.md#getloc))를 use_facet 하는 모든 요소를 추출 하 고 삭제 합니다. **is**( **ctype** \< **Elem**> :: **space**, **ch**)가 true입니다.

함수는 요소를 추출하는 동안 파일 끝에 도달하면 [setstate](../standard-library/basic-ios-class.md#setstate)( **eofbit**)를 호출합니다. *_Istr* 를 반환 합니다.

### <a name="example"></a>예제

`ws` 사용 예제는 [operator>>](../standard-library/istream-operators.md#op_gt_gt)를 참조하세요.

## <a name="see-also"></a>참고 항목

[\<istream>](../standard-library/istream.md)
