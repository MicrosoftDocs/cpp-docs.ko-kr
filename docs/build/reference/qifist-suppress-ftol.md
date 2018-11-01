---
title: /QIfist(_ftol 사용 안 함)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: e01ee0b7af68127f3a78b4cfda1d110f6187fa74
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50528114"
---
# <a name="qifist-suppress-ftol"></a>/QIfist(_ftol 사용 안 함)

더 이상 사용되지 않습니다. 부동 소수점 형식에서 정수 계열 형식으로 변환해야 할 때 도우미 함수 `_ftol` 이 호출되지 않도록 합니다.

## <a name="syntax"></a>구문

```
/QIfist
```

## <a name="remarks"></a>설명

> [!NOTE]
>  **/Qifist** 은 영어로 x86 대상 컴파일러가 컴파일러 옵션이 x64를 대상으로 한 컴파일러에서 제공 되지 않습니다. 또는 Arm입니다.

부동 소수점 형식에서 정수 계열 형식으로 변환 하는 것 외에도 `_ftol` 함수를 사용 하면 반올림 모드 (FPU) 부동 소수점 단위의 0 (잘라내기)으로 제어 단어의 10 및 11 비트를 설정 하 여 합니다. 이 (숫자의 소수 부분이 삭제 됩니다.)는 ANSI C 표준에 설명 된 대로 발생 부동 소수점 형식에서 정수 계열 형식으로 변환 함을 보장 합니다. 사용 하는 경우 **/QIfist**을이 변환이 적용 되지 않습니다. Intel 참조에에서 설명 된 대로 반올림 모드를 4 중 하나가 됩니다.

- 가장 가까운 (짝수 원에서 균등 한 거리 경우)으로 반올림

- 음의 무한대로 반올림 합니다.

- 양의 무한대 방향으로 반올림 합니다.

- 0으로 반올림

사용할 수는 [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C 런타임 함수 FPU의 반올림 동작을 수정 합니다. 반올림 모드 FPU의 기본값은 "가장 가까운 쪽으로 반올림"입니다. 사용 하 여 **/QIfist** 위험이 있지만 응용 프로그램의 성능을 향상 시킬 수 있습니다. 반올림 모드를 사용 하 여 빌드한 코드를 기반으로 신뢰 하기 전에 영향을 받는 코드 부분을 철저히 테스트 해야 **/QIfist** 프로덕션 환경에서.

[/arch (x86)](../../build/reference/arch-x86.md) 하 고 **/QIfist** 는 동일한 compiland에서 사용할 수 없습니다.

> [!NOTE]
>  **/Qifist** 는 실제로 기본적으로 비트도 부동 소수점을 부동으로 영향을 가리키지 반올림 (하는 발생 모든 계산 후), C-스타일 (0)으로 반올림 하는 것에 대 한 플래그를 설정 하면 부동 소수점 계산 달라질 수 있습니다. **/Qifist** 코드가 부동 소수점 숫자의 소수 부분을 자르기의 예상된 동작으로 사용할 수 해야 합니다. 확실 하지 않은 경우 사용 하지 마세요 **/QIfist**합니다.

합니다 **/QIfist** 옵션 Visual Studio 2005부터 사용 되지 않습니다. 컴파일러 크게 향상 되었습니다 float에서 int 변환 속도입니다. 사용 되지 않는 컴파일러 옵션의 목록을 참조 하세요 **컴파일러 옵션 및 사용 되지 않음** 에 [컴파일러 옵션 범주별 목록](../../build/reference/compiler-options-listed-by-category.md)합니다.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. **C/C++** 폴더를 클릭합니다.

1. **명령줄** 속성 페이지를 클릭합니다.

1. **추가 옵션** 상자에 컴파일러 옵션을 입력합니다.

### <a name="to-set-this-compiler-option-programmatically"></a>프로그래밍 방식으로 이 컴파일러 옵션을 설정하려면

- <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>을 참조하세요.

## <a name="see-also"></a>참고 항목

[/Q 옵션(하위 수준 작업)](../../build/reference/q-options-low-level-operations.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)