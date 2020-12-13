---
description: Vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l에 대해 자세히 알아보세요.
title: vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l
ms.date: 11/04/2016
api_name:
- _vsnwprintf_s
- _vsnwprintf_s_l
- _vsnprintf_s
- vsnprintf_s
- _vsnprintf_s_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ntdll.dll
- ucrtbase.dll
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _vsnprintf_s
- _vsntprintf_s
- _vsnwprintf_s
helpviewer_keywords:
- vsnwprintf_s function
- _vsntprintf_s function
- _vsntprintf_s_l function
- vsntprintf_s function
- vsnwprintf_s_l function
- vsnprintf_s_l function
- vsntprintf_s_l function
- _vsnwprintf_s_l function
- _vsnprintf_s function
- vsnprintf_s function
- _vsnprintf_s_l function
- _vsnwprintf_s function
- formatted text [C++]
ms.assetid: 147ccfce-58c7-4681-a726-ef54ac1c604e
ms.openlocfilehash: 27c91d6064b4a92da8a6f09e7d7e5b6bfb8bf95f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342155"
---
# <a name="vsnprintf_s-_vsnprintf_s-_vsnprintf_s_l-_vsnwprintf_s-_vsnwprintf_s_l"></a>vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l

인수 목록에 대한 포인터를 사용하여 형식이 지정된 출력을 씁니다. 이러한 함수는 [CRT의 보안 기능](../../c-runtime-library/security-features-in-the-crt.md)에 설명된 대로 강화된 보안 기능이 있는 [vsnprintf, _vsnprintf, _vsnprintf_l, _vsnwprintf, _vsnwprintf_l](vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)의 버전입니다.

## <a name="syntax"></a>구문

```C
int vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   va_list argptr
);
int _vsnprintf_s_l(
   char *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const char *format,
   locale_t locale,
   va_list argptr
);
int _vsnwprintf_s(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   va_list argptr
);
int _vsnwprintf_s_l(
   wchar_t *buffer,
   size_t sizeOfBuffer,
   size_t count,
   const wchar_t *format,
   locale_t locale,
   va_list argptr
);
template <size_t size>
int _vsnprintf_s(
   char (&buffer)[size],
   size_t count,
   const char *format,
   va_list argptr
); // C++ only
template <size_t size>
int _vsnwprintf_s(
   wchar_t (&buffer)[size],
   size_t count,
   const wchar_t *format,
   va_list argptr
); // C++ only
```

### <a name="parameters"></a>매개 변수

*버퍼*<br/>
출력을 위한 스토리지 위치입니다.

*sizeOfBuffer*<br/>
출력에 대 한 *버퍼* 의 크기 (문자 수)입니다.

*count*<br/>
작성할 최대 문자 수(종결 null은 포함되지 않음) 또는 [_TRUNCATE](../../c-runtime-library/truncate.md)입니다.

*format*<br/>
형식 사양입니다.

*argptr*<br/>
인수 목록에 대한 포인터입니다.

*locale*<br/>
사용할 로캘입니다.

자세한 내용은 [형식 사양](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)을 참조하세요.

## <a name="return-value"></a>반환 값

**vsnprintf_s**, **_vsnprintf_s** 및 **_vsnwprintf_s** 는 종료 null을 포함 하지 않고 작성 된 문자 수를 반환 하거나, 데이터 잘림 또는 출력 오류가 발생 하는 경우 음수 값을 반환 합니다.

* *Count* 가 *sizeOfBuffer* 보다 작고 데이터의 문자 수가 *count* 보다 작거나 같은 경우 또는 *개수가* [_TRUNCATE](../../c-runtime-library/truncate.md) 이 고 데이터의 문자 수가 *sizeOfBuffer* 보다 작은 경우에는 모든 데이터가 기록 되 고 문자 수가 반환 됩니다.

* *Count* 가 *sizeOfBuffer* 보다 작지만 데이터가 *개수* 문자를 초과 하는 경우 첫 번째 *카운트* 문자가 쓰여집니다. 나머지 데이터의 잘림이 발생 하며, 잘못 된 매개 변수 처리기를 호출 하지 않고-1이 반환 됩니다.

* *Count* 가 [_TRUNCATE](../../c-runtime-library/truncate.md) 이 고 데이터의 문자 수가 *sizeOfBuffer* 이거나이에 해당 하는 경우에는 *버퍼* (종료 null을 사용 하 여)에 맞는 문자열의 양이 기록 됩니다. 나머지 데이터의 잘림이 발생 하며, 잘못 된 매개 변수 처리기를 호출 하지 않고-1이 반환 됩니다.

* *Count* 가 *sizeOfBuffer* 보다 크거나 같고 데이터의 문자 수가 *sizeOfBuffer* 보다 작은 경우 모든 데이터 (null 종결)가 기록 되 고 문자 수가 반환 됩니다.

* *Count* 와 데이터의 문자 수가 모두 *sizeOfBuffer* 같거나이를 초과 하면 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명 된 대로 잘못 된 매개 변수 처리기가 호출 됩니다. 잘못 된 매개 변수 처리기 이후에 실행이 계속 되 면 이러한 함수는 *버퍼* 를 빈 문자열로 설정 하 고 **errno** 를 **ERANGE** 로 설정 하 고-1을 반환 합니다.

* *버퍼* 또는 *형식이* **NULL** 포인터 이거나 *count* 가 0 보다 작거나 같으면 잘못 된 매개 변수 처리기가 호출 됩니다. 계속 해 서 실행 하도록 허용한 경우 이러한 함수는 **errno** 를 **EINVAL** 로 설정 하 고-1을 반환 합니다.

