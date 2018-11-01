---
title: /vmb,-vmg (표시 메서드)
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
ms.openlocfilehash: 30d15105b9fe502e89f77b19e530d6cc762975a8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505497"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg(표시 메서드)

컴파일러는 클래스 멤버에 대 한 포인터를 나타내는 데 사용 하는 메서드를 선택 합니다.

사용 하 여 **/vmb** 정의 하는 경우 클래스는 클래스의 멤버에 대 한 포인터를 선언 하기 전에 합니다.

사용 하 여 **/vmg** 클래스를 정의 하기 전에 클래스의 멤버에 대 한 포인터를 선언 합니다. 이 서로 참조 하는 두 개의 서로 다른 클래스에 멤버를 정의 하는 경우에 발생할 수 있습니다. 이러한 상호 참조 클래스에 대 한 정의 되기 전에 하나의 클래스를 참조 해야 합니다.

## <a name="syntax"></a>구문

```
/vmb
/vmg
```

## <a name="remarks"></a>설명

사용할 수도 있습니다 [pointers_to_members](../../preprocessor/pointers-to-members.md) 하거나 [상속 키워드](../../cpp/inheritance-keywords.md) 사용자 코드에 대 한 포인터 표현을 지정 합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)