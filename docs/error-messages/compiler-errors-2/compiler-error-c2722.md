---
description: '자세한 정보: 컴파일러 오류 C2722'
title: 컴파일러 오류 C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 10d1af61f0b82621469f2d6e91d97296c59f22cf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155594"
---
# <a name="compiler-error-c2722"></a>컴파일러 오류 C2722

':: operator ': 다음 연산자 명령이 잘못 되었습니다. ' operator operator ' 사용

`operator`문이 또는를 다시 정의 `::new` `::delete` 합니다. `new`및 `delete` 연산자는 전역 이므로 범위 확인 연산자 ()는 `::` 의미가 없습니다. `::` 연산자를 제거합니다.
