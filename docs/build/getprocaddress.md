---
description: '자세한 정보: GetProcAddress'
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 32f0d6d623ea3a4499603a1b76e2c320537820fe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162874"
---
# <a name="getprocaddress"></a>GetProcAddress

DLL 호출 [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress)에의 연결을 명시적으로 처리하여 DLL의 내보낸 함수 주소를 가져옵니다. 반환된 함수 포인터를 사용하여 DLL 함수를 호출합니다. 합니다. **GetProcAddress** 는 매개 변수로 DLL 모듈 핸들(**LoadLibrary**, `AfxLoadLibrary` 또는 **GetModuleHandle** 에서 반환)을 사용하고 호출할 함수의 이름이나 함수의 내보내기 서수를 사용합니다.

포인터를 통해 DLL 함수를 호출하고 컴파일 시간 형식 검사가 없으므로 함수의 매개 변수를 올바로 설정해야만 스택에 할당된 메모리의 한계를 넘지 않고 액세스 위반이 발생하지 않습니다. 형식 안전성을 제공하기 위해서는 내보낸 함수의 함수 프로토타입을 살펴보고 함수 포인터에 대해 일치하는 형식 정의를 만들어야 합니다. 예를 들어:

```
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);
...

HINSTANCE hDLL;               // Handle to DLL
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
DWORD dwParam1;
UINT  uParam2, uReturnVal;

hDLL = LoadLibrary("MyDLL");
if (hDLL != NULL)
{
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,
                                           "DLLFunc1");
   if (!lpfnDllFunc1)
   {
      // handle the error
      FreeLibrary(hDLL);
      return SOME_ERROR_CODE;
   }
   else
   {
      // call the function
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);
   }
}
```

**GetProcAddress** 를 호출할 때 원하는 함수를 지정하는 방법은 DLL이 빌드된 방법에 따라 달라집니다.

연결하려는 DLL이 모듈 정의 파일(.def)로 빌드되고 서수가 DLL .def 파일의 **EXPORTS** 섹션에 함수와 함께 나열되어 있으면 내보내기 서수만 가져올 수 있습니다. 함수 이름이 아니라 내보내기 서수를 사용하여 **GetProcAddress** 를 호출하면 내보내기 서수가 DLL 내보내기 테이블의 인덱스 역할을 하므로 DLL에 내보낸 함수가 많은 경우 약간 더 빠릅니다. 내보내기 서수를 사용하면 **GetProcAddress** 는 지정된 이름을 DLL의 내보내기 테이블에 있는 함수 이름과 비교하지 않고 함수를 직접 찾을 수 있습니다. 그러나 .def 파일의 내보낸 함수에의 서수 할당을 제어할 수 있는 경우에만 내보내기 서수를 사용하여 **GetProcAddress** 를 호출해야 합니다.

## <a name="what-do-you-want-to-do"></a>원하는 작업을 선택하세요.

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#linking-implicitly)

- [DLL에 실행 파일 링크](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>추가 정보

- [LoadLibrary 및 AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [DEF 파일을 사용하여 DLL에서 내보내기](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>참조

[Visual Studio에서 C/C++ DLL 만들기](dlls-in-visual-cpp.md)
