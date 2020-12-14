---
description: '자세한 정보: 컴파일러 오류 C3453'
title: 컴파일러 오류 C3453
ms.date: 11/04/2016
f1_keywords:
- C3453
helpviewer_keywords:
- C3453
ms.assetid: dbefdbcf-f697-4239-b7a5-1d99b85e9e7f
ms.openlocfilehash: 2ff1c246dc66d60266f0fc44e134db3ab21605df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315974"
---
# <a name="compiler-error-c3453"></a>컴파일러 오류 C3453

'attribute': 'assembly' 한정자가 일치하지 않아 특성이 적용되지 않았습니다.

어셈블리 또는 모듈 수준 특성만 독립 실행형 명령으로 지정할 수 있습니다.

## <a name="example"></a>예제

다음 샘플에서는 C3453을 생성합니다.

```cpp
// C3453.cpp
// compile with: /clr /c
[assembly:System::CLSCompliant(true)]   // C3453
// try the following line instead
// [assembly:System::CLSCompliant(true)];
ref class X {};
```
