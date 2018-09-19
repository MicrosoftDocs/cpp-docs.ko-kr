---
title: 함수 선언 및 정의 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- local declarations
- function definitions, function declarations
- declaring functions, function definitions
- internal declarations
- external declarations
- function prototypes, basics
- external linkage, function declarations
- declaring functions
ms.assetid: 43fd98eb-7441-4473-a5d9-fc88c75577f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2bb5a6b1f184775b3e67a03b9544e609b33673ba
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106131"
---
# <a name="function-declarations-and-definitions"></a>함수 선언 및 정의

함수 프로토타입은 함수 이름, 해당 반환 형식 및 해당 정식 매개 변수의 형식 및 개수를 설정합니다. 함수 정의에는 함수 본문이 포함됩니다.

## <a name="remarks"></a>설명

함수 선언과 변수 선언 모두 함수 정의 내부 또는 외부에 나타날 수 있습니다. 함수 정의 내 모든 선언은 "내부" 또는 "로컬" 수준에서 표시되어야 합니다. 모든 함수 정의 외부 선언은 "외부," "전역" 또는 "파일 범위" 수준에서 표시되어야 합니다. 변수 정의는 선언처럼 내부 수준(함수 정의 내부) 또는 외부 수준(모든 함수 정의 외부)에서 표시될 수 있습니다. 함수 정의는 항상 외부 수준에서 발생합니다. 함수 정의에 대한 자세한 내용은 [함수 정의](../c-language/c-function-definitions.md)를 참조하세요. 함수 프로토타입은 [함수 프로토타입](../c-language/function-prototypes.md)에 설명되어 있습니다.

## <a name="see-also"></a>참고 항목

[원본 파일 및 원본 프로그램](../c-language/source-files-and-source-programs.md)