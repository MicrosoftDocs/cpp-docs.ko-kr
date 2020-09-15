---
title: /headerUnit (header unit IFC 사용)
description: /HeaderUnit 컴파일러 옵션을 사용 하 여 현재 컴파일에서 가져올 기존 IFC 헤더 단위를 지정 합니다.
ms.date: 09/13/2020
f1_keywords:
- /headerUnit
helpviewer_keywords:
- /headerUnit
- Use header unit IFC
ms.openlocfilehash: 2734df728b188dcfbbe5f475cfc67715a070975d
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079157"
---
# <a name="headerunit-use-header-unit-ifc"></a>`/headerUnit` (헤더 단위 IFC 사용)

`#include`텍스트 포함을 사용 하는 대신, 가져올 수 있는 헤더 이름에 대 한 지시문을 지시문으로 변환 하도록 컴파일러에 지시 `import header-name;` 합니다.

## <a name="syntax"></a>구문

> **`/headerUnit`** *`header-filename`*=*`ifc-filename`*

### <a name="arguments"></a>인수

*`header-filename`*\
컴파일러가를 확인 하는 파일의 이름입니다 `header-name` . 에서 `import header-name ;` 컴파일러가 `header-name` 디스크의 일부 파일로 확인 됩니다. 을 사용 *`header-filename`* 하 여 해당 파일을 지정 합니다. 일치 하면 컴파일러가를 가져오기 위해에 의해 이름이 지정 된 해당 IFC를 엽니다 *`ifc-filename`* .

*`ifc-filename`*\
*IFC 데이터*, 미리 작성 된 모듈 정보를 포함 하는 파일의 이름입니다. 둘 이상의 헤더 단위를 가져오려면 **`/headerUnit`** 각 파일에 대해 별도의 옵션을 포함 합니다.

## <a name="remarks"></a>설명

**`/headerUnit`** 컴파일러 옵션을 사용 하려면 [`/experimental:module`](experimental-module.md) [/sd: c + + 최신](std-specify-language-standard-version.md) 옵션과 함께 컴파일러 옵션을 사용 하 여 실험적 모듈 지원을 사용 하도록 설정 해야 합니다. 이 옵션은 Visual Studio 2019 버전 16.8부터 사용할 수 있습니다.

컴파일러는 단일 *`header-name`* 를 여러 IFC 파일에 매핑할 수 없습니다. 단일 IFC에 여러 인수를 매핑하는 것 *`header-name`* 이 가능 하지만 권장 하지 않습니다. IFC의 내용은로 지정 된 헤더만 된 것 처럼 가져옵니다 *`header-name`* .

### <a name="examples"></a>예제

다음 표에 나열 된 두 헤더 파일 및 해당 헤더 단위를 참조 하는 프로젝트가 제공 됩니다.

| 헤더 파일 | IFC 파일 |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

이러한 특정 헤더 파일의 헤더 단위를 참조 하는 컴파일러 옵션은 다음 예제 처럼 보일 수 있습니다.

```CMD
cl ... /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운을 **모든 구성**으로 설정 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 옵션 및 인수를 추가 하려면 **추가 옵션** 속성을 수정 합니다 *`/headerUnit`* . 그런 다음 **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[`/experimental:module` (모듈 지원 사용)](experimental-module.md)\
[`/module:exportHeader` (헤더 단위 만들기)](module-exportheader.md)\
[`/module:reference` (명명 된 모듈 (IFC) 사용)](module-reference.md)\
[`/translateInclude` (Include 지시문을 import 지시문으로 변환)](translateinclude.md)\
