---
description: '자세히 알아보기: &lt; streambuf&gt;'
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: 417b31b919c95d8aef741b2988c576ff6454ce4a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97183765"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Iostreams \<streambuf> 클래스의 작동에 대 한 기본 인 클래스 템플릿 [basic_streambuf](../standard-library/basic-streambuf-class.md)를 정의 하려면 iostreams 표준 헤더를 포함 합니다. 이 헤더는 일반적으로 다른 iostreams 헤더에 의해 포함되며, 직접 포함해야 하는 경우는 거의 없습니다.

## <a name="syntax"></a>Syntax

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|형식 이름|설명|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|를 `basic_streambuf` 템플릿 매개 변수로 사용 하는의 특수화입니다 **`char`** .|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|를 `basic_streambuf` 템플릿 매개 변수로 사용 하는의 특수화입니다 **`wchar_t`** .|

### <a name="classes"></a>클래스

|클래스|설명|
|-|-|
|[basic_streambuf 클래스](basic-streambuf-class.md)|클래스 템플릿에서는 스트림의 특정 표현과의 요소 전송을 제어 하는 스트림 버퍼 파생을 위한 추상 기본 클래스에 대해 설명 합니다.|

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream 프로그래밍](../standard-library/iostream-programming.md)\
[iostreams 규칙](../standard-library/iostreams-conventions.md)
