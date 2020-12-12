---
description: 자세히 알아보기:/QIfist (_ftol 표시 안 함)
title: /QIfist(_ftol 사용 안 함)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 79e9242d66b532f558307d05b222b2fd8cfd43ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225650"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist(_ftol 사용 안 함)

더 이상 사용되지 않습니다. 부동 소수점 형식에서 정수 계열 형식으로 변환해야 할 때 도우미 함수 `_ftol` 이 호출되지 않도록 합니다.

## <a name="syntax"></a>구문

```
/QIfist
```

## <a name="remarks"></a>설명

> [!NOTE]
> **/Qifist** 는 x86을 대상으로 하는 컴파일러 에서만 사용할 수 있습니다. 이 컴파일러 옵션은 x64 orARM을 대상으로 하는 컴파일러에서 사용할 수 없습니다.

함수는 부동 소수점 형식에서 정수 계열 형식으로 변환 하는 것 외에도 `_ftol` 제어 단어의 비트 10과 11을 설정 하 여 FPU (부동 소수점 단위)의 반올림 모드가 0 (잘림)을 향해 있는지 확인 합니다. 이를 통해 ANSI C 표준에 설명 된 대로 부동 소수점 형식에서 정수 계열 형식으로 변환 하는 것이 보장 됩니다 (숫자의 소수 부분이 무시 됨). **/Qifist** 를 사용 하는 경우이 보장은 더 이상 적용 되지 않습니다. 반올림 모드는 Intel 참조 설명서에 설명 된 대로 4 개 중 하나입니다.

- 가장 가까운 값으로 반올림 (등거리 인 경우에도)

- 음의 무한대로 반올림

- 양의 무한대로 반올림

- 0으로 반올림

[_Control87, _controlfp, \_ _control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C Run-Time 함수를 사용 하 여 FPU의 반올림 동작을 수정할 수 있습니다. FPU의 기본 반올림 모드는 "가장 가까운 쪽으로 반올림"입니다. **/Qifist** 를 사용 하면 응용 프로그램의 성능을 향상 시킬 수 있지만 위험 없이는 향상 됩니다. 프로덕션 환경에서 **/qifist** 로 빌드된 코드를 사용 하기 전에 반올림 모드에 민감한 코드 부분을 철저히 테스트 해야 합니다.

[/arch (x86)](arch-x86.md) 및 **/qifist** 는 동일한 compiland에서 사용할 수 없습니다.

> [!NOTE]
> 계산 비트는 모든 계산 후에 발생 하는 부동 소수점 반올림 (계산 후에 발생)에도 영향을 주기 때문에 **/qifist** 는 기본적으로 적용 되지 않습니다. 따라서 C 스타일 (0에 대 한) 반올림에 대 한 플래그를 설정 하면 부동 소수점 계산이 다를 수 있습니다. 코드가 부동 소수점 숫자의 소수 부분을 잘라내는 예상 동작에 따라 달라 지는 경우에는 **/qifist** 를 사용 하면 안 됩니다. 잘 모르겠으면 **/qifist** 를 사용 하지 마십시오.

**/Qifist** 옵션은 Visual Studio 2005부터 사용 되지 않습니다. 컴파일러가 float에서 int로의 변환 속도를 크게 개선 했습니다. 사용 되지 않는 컴파일러 옵션의 목록은 [컴파일러 옵션 범주별](compiler-options-listed-by-category.md)목록에서 **사용 되지 않는 컴파일러 옵션** 을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션 (하위 수준 작업)](q-options-low-level-operations.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
