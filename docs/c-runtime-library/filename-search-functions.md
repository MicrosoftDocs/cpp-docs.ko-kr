---
description: '자세히 알아보기: 파일 이름 검색 함수'
title: 파일 이름 검색 함수
ms.date: 11/04/2016
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
ms.openlocfilehash: 1ab547de95906909a75bdd73f653c5cdae519879
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332948"
---
# <a name="filename-search-functions"></a>파일 이름 검색 함수

이러한 함수는 지정된 파일 이름을 검색하고 검색을 닫습니다.

- [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>설명

`_findfirst` 함수는 `filespec` 인수에 지정된 파일과 일치하는 파일 이름의 첫 번째 인스턴스에 대한 정보를 제공합니다. `filespec` 에는 호스트 운영 체제에서 지원하는 와일드카드 문자를 임의로 조합하여 사용할 수 있습니다.

이 함수는 파일 정보를 IO.h에 정의된 `_finddata_t` 구조로 반환합니다. 패밀리의 다양한 함수가 `_finddata_t` 구조의 여러 변형을 사용합니다. 기본 `_finddata_t` 구조에는 다음과 같은 요소가 포함됩니다.

`unsigned attrib`<br/>
파일 특성입니다.

`time_t time_create`<br/>
파일을 만든 시간입니다(FAT 파일 시스템의 경우 –1L). 이 시간은 UTC 형식으로 저장됩니다. 현지 시간으로 변환하려면 [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)를 사용합니다.

`time_t time_access`<br/>
마지막 파일 액세스 시간입니다(FAT 파일 시스템의 경우 –1L). 이 시간은 UTC 형식으로 저장됩니다. 현지 시간으로 변환하려면 `localtime_s`를 사용합니다.

`time_t time_write`<br/>
파일에 마지막으로 쓴 시간입니다. 이 시간은 UTC 형식으로 저장됩니다. 현지 시간으로 변환하려면 `localtime_s`를 사용합니다.

`_fsize_t size`<br/>
파일의 길이(바이트)입니다.

`char name`[ `_MAX_PATH`] 일치하는 파일 또는 디렉터리의 null로 끝나는 이름이며, 경로는 제외합니다.

파일을 만든 시간과 마지막 액세스 시간을 지원하지 않는 FAT 시스템과 같은 파일 시스템에서는 `time_create` 및 `time_access` 필드가 항상 –1L입니다.

`_MAX_PATH`는 Stdlib.h에 260바이트로 정의되어 있습니다.

대상 특성(예: `_A_RDONLY`)을 지정하여 찾기 작업을 제한할 수 있습니다. 이러한 특성은 `attrib` 구조의 `_finddata_t` 필드로 반환되며 다음과 같은 값일 수 있습니다(IO.h에 정의). 사용자는 이러한 값만 `attrib` 필드에 사용할 수 있다고 간주해서는 안 됩니다.

`_A_ARCH`<br/>
보관 파일입니다. **BACKUP** 명령으로 파일을 변경하고 지울 때마다 설정합니다. 값: 0x20

`_A_HIDDEN`<br/>
숨김 파일입니다. **/AH** 옵션을 사용하지 않는 한 일반적으로 DIR 명령으로 표시되지 않습니다. 일반 파일 및 이 특성이 있는 파일에 대한 정보를 반환합니다. 값: 0x02

`_A_NORMAL`<br/>
일반 파일입니다. 설정된 다른 특성이 없고 제한 없이 읽거나 쓸 수 있는 파일입니다. 값: 0x00

`_A_RDONLY`<br/>
읽기 전용입니다. 쓰기 위해 파일을 열 수 없고 동일한 이름의 파일을 만들 수 없습니다. 값: 0x01

`_A_SUBDIR`<br/>
하위 디렉터리입니다. 값: 0x10

`_A_SYSTEM`<br/>
시스템 파일입니다. **/A** 또는 **/A:S** 옵션을 사용하지 않는 한 일반적으로 **DIR** 명령으로 표시되지 않습니다. 값: 0x04

`_findnext` 는 `filespec` 에 대한 이전 호출에 지정된 `_findfirst`인수와 일치하는 다음 이름(있는 경우)을 찾습니다. `fileinfo` 인수는 `_findfirst`에 대한 이전 호출에서 초기화되는 구조를 가리켜야 합니다. 일치하는 항목이 있으면 앞에서 설명한 대로 `fileinfo` 구조 내용이 변경됩니다. 일치하는 항목이 없으면 변경되지 않습니다. `_findclose` 는 지정된 검색 핸들을 닫고 `_findfirst` 및 `_findnext`모두에 연결된 모든 리소스를 해제합니다. `_findfirst` 또는 `_findnext` 에서 반환된 핸들을 먼저 `_findclose`에 전달해야만 전달되는 경로를 형성하는 디렉터리에서 삭제와 같은 수정 작업을 수행할 수 있습니다.

`_find` 함수를 중첩할 수 있습니다. 예를 들어 `_findfirst` 또는 `_findnext` 에 대한 호출에서 하위 디렉터리인 파일을 찾는 경우 `_findfirst` 또는 `_findnext`에 대한 다른 호출로 새 검색을 시작할 수 있습니다.

`_wfindfirst` 및 `_wfindnext` 는 `_findfirst` 및 `_findnext`의 와이드 문자 버전입니다. 와이드 문자 버전의 구조 인수는 IO.h 및 Wchar.h에 정의된 `_wfinddata_t` 데이터 형식입니다. 이 데이터 형식의 필드는 데이터 형식의 필드와 동일 합니다 `_finddata_t` . 단, `_wfinddata_t` 이름 필드의 형식은 **`wchar_t`** 형식이 아니라 형식입니다 **`char`** . 그 외에 `_wfindfirst` 및 `_wfindnext` 는 `_findfirst` 및 `_findnext`와 동일하게 작동합니다.

`_findfirst` 및 `_findnext` 는 64비트 시간 형식을 사용합니다. 이전 32비트 시간 형식을 사용해야 하는 경우 `_USE_32BIT_TIME_T`를 정의할 수 있습니다. 이러한 함수 중 이름에 `32` 접미사가 있는 버전은 32비트 시간 형식을 사용하고 `64` 접미사가 있는 버전은 64비트 시간 형식을 사용합니다.

`_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`및 `_wfindnext32i64` 함수도 64비트 파일 길이를 사용 및 반환한다는 점만 제외하고 이러한 함수의 32비트 형식 버전과 동일하게 작동합니다. `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32` 및 `_wfindnext64i32` 함수는 64비트 시간 형식을 사용하지만 32비트 파일 길이를 사용합니다. 이러한 함수는 시간과 파일 크기에 대한 필드의 형식이 다른 `_finddata_t` 형식의 적절한 변경을 사용합니다.

`_finddata_t` 는 실제로 `_finddata64i32_t` (또는 `_finddata32_t` 가 정의된 경우 `_USE_32BIT_TIME_T` )로 계산되는 매크로입니다. 다음 표에서는 `_finddata_t`의 변형을 요약하여 보여 줍니다.

|구조체|시간 형식|파일 크기 형식|
|---------------|---------------|--------------------|
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|**`__int64`**|
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|**`__int64`**|
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|

`_fsize_t` 는 **`typedef`** **`unsigned long`** (32 비트)의입니다.

## <a name="example"></a>예제

```c
// crt_find.c
// This program uses the 32-bit _find functions to print
// a list of all files (and their attributes) with a .C extension
// in the current directory.

#include <stdio.h>
#include <stdlib.h>
#include <io.h>
#include <time.h>

int main( void )
{
   struct _finddata_t c_file;
   intptr_t hFile;

   // Find first .c file in current directory
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )
      printf( "No *.c files in current directory!\n" );
   else
   {
      printf( "Listing of .c files\n\n" );
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );
      do {
         char buffer[30];
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );
         ctime_s( buffer, _countof(buffer), &c_file.time_write );
         printf( " %-12s %.24s  %9ld\n",
            c_file.name, buffer, c_file.size );
      } while( _findnext( hFile, &c_file ) == 0 );
      _findclose( hFile );
   }
}
```

```Output
Listing of .c files

RDO HID SYS ARC  FILE         DATE                           SIZE
--- --- --- ---  ----         ----                           ----
N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715
N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312
```

## <a name="see-also"></a>참고 항목

[시스템 호출](../c-runtime-library/system-calls.md)
