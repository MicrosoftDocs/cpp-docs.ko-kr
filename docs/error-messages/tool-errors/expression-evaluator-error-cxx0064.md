---
description: '자세한 정보: 식 계산기 오류 CXX0064'
title: 식 계산기 오류 CXX0064
ms.date: 11/04/2016
f1_keywords:
- CXX0064
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
ms.openlocfilehash: 58356a48fc52ee479c92cf5d65494763c3fc4adb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173196"
---
# <a name="expression-evaluator-error-cxx0064"></a>식 계산기 오류 CXX0064

바인딩된 가상 멤버 함수에는 중단점을 설정할 수 없습니다.

다음과 같이 개체에 대 한 포인터를 통해 가상 멤버 함수에 중단점을 설정 했습니다.

```
pClass->vfunc( int );
```

클래스를 입력 하 여 가상 함수에 중단점을 설정할 수 있습니다. 예를 들면 다음과 같습니다.

```
Class::vfunc( int );
```

이 오류는 CAN0064와 동일 합니다.
