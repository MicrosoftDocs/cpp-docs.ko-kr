---
description: 에 대해 자세히 알아보세요. 링커 입력 파일로 서의 Obj 파일
title: 링커 입력 파일로 사용하는 .Obj 파일
ms.date: 12/29/2017
helpviewer_keywords:
- linker [C++], OBJ files as input
- object files, linker output
- OMF object files
- LINK tool [C++], .obj files
- COFF files
- OBJ files as linker input
- .obj files as linker input
ms.openlocfilehash: 33b4a9d9a23854766100d0b023713f7ecbc71e32
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192722"
---
# <a name="obj-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Obj 파일

링커 도구 (LINK.EXE)는 COFF (Common Object File Format)에 있는 .obj 파일을 허용 합니다.

## <a name="remarks"></a>설명

Microsoft에서는 일반적인 개체 파일 형식에 대 한 전체 설명을 제공 합니다. 자세한 내용은 [PE 형식](/windows/win32/Debug/pe-format)을 참조 하세요.

## <a name="unicode-support"></a>유니코드 지원

Visual Studio 2005부터 Microsoft MSVC 컴파일러는 ISO/IEC C 및 c + + 표준에 정의 된 대로 식별자의 유니코드 문자를 지원 합니다. 이전 버전의 컴파일러는 식별자에서 ASCII 문자만 지원 했습니다. 함수, 클래스 및 정적 이름에서 유니코드를 지원 하기 위해 컴파일러와 링커는 .obj 파일의 COFF 기호에 유니코드 UTF-8 인코딩을 사용 합니다. UTF-8 인코딩은 이전 버전의 Visual Studio에서 사용 하는 ASCII 인코딩과 upwardly 호환 됩니다.

컴파일러 및 링커에 대 한 자세한 내용은 [컴파일러 및 링커의 유니코드 지원](unicode-support-in-the-compiler-and-linker.md)을 참조 하세요. 유니코드 표준에 대 한 자세한 내용은 [유니코드](https://home.unicode.org/) 조직을 참조 하세요.

## <a name="see-also"></a>참고 항목

[링크 입력 파일](link-input-files.md)<br/>
[MSVC 링커 옵션](linker-options.md)<br/>
[유니코드 지원](../../text/support-for-unicode.md)<br/>
[컴파일러 및 링커의 유니코드 지원](unicode-support-in-the-compiler-and-linker.md)<br/>
[유니코드 표준](https://home.unicode.org/)<br/>
[PE 형식](/windows/win32/Debug/pe-format)
