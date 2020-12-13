---
description: '자세히 알아보기: ConvertBSTRToString'
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: 72d6033003f186f358d9b4143498df65858ee354
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344616"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Microsoft 전용**

`BSTR` 값을 `char *`으로 변환합니다.

## <a name="syntax"></a>구문

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>매개 변수

*.Psrc*<br/>
BSTR 변수입니다.

## <a name="remarks"></a>설명

**ConvertBSTRToString** 는 삭제 해야 하는 문자열을 할당 합니다.

## <a name="example"></a>예제

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**Microsoft 전용 종료**

## <a name="requirements"></a>요구 사항

**헤더:**\<comutil.h>

**Lib:** comsuppw 또는 comsuppw .lib (자세한 내용은 [/zc: Wchar_t (wchar_t 네이티브 형식)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 참조)

## <a name="see-also"></a>참고 항목

[컴파일러 COM 전역 함수](../cpp/compiler-com-global-functions.md)
