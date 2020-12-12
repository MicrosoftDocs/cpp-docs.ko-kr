---
description: '자세한 정보: 컴파일러 오류 C2834'
title: 컴파일러 오류 C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: 6f74853f264af653988ed77ddb9a9c7935f3c542
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194438"
---
# <a name="compiler-error-c2834"></a>컴파일러 오류 C2834

' operator operator '는 전역적으로 정규화 되어야 합니다.

`new`및 연산자는 상주 하는 `delete` 클래스에 연결 됩니다. 범위 확인은 `new` 다른 클래스에서 또는의 버전을 선택 하는 데 사용할 수 없습니다 `delete` . Or 연산자의 여러 폼을 구현 하려면 `new` `delete` 추가 정식 매개 변수를 사용 하 여 연산자의 버전을 만듭니다.
