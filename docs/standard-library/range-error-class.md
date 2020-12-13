---
description: Range_error 클래스에 대해 자세히 알아보세요.
title: range_error 클래스
ms.date: 08/14/2018
f1_keywords:
- stdexcept/std::range_error
helpviewer_keywords:
- range_error class
ms.assetid: 8afb3e88-fc49-4213-b096-ed63d7aea37c
ms.openlocfilehash: c9d1ef328ba077b4b675d782df9c85d2db3a2072
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337960"
---
# <a name="range_error-class"></a>range_error 클래스

이 클래스는 범위 오류를 보고하기 위해 발생하는 모든 예외에 대한 기본 클래스로 사용됩니다.

## <a name="syntax"></a>구문

```cpp
class range_error : public runtime_error {
public:
    explicit range_error(const string& message);
    explicit range_error(const char *message);
};
```

## <a name="remarks"></a>설명

[에서 반환](../standard-library/exception-class.md) 되는 값은의 복사본입니다 `message.data` . 자세한 내용은 [basic_string::d ata](../standard-library/basic-string-class.md#data)를 참조 하세요.

## <a name="example"></a>예제

```cpp
// range_error.cpp
// compile with: /EHsc /GR
#include <iostream>
using namespace std;
int main()
{
   try
   {
      throw range_error( "The range is in error!" );
   }
   catch (range_error &e)
   {
      cerr << "Caught: " << e.what( ) << endl;
      cerr << "Type: " << typeid( e ).name( ) << endl;
   };
}
/* Output:
Caught: The range is in error!
Type: class std::range_error
*/
```

## <a name="requirements"></a>요구 사항

**헤더:**\<stdexcept>

**네임스페이스:** std

## <a name="see-also"></a>참고 항목

[runtime_error 클래스](../standard-library/runtime-error-class.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
