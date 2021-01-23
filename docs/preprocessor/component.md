---
description: pragmaMicrosoft C/c + +의 구성 요소 지시문에 대해 자세히 알아보세요.
title: 구성 요소 pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragma, component
no-loc:
- pragma
ms.openlocfilehash: 68a4117439390c6ec978ae9d766efb395a4ceaa4
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98712949"
---
# <a name="component-no-locpragma"></a>`component` pragma

소스 파일 내에서 찾아보기 정보 또는 종속성 정보의 컬렉션을 제어 합니다.

## <a name="syntax"></a>구문

> **`#pragma component( browser,`** { **`on`** \| **`off`** } \[ **`,`** **`references`** \[ **`,`** *name* ]] **`)`** \
> **`#pragma component( minrebuild,`** { **`on`** \| **`off`** } **`)`** \
> **`#pragma component( mintypeinfo,`** { **`on`** \| **`off`** } **`)`**

## <a name="remarks"></a>설명

### <a name="browser"></a>브라우저

수집을 설정하거나 해제할 수 있으며 정보가 수집됨에 따라 특정 이름을 무시하도록 지정할 수 있습니다.

On 또는 off를 사용 하면 앞에서의 찾아보기 정보 컬렉션을 제어 합니다 pragma . 예:

```cpp
#pragma component(browser, off)
```

컴파일러에서 찾아보기 정보 수집을 중지합니다.

> [!NOTE]
> 이를 사용 하 여 찾아보기 정보 수집을 설정 pragma 하려면 [먼저 찾아보기 정보를 사용 하도록 설정 해야](../build/reference/building-browse-information-files-overview.md)합니다.

**`references`** 옵션은 *name* 인수를 사용 하거나 사용 하지 않고 사용할 수 있습니다. **`references`** *이름* 없이를 사용 하면 참조 수집을 설정 하거나 해제 합니다. 그러나 다른 찾아보기 정보는 계속 수집 됩니다. 예:

```cpp
#pragma component(browser, off, references)
```

컴파일러에서 참조 정보 수집을 중지합니다.

With name을 사용 하 여 **`references`**  **`off`** *이름* 에 대 한 참조가 찾아보기 정보 창에 나타나지 않도록 합니다. 관심 없는 이름 및 형식을 무시하고 찾아보기 정보 파일의 크기를 줄이려면 이 구문을 사용합니다. 예:

```cpp
#pragma component(browser, off, references, DWORD)
```

해당 지점 앞에서 DWORD에 대 한 참조를 무시 합니다. 다음을 사용 하 여 DWORD에 대 한 참조 수집을 다시 설정할 수 있습니다 **`on`** .

```cpp
#pragma component(browser, on, references, DWORD)
```

*이름* 에 대 한 참조 수집을 다시 시작 하는 유일한 방법입니다. 해제 한 모든 *이름을* 명시적으로 설정 해야 합니다.

전처리기에서 *이름* 확장을 방지 하려면 (예: NULL을 0으로 확장) 따옴표를 앞에 추가 합니다.

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>최소 다시 빌드

사용 되지 않는 [ `/Gm` (최소 다시 빌드 사용)](../build/reference/gm-enable-minimal-rebuild.md) 기능을 사용 하려면 컴파일러가 디스크 공간을 차지 하는 c + + 클래스 종속성 정보를 만들고 저장 해야 합니다. 디스크 공간을 절약 하기 위해 변경 `#pragma component( minrebuild, off )` 되지 않은 헤더 파일에서 종속성 정보를 수집 하지 않아도 될 때마다를 사용할 수 있습니다. 변경 되지 않은 `#pragma component( minrebuild, on )` 클래스 뒤에를 삽입 하 여 종속성 컬렉션을 다시 설정 합니다.

### <a name="reduce-type-information"></a>유형 정보 줄이기

**`mintypeinfo`** 옵션은 지정 된 영역에 대 한 디버깅 정보를 줄입니다. 이 정보의 양이 상당하므로 .pdb 및 .obj 파일에 영향을 줍니다. 영역의 클래스와 구조체는 디버그할 수 없습니다 **`mintypeinfo`** . 옵션을 사용 하면 **`mintypeinfo`** 다음 경고를 방지 하는 데 도움이 될 수 있습니다.

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

자세한 내용은 [ `/Gm` (최소 다시 빌드 사용)](../build/reference/gm-enable-minimal-rebuild.md) 컴파일러 옵션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
