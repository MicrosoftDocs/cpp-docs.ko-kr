---
title: collate 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
dev_langs:
- C++
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 054246ce78601abf61f36d070500845275b61761
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44110375"
---
# <a name="collate-class"></a>collate 클래스

문자열 내 문자의 정렬 및 그룹화, 문자열 간의 비교, 문자열 해싱을 제어하는 로캘 패싯으로 사용할 수 있는 개체를 설명하는 템플릿 클래스입니다.

## <a name="syntax"></a>구문

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>매개 변수

*CharType*<br/>
문자를 인코딩하기 위해 프로그램 내 사용하는 형식

## <a name="remarks"></a>설명

모든 로캘 패싯과 마찬가지로, 고정 개체 ID에는 초기값 0이 저장되어 있습니다. 저장된 값에 액세스를 처음 시도하면 `id`에 고유한 양수 값이 저장됩니다. 일부 언어에서는 문자가 그룹화되고 단일 문자로 취급되며, 다른 언어에서는 개별 문자가 두 문자인 것처럼 취급됩니다. collate 클래스에서 제공하는 데이터 정렬 서비스는 이러한 경우를 정렬하는 방법을 제공합니다.

### <a name="constructors"></a>생성자

|생성자|설명|
|-|-|
|[collate](#collate)|문자열 정렬 규칙을 처리할 로캘 패싯으로 사용할 `collate` 클래스 개체의 생성자입니다.|

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[char_type](#char_type)|`CharType` 형식의 문자를 설명하는 형식입니다.|
|[string_type](#string_type)|`basic_string` 형식의 문자가 포함된 `CharType` 형식의 문자열을 설명하는 형식입니다.|

### <a name="member-functions"></a>멤버 함수

|멤버 함수|설명|
|-|-|
|[compare](#compare)|패싯별 규칙에 따라 두 문자 시퀀스의 같음 또는 동등성을 비교합니다.|
|[do_compare](#do_compare)|패싯별 규칙에 따라 두 문자 시퀀스를 비교하기 위해 가상 함수를 호출하여 두 문자 시퀀스의 같음 또는 동등성을 비교합니다.|
|[do_hash](#do_hash)|패싯별 규칙에 따라 시퀀스의 해시 값을 확인하기 위해 가상 함수를 호출합니다.|
|[do_transform](#do_transform)|가상 함수를 호출하여 문자 시퀀스를 로캘에서 문자열로 변환하고 동일한 로캘에서 유사한 방식으로 변환된 다른 문자 시퀀스와 사전순으로 비교하는 데 사용합니다.|
|[hash](#hash)|패싯별 규칙에 따라 시퀀스의 해시 값을 확인합니다.|
|[transform](#transform)|문자 시퀀스를 로캘에서 문자열로 변환하고 동일한 로캘에서 유사한 방식으로 변환된 다른 문자 시퀀스와 사전순으로 비교하는 데 사용합니다.|

## <a name="requirements"></a>요구 사항

**헤더:** \<locale>

**네임스페이스:** std

## <a name="char_type"></a>  collate::char_type

`CharType` 형식의 문자를 설명하는 형식입니다.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>설명

이 형식은 템플릿 매개 변수 `CharType`의 동의어입니다.

## <a name="collate"></a>  collate::collate

문자열 정렬 규칙을 처리하는 데 로캘 패싯으로 사용할 collate 클래스 개체의 생성자입니다.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>매개 변수

*_Refs*<br/>
개체에 대한 메모리 관리 형식을 지정하는 데 사용하는 정수값입니다.

*_Locname*<br/>
로캘 이름입니다.

### <a name="remarks"></a>설명

에 대 한 가능한 값을 *_Refs* 매개 변수 및 중요성은:

- 0: 개체를 포함하는 로캘에 의해 개체의 수명이 관리됩니다.

- 1: 개체의 수명을 수동으로 관리해야 합니다.

- \> 1: 이러한 값은 정의 되지 않습니다.

생성자를 통해 해당 기준 개체를 초기화 **locale::**[패싯](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>  collate::compare

패싯별 규칙에 따라 두 문자 시퀀스의 같음 또는 동등성을 비교합니다.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>매개 변수

*first1*<br/>
비교할 첫 번째 시퀀스의 첫 번째 요소에 대한 포인터입니다.

*last1*<br/>
비교할 첫 번째 시퀀스의 마지막 요소에 대한 포인터입니다.

*first2*<br/>
비교할 두 번째 시퀀스의 첫 번째 요소에 대한 포인터입니다.

*last2*<br/>
비교할 두 번째 시퀀스의 마지막 요소에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

멤버 함수는 다음을 반환합니다.

- 첫 번째 시퀀스가 두 번째 시퀀스보다 작은 것으로 비교되는 경우, -1

- 두 번째 시퀀스가 첫 번째 시퀀스보다 작은 것으로 비교되는 경우, +1

- 시퀀스가 같은 경우, 0

### <a name="remarks"></a>설명

시퀀스 내에서 가장 앞의 서로 다른 쌍에 더 작은 요소가 있는 경우 또는 서로 다른 쌍이 없지만 첫 번째 시퀀스가 더 짧은 경우 첫 번째 시퀀스는 더 작은 것으로 비교됩니다.

멤버 함수는 [do_compare](#do_compare)(`first1`, `last1`, `first2`, `last2`)를 반환합니다.

### <a name="example"></a>예제

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="do_compare"></a>  collate::do_compare

패싯별 규칙에 따라 두 문자 시퀀스를 비교하기 위해 가상 함수를 호출하여 두 문자 시퀀스의 같음 또는 동등성을 비교합니다.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>매개 변수

*first1*<br/>
비교할 첫 번째 시퀀스의 첫 번째 요소에 대한 포인터입니다.

*last1*<br/>
비교할 첫 번째 시퀀스의 마지막 요소에 대한 포인터입니다.

*first2*<br/>
비교할 두 번째 시퀀스의 첫 번째 요소에 대한 포인터입니다.

*last2*<br/>
비교할 두 번째 시퀀스의 마지막 요소에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

멤버 함수는 다음을 반환합니다.

- 첫 번째 시퀀스가 두 번째 시퀀스보다 작은 것으로 비교되는 경우, -1

- 두 번째 시퀀스가 첫 번째 시퀀스보다 작은 것으로 비교되는 경우, +1

- 시퀀스가 같은 경우, 0

### <a name="remarks"></a>설명

보호 된 가상 멤버 함수에 순서 비교 [* first1, Last1) *의 시퀀스 *[first2, last2*). 적용 하 여 값을 비교 `operator<` 형식의 해당 요소 쌍 간에 `CharType`입니다. 시퀀스 내에서 가장 앞의 서로 다른 쌍에 더 작은 요소가 있는 경우 또는 서로 다른 쌍이 없지만 첫 번째 시퀀스가 더 짧은 경우 첫 번째 시퀀스는 더 작은 것으로 비교됩니다.

### <a name="example"></a>예제

`do_compare`를 호출하는 [collate::compare](#compare)에 대한 예제를 참조하세요.

## <a name="do_hash"></a>  collate::do_hash

패싯별 규칙에 따라 시퀀스의 해시 값을 확인하기 위해 가상 함수를 호출합니다.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*first*<br/>
결정할 값이 있는 시퀀스의 첫 번째 문자에 대한 포인터입니다.

*last*<br/>
결정할 값이 있는 시퀀스의 마지막 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

시퀀스에 대한 **long** 형식의 해시 값입니다.

### <a name="remarks"></a>설명

해시 값은 목록의 배열에 의사(pseudo) 임의로 시퀀스를 분산하는 경우 등에 유용할 수 있습니다.

### <a name="example"></a>예제

`do_hash`를 호출하는 [hash](#hash)에 대한 예제를 참조하세요.

## <a name="do_transform"></a>  collate::do_transform

가상 함수를 호출하여 문자 시퀀스를 로캘에서 문자열로 변환하고 동일한 로캘에서 유사한 방식으로 변환된 다른 문자 시퀀스와 사전순으로 비교하는 데 사용합니다.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*first*<br/>
변환할 시퀀스의 첫 번째 문자에 대한 포인터입니다.

*last*<br/>
변환할 시퀀스의 마지막 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

변환된 문자 시퀀스인 문자열입니다.

### <a name="remarks"></a>설명

보호된 가상 멤버 함수는 제어된 시퀀스가 시퀀스 [`first`, `last`)의 복사본인 [string_type](#string_type) 클래스의 개체를 반환합니다. collate\< **CharType**>에서 파생된 클래스가 [do_compare](#do_compare)를 재정의하는 경우 `do_transform`도 일치하도록 재정의해야 합니다. `collate::compare`에 전달된 경우 두 개의 변형된 문자열은 파생된 클래스에서 비교할 변환되지 않은 문자열을 전달하여 얻을 수 있는 것과 동일한 결과를 생성해야 합니다.

### <a name="example"></a>예제

`do_transform`을 호출하는 [transform](#transform)에 대한 예제를 참조하세요.

## <a name="hash"></a>  collate::hash

패싯별 규칙에 따라 시퀀스의 해시 값을 확인합니다.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*first*<br/>
결정할 값이 있는 시퀀스의 첫 번째 문자에 대한 포인터입니다.

*last*<br/>
결정할 값이 있는 시퀀스의 마지막 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

시퀀스에 대한 **long** 형식의 해시 값입니다.

### <a name="remarks"></a>설명

멤버 함수는 [do_hash](#do_hash)(`first`, `last`)를 반환합니다.

해시 값은 목록의 배열에 의사(pseudo) 임의로 시퀀스를 분산하는 경우 등에 유용할 수 있습니다.

### <a name="example"></a>예제

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="string_type"></a>  collate::string_type

`basic_string` 형식의 문자가 포함된 `CharType` 형식의 문자열을 설명하는 형식입니다.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>설명

이 형식은 개체가 소스 시퀀스의 복사본을 저장할 수 있는 템플릿 클래스 [basic_string](../standard-library/basic-string-class.md)의 특수화를 설명합니다.

### <a name="example"></a>예제

`string_type`의 선언 및 사용 방법의 예는 [transform](#transform)을 참조하세요.

## <a name="transform"></a>  collate::transform

문자 시퀀스를 로캘에서 문자열로 변환하고 동일한 로캘에서 유사한 방식으로 변환된 다른 문자 시퀀스와 사전순으로 비교하는 데 사용합니다.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>매개 변수

*first*<br/>
변환할 시퀀스의 첫 번째 문자에 대한 포인터입니다.

*last*<br/>
변환할 시퀀스의 마지막 문자에 대한 포인터입니다.

### <a name="return-value"></a>반환 값

변환된 문자 시퀀스가 포함된 문자열입니다.

### <a name="remarks"></a>설명

멤버 함수는 반환 [do_transform](#do_transform)(`first`, `last`).

### <a name="example"></a>예제

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>참고자료

[\<locale>](../standard-library/locale.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
