---
title: 컴파일러 오류 C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 7c1a9e4e099fc33dd585e5cdbffa2bbb8ea36987
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755592"
---
# <a name="compiler-error-c3370"></a>컴파일러 오류 C3370

'idl_module name': idl_module이 아직 정의되지 않았습니다.

[idl_module](../../windows/idl-module.md) 을 사용하여 DLL의 진입점을 지정하려면 먼저 `idl_module` 를 사용하여 DLL 이름을 지정해야 합니다.

다음 샘플에서는 C3370을 생성합니다.

```cpp
// C3370.cpp
[module(name=MyLibrary)];
// uncomment the following line to resolve the error
// [idl_module(name="name1", dllname=x.dll)];
[idl_module(name="name1"), entry(100)] // C3370
int f1();

int main()
{
}
```
