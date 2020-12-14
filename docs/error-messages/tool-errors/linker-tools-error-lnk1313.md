---
description: '자세한 정보: 링커 도구 오류 LNK1313'
title: 링커 도구 오류 LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: 1c10038def9a448645e80ae10fc47d4372769b58
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97310727"
---
# <a name="linker-tools-error-lnk1313"></a>링커 도구 오류 LNK1313

> ijw/native 모듈이 발견되었습니다. 순수 모듈에 링크할 수 없습니다.

## <a name="remarks"></a>설명

Visual C++의 현재 버전에서는 **/clr: pure** 로 컴파일된 .obj 파일과 네이티브 또는 혼합 된 관리/네이티브 .obj 파일의 연결을 지원 하지 않습니다.

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

## <a name="examples"></a>예제

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

다음 샘플에서는 LNK1313을 생성합니다.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
