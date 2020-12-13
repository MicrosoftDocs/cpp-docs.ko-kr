---
description: '자세한 정보: 단일 인수를 사용 하는 출력 스트림 조작자 (int 또는 long)'
title: 하나의 인수를 포함하는 출력 스트림 조작자(int 또는 long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: e04486f7d207731d9fbf7ba8083ffcb02a82ba8a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340894"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>하나의 인수를 포함하는 출력 스트림 조작자(int 또는 long)

iostream 클래스 라이브러리는 매개 변수가 있는 조작자를 만들기 위한 매크로 집합을 제공합니다. 단일 또는 인수를 사용 하는 조작자는 **`int`** **`long`** 특수 한 경우입니다. 단일 또는 인수 (예:)를 허용 하는 출력 스트림 조작자를 만들려면 **`int`** **`long`** `setw` 에 정의 되어 있는 _Smanip 매크로를 사용 해야 합니다 \<iomanip> . 이 예제에서는 지정된 수의 공백을 스트림에 삽입하는 `fillblank` 조작자를 정의합니다.

## <a name="example"></a>예제

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>참고 항목

[인수가 있는 사용자 지정 조작자](../standard-library/custom-manipulators-with-arguments.md)
