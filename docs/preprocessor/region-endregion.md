---
description: pragmaMicrosoft C/c + +에서 지역 및 endregion 지시문에 대해 자세히 알아보세요.
title: 지역 및 endregion pragma
ms.date: 01/22/2021
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragma, region
- pragma, endregion
- endregion pragma
- region pragma
no-loc:
- pragma
ms.openlocfilehash: 68964cd2cab4ff344a8319f970f7ee94be4d378d
ms.sourcegitcommit: a26a66a3cf479e0e827d549a9b850fad99b108d1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/22/2021
ms.locfileid: "98713287"
---
# <a name="region-and-endregion-no-locpragma"></a>`region` 및 `endregion` pragma

`#pragma region` Visual Studio 편집기의 [개요 기능](/visualstudio/ide/outlining) 을 사용할 때 확장 하거나 축소할 수 있는 코드 블록을 지정할 수 있습니다.

## <a name="syntax"></a>구문

> **`#pragma region`***이름*\
> **`#pragma endregion`***설명*

### <a name="parameters"></a>매개 변수

*주석의*\
필드 코드 편집기에 표시 되는 주석입니다.

*이름의*\
필드 영역 이름입니다. 이 이름은 코드 편집기에 표시 됩니다.

## <a name="remarks"></a>설명

`#pragma endregion` 블록의 끝을 표시 `#pragma region` 합니다.

`#pragma region`블록은 지시문으로 종료 해야 합니다 `#pragma endregion` .

## <a name="example"></a>예제

```cpp
// pragma_directives_region.cpp
#pragma region Region_1
void Test() {}
void Test2() {}
void Test3() {}
#pragma endregion Region_1

int main() {}
```

## <a name="see-also"></a>참고 항목

[Pragma 지시문 및 `__pragma` 및 `_Pragma` 키워드](./pragma-directives-and-the-pragma-keyword.md)
