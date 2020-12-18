---
description: '자세한 정보: main 함수 및 프로그램 실행'
title: 기본 함수 및 프로그램 실행
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: 00fb10526b558631c024366c09a773363bd81683
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257084"
---
# <a name="main-function-and-program-execution"></a>기본 함수 및 프로그램 실행

모든 C 프로그램에는 **main** 이라는 이름을 지정해야 하는 기본(main) 함수가 있습니다. 코드가 유니코드 프로그래밍 모델을 따르는 경우 **main** 의 와이드 문자 버전인 **wmain** 을 사용할 수 있습니다. **main** 함수는 프로그램 실행을 위한 시작 지점 역할을 하며, 일반적으로 프로그램의 다른 함수로 호출을 보내 프로그램 실행을 제어합니다. 프로그램은 여러 가지 이유로 프로그램의 다른 지점에서 종료될 수 있지만 대개 **main** 끝에서 실행을 중지합니다. 때때로 특정 오류가 감지될 때 등에 프로그램을 강제 종료해야 할 수 있습니다. 이렇게 하려면 **exit** 함수를 사용합니다. [exit](../c-runtime-library/reference/exit-exit-exit.md) 함수 사용에 대한 정보 및 예제는 *런타임 라이브러리 참조* 를 참조하세요.

## <a name="syntax"></a>구문

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>설명

소스 프로그램 내의 함수는 하나 이상의 특정 작업을 수행합니다. **main** 함수는 각 작업을 수행하기 위해 이러한 함수를 호출할 수 있습니다. 다른 함수를 호출할 때 **main** 은 실행이 함수의 첫 번째 문에서 시작될 수 있도록 해당 함수에 실행 제어를 전달합니다. 함수는 **`return`** 문이 실행되거나 함수 끝에 도달할 때 **main** 에 제어를 반환합니다.

**main** 을 포함한 모든 함수가 매개 변수를 가지도록 선언할 수 있습니다. "매개 변수" 또는 "정식 매개 변수"라는 용어는 함수에 전달되는 값을 받는 식별자를 가리킵니다. 매개 변수로의 인수 전달에 대한 자세한 내용은 [매개 변수](../c-language/parameters.md)를 참조하세요. 한 함수가 다른 함수를 호출할 때 호출된 함수는 호출 함수에서 해당 매개 변수에 대한 값을 받습니다. 이러한 값을 "인수"라고 합니다. 이 형식을 사용하여 명령줄에서 인수를 받을 수 있도록 **main** 에 정식 매개 변수를 선언할 수 있습니다.

**main** 함수에 정보를 전달하려는 경우 일반적으로 매개 변수의 이름을 `argc` 및 `argv`로 지정합니다. 단, C 컴파일러는 이러한 이름을 요구하지 않습니다. `argc` 및 `argv`에 대한 형식은 C 언어에서 정의됩니다. 일반적으로 세 번째 매개 변수가 **main** 에 전달될 경우 해당 매개 변수의 이름은 `envp`로 지정됩니다. 이 단원의 뒷부분에 나오는 예제에서는 이러한 세 가지 매개 변수를 사용하여 명령줄 인수에 액세스하는 방법을 보여 줍니다. 다음 단원에서는 이러한 매개 변수를 설명합니다.

**main** 의 와이드 문자 버전에 대한 설명은 [wmain 사용](../c-language/using-wmain.md)을 참조하세요.

## <a name="see-also"></a>참조

[main 함수와 명령줄 인수(C++)](../cpp/main-function-command-line-args.md)\
[C 명령줄 인수 구문 분석](../c-language/parsing-c-command-line-arguments.md)
