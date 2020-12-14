---
description: 자세히 알아보기:/vd (생성 치환 사용 안 함)
title: /vd(생성 치환 비활성화)
ms.date: 11/04/2016
f1_keywords:
- /vd
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
ms.openlocfilehash: 9c90e2fa4f93ea0ba3892a07e13f2a15e848d608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97253197"
---
# <a name="vd-disable-construction-displacements"></a>/vd(생성 치환 비활성화)

## <a name="syntax"></a>구문

```
/vdn
```

## <a name="arguments"></a>인수

**0**<br/>
Vtordisp 생성자/소멸자 치환 멤버를 표시 하지 않습니다. 모든 클래스 생성자와 소멸자가 가상 함수를 실제로 호출 하는 것이 확실 한 경우에만이 옵션을 선택 합니다.

**1**<br/>
숨겨진 vtordisp 생성자/소멸자 치환 멤버를 만들 수 있도록 합니다. 기본 선택 사항입니다.

**2**<br/>
생성 되는 개체에 대해 [Dynamic_cast 연산자](../../cpp/dynamic-cast-operator.md) 를 사용할 수 있습니다. 예를 들어 가상 기본 클래스에서 파생 클래스에 대 한 dynamic_cast입니다.

**/vd2** 가상 함수를 사용 하는 가상 베이스가 있는 경우 vtordisp 필드를 추가 합니다. **/vd1** 면 충분 합니다. **/Vd2** 가 필요한 가장 일반적인 경우는 가상 기본의 유일한 가상 함수가 소멸자 인 경우입니다.

## <a name="remarks"></a>설명

이러한 옵션은 가상 베이스를 사용 하는 c + + 코드에만 적용 됩니다.

Visual C++는 가상 상속이 사용 되는 경우 c + + 생성 치환 지원을 구현 합니다. 생성 치환은 가상 기본에서 선언 되 고 파생 클래스에서 재정의 된 가상 함수를 추가 파생 클래스를 생성 하는 동안 생성자에서 호출 하는 경우 생성 되는 문제를 해결 합니다.

문제는 **`this`** 클래스의 가상 기본에 대 한 치환과 파생 된 클래스에 대 한 치환 간의 불일치 때문에 가상 함수에 잘못 된 포인터가 전달 될 수 있다는 것입니다. 이 솔루션은 클래스의 각 가상 기본에 대해 vtordisp 필드 라고 하는 단일 생성 치환 조정을 제공 합니다.

기본적으로 vtordisp 필드는 코드가 사용자 정의 생성자 및 소멸자를 정의 하 고 가상 기본의 가상 함수도 재정의할 때마다 도입 됩니다.

이러한 옵션은 전체 소스 파일에 영향을 줍니다. [Vtordisp](../../preprocessor/vtordisp.md) 를 사용 하 여 클래스 별로 vtordisp 필드를 표시 하지 않고 다시 사용 하도록 설정 합니다.

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
