---
description: '자세히 알아보기: 첨자'
title: 첨자
ms.date: 11/04/2016
helpviewer_keywords:
- subscript operator [C++], overloaded
- arrays [C++], subscripting
- subscripting [C++]
- operators [C++], overloading
- operator overloading [C++], examples
- subscript operator
ms.assetid: eb151281-6733-401d-9787-39ab6754c62c
ms.openlocfilehash: 77230045e66336e9989f49dd54557fa92d2ab001
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97178201"
---
# <a name="subscripting"></a>첨자

함수 호출 연산자와 같은 첨자 연산자 (**[]**)는 이항 연산자로 간주 됩니다. 첨자 연산자는 단일 인수를 사용하는 비정적 멤버 함수여야 합니다. 이 인수는 어떠한 형식도 될 수 있으며 원하는 배열 첨자를 지정합니다.

## <a name="example"></a>예제

다음 예제에서는 범위 검사를 구현 하는 형식의 벡터를 만드는 방법을 보여 줍니다 **`int`** .

```cpp
// subscripting.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class IntVector {
public:
   IntVector( int cElements );
   ~IntVector() { delete [] _iElements; }
   int& operator[](int nSubscript);
private:
   int *_iElements;
   int _iUpperBound;
};

// Construct an IntVector.
IntVector::IntVector( int cElements ) {
   _iElements = new int[cElements];
   _iUpperBound = cElements;
}

// Subscript operator for IntVector.
int& IntVector::operator[](int nSubscript) {
   static int iErr = -1;

   if( nSubscript >= 0 && nSubscript < _iUpperBound )
      return _iElements[nSubscript];
   else {
      clog << "Array bounds violation." << endl;
      return iErr;
   }
}

// Test the IntVector class.
int main() {
   IntVector v( 10 );
   int i;

   for( i = 0; i <= 10; ++i )
      v[i] = i;

   v[3] = v[9];

   for ( i = 0; i <= 10; ++i )
      cout << "Element: [" << i << "] = " << v[i] << endl;
}
```

```Output
Array bounds violation.
Element: [0] = 0
Element: [1] = 1
Element: [2] = 2
Element: [3] = 9
Element: [4] = 4
Element: [5] = 5
Element: [6] = 6
Element: [7] = 7
Element: [8] = 8
Element: [9] = 9
Array bounds violation.
Element: [10] = 10
```

## <a name="comments"></a>의견

`i`이전 프로그램에서 10에 도달 하면 **operator []** 는 범위를 벗어난 첨자가 사용 중임을 감지 하 고 오류 메시지를 발행 합니다.

함수 **연산자 []** 는 참조 형식을 반환 합니다. 이에 따라 l-value가 되므로 할당 연산자의 양쪽에서 첨자 식을 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

[연산자 오버로드](../cpp/operator-overloading.md)
