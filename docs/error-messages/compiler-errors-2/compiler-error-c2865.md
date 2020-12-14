---
description: '자세한 정보: 컴파일러 오류 C2865'
title: 컴파일러 오류 C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 0c57fdb120eb147b3877cc834e142ab92f147aaa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220749"
---
# <a name="compiler-error-c2865"></a>컴파일러 오류 C2865

' function ': handle_or_pointer에 대 한 비교가 잘못 되었습니다.

동일한 개체 (= =) 또는 다른 개체 (! =)를 참조 하는지 여부를 확인 하기 위해 [클래스와 구조체](../../extensions/classes-and-structs-cpp-component-extensions.md) 또는 관리 되는 참조 형식에 대 한 참조를 비교할 수 있습니다.

.NET 런타임에서 관리 되는 개체를 언제 든 지 이동 하 여 테스트 결과를 변경할 수 있기 때문에 순서를 비교할 수 없습니다.
