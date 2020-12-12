---
description: '자세한 정보: 식 계산기 오류 CXX0030'
title: 식 계산기 오류 CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: d9679d260ce81c2cb9bb8be4c082ffe8c1cfc6a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97237429"
---
# <a name="expression-evaluator-error-cxx0030"></a>식 계산기 오류 CXX0030

식이 evaluatable 되지 않음

디버거의 식 계산기에서 작성 된 식의 값을 가져올 수 없습니다. 한 가지 가능한 원인은 식이 프로그램의 주소 공간을 벗어난 메모리를 참조 하는 것입니다 (null 포인터를 역참조 하는 한 가지 예). Windows에서는 프로그램의 주소 공간 밖에 있는 메모리에 대 한 액세스를 허용 하지 않습니다.

괄호를 사용 하 여 식을 다시 작성 하 여 계산 순서를 제어할 수 있습니다.

이 오류는 CAN0030와 동일 합니다.
