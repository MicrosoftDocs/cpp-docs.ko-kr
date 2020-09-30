---
title: /kernel(커널 모드 이진 만들기)
description: Microsoft C/c + + 컴파일러/kernel 옵션은 커널 모드 실행을 위한 프로젝트를 빌드하고 연결 합니다.
ms.date: 09/28/2020
f1_keywords:
- /kernel
- /kernel-
ms.assetid: 6d7fdff0-c3d1-4b78-9367-4da588ce8b05
ms.openlocfilehash: 8a8c02a6f102a52afbc52c154ce215ede3f38f74
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509353"
---
# <a name="kernel-create-kernel-mode-binary"></a>/kernel(커널 모드 이진 만들기)

Windows 커널에서 실행할 수 있는 이진 파일을 만듭니다. 현재 프로젝트의 코드는 커널 모드에서 실행 되는 코드와 관련 된 간단한 c + + 언어 기능 집합을 사용 하 여 컴파일되고 연결 됩니다.

## <a name="syntax"></a>구문

> **`/kernel`**

## <a name="remarks"></a>설명

옵션을 지정 하면 **`/kernel`** 컴파일러와 링커가 커널 모드에서 허용 되는 언어 기능을 조정 하 고 커널 모드 c + +에 고유한 런타임 불안정성을 방지 하기 위해 충분 한 표현 능력이 있는지를 확인 합니다. 커널 모드에서 중단 되는 c + + 언어 기능을 사용 하는 것을 금지 하 여 수행 됩니다. 컴파일러는 잠재적으로 중단 되지만 사용 하지 않도록 설정할 수 없는 c + + 언어 기능에 대 한 경고를 생성 합니다.

**`/kernel`** 옵션은 빌드의 컴파일러 및 링커 단계 모두에 적용 되며 프로젝트 수준에서 설정 됩니다. 스위치를 전달 **`/kernel`** 하 여 링크 한 후에 결과 이진 파일이 Windows 커널로 로드 되도록 컴파일러에 지시 합니다. 컴파일러는 커널에 호환 되는 하위 집합으로 c + + 언어 기능 스펙트럼의 범위를 좁힙니다.

다음 표에서 **`/kernel`** 는가 지정 된 경우 컴파일러 동작의 변경 내용을 보여 줍니다.

| 동작 유형 | **`/kernel`** 행동 |
|--|--|
| C++ 예외 처리 | 사용 안 함. 및 키워드의 모든 **`throw`** 인스턴스 **`try`** 는 컴파일러 오류를 내보냅니다 (예외 사양을 제외 `throw()` ). 는를 제외 하 고 **`/EH`** 과 호환 되는 옵션은 없습니다 **`/kernel`** **`/EH-`** . |
| RTTI | 사용 안 함. **`dynamic_cast`** **`typeid`** 가 정적으로 사용 되지 않는 경우 및 키워드의 모든 인스턴스는 컴파일러 오류를 내보냅니다 **`dynamic_cast`** . |
| `new` 및 `delete` | 또는 연산자를 명시적으로 정의 해야 합니다 `new()` `delete()` . 컴파일러와 런타임에서는 기본 정의를 제공 하지 않습니다. |

옵션을 사용 하면 사용자 지정 호출 규칙, [`/GS`](gs-buffer-security-check.md) 빌드 옵션 및 모든 최적화가 허용 됩니다 **`/kernel`** . 인라인은 컴파일러에서 적용 되는 것 **`/kernel`** 과 같은 의미 체계를 사용 하 여 대부분의 영향을 받지 않습니다. **`__forceinline`** 인라인 한정자가 적용 되도록 하려면 특정 함수가 인라이닝 되지 않는 경우를 알 수 있도록 경고 [C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md) 사용 하도록 설정 해야 합니다 **`__forceinline`** .

`#pragma`이 옵션을 제어 하는 것과 동일한 기능이 없습니다.

컴파일러가 스위치를 전달 하면 **`/kernel`** 명명 된 전처리기 매크로를 다시 지정 하 `_KERNEL_MODE` 고 값 **1**을 갖습니다. 이 매크로를 사용 하 여 실행 환경이 사용자 모드 또는 커널 모드 인지에 따라 코드를 조건부로 컴파일할 수 있습니다. 예를 들어 다음 코드는 `MyNonPagedClass` 커널 모드 실행을 위해 컴파일될 때 클래스가 페이징할 수 없는 메모리 세그먼트에 있도록 지정 합니다.

```cpp
#ifdef _KERNEL_MODE
#define NONPAGESECTION __declspec(code_seg("$kerneltext$"))
#else
#define NONPAGESECTION
#endif

class NONPAGESECTION MyNonPagedClass
{
   // ...
};
```

다음 대상 아키텍처와 옵션의 조합 중 일부는 **`/arch`** 와 함께 사용 될 때 오류를 생성 합니다 **`/kernel`** .

- **`/arch:SSE`**,,, **`/arch:SSE2`** **`/arch:AVX`** 및는 **`/arch:AVX2`** **`/arch:AVX512`** x86에서 지원 되지 않습니다. **`/arch:IA32`** 는 x 86 에서만 지원 됩니다 **`/kernel`** .

- **`/arch:AVX`**, **`/arch:AVX2`** 및 **`/arch:AVX512`** 은 x **`/kernel`** 64의에서 지원 되지 않습니다.

를 사용 하 여 빌드하면 **`/kernel`** **`/kernel`** 링커에 전달 됩니다. 옵션이 링커 동작에 미치는 영향은 다음과 같습니다.

- 증분 링크를 사용할 수 없습니다. 명령줄에를 추가 하 **`/incremental`** 는 경우 링커는이 심각한 오류를 내보냅니다.

   **심각한 오류 LNK1295: '/INCREMENTAL '은 '/KERNEL ' 사양과 호환 되지 않습니다. '/INCREMENTAL ' 없이 링크**

- 링커는 각 개체 파일 (또는 정적 라이브러리의 포함 된 보관 멤버)을 검사 하 여 옵션을 사용 하 여 컴파일 되었는지 여부를 확인 **`/kernel`** 합니다. 이 조건을 충족 하는 인스턴스가 있으면 링커가 성공적으로 연결 되지만 다음 표에 표시 된 것 처럼 경고가 발생할 수 있습니다.

   | 명령 | **`/kernel`** 인스턴스인 | obj가 아닌 **`/kernel`** , MASM obj 또는 cvtres obj | **`/kernel`** 및 비 obj의 조합 **`/kernel`** |
   |--|--|--|--|
   | **`link /kernel`** | 예 | 예 | 예, 경고 LNK4257 |
   | **`link`** | 예 | 예 | 예 |

   **/KERNEL로 컴파일되지 않은 LNK4257 링크 개체 이미지가 실행 되지 않을 수 있습니다.**

**`/kernel`** 옵션과 **`/driver`** 옵션은 독립적으로 작동 합니다. 서로에 게는 영향을 주지 않습니다.

### <a name="to-set-the-kernel-compiler-option-in-visual-studio"></a>Visual Studio에서/kernel 컴파일러 옵션을 설정 하려면

1. 프로젝트에 대한 **속성 페이지** 대화 상자를 엽니다. 자세한 정보는 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조하세요.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 상자에서를 추가 *`/kernel`* 합니다. **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[MSVC 컴파일러 옵션](compiler-options.md)\
[MSVC 컴파일러 명령줄 구문](compiler-command-line-syntax.md)
