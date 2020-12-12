---
description: '자세한 정보: c + +/CLI의 마샬링 개요'
title: C++ 마샬링 개요
ms.date: 07/12/2019
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
ms.openlocfilehash: 35294a204d338087a609746e6ae2e5e07ea07b59
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255537"
---
# <a name="overview-of-marshaling-in-ccli"></a>C + +/CLI의 마샬링 개요

혼합 모드에서는 경우에 따라 네이티브 및 관리 되는 형식 간에 데이터를 마샬링해야 합니다. *마샬링 라이브러리* 를 사용 하면 간단한 방법으로 데이터를 마샬링 및 변환할 수 있습니다.  마샬링 라이브러리는 함수 집합 및 `marshal_context` 공용 형식에 대 한 마샬링을 수행 하는 클래스로 구성 됩니다. 라이브러리는 Visual Studio 버전용 **include/msclr** 디렉터리에서 다음 헤더에 정의 됩니다.

|헤더|설명|
|---------------|-----------------|
|marshal. h|`marshal_context` 클래스 및 컨텍스트 없는 마샬링 함수|
|marshal_atl. h| ATL 형식 마샬링을 위한 함수|
|marshal_cppstd. h|표준 c + + 형식을 마샬링하기 위한 함수|
|marshal_windows. h|Windows 형식 마샬링을 위한 함수|

**Msclr** 폴더의 기본 경로는 보유 하 고 있는 버전 및 빌드 번호에 따라 다음과 같이 표시 됩니다.

```cmd
C:\\Program Files (x86)\\Microsoft Visual Studio\\Preview\\Enterprise\\VC\\Tools\\MSVC\\14.15.26528\\include\\msclr
```

[Marshal_context 클래스](../dotnet/marshal-context-class.md)를 사용 하거나 사용 하지 않고 마샬링 라이브러리를 사용할 수 있습니다. 일부 변환에는 컨텍스트가 필요 합니다. [Marshal_as](../dotnet/marshal-as.md) 함수를 사용 하 여 다른 변환을 구현할 수 있습니다. 다음 표에는 현재 지원 되는 변환, 컨텍스트가 필요한 지 여부 및 포함 해야 하는 마샬링 파일이 나열 되어 있습니다.

|원본 형식|형식으로|Marshal 메서드|포함 파일|
|---------------|-------------|--------------------|------------------|
|System:: String ^|const 문자 \*|marshal_context|marshal. h|
|const 문자 \*|System:: String ^|marshal_as|marshal. h|
|문자가 \*|System:: String ^|marshal_as|marshal. h|
|System:: String ^|const wchar_t\*|marshal_context|marshal. h|
|const wchar_t \*|System:: String ^|marshal_as|marshal. h|
|wchar_t \*|System:: String ^|marshal_as|marshal. h|
|System:: IntPtr|HANDLE|marshal_as|marshal_windows. h|
|HANDLE|System:: IntPtr|marshal_as|marshal_windows. h|
|System:: String ^|BSTR|marshal_context|marshal_windows. h|
|BSTR|System:: String ^|marshal_as|marshal. h|
|System:: String ^|bstr_t|marshal_as|marshal_windows. h|
|bstr_t|System:: String ^|marshal_as|marshal_windows. h|
|System:: String ^|std:: string|marshal_as|marshal_cppstd. h|
|std:: string|System:: String ^|marshal_as|marshal_cppstd. h|
|System:: String ^|std::wstring|marshal_as|marshal_cppstd. h|
|std::wstring|System:: String ^|marshal_as|marshal_cppstd. h|
|System:: String ^|CStringT\<char>|marshal_as|marshal_atl. h|
|CStringT\<char>|System:: String ^|marshal_as|marshal_atl. h|
|System:: String ^|CStringT<wchar_t>|marshal_as|marshal_atl. h|
|CStringT<wchar_t>|System:: String ^|marshal_as|marshal_atl. h|
|System:: String ^|CComBSTR|marshal_as|marshal_atl. h|
|CComBSTR|System:: String ^|marshal_as|marshal_atl. h|

마샬링을 사용 하려면 관리 되는 네이티브 데이터 형식에서 네이티브 데이터 형식으로 마샬링할 때와 변환할 네이티브 형식에 자동 정리를 위한 소멸자가 없는 경우에만 컨텍스트가 필요 합니다. 마샬링 컨텍스트는 해당 소멸자에서 할당 된 네이티브 데이터 형식을 소멸 시킵니다. 따라서 컨텍스트가 필요한 변환은 컨텍스트가 삭제 될 때 까지만 유효 합니다. 마샬링되는 값을 저장 하려면 고유한 변수에 값을 복사 해야 합니다.

> [!NOTE]
> 문자열에를 포함 하는 경우 `NULL` 문자열을 마샬링하는 결과가 보장 되지 않습니다. 포함 된를 통해 `NULL` 문자열이 잘리거나 유지 될 수 있습니다.

이 예제에서는 포함 헤더 선언에 msclr 디렉터리를 포함 하는 방법을 보여 줍니다.

`#include "msclr\marshal_cppstd.h"`

마샬링 라이브러리는 사용자 고유의 마샬링 형식을 추가할 수 있도록 확장 가능 합니다. 마샬링 라이브러리를 확장 하는 방법에 대 한 자세한 내용은 [방법: 마샬링 라이브러리 확장](../dotnet/how-to-extend-the-marshaling-library.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[C + + 지원 라이브러리](../dotnet/cpp-support-library.md)<br/>
[방법: 마샬링 라이브러리 확장](../dotnet/how-to-extend-the-marshaling-library.md)
