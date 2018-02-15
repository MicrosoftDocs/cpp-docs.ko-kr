---
title: _open, _wopen | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _open
- _wopen
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wopen
- _topen
- _open
dev_langs:
- C++
helpviewer_keywords:
- opening files, for file I/O
- topen function
- _open function
- _topen function
- _wopen function
- files [C++], opening
- wopen function
- open function
ms.assetid: 13f6a0c3-d1aa-450d-a7aa-74abc91b163e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e8abb4d652c993f3cf45f1840c820261ac989c9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2018
---
# <a name="open-wopen"></a>_open, _wopen
파일을 엽니다. 더욱 안전한 버전을 사용할 수 있으므로 이러한 함수는 사용되지 않습니다. [_sopen_s, _wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)를 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```  
int _open(  
   const char *filename,  
   int oflag [,  
   int pmode]   
);  
int _wopen(  
   const wchar_t *filename,  
   int oflag [,  
   int pmode]   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `filename`  
 파일 이름.  
  
 `oflag`  
 허용되는 연산의 종류  
  
 `pmode`  
 권한 모드  
  
## <a name="return-value"></a>반환 값  
 이러한 각 함수는 열린 파일에 대한 파일 설명자를 반환합니다. 반환 값이 -1이면 오류를 나타냅니다. 이 경우 `errno`는 다음 값 중 하나로 설정되어 있습니다.  
  
 `EACCES`  
 쓰기 위해 읽기 전용 파일을 열려고 했습니다. 파일의 공유 모드가 지정한 작업을 허용하지 않거나 지정한 경로가 디렉터리입니다.  
  
 `EEXIST`  
 `_O_CREAT` 및 `_O_EXCL` 플래그를 지정했으나 `filename`이 이미 있습니다.  
  
 `EINVAL`  
 
          `oflag` 또는 `pmode` 인수가 잘못되었습니다.  
  
 `EMFILE`  
 사용할 수 있는 추가 파일 설명자가 없습니다. 열려 있는 파일이 너무 많습니다.  
  
 `ENOENT`  
 파일 또는 경로를 찾을 수 없습니다.  
  
 이러한 반환 코드 및 기타 반환 코드에 대한 자세한 내용은 [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)을 참조하세요.  
  
## <a name="remarks"></a>설명  
 `_open` 함수는 `filename`이 지정한 파일을 열고 `oflag`가 지정한 대로 읽기 또는 쓰기를 위해 해당 파일을 준비합니다. `_wopen`은 `_open`의 와이드 문자 버전이며, `filename`에 대한 `_wopen` 인수는 와이드 문자열입니다. 그렇지 않으면 `_wopen`과 `_open`이 동일하게 작동합니다.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 라우팅 매핑  
  
|Tchar.h 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_topen`|`_open`|`_open`|`_wopen`|  
  
 `oflag`는 \<fcntl.h>에 정의된 다음 매니페스트 상수 또는 상수 조합 중 하나 이상으로 구성된 정수 식입니다.  
  
 `_O_APPEND`  
 모든 쓰기 작업 전에 파일 끝으로 파일 포인터를 이동합니다.  
  
 `_O_BINARY`  
 파일을 이진(변환되지 않음) 모드에서 엽니다. 이진 모드에 대한 설명은 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)을 참조하세요.  
  
 `_O_CREAT`  
 파일을 만든 다음 쓰기 위해 엽니다. `filename`에서 지정한 파일이 있으면 의미가 없습니다. 
          `pmode`를 지정하는 경우 `_O_CREAT` 인수가 필요합니다.  
  
 `_O_CREAT` &#124; `_O_SHORT_LIVED`  
 파일을 임시로 만든 다음 가능한 경우 디스크로 플러시하지 않습니다. 
          `pmode`를 지정하는 경우 `_O_CREAT` 인수가 필요합니다.  
  
 `_O_CREAT` &#124; `_O_TEMPORARY`  
 파일을 임시로 만듭니다. 마지막 파일 설명자가 닫히면 파일이 삭제됩니다. 
          `pmode`를 지정하는 경우 `_O_CREAT` 인수가 필요합니다.  
  
 `_O_CREAT` &#124; `_O_EXCL`  
 `filename`에서 지정한 파일이 있으면 오류 값을 반환합니다. 
          `_O_CREAT`와 함께 사용하는 경우에만 적용됩니다.  
  
 `_O_NOINHERIT`  
 공유 파일 설명자의 생성을 방지합니다.  
  
 `_O_RANDOM`  
 캐싱이 디스크에서 임의 액세스를 위해 최적화되며 이에 제한되지 않습니다.  
  
 `_O_RDONLY`  
 읽으려는 경우에만 파일을 엽니다. `_O_RDWR` 또는 `_O_WRONLY`와 함께 지정할 수 없습니다.  
  
 `_O_RDWR`  
 읽고 쓰기 위해 파일을 엽니다. `_O_RDONLY` 또는 `_O_WRONLY`와 함께 지정할 수 없습니다.  
  
 `_O_SEQUENTIAL`  
 캐싱이 디스크에서 순차적 액세스를 위해 최적화되며 이에 제한되지 않습니다.  
  
 `_O_TEXT`  
 파일을 텍스트(변환됨) 모드에서 엽니다. 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 및 [fopen](../../c-runtime-library/reference/fopen-wfopen.md)을 참조하세요.  
  
 `_O_TRUNC`  
 파일을 열고 길이가 0이 되도록 자릅니다. 이 파일에는 쓰기 권한이 있어야 합니다. `_O_RDONLY`와 함께 지정할 수 없습니다. `_O_TRUNC`와 함께 `_O_CREAT`를 사용하면 기존 파일을 열거나 파일을 만듭니다.  
  
