---
description: '자세히 알아보기: &lt; b&gt;'
title: '&lt;cstdlib&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstdlib>
helpviewer_keywords:
- cstdlib header
ms.assetid: 0a6aaebf-84e9-4b60-ae90-17e11981cf54
ms.openlocfilehash: 8ab3ecc7a2db1d1cf90c69230c34a301587fc1e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324724"
---
# <a name="ltcstdlibgt"></a>&lt;cstdlib&gt;

C 표준 라이브러리 헤더를 포함 \<stdlib.h> 하 고 네임 스페이스에 연결 된 이름을 추가 합니다 `std` . 이 헤더를 포함 하면 C 표준 라이브러리 헤더의 외부 링크를 사용 하 여 선언한 이름이 네임 스페이스에 선언 됩니다 `std` .

> [!NOTE]
> \<stdlib.h> 에는 형식이 포함 되지 않습니다 **`wchar_t`** .

## <a name="requirements"></a>요구 사항

**헤더**: \<cstdlib>

**네임스페이스:** std

## <a name="namespace-and-macros"></a>네임 스페이스 및 매크로

```cpp
namespace std {
    using size_t = see definition;
    using div_t = see definition;
    using ldiv_t = see definition;
    using lldiv_t = see definition;
}

#define NULL
#define EXIT_FAILURE
#define EXIT_SUCCESS
#define RAND_MAX
#define MB_CUR_MAX
```

## <a name="exposition-only-functions"></a>표시 함수

```cpp
extern "C" using c-atexit-handler = void();
extern "C++" using atexit-handler = void();
extern "C" using c-compare-pred = int(const void*, const void*);
extern "C++" using compare-pred = int(const void*, const void*);
```

## <a name="start-and-termination-functions"></a>시작 및 종료 함수

