---
title: -volatile (volatile 키워드 해석) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /volatile:iso
- /volatile:ms
- /volatile
dev_langs:
- C++
helpviewer_keywords:
- /volatile compiler option
- /volatile compiler option [C++]
- -volatile compiler option
- volatile compiler option [C++]
- volatile compiler option
- -volatile compiler option [C++]
ms.assetid: 9d08fcc6-5bda-44c8-8151-8d8d54f164b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4204d602d1390bf30080a800174426513faf0467
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723636"
---
# <a name="volatile-volatile-keyword-interpretation"></a>/volatile(volatile 키워드 해석)

지정 하는 방법을 [volatile](../../cpp/volatile-cpp.md) 해석 해야 하는 키워드입니다.

## <a name="syntax"></a>구문

> **/volatile:**{**iso**|**ms**}

## <a name="arguments"></a>인수

**/volatile:iso**<br/>
엄격한 선택 `volatile` ISO 표준 c + + 언어에서 정의 된 의미 체계. Volatile 액세스에 acquire/release 의미 체계가 보장 되지 않습니다. 컴파일러가 ARM을 대상으로 하는 경우의 기본 해석입니다 `volatile`합니다.

**/volatile:ms**<br/>
Microsoft 확장 선택 `volatile` 의미 체계를 memory ordering 보장 ISO 표준 c + + 언어 외에 추가 합니다. Volatile 액세스에 acquire/release 의미 체계가 보장 됩니다. 그러나이 옵션에는 ARM 및 취약 한 기타 메모리 순서가 아키텍처에 상당한 오버 헤드를 추가할 수 있는 하드웨어 메모리 장벽을 생성 하도록 컴파일러에도 실행 하도록 합니다. 컴파일러가 ARM 제외한 모든 플랫폼을 대상으로 하는 경우의 기본 해석입니다 `volatile`합니다.

## <a name="remarks"></a>설명

사용 하는 것이 좋습니다 **/volatile:iso** 명시적 동기화 기본 형식 및 컴파일러 내장 함수는 스레드 간에 공유 되는 메모리를 처리할 때 함께 합니다. 자세한 내용은 [volatile](../../cpp/volatile-cpp.md)합니다.

를 기존 코드를 이식 하거나 프로젝트 중간에이 옵션을 변경 하는 경우 경고를 사용 하도록 설정 하려면 유용할 수 있습니다 [C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md) 의미 체계의 영향을 받는 코드 위치를 식별 합니다.

방법이 없는 `#pragma` 이 옵션을 제어 하에 해당 합니다.

### <a name="to-set-the-volatile-compiler-option-in-visual-studio"></a>/Volatile를 설정 하려면 Visual Studio에서 컴파일러 옵션

1. 엽니다는 **속성 페이지** 프로젝트에 대 한 대화 상자. 자세한 내용은 [프로젝트 속성 작업](../../ide/working-with-project-properties.md)을 참조하세요.

1. 선택 된 **구성 속성** > **C/c + +** > **명령줄** 속성 페이지.

1. 에 **추가 옵션** 상자에서 추가 **/volatile:iso** 또는 **찾는데** 를 선택한 후 **확인** 또는 **적용** 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고자료

[volatile](../../cpp/volatile-cpp.md)<br/>
[컴파일러 옵션](../../build/reference/compiler-options.md)<br/>
[컴파일러 옵션 설정](../../build/reference/setting-compiler-options.md)
