---
description: '자세한 정보: 컴파일러 오류 C3610'
title: 컴파일러 오류 C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 0fca8f57fcdf2e935620118092708ba1c94f5ec0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97223141"
---
# <a name="compiler-error-c3610"></a>컴파일러 오류 C3610

' valuetype ': 값 형식은 ' method ' 메서드를 호출 하기 전에 ' boxed ' 여야 합니다.

기본적으로 값 형식은 관리 되는 힙에 있지 않습니다. 등의 .NET 런타임 클래스에서 메서드를 호출 `Object` 하려면 먼저 값 형식을 관리 되는 힙으로 이동 해야 합니다.

C3610는 사용 되지 않는 컴파일러 옵션 **/clr: oldSyntax** 를 사용 하는 경우에만 연결할 수 있습니다.
