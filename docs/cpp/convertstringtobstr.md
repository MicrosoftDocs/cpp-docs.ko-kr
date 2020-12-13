---
description: '자세한 정보: ConvertStringToBSTR'
title: ConvertStringToBSTR
ms.date: 11/04/2016
f1_keywords:
- ConvertStringToBSTR
helpviewer_keywords:
- ConvertStringToBSTR function
ms.assetid: 071f9b3b-9643-4e06-a1e5-de96ed15bab2
ms.openlocfilehash: 7348fdec3448d17b51fd77385297422a8f10fd05
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344603"
---
# <a name="convertstringtobstr"></a>ConvertStringToBSTR

**Microsoft 전용**

`char *` 값을 `BSTR`으로 변환합니다.

## <a name="syntax"></a>구문

```
BSTR __stdcall ConvertStringToBSTR(const char* pSrc)
```

#### <a name="parameters"></a>매개 변수

*.Psrc*<br/>
`char *`변수입니다.

## <a name="example"></a>예제

```cpp
// ConvertStringToBSTR.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")
#pragma comment(lib, "kernel32.lib")

int main() {
   char* lpszText = "Test";
   printf_s("char * text: %s\n", lpszText);

   BSTR bstrText = _com_util::ConvertStringToBSTR(lpszText);
   wprintf_s(L"BSTR text: %s\n", bstrText);

   SysFreeString(bstrText);
}
```

```Output
char * text: Test
BSTR text: Test
```

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:**\<comutil.h>

**Lib:** comsuppw 또는 comsuppw .lib (자세한 내용은 [/zc: Wchar_t (wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 참조)

## <a name="see-also"></a>참고 항목

[컴파일러 COM 전역 함수](../cpp/compiler-com-global-functions.md)
