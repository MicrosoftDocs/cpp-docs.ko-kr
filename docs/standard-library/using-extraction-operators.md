---
description: '자세한 정보: 추출 연산자 사용'
title: 추출 연산자 사용
ms.date: 11/04/2016
helpviewer_keywords:
- extraction operators [C++]
- '&gt;&gt; operator [C++], extraction operators'
- operators [C++], extraction
ms.assetid: a961e1a9-4897-41de-b210-89d5b2d051ae
ms.openlocfilehash: 11115ed9d7f83b5e4d8cefe088c638afe8d95f38
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153579"
---
# <a name="using-extraction-operators"></a>추출 연산자 사용

모든 표준 C++ 데이터 형식용으로 프로그래밍된 추출 연산자(`>>`)를 사용하면 입력 스트림 개체에서 바이트를 가장 쉽게 가져올 수 있습니다.

서식 있는 텍스트 입력 추출 연산자는 공백을 사용하여 들어오는 데이터 값을 구분합니다. 텍스트 필드에 단어가 여러 개 있거나 숫자가 쉼표로 구분되는 경우에는 이러한 방식이 불편합니다. 이러한 경우에 대신 사용할 수 있는 방법 중 하나는 서식 없는 입력 구성원 함수 [istream::getline](../standard-library/basic-istream-class.md#getline)을 사용하여 공백이 포함된 텍스트 블록을 읽은 다음 특수 함수로 해당 블록을 구문 분석하는 것입니다. istream 구성원를 호출하여 문자 데이터를 추출하고 서식을 지정할 수 있는 `GetNextToken` 등의 구성원 함수를 사용하여 입력 스트림 클래스를 파생할 수도 있습니다.

## <a name="see-also"></a>참고 항목

[입력 스트림](../standard-library/input-streams.md)
