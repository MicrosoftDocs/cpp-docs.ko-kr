---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 15bfa86a3c697442b66a5f77aa6ea7a9aba5643c
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521033"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

iostreams 클래스 작동의 기본 요소인 템플릿 클래스 [basic_streambuf](../standard-library/basic-streambuf-class.md)를 정의하는 iostreams 표준 헤더 \<streambuf>를 포함합니다. 이 헤더는 일반적으로 다른 iostreams 헤더에 의해 포함되며, 직접 포함해야 하는 경우는 거의 없습니다.

## <a name="syntax"></a>구문

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>형식 정의

|형식 이름|설명|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|특수화 `basic_streambuf` 를 사용 하는 **char** 템플릿 매개 변수로 합니다.|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|특수화 `basic_streambuf` 를 사용 하는 **wchar_t** 템플릿 매개 변수로 합니다.|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_streambuf 클래스](basic-streambuf-class.md)|템플릿 클래스는 스트림의 특정 표현과 요소 간의 전송을 제어하는 스트림 버퍼 파생을 위한 추상 기본 클래스에 대해 설명합니다.|

## <a name="see-also"></a>참고자료

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream 프로그래밍](../standard-library/iostream-programming.md)<br/>
[iostreams 규칙](../standard-library/iostreams-conventions.md)<br/>
