---
title: 문자열 및 I-o 서식 (최신 c + +) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d73e42beb086f3db3e6a6fd060048fcb700156c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099826"
---
# <a name="string-and-io-formatting-modern-c"></a>문자열 및 I/O 서식 지정(최신 C++)

C + + [iostreams](../standard-library/iostream.md) 서식 문자열 I/O 수입니다. 예를 들어, 다음 코드를 보여 줍니다 정수 먼저 현재 상태를 저장 하 고 나중에 다시 설정, 이런 방식으로 한 줄에 대 한 뿐 아니라 변경 될 때까지 상태 서식 지정이 cout에 전달 된 후 유지 하기 때문에 16 진수로 출력 서식을 지정 하도록 cout를 설정 하는 방법 코드입니다.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main() 
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex 
        << uppercase 
        << setw(8) 
        << setfill('0') 
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

완전히 수 대부분에서 너무 복잡 합니다. 대신 비표준 이지만 Boost c + + 라이브러리에서 Boost.Format 사용할 수 있습니다. Boost 라이브러리를 다운로드할 수 있습니다 합니다 [Boost](http://www.boost.org/) 웹 사이트입니다.

Boost.Format의 몇 가지 이점은 다음과 같습니다.

- 안전: 형식이 안전한 오류에 대 한 예외를 throw-예를 들어, 너무 적거나 너무 많은 항목 사양입니다.

- 스트리밍할 수 있는 모든 형식에 대 한 확장 가능: 작동 합니다.

- 간편함: 표준 Posix와 유사한 형식 문자열입니다.

Boost.Format c + +에 빌드되어 있지만 [iostreams](../standard-library/iostream-programming.md), 성능 최적화 하지 않은 안전 하 고 확장 가능 합니다. 성능 최적화를 요구 하면 C는 것이 좋습니다 [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 하 고 [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), 빠르고 쉽게 사용할 수는 있습니다. 그러나 없는 확장 가능한 또는 취약성 으로부터 안전 합니다. (안전한 버전이 존재 하지만 성능이 약간 저하 있습니다. 자세한 내용은 [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) 하 고 [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

다음 코드는 Boost 서식 기능 중 일부를 보여 줍니다.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"  

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>참고자료

[C++의 진화](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 언어 참조](../cpp/cpp-language-reference.md)<br/>
[C++ 표준 라이브러리](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)