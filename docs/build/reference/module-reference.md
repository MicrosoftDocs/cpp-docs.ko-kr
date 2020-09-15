---
title: '/smodule: reference (명명 된 모듈 IFC 사용)'
description: '/Smodule: reference 컴파일러 옵션을 사용 하 여 헤더 이름 또는 지정 된 포함 파일에 대 한 모듈 헤더 단위를 만듭니다.'
ms.date: 09/13/2020
f1_keywords:
- /module:reference
helpviewer_keywords:
- /module:reference
- Use named module IFC
ms.openlocfilehash: 5f40f6b700c38f3238cc7a621313621085fbc289
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079153"
---
# <a name="modulereference-use-named-module-ifc"></a>`/module:reference` (명명 된 모듈 (IFC) 사용)

현재 컴파일에 기존 IFC ()를 사용 하도록 컴파일러에 지시 *`.ifc`* 합니다.

## <a name="syntax"></a>구문

> **`/module:reference`** *`module-name=filename`*\
> **`/module:reference`** *`filename`*

### <a name="arguments"></a>인수

*`filename`*\
*IFC 데이터*, 미리 작성 된 모듈 정보를 포함 하는 파일의 이름입니다. 둘 이상의 모듈을 가져오려면 **`/module:reference`** 각 파일에 대해 별도의 옵션을 포함 합니다.

*`module-name`*\
내보낸 기본 모듈 인터페이스 단위 이름 또는 전체 모듈 파티션 이름의 유효한 이름입니다.

## <a name="remarks"></a>설명

**`/module:reference`** 컴파일러 옵션을 사용 하려면 [`/experimental:module`](experimental-module.md) [/sd: c + + 최신](std-specify-language-standard-version.md) 옵션과 함께 컴파일러 옵션을 사용 하 여 실험적 모듈 지원을 사용 하도록 설정 해야 합니다. 이 옵션은 Visual Studio 2019 버전 16.8부터 사용할 수 있습니다.

**`/module:reference`** 인수가 없이 인 경우 *`filename`* *`module-name`* 파일은 런타임에 열려 있어 *`filename`* 인수 이름이 특정 가져오기 인지 확인 합니다. 이로 인해 인수가 많은 시나리오에서 런타임 성능이 저하 될 수 있습니다 **`/module:reference`** .

는 *`module-name`* 유효한 주 모듈 인터페이스 단위 이름 또는 전체 모듈 파티션 이름 이어야 합니다. 기본 모듈 인터페이스 이름의 예는 다음과 같습니다.

- `M`
- `M.N.O`
- `MyModule`
- `my_module`

전체 모듈 파티션 이름의 예는 다음과 같습니다.

- `M:P`
- `M.N.O:P.Q`
- `MyModule:Algorithms`
- `my_module:algorithms`

를 사용 하 여 모듈 참조를 만드는 경우 *`module-name`* 컴파일러에서 해당 이름의 가져오기가 발견 되 면 명령줄의 다른 모듈이 검색 되지 않습니다. 예를 들어, 다음 명령줄이 제공 됩니다.

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m=n.ifc
```

위의 경우 컴파일러에서 확인할 경우 `import m;` *`m.ifc`* 검색 되지 않습니다.

### <a name="examples"></a>예제

다음 표에 나열 된 세 개의 모듈이 제공 됩니다.

| 모듈 | IFC 파일 |
|--|--|
| *`M`* | *`m.ifc`* |
| *`M:Part1`* | *`m-part1.ifc`* |
| *`Core.Networking`* | *`Networking.ifc`* |

인수를 사용 하는 참조 옵션은 *`filename`* 다음과 같습니다.

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m-part.ifc /module:reference Networking.ifc
```

를 사용 하는 참조 옵션은 *`module-name=filename`* 다음과 같습니다.

```cmd
cl ... /experimental:module /module:reference m=m.ifc /module:reference M:Part1=m-part.ifc /module:reference Core.Networking=Networking.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성** 드롭다운을 **모든 구성**으로 설정 합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 옵션 및 해당 인수를 추가 하려면 **추가 옵션** 속성을 수정 합니다 *`/module:reference`* . 그런 다음 **확인** 또는 **적용** 을 선택 하 여 변경 내용을 저장 합니다.

## <a name="see-also"></a>참고 항목

[`/experimental:module` (모듈 지원 사용)](experimental-module.md)\
[`/headerUnit` (헤더 단위 IFC 사용)](headerunit.md)\
[`/module:exportHeader` (헤더 단위 만들기)](module-exportheader.md)\
[`/translateInclude` (Include 지시문을 import 지시문으로 변환)](translateinclude.md)
