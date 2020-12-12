---
description: '자세한 정보: 링커 도구 오류 LNK1237'
title: 링커 도구 오류 LNK1237
ms.date: 11/04/2016
f1_keywords:
- LNK1237
helpviewer_keywords:
- LNK1237
ms.assetid: 8722ffa8-096a-4bb0-85f9-f3aa0e10872a
ms.openlocfilehash: ba6a0d23eea4d8d555115950fcd54a5e4f6a8bde
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193984"
---
# <a name="linker-tools-error-lnk1237"></a>링커 도구 오류 LNK1237

코드를 생성 하는 동안 컴파일러가/GL로 컴파일된 ' module ' 모듈에 정의 된 ' symbol ' 기호에 대 한 참조를 도입 했습니다.

코드를 생성 하는 동안 컴파일러는 나중에 정의 된 **/gl** 로 확인 되는 기호를 도입 하면 안 됩니다. `symbol` 는 도입 되었고 나중에 **/gl** 로 컴파일된 정의로 확인 된 기호입니다.

자세한 내용은 [/GL(전체 프로그램 최적화)](../../build/reference/gl-whole-program-optimization.md)을 참조하세요.

LNK1237를 해결 하려면 **/gl** 을 사용 하 여 기호를 컴파일하거나 [/INCLUDE (강제 기호 참조)](../../build/reference/include-force-symbol-references.md) 를 사용 하 여 기호에 대 한 참조를 강제로 실행 하지 마십시오.

## <a name="example"></a>예제

다음 샘플에서는 LNK1237를 생성 합니다. 이 오류를 해결 하려면 LNK1237_a에서 배열을 초기화 하지 않고 link 명령에 **/include: __chkstk** 를 추가 합니다.

```cpp
// LNK1237_a.cpp
int main() {
   char c[5000] = {0};
}
```

```cpp
// LNK1237_b.cpp
// compile with: /GS- /GL /c LNK1237_a.cpp
// processor: x86
// post-build command: (lib LNK1237_b.obj /LTCG & link LNK1237_a.obj LNK1237_b.lib /nodefaultlib /entry:main /LTCG)
extern "C" void _chkstk(size_t s) {}
```