|함수|설명|
|-|-|
|[_Exit](#_exit)|소멸자 또는 등록 된 함수를 사용 하지 않고 프로그램을 종료 합니다.|
|[중단이](#abort)|소멸자를 사용 하지 않고 프로그램을 종료 합니다.|
|[atexit](#atexit)|프로그램 종료를 위한 함수를 등록 합니다.|
|[exit](#exit)|스레드 및 정적 저장소를 사용 하 여 개체를 삭제 한 다음 컨트롤을 반환 합니다.|
|[at_quick_exit](#at_quick_exit)|프로그램 종료에 대 한 인수 없이 함수를 등록 합니다.|
|[quick_exit](#quick_exit)|프로그램 종료를 위해 유지 된 개체를 사용 하 여 함수를 등록 합니다.|
|[getenv](#getenv)|C 표준 라이브러리 참조를 참조 하세요.|
|[시스템](#system)|C 표준 라이브러리 참조를 참조 하세요.|

### <a name="_exit"></a><a name="_exit"></a> _Exit

```cpp
[[noreturn]] void _Exit(int status) noexcept;
```

#### <a name="remarks"></a>설명

자동, 스레드 또는 정적 저장 기간 개체에 대 한 소멸자를 실행 하지 않고에 전달 된 함수를 호출 하지 않고 프로그램이 종료 됩니다 `atexit()` . 함수는 `_Exit` 신호를 안전 하 게 보호 합니다.

### <a name="abort"></a><a name="abort"></a> 중단이

```cpp
[[noreturn]] void abort() noexcept;
```

#### <a name="remarks"></a>설명

자동, 스레드 또는 정적 저장 기간 개체에 대 한 소멸자를 실행 하지 않고에 전달 된 함수를 호출 하지 않고 프로그램이 종료 됩니다 `atexit()` . 함수는 `abort` 신호를 안전 하 게 보호 합니다.

### <a name="at_quick_exit"></a><a name="at_quick_exit"></a> at_quick_exit

```cpp
int at_quick_exit(c-atexit-handler * func) noexcept;
int at_quick_exit(atexit-handler * func) noexcept;
```

#### <a name="return-value"></a>반환 값

등록이 성공 하면 0이 고, 실패 하면 0이 아닙니다.

#### <a name="remarks"></a>설명

`at_quick_exit()`함수는를 호출할 때 인수 없이 호출 되는 함수 *func* 를 등록 `quick_exit` 합니다. 에 대 한 호출이 `at_quick_exit()` `quick_exit` 성공 하지 못할 수 있습니다. `at_quick_exit()`함수는 데이터 레이스를 도입 하지 않습니다. 둘 `at_quick_exit` 이상의 스레드에서가 호출 된 경우 등록 순서는 결정 되지 않을 수 있습니다. 등록 `at_quick_exit` 은 `atexit` 등록과 다르므로 응용 프로그램은 동일한 인수를 사용 하 여 두 등록 함수를 호출 해야 할 수도 있습니다. MSVC은 32 이상의 함수 등록을 지원 합니다.

### <a name="atexit"></a><a name="atexit"></a> atexit

```cpp
int atexit(c-atexit-handler * func) noexcept;
int atexit(atexit-handler * func) noexcept;
```

#### <a name="remarks"></a>설명

함수는 함수에 `atexit()` 의해 가리키는 함수를  정상적으로 프로그램 종료 시 인수 없이 호출 되도록 등록 합니다. 에 대 한 호출이 `atexit()` `exit()` 성공 하지 못할 수 있습니다. `atexit()`함수는 데이터 레이스를 도입 하지 않습니다.

#### <a name="return-value"></a>반환 값

등록이 성공 하면 0을 반환 하 고, 실패 하면 0을 반환 합니다.

### <a name="exit"></a><a name="exit"></a> 끝낸

```cpp
[[noreturn]] void exit(int status);
```

#### <a name="remarks"></a>설명

첫째, 스레드 저장 기간이 있는 개체와 현재 스레드와 연결 된 개체가 제거 됩니다.

그런 다음 정적 저장 기간이 있는 개체가 제거 되 고를 호출 하 여 등록 된 함수가 `atexit` 호출 됩니다. 자동 개체는가 호출 될 때 소멸 되지 않습니다 `exit()` . `exit`함수가 throw 된 예외에 대 한 처리기를 제공 하지 않기 때문에에서 호출 된 등록 된 함수를 벗어나면 `std::terminate()` 가 호출 됩니다. 함수는 등록 될 때마다 한 번씩 호출 됩니다. 자동 저장 기간이 포함 된 개체는 모두 `main` 함수에 자동 개체가 없고에 대 한 호출을 실행 하는 프로그램에서 모두 제거 됩니다 `exit()` . `main`에서 catch 된 예외를 throw 하 여 컨트롤을 이러한 함수로 직접 전송할 수 있습니다 `main` .

그런 다음, 기록 되지 않은 버퍼링 된 데이터를 사용 하 여 열려 있는 모든 C 스트림 (에 선언 된 함수 서명에서 조정 \<cstdio> )이 플러시되고, 모든 열린 c 스트림이 닫히고,를 호출 하 여 만든 모든 파일이 `tmpfile()` 제거 됩니다.

마지막으로 컨트롤이 호스트 환경으로 반환 됩니다. *Status* 가 0 또는 EXIT_SUCCESS 이면 성공적인 종료 상태의 구현 정의 된 양식이 반환 됩니다. MSVC는 값 0을 반환 합니다. *상태가* EXIT_FAILURE 이면 MSVC는 값 3을 반환 합니다. 그렇지 않으면 MSVC는 *상태* 매개 변수 값을 반환 합니다.

### <a name="getenv"></a><a name="getenv"></a> getenv

```cpp
char* getenv(const char* name);
```

### <a name="quick_exit"></a><a name="quick_exit"></a> quick_exit

```cpp
[[noreturn]] void quick_exit(int status) noexcept;
```

#### <a name="remarks"></a>설명

일반적으로에 대 한 호출로 등록 된 함수 `at_quick_exit` 는 해당 등록의 반대 순서로 호출 됩니다. 이 순서는 다른 등록 된 함수가 이미 호출 된 후에 등록 된 함수에는 적용 되지 않습니다. 가 호출 되 면 개체가 제거 되지 않습니다 `quick_exit` . `quick_exit`함수가 throw 된 예외에 대 한 처리기를 제공 하지 않기 때문에에서 호출 된 등록 된 함수를 벗어나면 `std::terminate()` 가 호출 됩니다. 를 통해 등록 된 함수는 `at_quick_exit` 를 호출 하는 스레드에서 호출 됩니다 .이 함수는 `quick_exit` 해당 함수를 등록 한 스레드와 다른 스레드가 될 수 있습니다. 즉, 등록 된 함수는 스레드 저장 기간이 있는 개체의 id를 사용 하지 않아야 합니다. 등록 된 함수를 호출한 후에는를 `quick_exit` 호출 `_Exit(status)` 합니다. 표준 파일 버퍼는 플러시되지 않습니다. `quick_exit`에 등록 된 함수가 인 경우 함수는 신호를 안전 하 게 보호 `at_quick_exit` 합니다.

### <a name="system"></a><a name="system"></a> 컴퓨터

```cpp
int system(const char* string);
```

## <a name="memory-allocation-functions"></a>메모리 할당 함수

```cpp
// void* aligned_alloc(size_t alignment, size_t size); // Unsupported in MSVC
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다. MSVC는 함수를 지원 하지 않습니다 `aligned_alloc` . C11는 `aligned_alloc()` 의 Microsoft 구현과 호환 되지 않는 방식으로 지정 `free()` `free()` 됩니다. 즉, 매우 정렬 된 할당을 처리할 수 있어야 합니다.

## <a name="numeric-string-conversions"></a>숫자 문자열 변환

```cpp
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
double strtod(const char* nptr, char** endptr);
float strtof(const char* nptr, char** endptr);
long double strtold(const char* nptr, char** endptr);
long int strtol(const char* nptr, char** endptr, int base);
long long int strtoll(const char* nptr, char** endptr, int base);
unsigned long int strtoul(const char* nptr, char** endptr, int base);
unsigned long long int strtoull(const char* nptr, char** endptr, int base);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다.

## <a name="multibyte--wide-string-and-character-conversion-functions"></a>멀티 바이트/와이드 문자열 및 문자 변환 함수

```cpp
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* pwc, const char* s, size_t n);
int wctomb(char* s, wchar_t wchar);
size_t mbstowcs(wchar_t* pwcs, const char* s, size_t n);
size_t wcstombs(char* s, const wchar_t* pwcs, size_t n);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다.

## <a name="algorithm-functions"></a>알고리즘 함수

```cpp
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void* bsearch(const void* key, const void* base, size_t nmemb, size_t size, compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, c-compare-pred * compar);
void qsort(void* base, size_t nmemb, size_t size, compare-pred * compar);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다.

## <a name="low-quality-random-number-generation-functions"></a>낮은 품질의 난수 생성 함수

```cpp
int rand();
void srand(unsigned int seed);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다.

## <a name="absolute-values"></a>절대값

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
long int labs(long int j);
long long int llabs(long long int j);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다.

## <a name="integer-division"></a>정수 나누기

```cpp
div_t div(int numer, int denom);
ldiv_t div(long int numer, long int denom);
lldiv_t div(long long int numer, long long int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
```

### <a name="remarks"></a>설명

이러한 함수는 C 표준 라이브러리에 지정 된 의미 체계를 가집니다.

## <a name="see-also"></a>참고 항목

[헤더 파일 참조](../standard-library/cpp-standard-library-header-files.md)\
[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)\
[C + + 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)
