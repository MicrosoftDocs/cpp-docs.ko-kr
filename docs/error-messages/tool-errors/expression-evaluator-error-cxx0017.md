---
description: '자세한 정보: 식 계산기 오류 CXX0017'
title: 식 계산기 오류 CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 0abb99422383f95e13d4137a5ad899730d485f87
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228276"
---
# <a name="expression-evaluator-error-cxx0017"></a>식 계산기 오류 CXX0017

기호를 찾을 수 없습니다.

식에 지정 된 기호를 찾을 수 없습니다.

이 오류의 한 가지 가능한 원인은 기호 이름에서 대/소문자가 일치 하지 않는 경우입니다. C 및 c + +는 대/소문자를 구분 하므로 소스에 정의 된 정확한 경우에 기호 이름을 제공 해야 합니다.

이 오류는 디버깅 하는 동안 변수를 조사 하기 위해 변수를 형식 캐스팅 할 때 발생할 수 있습니다. 는 `typedef` 형식에 대 한 새 이름을 선언 하지만 새 형식을 정의 하지는 않습니다. 디버거에서 시도한 형식 캐스팅에는 정의 된 형식의 이름이 필요 합니다.

이 오류는 CAN0017와 동일 합니다.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>아래의 해결 방법 따라 수정합니다.

1. 기호가 사용 되 고 있는 프로그램의 지점에서 기호가 이미 선언 되었는지 확인 합니다.

1. 실제 형식 이름을 사용 하 여 정의 된 이름이 아니라 디버거의 변수를 캐스팅 `typedef` 합니다.
