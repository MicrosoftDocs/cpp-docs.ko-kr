---
title: /Zc:externConstexpr(extern constexpr 변수 사용)
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: db5a8892bcc11538c3ff883a0e9a3a27db0ee14f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502798"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>`/Zc:externConstexpr` (Extern constexpr 변수 사용)

**`/Zc:externConstexpr`** 컴파일러 옵션은 c + + 표준을 준수 하 고 변수에 대 한 외부 링크를 허용 하도록 컴파일러에 지시 합니다 **`constexpr`** . 기본적으로 Visual Studio는 **`constexpr`** 키워드를 지정 하는 경우에도 항상 변수 내부 링크를 제공 **`extern`** 합니다.

## <a name="syntax"></a>구문

> **`/Zc:externConstexpr`**[**`-`**]

## <a name="remarks"></a>설명

**`/Zc:externConstexpr`** 컴파일러 옵션을 사용 하면 컴파일러가를 사용 하 여 선언 된 변수에 외부 링크를 적용 합니다 `extern constexpr` . 이전 버전의 Visual Studio에서는 기본적으로 또는 **`/Zc:externConstexpr-`** 이 지정 된 경우 키워드가 사용 되는 경우에도 Visual studio에서 변수에 내부 링크를 적용 **`constexpr`** **`extern`** 합니다. **`/Zc:externConstexpr`** 이 옵션은 Visual Studio 2017 업데이트 15.6부터 사용할 수 있습니다. 및는 기본적으로 해제 되어 있습니다. [`/permissive-`](permissive-standards-conformance.md)옵션은 사용할 수 없습니다 **`/Zc:externConstexpr`** .

헤더 파일에 선언 된 변수가 포함 되어 있으면 `extern constexpr` [`__declspec(selectany)`](../../cpp/selectany.md) 중복 된 선언을 연결 된 이진의 단일 인스턴스로 병합 하기 위해이 파일을 표시 해야 합니다. 그렇지 않으면 단일 정의 규칙의 위반에 대 한 링커 오류 (예: LNK2005)가 표시 될 수 있습니다.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Visual Studio에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **`/Zc:externConstexpr`** **`/Zc:externConstexpr-`** **추가 옵션:** 창에 또는를 추가 합니다.

## <a name="see-also"></a>참고 항목

[`/Zc` 규칙](zc-conformance.md)<br/>
[`auto` 키워드](../../cpp/auto-cpp.md)
