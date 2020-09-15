---
title: '/smodule: exportHeader (헤더 단위 만들기)'
description: '/Smodule: exportHeader 컴파일러 옵션을 사용 하 여 헤더 이름 또는 지정 된 포함 파일에 대 한 모듈 헤더 단위를 만듭니다.'
ms.date: 09/13/2020
f1_keywords:
- /module:exportHeader
helpviewer_keywords:
- /module:exportHeader
- Create header units
ms.openlocfilehash: f0c0ce1c593df742af77aa36189df1e89de75b6b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079149"
---
# <a name="moduleexportheader-create-header-units"></a>`/module:exportHeader` (헤더 단위 만들기)

컴파일러에 입력 인수에 지정 된 헤더 단위를 만들도록 지시 합니다. 컴파일러는 IFC () 파일에 출력을 생성 합니다 *`.ifc`* .

## <a name="syntax"></a>구문

> **`/module:exportHeader`** *`header-name`* \[...]\
> **`/module:exportHeader`** *`filename`* \[...]

### <a name="arguments"></a>인수

*`header-name`*\
내보낼 헤더 파일입니다. *`header-name`* 인수는 지시문에 대 한 인수와 동일한 형식을 사용 해야 합니다 `#include` .

*`filename`*\
헤더 단위를 만들 헤더 파일에 대 한 상대 또는 절대 경로입니다.

## <a name="remarks"></a>설명

**`/module:exportHeader`** 컴파일러 옵션을 사용 하려면 [`/experimental:module`](experimental-module.md) [/sd: c + + 최신](std-specify-language-standard-version.md) 옵션과 함께 컴파일러 옵션을 사용 하 여 실험적 모듈 지원을 사용 하도록 설정 해야 합니다. 이 옵션은 Visual Studio 2019 버전 16.8부터 사용할 수 있습니다.

한 **`/module:exportHeader`** 컴파일러 옵션은 빌드에 필요한 만큼의 헤더 이름 인수를 지정할 수 있습니다. 별도로 지정할 필요가 없습니다.

기본적으로 컴파일러는 헤더 단위가 컴파일될 때 개체 파일을 생성 하지 않습니다. 개체 파일을 생성 하려면 **`/Fo`** 컴파일러 옵션을 지정 합니다. 자세한 내용은 [ `/Fo` (개체 파일 이름)](fo-object-file-name.md)를 참조 하세요.

컴파일러는 지정 된을 포함 하 여 *`header-name`* 포함 디렉터리 검색 순서에 따라를 확인 합니다. 자세한 내용은 [ `/I` (추가 포함 디렉터리)](i-additional-include-directories.md)를 참조 하세요.

인수는 *`header-name`* 소스에 표시 되는 것과 같은 방식으로 지정 해야 합니다. 인수는 명령줄에서 규칙과 연산자 및에 대 한 따옴표를 구분 합니다 `<` `>` . VS2019 명령 프롬프트를 사용 하는 등의 헤더 단위를 빌드하기 위해 올바르게 이스케이프 된 명령은 `<vector>` 다음과 같습니다.

```cmd
cl ... /experimental:module /module:exportHeader "<vector>"
```

와 같은 로컬 프로젝트 헤더를 빌드하는 것은 `"utils/util.h"` 다음과 같습니다.

```cmd
cl ... /experimental:module /module:exportHeader """util/util.h"""
```

다른 명령줄 프로세서의 따옴표 규칙은 다를 수 있습니다.

형식을 사용 하는 경우 *`header-name`* **`/module:exportHeader`** 보완 옵션을 사용 하는 것이 도움이 될 수 있습니다 **`/module:showResolvedHeader`** . **`/module:showResolvedHeader`** 옵션은 인수를 확인 하는 파일에 대 한 절대 경로를 인쇄 *`header-name`* 합니다.

**`/module:exportHeader`** 는 에서도 여러 입력을 한 번에 처리할 수 있습니다 **`/MP`** . 를 사용 하 여 **`/module:output <directory>`** 각 컴파일에서 별도의 IFC 파일을 만드는 것이 좋습니다.

### <a name="examples"></a>예제

헤더 `"C:\util\util.h"` 및 `"C:\app\app.h"` 를 지정 하면 다음 *`header-name`* 명령을 사용 하 여 인수로 내보낼 수 있습니다.

```cmd
cl /IC:\ /experimental:module /module:exportHeader """util/util.h""" """app/app.h""" /FoC:\obj
```

*`filename`* 다음 명령을 사용 하 여 인수로 내보낼 수 있습니다.

```cmd
cl /IC:\ /experimental:module /module:exportHeader C:\util\util.h C:\app\app.h /FoC:\obj
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운을 **모든 구성**으로 설정 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. **추가 옵션** 속성을 수정 하 여 옵션과 인수를 추가 합니다 *`/module:exportHeader`* . 그런 다음 **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[`/experimental:module` (모듈 지원 사용)](experimental-module.md)\
[`/headerUnit` (헤더 단위 IFC 사용)](headerunit.md)\
[`/module:reference` (명명 된 모듈 (IFC) 사용)](module-reference.md)\
[`/translateInclude` (Include 지시문을 import 지시문으로 변환)](translateinclude.md)
