---
description: '자세한 정보: 링커 도구 오류 LNK2031'
title: 링커 도구 오류 LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 3d955f106f569f91df9640bacfcca4df511ffd95
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97275674"
---
# <a name="linker-tools-error-lnk2031"></a>링커 도구 오류 LNK2031

> "*function_declaration*" *decorated_name*;에 대해 p/invoke를 생성할 수 없습니다. 메타 데이터에 누락 된 호출 규칙이 있습니다.

## <a name="remarks"></a>설명

네이티브 함수를 순수 이미지로 가져오는 경우 네이티브 컴파일 및 순수 컴파일 간에 암시적 호출 규칙이 서로 다르다는 점에 주의 해야 합니다. 순수 이미지에 대 한 자세한 내용은 [순수형 및 안정형 코드 (c + +/cli)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)를 참조 하세요.

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

## <a name="examples"></a>예제

이 코드 샘플에서는 호출 규칙이 암시적으로 [__cdecl](../../cpp/cdecl.md)있는 내보낸 네이티브 함수를 사용 하 여 구성 요소를 생성 합니다.

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

다음 샘플에서는 네이티브 함수를 사용 하는 순수 클라이언트를 만듭니다. 그러나 **/clr: pure** 의 호출 규칙은 [__clrcall](../../cpp/clrcall.md)입니다. 다음 샘플에서는 LNK2031를 생성 합니다.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

다음 샘플에서는 순수 이미지에서 네이티브 함수를 사용 하는 방법을 보여 줍니다. 명시적 **`__cdecl`** 호출 규칙 지정자를 확인 합니다.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```
