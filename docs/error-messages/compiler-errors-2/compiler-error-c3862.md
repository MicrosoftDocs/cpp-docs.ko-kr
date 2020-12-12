---
description: '자세한 정보: 컴파일러 오류 C3862'
title: 컴파일러 오류 C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: b8955a69bcd04c0a40aed8fab722c6c734bfa65b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222894"
---
# <a name="compiler-error-c3862"></a>컴파일러 오류 C3862

> '*function*':/clr: pure 또는/clr: safe를 사용 하 여 관리 되지 않는 함수를 컴파일할 수 없습니다.

## <a name="remarks"></a>설명

**/Clr: pure** 및 **/clr: safe** 컴파일러 옵션은 visual studio 2015에서 더 이상 사용 되지 않으며 visual studio 2017에서는 지원 되지 않습니다.

**/Clr: pure** 또는 **/clr: safe** 를 사용 하는 컴파일은 네이티브 (비관리) 코드가 없는 이미지인 MSIL 전용 이미지를 생성 합니다.  따라서 `unmanaged` **/clr: pure** 또는 **/clr: safe** 컴파일에서 pragma를 사용할 수 없습니다.

자세한 내용은 [/clr (공용 언어 런타임 컴파일)](../../build/reference/clr-common-language-runtime-compilation.md) 및 [관리 되는 관리 되지 않는](../../preprocessor/managed-unmanaged.md)를 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3862를 생성 합니다.

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```
