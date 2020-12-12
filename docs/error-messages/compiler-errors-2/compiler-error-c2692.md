---
description: '자세한 정보: 컴파일러 오류 C2692'
title: 컴파일러 오류 C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 5a9666bf437d65c54d0cb8c460054b2b3ebd0b55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326686"
---
# <a name="compiler-error-c2692"></a>컴파일러 오류 C2692

' function_name ': C 컴파일러에 '/clr ' 옵션으로 완전히 프로토타입화 된 함수가 필요 합니다.

.NET 관리 코드를 컴파일하는 경우 C 컴파일러에는 ANSI 함수 선언이 필요 합니다. 또한 함수에서 매개 변수를 사용 하지 않는 경우 명시적으로를 **`void`** 매개 변수 형식으로 선언 해야 합니다.