### <a name="error-conditions"></a>오류 조건

|**Condition**|반환 값|**errno**|
|-----------------|------------|-------------|
|*버퍼가* **NULL** 입니다.|-1|**EINVAL**|
|*형식이* **NULL** 입니다.|-1|**EINVAL**|
|*개수* <= 0|-1|**EINVAL**|
|*sizeOfBuffer* 너무 작음 (and *count* ! = **_TRUNCATE**)|-1 (및 *버퍼* 를 빈 문자열로 설정)|**ERANGE**|

## <a name="remarks"></a>설명

**vsnprintf_s** 은 **_vsnprintf_s** 와 동일 합니다. **VSNPRINTF_S** ANSI 표준 준수를 위해 포함 됩니다. **_vnsprintf** 은 이전 버전과의 호환성을 위해 유지 됩니다.

이러한 각 함수는 인수 목록에 대 한 포인터를 사용 하 여 *버퍼* 에서 가리키는 메모리에 지정 된 데이터의 문자 *수를 계산* 하 고 종료 null을 추가 합니다.

*Count* 가 [_TRUNCATE](../../c-runtime-library/truncate.md)이면 이러한 함수는 종료 null을 위한 공간을 남겨 둘 때 *버퍼* 에 맞는 만큼의 문자열을 씁니다. 종료 null을 포함 하는 전체 문자열이 *버퍼* 에 있으면 이러한 함수는 종료 null을 포함 하지 않고 작성 된 문자 수를 반환 합니다. 그렇지 않으면 이러한 함수는 잘림이 발생 했음을 나타내는-1을 반환 합니다.

**_L** 접미사가 있는 이러한 함수 버전은 현재 스레드 로캘 대신 전달 된 로캘 매개 변수를 사용 한다는 점을 제외 하 고는 동일 합니다.

> [!IMPORTANT]
> *format* 이 사용자 정의 문자열이 아닌지 확인하세요. 자세한 내용은 [버퍼 오버런 방지](/windows/win32/SecBP/avoiding-buffer-overruns)를 참조하세요.

> [!NOTE]
> 종료 null에 대 한 공간이 있는지 확인 하려면 *개수가* 버퍼 길이 보다 엄격 하 게 작거나 **_TRUNCATE** 를 사용 해야 합니다.

C++에서는 템플릿 오버로드로 인해 이러한 함수를 사용하는 것이 보다 간단해 집니다. 오버로드는 버퍼 길이를 자동으로 유추할 수 있으며(크기 인수를 지정할 필요가 없어짐), 기존의 비보안 함수를 보다 최신의 보안 대응 함수로 자동으로 바꿀 수 있습니다. 자세한 내용은 [안전한 템플릿 오버로드](../../c-runtime-library/secure-template-overloads.md)를 참조하세요.

### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑

|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_vsntprintf_s**|**_vsnprintf_s**|**_vsnprintf_s**|**_vsnwprintf_s**|
|**_vsntprintf_s_l**|**_vsnprintf_s_l**|**_vsnprintf_s_l**|**_vsnwprintf_s_l**|

## <a name="requirements"></a>요구 사항

|루틴에서 반환된 값|필수 헤더|선택적 헤더|
|-------------|---------------------|----------------------|
|**vsnprintf_s**|\<stdio.h> 및 \<stdarg.h>|\<varargs.h>*|
|**_vsnprintf_s**, **_vsnprintf_s_l**|\<stdio.h> 및 \<stdarg.h>|\<varargs.h>*|
|**_vsnwprintf_s**, **_vsnwprintf_s_l**|\<stdio.h> 또는 \<wchar.h> , 및 \<stdarg.h>|\<varargs.h>*|

\* UNIX V 호환성을 위해 필요합니다.

호환성에 대한 자세한 내용은 [Compatibility](../../c-runtime-library/compatibility.md)을 참조하세요.

## <a name="example"></a>예제

```cpp
// crt_vsnprintf_s.cpp
#include <stdio.h>
#include <wtypes.h>

void FormatOutput(LPCSTR formatstring, ...)
{
   int nSize = 0;
   char buff[10];
   memset(buff, 0, sizeof(buff));
   va_list args;
   va_start(args, formatstring);
   nSize = vsnprintf_s( buff, _countof(buff), _TRUNCATE, formatstring, args);
   printf("nSize: %d, buff: %s\n", nSize, buff);
   va_end(args);
}

int main() {
   FormatOutput("%s %s", "Hi", "there");
   FormatOutput("%s %s", "Hi", "there!");
   FormatOutput("%s %s", "Hi", "there!!");
}
```

```Output
nSize: 8, buff: Hi there
nSize: 9, buff: Hi there!
nSize: -1, buff: Hi there!
```

## <a name="see-also"></a>참고 항목

[스트림 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[vprintf 함수](../../c-runtime-library/vprintf-functions.md)<br/>
[fprintf, _fprintf_l, fwprintf, _fwprintf_l](fprintf-fprintf-l-fwprintf-fwprintf-l.md)<br/>
[printf, _printf_l, wprintf, _wprintf_l](printf-printf-l-wprintf-wprintf-l.md)<br/>
[sprintf, _sprintf_l, swprintf, _swprintf_l, \_ _swprintf_l](sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)<br/>
[va_arg, va_copy, va_end, va_start](va-arg-va-copy-va-end-va-start.md)<br/>
