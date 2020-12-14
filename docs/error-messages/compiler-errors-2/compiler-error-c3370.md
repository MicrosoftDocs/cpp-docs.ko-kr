---
description: '자세한 정보: 컴파일러 오류 C3370'
title: 컴파일러 오류 C3370
ms.date: 11/04/2016
f1_keywords:
- C3370
helpviewer_keywords:
- C3370
ms.assetid: ee6d4c85-78fc-42b2-836e-5cc491a3b2ba
ms.openlocfilehash: 9c34636f91035177e7408dfd4b3bdaaed0fe84c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97245267"
---
# <a name="compiler-error-c3370"></a>컴파일러 오류 C3370

'idl_module name': idl_module이 아직 정의되지 않았습니다.

[idl_module](../../windows/attributes/idl-module.md) 을 사용하여 DLL의 진입점을 지정하려면 먼저 `idl_module` 를 사용하여 DLL 이름을 지정해야 합니다.

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
