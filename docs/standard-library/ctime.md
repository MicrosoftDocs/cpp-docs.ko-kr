---
description: '자세히 알아보기: &lt; ctime&gt;'
title: '&lt;ctime&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ctime>
helpviewer_keywords:
- ctime header
ms.assetid: c1f7d4a4-4bfe-4e35-92cb-f63dbd3c39a8
ms.openlocfilehash: 3ebf4849f990f7e0ae835fca88a6b38a8ca1838d
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126704"
---
# <a name="ltctimegt"></a>&lt;ctime&gt;

표준 C 라이브러리 헤더를 포함 \<time.h> 하 고 네임 스페이스에 연결 된 이름을 추가 합니다 `std` .

## <a name="syntax"></a>구문

```cpp
#include <ctime>
```

## <a name="remarks"></a>설명

이 헤더를 포함하는 경우 표준 C 라이브러리 헤더의 외부 링크를 사용하여 선언한 이름이 `std` 네임스페이스에도 선언됩니다.

## <a name="constants"></a>상수

```cpp
#define NULL
#define CLOCKS_PER_SEC
#define TIME_UTC

namespace std {
    using size_t = see below;
    using clock_t = see below ;
    using time_t = see below ;
}
```

## <a name="structures"></a>구조체

```cpp
struct timespec;
struct tm;
```

## <a name="functions"></a>함수

```cpp
clock_t clock();
double difftime(time_t time1, time_t time0);
time_t mktime(struct tm* timeptr);
time_t time(time_t* timer);
int timespec_get(timespec* ts, int base);
char* asctime(const struct tm* timeptr);
char* ctime(const time_t* timer);
struct tm* gmtime(const time_t* timer);
struct tm* localtime(const time_t* timer);
size_t strftime(char* s, size_t maxsize, const char* format, const struct tm* timeptr);
```

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
