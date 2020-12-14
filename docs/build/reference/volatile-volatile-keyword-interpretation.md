---
description: 자세히 알아보기:/volatile (volatile 키워드 해석)
title: /volatile(volatile 키워드 해석)
ms.date: 11/04/2016
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
ms.openlocfilehash: e75a9932cff59748cf75b89a3a85e89130de84f5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259216"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile(volatile 키워드 해석)

[Volatile](../../cpp/volatile-cpp.md) 키워드를 해석 하는 방법을 지정 합니다.

## <a name="syntax"></a>Syntax

> **/volatile:**{**iso** | **ms**}

## <a name="arguments"></a>인수

**/volatile: iso**<br/>
**`volatile`** ISO 표준 c + + 언어에서 정의한 엄격한 의미 체계를 선택 합니다. Volatile 액세스에 대해 획득/릴리스 의미 체계가 보장 되지 않습니다. 컴파일러가 ARM을 대상으로 하는 경우의 기본 해석입니다 **`volatile`** .

**/volatile: ms**<br/>
**`volatile`** ISO 표준 c + + 언어 이상의 메모리 정렬 보장을 추가 하는 Microsoft 확장 의미 체계를 선택 합니다. Volatile 액세스에 대해 획득/릴리스 의미 체계가 보장 됩니다. 그러나이 옵션을 선택 하면 컴파일러가 하드웨어 메모리 장벽을 생성 하 여 ARM 및 기타 weak 메모리 정렬 아키텍처에 상당한 오버 헤드를 추가할 수 있습니다. 컴파일러가 ARM을 제외한 모든 플랫폼을 대상으로 하는 경우의 기본 해석입니다 **`volatile`** .

## <a name="remarks"></a>설명

스레드 간에 공유 되는 메모리를 처리할 때 명시적인 동기화 기본 형식 및 컴파일러 내장 함수와 함께 **/volatile: iso** 를 사용 하는 것이 좋습니다. 자세한 내용은 [volatile](../../cpp/volatile-cpp.md)을 참조 하세요.

기존 코드를 이식 하거나 프로젝트 중간에이 옵션을 변경 하는 경우 경고 [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) 를 사용 하 여 의미 체계의 차이로 인해 영향을 받는 코드 위치를 식별 하는 것이 유용할 수 있습니다.

`#pragma`이 옵션을 제어 하는 것과 동일한 기능이 없습니다.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>Visual Studio에서/volatile 컴파일러 옵션을 설정 하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에서 **/volatile: iso** 또는 **/volatile: Ms** 를 추가 하 고 **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[volatile](../../cpp/volatile-cpp.md)<br/>
[MSVC 컴파일러 옵션](compiler-options.md)<br/>
[MSVC 컴파일러 Command-Line 구문](compiler-command-line-syntax.md)
