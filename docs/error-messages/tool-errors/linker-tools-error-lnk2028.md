---
title: 링커 도구 오류 LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: 29aaed167f750186d956589e9daa0d21c441149e
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90684199"
---
# <a name="linker-tools-error-lnk2028"></a>링커 도구 오류 LNK2028

"*function_containing_function_call*" 함수 (*decorated_name*)에서 참조 되는 "*exported_function*" (*decorated_name*)

## <a name="remarks"></a>설명

네이티브 함수를 순수 이미지로 가져오는 경우 네이티브 컴파일 및 순수 컴파일 간에 암시적 호출 규칙이 서로 다르다는 점에 주의 해야 합니다.

**/Clr: pure** 컴파일러 옵션은 visual studio 2015에서는 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

## <a name="examples"></a>예제

이 코드 샘플에서는 호출 규칙이 암시적으로 [__cdecl](../../cpp/cdecl.md)있는 내보낸 네이티브 함수를 사용 하 여 구성 요소를 생성 합니다.

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

다음 샘플에서는 네이티브 함수를 사용 하는 순수 클라이언트를 만듭니다. 그러나 **/clr: pure** 의 호출 규칙은 [__clrcall](../../cpp/clrcall.md)입니다. 다음 샘플에서는 LNK2028를 생성 합니다.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
