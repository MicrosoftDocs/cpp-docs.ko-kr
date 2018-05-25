---
title: gets, _getws | Microsoft 문서
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
dev_langs:
- C++
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a597ad1a72f903d08e848727045e05bf014879b1
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/22/2018
---
# <a name="gets-getws"></a>gets, _getws
`stdin` 스트림에서 줄을 가져옵니다. 이러한 함수의 더 안전한 버전을 사용할 수 있습니다. [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)를 참조하세요.  
  
> [!IMPORTANT]
>  이러한 함수는 사용되지 않습니다. Visual Studio 2015부터 CRT에서 사용할 수 없습니다. 이러한 함수의 안전한 버전인 gets_s 및 _getws_s는 계속 사용할 수 있습니다. 이러한 대체 함수에 대한 자세한 내용은 [gets_s, _getws_s](../c-runtime-library/reference/gets-s-getws-s.md)를 참조하세요.  
  
> [!IMPORTANT]
>  이 API는 Windows 런타임에서 실행되는 응용 프로그램에서 사용할 수 없습니다. 자세한 내용은 [유니버설 Windows 플랫폼 앱에서 지원되지 않는 CRT 함수](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)를 참조하세요.  
  
## <a name="syntax"></a>구문  
  
```  
char *gets(   
   char *buffer   
);  
wchar_t *_getws(   
   wchar_t *buffer   
);  
template <size_t size>  
char *gets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>매개 변수  
 `buffer`  
 입력 문자열에 대한 저장소 위치입니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 해당 인수를 반환합니다. **NULL** 포인터는 오류 또는 파일 끝 조건을 나타냅니다. 어떤 것이 발생했는지 확인하려면 [ferror](../c-runtime-library/reference/ferror.md) 또는 [feof](../c-runtime-library/reference/feof.md) 를 사용하십시오. `buffer`이 **NULL**인 경우 이러한 함수는 [매개 변수 유효성 검사](../c-runtime-library/parameter-validation.md)에 설명된 대로 잘못된 매개 변수 처리기를 호출합니다. 계속해서 실행하도록 허용된 경우 이러한 함수는 **NULL**을 반환하고 errno를 `EINVAL`로 설정합니다.  
  
## <a name="remarks"></a>설명  
 `gets` 함수는 표준 입력 스트림 `stdin`에서 줄을 읽고 `buffer`에 저장합니다. 줄은 첫 번째 줄 바꿈 문자('\n')까지 모든 문자로 구성됩니다. `gets` 는 줄을 반환하기 전에 줄 바꿈 문자를 null 문자('\0')로 대체합니다. 반대로 `fgets` 함수는 줄 바꿈 문자를 유지합니다. `_getws` 는 `gets`의 와이드 문자 버전입니다. 해당 인수 및 반환 값은 와이드 문자열입니다.  
  
> [!IMPORTANT]
>  gets에서 읽은 문자 수에 대한 제한이 없으므로 신뢰할 수 없는 입력에서 쉽게 버퍼 오버런이 발생할 수 있습니다. 대신 `fgets` 를 사용하세요.  
  
 C++에서 이러한 함수는 보다 최신의 보안 대응 함수를 호출하는 템플릿 오버로드를 갖고 있습니다. 자세한 내용은 [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md)을 참조하세요.  
  
### <a name="generic-text-routine-mappings"></a>제네릭 텍스트 루틴 매핑  
  
|TCHAR.H 루틴|_UNICODE 및 _MBCS 정의되지 않음|_MBCS 정의됨|_UNICODE 정의됨|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets`|`gets`|`_getws`|  
  
## <a name="requirements"></a>요구 사항  
  
|루틴에서 반환된 값|필수 헤더|  
|-------------|---------------------|  
|`gets`|\<stdio.h>|  
|`_getws`|\<stdio.h> 또는 \<wchar.h>|  
  
 호환성에 대한 자세한 내용은 [호환성](../c-runtime-library/compatibility.md)을 참조하세요.  
  
## <a name="example"></a>예  
  
```  
// crt_gets.c  
// compile with: /WX /W3  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C4996  
   // Danger: No way to limit input to 20 chars.  
   // Consider using gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
 20자보다 긴 입력에서 줄 버퍼를 오버런하면 대부분 프로그램에서 충돌이 유발될 수 있습니다.  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>참고 항목  
 [스트림 I/O](../c-runtime-library/stream-i-o.md)   
 [fgets, fgetws](../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs, fputws](../c-runtime-library/reference/fputs-fputws.md)   
 [puts, _putws](../c-runtime-library/reference/puts-putws.md)