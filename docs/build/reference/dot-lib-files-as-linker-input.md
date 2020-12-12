---
description: 에 대해 자세히 알아보세요. 링커 입력 파일로 서의 Lib 파일
title: 링커 입력 파일로 사용하는 .Lib 파일
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.AdditionalDependencies
helpviewer_keywords:
- OMF libraries
- linking [C++], OMF libraries
- import libraries, linker files
- libraries [C++], .lib files as linker input
- COFF files, import libraries
- default libraries [C++], linker output
- default libraries [C++]
- defaults [C++], libraries
- .lib files
ms.assetid: dc5d2b1c-2487-41fa-aa71-ad1e0647958b
ms.openlocfilehash: f4a3b6c6487947772fb72135fb26f67857f0937e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201263"
---
# <a name="lib-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Lib 파일

LINK는 COFF 표준 라이브러리 및 COFF 가져오기 라이브러리를 수락 하며, 둘 다 일반적으로 확장명이 .lib입니다. 표준 라이브러리는 개체를 포함 하 고 LIB 도구를 통해 생성 됩니다. 가져오기 라이브러리는 다른 프로그램의 내보내기에 대 한 정보를 포함 하며 내보내기 또는 LIB 도구를 포함 하는 프로그램을 빌드할 때 링크를 통해 생성 됩니다. LIB를 사용 하 여 표준 또는 가져오기 라이브러리를 만드는 방법에 대 한 자세한 내용은 [Lib 참조](lib-reference.md)를 참조 하세요. 링크를 사용 하 여 가져오기 라이브러리를 만드는 방법에 대 한 자세한 내용은 [/dll](dll-build-a-dll.md) 옵션을 참조 하세요.

라이브러리를 파일 이름 인수나 기본 라이브러리로 연결 하도록 지정 합니다. LINK는 명령줄에 지정 된 라이브러리에서 먼저 검색 한 다음 [/DEFAULTLIB](defaultlib-specify-default-library.md) 옵션을 사용 하 여 지정 된 기본 라이브러리와 .obj 파일에 명명 된 기본 라이브러리에서 외부 참조를 확인 합니다. 라이브러리 이름으로 경로를 지정 하는 경우 링크는 해당 디렉터리에서 라이브러리를 찾습니다. 경로를 지정 하지 않으면 link는 링크를 실행 하는 디렉터리에서 먼저 찾은 다음 LIB 환경 변수에 지정 된 모든 디렉터리에서 찾습니다.

## <a name="to-add-lib-files-as-linker-input-in-the-development-environment"></a>개발 환경에서 링커 입력으로 .lib 파일을 추가 하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **링커** 폴더에서 **입력** 속성 페이지를 선택 합니다.

1. **추가 종속성** 속성을 수정 하 여 .lib 파일을 추가 합니다.

## <a name="to-programmatically-add-lib-files-as-linker-input"></a>프로그래밍 방식으로 .lib 파일을 링커 입력으로 추가 하려면

- [Additionaldependencies](/dotnet/api/microsoft.visualstudio.vcprojectengine.vclinkertool.additionaldependencies)을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 .lib 파일을 작성 하 고 사용 하는 방법을 보여 줍니다. 먼저 .lib 파일을 빌드합니다.

```cpp
// lib_link_input_1.cpp
// compile by using: cl /LD lib_link_input_1.cpp
__declspec(dllexport) int Test() {
   return 213;
}
```

그런 다음 방금 만든 .lib 파일을 사용 하 여이 샘플을 컴파일합니다.

```cpp
// lib_link_input_2.cpp
// compile by using: cl /EHsc lib_link_input_1.lib lib_link_input_2.cpp
__declspec(dllimport) int Test();
#include <iostream>
int main() {
   std::cout << Test() << std::endl;
}
```

```Output
213
```

## <a name="see-also"></a>참고 항목

[링크 입력 파일](link-input-files.md)<br/>
[MSVC 링커 옵션](linker-options.md)
