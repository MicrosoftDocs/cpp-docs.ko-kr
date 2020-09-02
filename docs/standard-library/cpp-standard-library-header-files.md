---
title: C + + 표준 라이브러리 헤더 파일
description: C + + 표준 라이브러리 헤더 파일, 분류
ms.date: 08/31/2020
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 0bbd67468c1df8b9e7c078f498d19f01f848149c
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281850"
---
# <a name="c-standard-library-header-files"></a>C + + 표준 라이브러리 헤더 파일

C + + 표준 라이브러리 및 확장에 대 한 헤더 파일 (범주별).

## <a name="headers-by-category"></a>범주별 헤더

::: moniker range=">=vs-2017"

| 범주 | headers |
| - | - |
| [알고리즘](../cpp/algorithms-modern-cpp.md) | [\<algorithm>](algorithm.md), [\<cstdlib>](cstdlib.md), [\<numeric>](numeric.md) |
| 원자 단위 연산 |  [\<atomic>](atomic.md)<sup>pt</sup> |
| C 라이브러리 래퍼 | [\<cassert>](cassert.md), [\<ccomplex>](ccomplex.md) <sup>11 a b</sup>,,, [\<cctype>](cctype.md) [\<cerrno>](cerrno.md) [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cfloat>](cfloat.md) , [\<cinttypes>](cinttypes.md) <sup>11</sup>, b,,,,,, [\<ciso646>](ciso646.md) <sup>b</sup> [\<climits>](climits.md) [\<clocale>](clocale.md) [\<cmath>](cmath.md) [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) [\<cstdalign>](cstdalign.md) <sup>11 a b</sup>, [\<cstdarg>](cstdarg.md) , [\<cstdbool>](cstdbool.md) <sup>11 a b</sup>, [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdio>](cstdio.md) ,,, [\<cstdlib>](cstdlib.md) [\<cstring>](cstring.md) [\<ctgmath>](ctgmath.md) <sup>11 a b</sup>, [\<ctime>](ctime.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) ,[\<cwctype>](cwctype.md) |
| 개념 | \<concepts><sup>720</sup> |
| [컨테이너](../cpp/containers-modern-cpp.md) | |
| 시퀀스 컨테이너 | [\<array>](array.md)<sup>11</sup>, [\<deque>](deque.md) , [\<forward_list>](forward-list.md) <sup>11</sup>, [\<list>](list.md) ,[\<vector>](vector.md) |
| 정렬 된 연관 컨테이너| [\<map>](map.md), [\<set>](set.md) |
| 순서가 지정 되지 않은 연관 컨테이너 | [\<unordered_map>](unordered-map.md)<sup>11</sup>, [\<unordered_set>](unordered-set.md) <sup>11</sup> |
| 컨테이너 어댑터 | [\<queue>](queue.md), [\<stack>](stack.md) |
| 컨테이너 뷰 | [\<span>](span.md)<sup>720</sup> |
| [오류 및 예외 처리](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert>](cassert.md), [\<exception>](exception.md) , [\<stdexcept>](stdexcept.md) , [\<system_error>](system-error.md) <sup>11</sup> |
| 일반 유틸리티 | \<any><sup>17</sup>, [\<bit>](bit.md) <sup>20</sup>, [\<bitset>](bitset.md) , [\<cstdlib>](cstdlib.md) , \<execution> <sup>17</sup>, [\<functional>](functional.md) , [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, \<optional> <sup>17</sup>, [\<ratio>](ratio.md) <sup>11</sup>, [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup>, 11, [\<tuple>](tuple.md) <sup>11</sup> [\<type_traits>](type-traits.md) <sup>11</sup>, [\<typeindex>](typeindex.md) <sup>11</sup>, [\<utility>](utility.md) \<variant> <sup>17</sup> |
| [I/o 및 서식 지정](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<cstdio>](cstdio.md) , [\<filesystem>](filesystem.md) <sup>17</sup>,,,,,,,,,, [\<fstream>](fstream.md) [\<iomanip>](iomanip.md) [\<ios>](ios.md) [\<iosfwd>](iosfwd.md) [\<iostream>](iostream.md) [\<istream>](istream.md) [\<ostream>](ostream.md) [\<sstream>](sstream.md) [\<streambuf>](streambuf.md) [\<strstream>](strstream.md) <sup>c</sup>, \<syncstream> <sup>20</sup> |
| 반복기 | [\<iterator>](iterator.md) |
| 언어 지원 | [\<cfloat>](cfloat.md), [\<climits>](climits.md) , [\<codecvt>](codecvt.md) <sup>11 a</sup>, \<compare> <sup>20</sup>, \<contract> <sup>20</sup>, \<coroutine> <sup>20</sup>,,,,, [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) [\<cstdarg>](cstdarg.md) [\<cstddef>](cstddef.md) [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdlib>](cstdlib.md) , [\<exception>](exception.md) , [\<initializer_list>](initializer-list.md) <sup>11</sup>, [\<limits>](limits.md) [\<new>](new.md) [\<typeinfo>](typeinfo.md) \<version> <sup>20</sup> ,,, 20 |
| 지역화 | [\<clocale>](clocale.md), [\<codecvt>](codecvt.md) <sup>11 a</sup>, [\<cvt/wbuffer>](cvt-wbuffer.md) , [\<cvt/wstring>](cvt-wstring.md) ,[\<locale>](locale.md) |
| 수학 및 숫자 | \<bit><sup>20</sup>, [\<cfenv>](cfenv.md) <sup>11</sup>,,,,, [\<cmath>](cmath.md) [\<complex>](complex.md) [\<cstdlib>](cstdlib.md) [\<limits>](limits.md) [\<numeric>](numeric.md) , [\<random>](random.md) <sup>11</sup>, [\<ratio>](ratio.md) <sup>11</sup>,[\<valarray>](valarray.md) |
| [메모리 관리](../cpp/smart-pointers-modern-cpp.md) | [\<allocators>](allocators-header.md), [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, [\<new>](new.md) , [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> |
| 다중 스레딩 | [\<atomic>](atomic.md)<sup>11</sup>, [\<condition_variable>](condition-variable.md) <sup>11</sup>, [\<future>](future.md) <sup>11</sup>, [\<mutex>](mutex.md) <sup>11</sup>, [\<shared_mutex>](shared-mutex.md) <sup>14</sup>, [\<thread>](thread.md) <sup>11</sup> |
| 범위 | \<ranges><sup>720</sup> |
| 정규식 | [\<regex>](regex.md)<sup>pt</sup> |
| 문자열 및 문자 데이터 | [\<charconv>](charconv.md)<sup>17</sup>, [\<cctype>](cctype.md) , [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) , [\<cwctype>](cwctype.md) , [\<regex>](regex.md) <sup>11</sup>, [\<string>](string.md) , [\<string_view>](string-view.md) <sup>17</sup> |
| 시간 | [\<chrono>](chrono.md)<sup>11</sup>, [\<ctime>](ctime.md) |

<sup>11</sup> c + + 11 표준에서 추가 되었습니다.
<sup>14</sup> 는 c + + 14 표준에 추가 되었습니다.
<sup>17</sup> c + + 17 표준에서 추가 되었습니다.
<sup>20</sup> 은 초안 c + + 20 standard에서 추가 되었습니다.
<sup>는</sup> c + + 17 standard에서 사용 되지 않습니다.
<sup>b</sup> 는 초안 c + + 20 표준에서 제거 되었습니다.
<sup>c</sup> c + + 98 표준에서 사용 되지 않습니다.

::: moniker-end

::: moniker range="vs-2015"

|범주|headers|
|-|-|
|[알고리즘](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|C 라이브러리 래퍼|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[컨테이너](../cpp/containers-modern-cpp.md)||
|시퀀스 컨테이너|[\<array>](array.md), [\<deque>](deque.md), [\<forward_list>](forward-list.md), [\<list>](list.md), [\<vector>](vector.md)|
|정렬 된 연관 컨테이너| [\<map>](map.md), [\<set>](set.md)|
|순서가 지정 되지 않은 연관 컨테이너|[\<unordered_map>](unordered-map.md), [\<unordered_set>](unordered-set.md)|
|어댑터 컨테이너|[\<queue>](queue.md), [\<stack>](stack.md)|
|[오류 및 예외 처리](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception>](exception.md), [\<stdexcept>](stdexcept.md), [\<system_error>](system-error.md)|
|[I/o 및 서식 지정](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|반복기|[\<iterator>](iterator.md)|
|지역화|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|수학 및 숫자|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[메모리 관리](../cpp/smart-pointers-modern-cpp.md)|[\<allocators>](allocators-header.md), [\<memory>](memory.md), [\<new>](new.md), [\<scoped_allocator>](scoped-allocator.md)|
|다중 스레딩|[\<atomic>](atomic.md), [\<condition_variable>](condition-variable.md), [\<future>](future.md), [\<mutex>](mutex.md), [\<shared_mutex>](shared-mutex.md), [\<thread>](thread.md)|
|기타 유틸리티|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|문자열 및 문자 데이터|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>참고 항목

[C + + 라이브러리 헤더 사용](using-cpp-library-headers.md)\
[C++ 표준 라이브러리](cpp-standard-library-reference.md)
