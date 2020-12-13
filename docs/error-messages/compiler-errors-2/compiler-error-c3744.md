---
description: '자세한 정보: 컴파일러 오류 C3744'
title: 컴파일러 오류 C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 6d8e9184db37f65fd73a85aaaa6c350303802216
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340231"
---
# <a name="compiler-error-c3744"></a>컴파일러 오류 C3744

__unhook는 관리 되는 이벤트에 대해 세 개 이상의 인수가 있어야 합니다.

[`__unhook`](../../cpp/unhook.md)함수는 Managed Extensions for C++에 대해 컴파일된 프로그램에서 사용 되는 경우 세 개의 매개 변수를 사용 해야 합니다.

**`__hook`** 및 **`__unhook`** 는 프로그래밍과 호환 되지 않습니다 **`/clr`** . 대신 + = 및-= 연산자를 사용 합니다.

C3744는 사용 되지 않는 컴파일러 옵션을 사용 하 여 연결할 수 **`/clr:oldSyntax`** 있습니다.
