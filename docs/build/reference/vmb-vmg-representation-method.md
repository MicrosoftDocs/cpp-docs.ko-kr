---
description: 자세히 알아보기:/vmb,/vmg (표시 메서드)
title: /vmb, /vmg(표시 메서드)
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: 19d183ef8d1dd152043d7249d907c9d5b48de230
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97254287"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg(표시 메서드)

컴파일러가 클래스 멤버에 대 한 포인터를 나타내는 데 사용 하는 메서드를 선택 합니다.

클래스 멤버에 대 한 포인터를 선언 하기 전에 항상 클래스를 정의 하는 경우 **/vmb** 를 사용 합니다.

클래스를 정의 하기 전에 **/vmg** 를 사용 하 여 클래스의 멤버에 대 한 포인터를 선언 합니다. 서로 다른 두 클래스에서 멤버를 정의 하는 경우 이러한 요구 사항이 발생할 수 있습니다. 상호 참조 하는 이러한 클래스의 경우 정의 되기 전에 한 클래스를 참조 해야 합니다.

## <a name="syntax"></a>구문

```
/vmb
/vmg
```

## <a name="remarks"></a>설명

코드에서 [pointers_to_members](../../preprocessor/pointers-to-members.md) 또는 [상속 키워드](../../cpp/inheritance-keywords.md) 를 사용 하 여 포인터 표현을 지정할 수도 있습니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
