---
title: 컴파일러 경고 (수준 1) C4165
ms.date: 11/04/2016
f1_keywords:
- C4165
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
ms.openlocfilehash: bb036f7672a074e859d3e19083e256bd80c93578
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80176102"
---
# <a name="compiler-warning-level-1-c4165"></a>컴파일러 경고 (수준 1) C4165

' HRESULT '가 ' bool '로 변환 되 고 있습니다. 원하는 작업을 수행 하 시겠습니까?

[If](../../cpp/if-else-statement-cpp.md) 문에서 hresult를 사용 하는 경우 변수를 hresult로 명시적으로 테스트 하지 않으면 hresult가 [bool](../../cpp/bool-cpp.md) 로 변환 됩니다. 기본적으로 이 경고는 해제되어 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C4165를 생성 합니다.

```cpp
// C4165.cpp
// compile with: /W1
#include <windows.h>
#pragma warning(1:4165)

extern HRESULT hr;
int main() {
   if (hr) {
   // try either of the following ...
   // if (FAILED(hr)) { // C4165 expected
   // if (hr != S_OK) {
   }
}
```
