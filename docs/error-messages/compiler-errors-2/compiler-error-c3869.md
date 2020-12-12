---
description: '자세한 정보: 컴파일러 오류 C3869'
title: 컴파일러 오류 C3869
ms.date: 11/04/2016
f1_keywords:
- C3869
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
ms.openlocfilehash: 8b5bcd59bfeb5407edcfbea6217212dfc44c6643
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222790"
---
# <a name="compiler-error-c3869"></a>컴파일러 오류 C3869

gcnew 제약 조건에 빈 매개 변수 목록 ' () '가 없습니다.

**`gcnew`** 빈 매개 변수 목록을 사용 하지 않고 특수 제약 조건을 지정 했습니다. 자세한 내용은 [제네릭 형식 매개 변수에 대 한 제약 조건 (c + +/cli)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 을 참조 하세요.

## <a name="example"></a>예제

다음 샘플에서는 C3869를 생성 합니다.

```cpp
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```
