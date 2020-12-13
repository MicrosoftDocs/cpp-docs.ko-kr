---
description: '자세한 정보: 수학 오류 M6108'
title: 수학 오류 M6108
ms.date: 11/04/2016
f1_keywords:
- M6108
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
ms.openlocfilehash: 1a0acf13bd166e499334cb13de33093c2c804f5f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97143886"
---
# <a name="math-error-m6108"></a>수학 오류 M6108

제곱근

제곱근 연산에서 피연산자가 음수입니다.

프로그램이 종료 코드 136를 사용 하 여 종료 됩니다.

> [!NOTE]
> `sqrt`C 런타임 라이브러리 및 포트란 내장 함수 **SQRT** 의 함수는이 오류를 생성 하지 않습니다. C `sqrt` 함수는 작업을 수행 하기 전에 인수를 확인 하 고 피연산자가 음수인 경우 오류 값을 반환 합니다. 포트란 **SQRT** 함수는이 오류 대신 도메인 오류 [M6201](../../error-messages/tool-errors/math-error-m6201.md) 를 생성 합니다.