> [!NOTE]
>  `_O_TRUNC` 플래그는 지정된 파일의 내용을 제거합니다.  
  
 `_O_WRONLY`  
 쓰려는 경우에만 파일을 엽니다. `_O_RDONLY` 또는 `_O_RDWR`와 함께 지정할 수 없습니다.  
  
 `_O_U16TEXT`  
 유니코드 UTF-16 모드에서 파일을 엽니다.  
  
 `_O_U8TEXT`  
 유니코드 UTF-8 모드에서 파일을 엽니다.  
  
 `_O_WTEXT`  
 유니코드 모드에서 파일을 엽니다.  
  
 파일 액세스 모드를 지정하려면 `_O_RDONLY`, `_O_RDWR` 또는 `_O_WRONLY`를 지정해야 합니다. 액세스 모드의 기본값은 없습니다.  
  
 `_O_WTEXT`를 사용하여 읽기 위해 파일을 연 경우 `_open`은 파일의 시작 부분을 읽고 BOM(바이트 순서 표시)이 있는지 확인합니다. BOM이 있으면 해당 파일은 BOM에 따라 UTF-8 또는 UTF-16LE로 처리됩니다. BOM이 없으면 해당 파일은 ANSI로 처리됩니다. `_O_WTEXT`를 사용하여 쓰기 위해 파일을 열면 UTF-16이 사용됩니다. 이전 설정 또는 바이트 순서 표시와 상관없이 `_O_U8TEXT`를 사용하면 파일이 항상 UTF-8로 열립니다. `_O_U16TEXT`를 사용하면 파일은 항상 UTF-16으로 열립니다.  
  
 `_O_WTEXT`, `_O_U8TEXT` 또는 `_O_U16TEXT`를 사용하여 파일을 유니코드 모드에서 열면 입력 함수는 해당 파일에서 읽은 데이터를 UTF-16 데이터로 변환하고 `wchar_t` 형식으로 저장합니다. 유니코드 모드에서 연 파일에 쓰는 함수는 UTF-16 데이터가 포함된 버퍼가 `wchar_t` 형식으로 저장되는 것으로 예상합니다. 이 파일이 UTF-8로 인코딩되면 UTF-16 데이터는 쓸 때 UTF-8로 변환되고 이 파일의 UTF-8로 인코딩된 내용은 읽을 때 UTF-16으로 변환됩니다. 유니코드 모드에서 홀수 바이트를 읽거나 쓰려고 하면 매개 변수 유효성 검사 오류가 발생합니다. 프로그램에 UTF-8로 저장된 데이터를 읽거나 쓰려는 경우 유니코드 모드 대신 텍스트 또는 이진 파일 모드를 사용합니다. 필수 인코딩은 사용자가 변환해야 합니다.  
  
 `_open`를 `_O_WRONLY|_O_APPEND`(추가 모드) 및 `_O_WTEXT`, `_O_U16TEXT` 또는 `_O_U8TEXT`로 호출하면 먼저 읽고 쓰기 위해 파일을 열고 BOM을 읽은 다음 쓰기를 위해서만 파일을 다시 엽니다. 읽고 쓰기 위해 파일을 여는데 실패하면 쓰기 위해서만 파일을 열고 유니코드 모드 설정에 기본값을 사용합니다.  
  
 매니페스트 상수를 두 개 이상 사용하여 `oflag` 인수를 구성하면 해당 상수는 비트 OR 연산자를 사용하여 결합됩니다(`|`). 이진 및 텍스트 모드에 대한 자세한 내용은 [텍스트 및 이진 모드 파일 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)를 참조하세요.  
  
 `pmode`를 지정할 때만 `_O_CREAT` 인수가 필요합니다. 이 파일이 있으면 `pmode`가 무시됩니다. 그렇지 않으면 `pmode`는 새 파일이 처음으로 닫힐 때 설정되는 파일 권한 설정을 지정합니다. 권한을 설정하기 전에 `_open`는 현재 파일 권한 마스크를 `pmode`에 적용합니다. 자세한 내용은 [_umask](../../c-runtime-library/reference/umask.md)를 참조하세요. `pmode`는 \<sys\stat.h>에 정의된 다음 매니페스트 상수 중 하나 또는 두 상수가 모두 포함된 정수 식입니다.  
  
 `_S_IREAD`  
 읽기만 허용합니다.  
  
 `_S_IWRITE`  
 쓰기를 허용합니다. 실제로는 읽기 및 쓰기를 모두 허용합니다.  
  
 `_S_IREAD`  `|`  `_S_IWRITE`  
 읽기 및 쓰기를 허용합니다.  
  
 두 상수가 지정된 경우 비트 OR 연산자(`|`)를 사용하여 결합됩니다. Windows에서는 모든 파일을 읽을 수 있으므로 쓰기 전용 권한은 설정할 수 없습니다. 따라서 `_S_IWRITE` 및 `_S_IREAD` `|` `_S_IWRITE`는 동일합니다.  
  
 `pmode`에 대해 `_S_IREAD` 및 `_S_IWRITE`의 몇 가지 조합 이외의 값을 지정한 경우(다른 운영 체제에서 올바른 `pmode`를 지정하는 경우 포함) 또는 허용된 `oflag` 값 이외의 모든 값이 지정된 경우 이 함수는 [매개 변수 유효성 검사](../../c-runtime-library/parameter-validation.md)에 설명된 대로 디버그 모드에서 어설션을 생성하고 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용한 경우 함수는 -1을 반환하고 `errno` 를 `EINVAL`로 설정합니다.  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|선택적 헤더|  
