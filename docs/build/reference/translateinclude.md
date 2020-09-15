---
title: /translateInclude (include 지시문을 import 지시문으로 변환)
description: '/TranslateInclude 컴파일러 옵션을 사용 하 여 가져올 수 있는 헤더 이름에 대 한 #include 지시문을 import header name 지시어로 변환 합니다.'
ms.date: 09/13/2020
f1_keywords:
- /translateInclude
helpviewer_keywords:
- /translateInclude
- Translate include directives into import directives
ms.openlocfilehash: 0050f2cb117e48d69cf97a587ef128b9b45790af
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079148"
---
# <a name="translateinclude-translate-include-directives-into-import-directives"></a>`/translateInclude` (Include 지시문을 import 지시문으로 변환)

`#include`텍스트 포함을 사용 하는 대신, 가져올 수 있는 헤더 이름에 대 한 지시문을 지시문으로 변환 하도록 컴파일러에 지시 `import header-name;` 합니다.

## <a name="syntax"></a>구문

> **`/translateInclude`**

## <a name="remarks"></a>설명

**`/translateInclude`** 컴파일러 옵션을 사용 하려면 [`/experimental:module`](experimental-module.md) [/sd: c + + 최신](std-specify-language-standard-version.md) 옵션과 함께 컴파일러 옵션을 사용 하 여 실험적 모듈 지원을 사용 하도록 설정 해야 합니다. 이 옵션은 Visual Studio 2019 버전 16.8부터 사용할 수 있습니다.

**`/translateInclude`** 이 옵션은 다음과 같은 변환을 효과적으로 수행 합니다. 여기서 예제는 `<vector>` 가져올 수 있는 헤더 단위입니다.

```cpp
#include <vector>
```

컴파일러는이 지시문을 다음과 같이 바꿉니다.

```cpp
import <vector> ;
```

MSVC에서 가져올 수 있는 헤더 단위는 참조에 의해 이름이 지정 된 것입니다 **`/headerUnit`** . 자세한 내용은 [ `/headerUnit` (헤더 단위 IFC 사용)](headerunit.md)을 참조 하세요.

### <a name="examples"></a>예제

다음 표에 나열 된 두 헤더 파일 및 해당 헤더 단위를 참조 하는 프로젝트가 제공 됩니다.

| 헤더 파일 | IFC 파일 |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

*`.cpp`* 헤더를 포함 하는 소스 파일,

```cpp
#include "utils/util.h"
#include "app/app.h"

int main() { }
```

**`/translateInclude`** 옵션을 사용 하면 컴파일러가 헤더를 다시 컴파일하는 대신 헤더 단위를 가져올 수 있습니다. 다음은 및의 include 지시문을 *`util.h`* *`app.h`* 헤더 단위의 가져오기로 변환 하는 예제 명령줄입니다.

```CMD
cl /IC:\ /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운을 **모든 구성**으로 설정 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 옵션을 추가 하려면 **추가 옵션** 속성을 수정 합니다 *`/translateInclude`* . 그런 다음 **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[`/experimental:module` (모듈 지원 사용)](experimental-module.md)\
[ `/headerUnit` (헤더 단위 IFC 사용)](headerunit.md). \
[`/module:exportHeader` (헤더 단위 만들기)](module-exportheader.md)\
[`/module:reference` (명명 된 모듈 (IFC) 사용)](module-reference.md)
