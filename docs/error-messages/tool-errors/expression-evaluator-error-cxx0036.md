---
description: '자세한 정보: 식 계산기 오류 CXX0036'
title: 식 계산기 오류 CXX0036
ms.date: 11/04/2016
f1_keywords:
- CXX0036
helpviewer_keywords:
- CXX0036
- CAN0036
ms.assetid: 383404be-df5b-4eec-b113-df21bb5d269d
ms.openlocfilehash: fa595c590b6e59b74d693f3b6ff777055b5af2c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338537"
---
# <a name="expression-evaluator-error-cxx0036"></a>식 계산기 오류 CXX0036

잘못 된 컨텍스트 {...} 사양

이 메시지는 컨텍스트 연산자 () 사용 시 여러 오류에 의해 생성 될 수 있습니다 **{}** .

- 컨텍스트 연산자 ()의 구문이 **{}** 잘못 지정 되었습니다.

   컨텍스트 연산자의 구문은 다음과 같습니다.

     {*function*,*module*,*dll*} *식*

   *식* 의 컨텍스트를 지정 합니다. 컨텍스트 연산자의 우선 순위와 사용량은 유형 캐스트와 동일 합니다.

   후행 쉼표는 생략할 수 있습니다. *함수*, *모듈* 또는 *dll* 이 리터럴 쉼표를 포함 하는 경우 전체 이름을 괄호로 묶어야 합니다.

- 함수 이름의 철자가 잘못 되었거나 지정 된 모듈 또는 동적 연결 라이브러리에 없습니다.

   C는 대/소문자를 구분 하는 언어 이므로 *함수* 는 소스에 정의 된 대로 정확한 대/소문자에 지정 해야 합니다.

- 모듈 또는 DLL을 찾을 수 없습니다.

   지정한 모듈 또는 DLL의 전체 경로 이름을 확인 하십시오.

이 오류는 CAN0036와 동일 합니다.