|-------------|---------------------|---------------------|  
|`_open`|\<io.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|  
|`_wopen`|\<io.h> 또는 \<wchar.h>|\<fcntl.h>, \<sys\types.h>, \<sys\stat.h>|  
  
 `_open` 및 `_wopen`는 Microsoft 확장입니다. 호환성에 대한 자세한 내용은 [호환성](../../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="libraries"></a>라이브러리  
 모든 버전의 [C 런타임 라이브러리](../../c-runtime-library/crt-library-features.md)입니다.  
  
## <a name="example"></a>예  
  
```  
// crt_open.c  
// compile with: /W3  
/* This program uses _open to open a file  
 * named CRT_OPEN.C for input and a file named CRT_OPEN.OUT  
 * for output. The files are then closed.  
 */  
#include <fcntl.h>  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int fh1, fh2;  
  
   fh1 = _open( "CRT_OPEN.C", _O_RDONLY ); // C4996  
   // Note: _open is deprecated; consider using _sopen_s instead  
   if( fh1 == -1 )  
      perror( "Open failed on input file" );  
   else  
   {  
      printf( "Open succeeded on input file\n" );  
      _close( fh1 );  
   }  
  
   fh2 = _open( "CRT_OPEN.OUT", _O_WRONLY | _O_CREAT, _S_IREAD |   
                            _S_IWRITE ); // C4996  
   if( fh2 == -1 )  
      perror( "Open failed on output file" );  
   else  
   {  
      printf( "Open succeeded on output file\n" );  
      _close( fh2 );  
   }  
}  
```  
  
## <a name="output"></a>출력  
  
```  
Open succeeded on input file  
Open succeeded on output file  
```  
  
## <a name="see-also"></a>참고 항목  
 [하위 수준 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod, _wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_creat, _wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [_dup, _dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_sopen, _wsopen](../../c-runtime-library/reference/sopen-wsopen.md)