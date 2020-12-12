---
description: '자세한 정보: 링커 도구 오류 LNK1312'
title: 링커 도구 오류 LNK1312
ms.date: 11/04/2016
f1_keywords:
- LNK1312
helpviewer_keywords:
- LNK1312
ms.assetid: 48284abb-d849-43fc-ab53-45aded14fd8a
ms.openlocfilehash: d861b6976f9b065e3a693e916164879a3311d3db
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193632"
---
# <a name="linker-tools-error-lnk1312"></a>링커 도구 오류 LNK1312

잘못 되었거나 손상 된 파일: 어셈블리를 가져올 수 없습니다.

어셈블리를 빌드할 때 **/clr** 로 컴파일된 모듈이 나 어셈블리가 아닌 파일은 **/ASSEMBLYMODULE** 링커 옵션으로 전달 되었습니다.  **/ASSEMBLYMODULE** 에 개체 파일을 전달한 경우 **/ASSEMBLYMODULE** 대신 링커에 직접 개체를 전달 하면 됩니다.

## <a name="examples"></a>예제

다음 샘플에서는 .obj 파일을 만들었습니다.

```cpp
// LNK1312.cpp
// compile with: /clr /LD
public ref class A {
public:
   int i;
};
```

다음 샘플에서는 LNK1312를 생성 합니다.

```cpp
// LNK1312_b.cpp
// compile with: /clr /LD /link /assemblymodule:LNK1312.obj
// LNK1312 error expected
public ref class M {};
```
