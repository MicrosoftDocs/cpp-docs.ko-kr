---
title: 대괄호로 묶은 파일 이름 포함 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37b4d0e6ccf0c0c01671082d2596528632fba6cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46100866"
---
# <a name="including-bracketed-filenames"></a>대괄호로 묶은 파일 이름 포함

**ANSI 3.8.2** 포함 가능한 소스 파일을 찾기 위한 메서드

꺾쇠 괄호로 묶인 파일 사양의 경우 전처리기는 부모 파일의 디렉터리를 검색하지 않습니다. "부모" 파일은 [#include](../preprocessor/hash-include-directive-c-cpp.md) 지시문을 포함하는 파일입니다. 대신 전처리기는 먼저 컴파일러 명령줄에서 /I 다음에 지정된 디렉터리의 파일을 검색합니다. /I 옵션이 없거나 실패할 경우 전처리기는 INCLUDE 환경 변수를 사용하여 꺾쇠 괄호 안에 있는 모든 include 파일을 찾습니다. INCLUDE 환경 변수에는 세미콜론(**;**)으로 구분된 여러 경로가 포함될 수 있습니다. 두 개 이상의 디렉터리가 /I 옵션의 일부로 또는 INCLUDE 환경 변수 안에 있으면 전처리기는 디렉터리가 표시된 순서대로 검색합니다.

## <a name="see-also"></a>참고 항목

[전처리 지시문](../c-language/preprocessing-directives.md)