---
title: /Zc:auto(변수 형식 추론)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: 6bb1c8f2b14c483cbd46ecb6534a33db020e23e0
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502825"
---
# <a name="zcauto-deduce-variable-type"></a>`/Zc:auto` (변수 형식 추론)

**`/Zc:auto`** 컴파일러 옵션을 사용 하면 컴파일러에서 [ `auto` 키워드](../../cpp/auto-cpp.md) 를 사용 하 여 변수를 선언 하는 방법을 알 수 있습니다. 기본 옵션인를 지정 하는 경우 **`/Zc:auto`** 컴파일러는 초기화 식에서 선언 된 변수의 형식을 추론 합니다. 를 지정 하면 **`/Zc:auto-`** 컴파일러가 자동 저장소 클래스에 변수를 할당 합니다.

## <a name="syntax"></a>구문

> **`/Zc:auto`**[**`-`**]

## <a name="remarks"></a>설명

C + + 표준은 키워드의 원래 의미와 수정 된 의미를 정의 합니다 **`auto`** . Visual Studio 2010 이전에는 키워드가 자동 저장소 클래스에서 변수를 선언 합니다. 즉, 로컬 수명을 포함 하는 변수입니다. Visual Studio 2010부터 키워드는 선언의 초기화 식에서 변수의 형식을 추론 합니다. 컴파일러 옵션을 사용 하 여 **`/Zc:auto`** 키워드의 수정 된 의미를 사용 하도록 컴파일러에 지시 **`auto`** 합니다. **`/Zc:auto`** 옵션은 기본적으로 설정 되어 있습니다. [`/permissive-`](permissive-standards-conformance.md)옵션은의 기본 설정을 변경 하지 않습니다 **`/Zc:auto`** .

키워드 사용이 **`auto`** 현재 컴파일러 옵션과 모순 되는 경우 컴파일러에서 적절 한 진단 메시지를 발생 시킵니다 **`/Zc:auto`** . 자세한 내용은 [ `auto` 키워드](../../cpp/auto-cpp.md)를 참조 하세요. Visual C++의 규칙 문제에 대 한 자세한 내용은 [비표준 동작](../../cpp/nonstandard-behavior.md)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **`/Zc:auto`** **`/Zc:auto-`** **추가 옵션:** 창에 또는를 추가 합니다.

## <a name="see-also"></a>참고 항목

[`/Zc` 규칙](zc-conformance.md)<br/>
[`auto` 키워드](../../cpp/auto-cpp.md)
