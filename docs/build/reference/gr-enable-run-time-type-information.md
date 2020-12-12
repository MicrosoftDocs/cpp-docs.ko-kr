---
description: 자세히 알아보기:/GR (Run-Time 형식 정보 사용)
title: /GR(런타임 형식 정보 사용)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: 61b1a595999e5e00bf6b28c75be2de03467cc4ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200167"
---
# <a name="gr-enable-run-time-type-information"></a>/GR(런타임 형식 정보 사용)

런타임에 개체 형식을 검사 하는 코드를 추가 합니다.

## <a name="syntax"></a>구문

```
/GR[-]
```

## <a name="remarks"></a>설명

**/Gr** 가 on으로 설정 된 경우 컴파일러는 `_CPPRTTI` 전처리기 매크로를 정의 합니다. 기본적으로 **/gr** 는 on입니다. **/GR-** 는 런타임 형식 정보를 사용 하지 않도록 설정 합니다.

컴파일러가 코드에서 개체 형식을 정적으로 확인할 수 없는 경우에는 **/gr** 를 사용 합니다. 코드에서 연산자 또는 [typeid](../../cpp/typeid-operator.md) [dynamic_cast](../../cpp/dynamic-cast-operator.md) 사용 하는 경우 일반적으로 **/gr** 옵션이 필요 합니다. 그러나 **/gr** 는 이미지의 .rdata 섹션 크기를 늘립니다. 코드에서 또는를 사용 하지 않는 경우 **`dynamic_cast`** **`typeid`** **/GR-** 는 더 작은 이미지를 생성할 수 있습니다.

런타임 형식 검사에 대 한 자세한 내용은 *c + + 언어 참조* 의 [런타임 형식 정보](../../cpp/run-time-type-information.md) 를 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **언어** 속성 페이지를 클릭 합니다.

1. **Run-Time 형식 정보 사용** 속성을 수정 합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
