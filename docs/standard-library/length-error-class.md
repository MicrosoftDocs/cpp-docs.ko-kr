---
description: Length_error 클래스에 대해 자세히 알아보세요.
title: length_error 클래스
ms.date: 11/04/2016
f1_keywords:
- stdexcept/std::length_error
helpviewer_keywords:
- length_error class
ms.assetid: d53c46c5-4626-400d-bd76-bf3e1e0f64ae
ms.openlocfilehash: 051f79da569a153413a88af4976cb619e4b04e66
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112052"
---
# <a name="length_error-class"></a>length_error 클래스

이 클래스는 너무 길어서 지정할 수 없는 개체 생성 시도를 보고하기 위해 발생하는 모든 예외에 대한 기본 클래스로 사용됩니다.

## <a name="syntax"></a>구문

```cpp
class length_error : public logic_error {
public:
    explicit length_error(const string& message);

    explicit length_error(const char *message);

};
```

## <a name="remarks"></a>설명

에서 반환 하는 값은 `what()` 의 복사본입니다 `message.data()` . 자세한 내용은 [`what`](../standard-library/exception-class.md) 및 [`data`](../standard-library/basic-string-class.md#data)을 참조하세요.

## <a name="example"></a>예제

```cpp
// length_error.cpp
// compile with: /EHsc /GR /MDd
#include <vector>
#include <iostream>

using namespace std;

template<class  T>
class stingyallocator : public allocator< T>
{
public:
   template <class U>
      struct rebind { typedef stingyallocator<U> other; };
   _SIZT max_size( ) const
   {
         return 10;
   };

};

int main( )
{
   try
   {
      vector<int, stingyallocator< int > > myv;
      for ( int i = 0; i < 11; i++ ) myv.push_back( i );
   }
   catch ( exception &e )
   {
      cerr << "Caught " << e.what( ) << endl;
      cerr << "Type " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught vector<T> too long
Type class std::length_error
*/
```

## <a name="requirements"></a>요구 사항

**헤더:**\<stdexcept>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[logic_error 클래스](../standard-library/logic-error-class.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
