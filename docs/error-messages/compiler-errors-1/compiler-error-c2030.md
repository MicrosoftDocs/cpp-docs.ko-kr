---
description: '자세한 정보: 컴파일러 오류 C2030'
title: 컴파일러 오류 C2030
ms.date: 11/04/2016
f1_keywords:
- C2030
helpviewer_keywords:
- C2030
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
ms.openlocfilehash: b29996051a87f050e61c94b4134d046f52be6f09
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175484"
---
# <a name="compiler-error-c2030"></a>컴파일러 오류 C2030

'protected private' 접근성을 가진 소멸자는 'sealed'로 선언된 클래스의 멤버일 수 없습니다.

로 선언 된 Windows 런타임 클래스에는 **`sealed`** protected private 소멸자를 사용할 수 없습니다. sealed 형식에서는 public virtual 및 private non-virtual 소멸자만 허용됩니다. 자세한 내용은 [Ref 클래스 및 구조체](../../cppcx/ref-classes-and-structs-c-cx.md)를 참조 하세요.

이 오류를 해결하려면 소멸자의 접근성을 변경합니다.
