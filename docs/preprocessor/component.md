---
title: 구성 요소 pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.component
- component_CPP
helpviewer_keywords:
- component pragma
- pragmas, component
ms.assetid: 7b66355e-3201-4c14-8190-f4a2a81a604a
ms.openlocfilehash: 73b308fdc426be9b403b808d4e638b4f5c1e9149
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040732"
---
# <a name="component-pragma"></a>구성 요소 pragma

소스 파일 내에서 찾아보기 정보 또는 종속성 정보의 컬렉션을 제어 합니다.

## <a name="syntax"></a>구문

> **#pragma 구성 요소 (browser,** { **on** \| **off** } \[ **,** **참조** \[ **,** *이름* ]] **)** \
> **#pragma 구성 요소 (minrebuild,** { **on** \| **off** } **)** \
> **#pragma 구성 요소 (mintypeinfo,** { **on** \| **off** } **)**

## <a name="remarks"></a>설명

### <a name="browser"></a>브라우저

수집을 설정하거나 해제할 수 있으며 정보가 수집됨에 따라 특정 이름을 무시하도록 지정할 수 있습니다.

설정 또는 해제를 사용하면 pragma 정방향에서의 찾아보기 정보 수집을 제어합니다. 다음은 그 예입니다. 

```cpp
#pragma component(browser, off)
```

컴파일러에서 찾아보기 정보 수집을 중지합니다.

> [!NOTE]
> 이 pragma를 사용 하 여 찾아보기 정보 수집을 켜려면 [먼저 찾아보기 정보를 사용 하도록 설정 해야](../build/reference/building-browse-information-files-overview.md)합니다.

**References** 옵션은 *name* 인수를 사용 하거나 사용 하지 않고 사용할 수 있습니다. *이름* 없이 **참조** 를 사용 하면 참조 수집을 설정 하거나 해제 합니다. 그러나 다른 찾아보기 정보는 계속 수집 됩니다. 다음은 그 예입니다. 

```cpp
#pragma component(browser, off, references)
```

컴파일러에서 참조 정보 수집을 중지합니다.

*이름* 및 **off** 를 사용 하 여 **참조** 를 사용 하면 *이름* 에 대 한 참조가 찾아보기 정보 창에 나타나지 않습니다. 관심 없는 이름 및 형식을 무시하고 찾아보기 정보 파일의 크기를 줄이려면 이 구문을 사용합니다. 다음은 그 예입니다. 

```cpp
#pragma component(browser, off, references, DWORD)
```

해당 지점 앞에서 DWORD에 대 한 참조를 무시 합니다. 다음 **을**사용 하 여 DWORD에 대 한 참조 수집을 다시 설정할 수 있습니다.

```cpp
#pragma component(browser, on, references, DWORD)
```

*이름*에 대 한 참조 수집을 다시 시작 하는 유일한 방법입니다. 해제 한 모든 *이름을* 명시적으로 설정 해야 합니다.

전처리기에서 *이름* 확장을 방지 하려면 (예: NULL을 0으로 확장) 따옴표를 앞에 추가 합니다.

```cpp
#pragma component(browser, off, references, "NULL")
```

### <a name="minimal-rebuild"></a>최소 다시 빌드

사용 되지 않는 [/gm (최소 다시 빌드 사용)](../build/reference/gm-enable-minimal-rebuild.md) 기능을 사용 하려면 컴파일러가 디스크 공간을 차지 하는 c + + 클래스 종속성 정보를 만들고 저장 해야 합니다. 디스크 공간을 절약 하기 위해 변경 `#pragma component( minrebuild, off )` 되지 않은 헤더 파일에서 종속성 정보를 수집 하지 않아도 될 때마다를 사용할 수 있습니다. 변경 되지 않은 `#pragma component( minrebuild, on )` 클래스 뒤에를 삽입 하 여 종속성 컬렉션을 다시 설정 합니다.

### <a name="reduce-type-information"></a>유형 정보 줄이기

`mintypeinfo`옵션은 지정 된 영역에 대 한 디버깅 정보를 줄입니다. 이 정보의 양이 상당하므로 .pdb 및 .obj 파일에 영향을 줍니다. mintypeinfo 영역에서 클래스 및 구조체를 디버깅할 수 없습니다. mintypeinfo 옵션을 사용하면 다음 경고가 발생하지 않도록 하는 데 도움이 될 수 있습니다.

```cmd
LINK : warning LNK4018: too many type indexes in PDB "filename", discarding subsequent type information
```

자세한 내용은 [/gm (최소 다시 빌드 사용)](../build/reference/gm-enable-minimal-rebuild.md)  컴파일러 옵션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 __pragma 키워드](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
