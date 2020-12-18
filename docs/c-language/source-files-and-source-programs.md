---
description: '자세한 정보: 원본 파일 및 원본 프로그램'
title: 원본 파일 및 원본 프로그램
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: 9fd389f74efac11288b805d95dc2d95d4ec6d2bf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97296903"
---
# <a name="source-files-and-source-programs"></a>원본 파일 및 원본 프로그램

소스 프로그램은 하나 이상의 "소스 파일" 또는 "변환 단위"로 나뉠 수 있습니다. 컴파일러로 입력된 것은 "변환 단위"라고 합니다.

## <a name="syntax"></a>구문

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

[선언의 개요](../c-language/overview-of-declarations.md)에서는 `declaration` 비터미널에 대한 구문을 제공하고 *전처리기 참조* 는 [변환 단위](../preprocessor/phases-of-translation.md)가 어떻게 처리되는지 설명합니다.

> [!NOTE]
> ANSI 구문 규칙에 대한 설명은 [C 언어 구문 요약](../c-language/c-language-syntax-summary.md)에 대한 소개를 참조하세요.

변환 단위의 구성 요소는 함수 정의 및 식별자 선언이 포함되어 있는 외부 선언입니다. 이러한 선언 및 정의는 프로그램에 필요한 소스 파일, 헤더 파일, 라이브러리와 기타 파일에 존재할 수 있습니다. 각 변환 단위를 컴파일하고 결과 개체 파일을 연결하여 프로그램을 만들어야 합니다.

C "소스 프로그램"은 지시문, pragma, 선언, 정의, 문 블록 및 함수의 컬렉션입니다. Microsoft C 프로그램에서 유효한 컴포넌트가 되려면, 이 책에서 설명된 규칙에 따른 순서로 프로그램에 나타났다 하더라도 이 책에서 설명된 구문을 지켜야 합니다. 프로그램에서 이러한 구성 요소의 위치는 프로그램에서 변수와 함수를 사용하는 방식에 영향을 미치지 않습니다. 자세한 내용은 [수명, 범위, 표시 유형 및 링크](../c-language/lifetime-scope-visibility-and-linkage.md)를 참조하세요.

소스 파일은 실행 문을 포함할 필요가 없습니다. 이는 변수 정의를 소스 파일 하나에 배치한 다음 이 변수를 사용 중인 다른 소스 파일에서 이 변수에 대한 참조를 선언할 때 유용합니다. 이 방법을 통해 필요할 때 정의를 쉽게 찾고 업데이트할 수 있습니다. 이와 같은 이유로 상수 및 매크로는 필요에 따라 소스 파일에서 참조할 수 있는 "파일 포함" 또는 "헤더 파일"이라는 별도 파일에 정리되곤 합니다. [매크로](../preprocessor/macros-c-cpp.md) 및 [include 파일](../preprocessor/hash-include-directive-c-cpp.md)에 대한 내용은 *처리기 참조* 를 참조하세요.

## <a name="see-also"></a>참조

[프로그램 구조](../c-language/program-structure.md)
