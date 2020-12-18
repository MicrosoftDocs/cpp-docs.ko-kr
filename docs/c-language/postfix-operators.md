---
description: '자세한 정보: 후위 연산자'
title: 후위 연산자
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: be8e7354d512174a4ab11ffcdcb82f9418baa894
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97195868"
---
# <a name="postfix-operators"></a>후위 연산자

후위 연산자는 식 계산에서 가장 높은 우선 순위(가장 강력한 바인딩)를 가집니다.

## <a name="syntax"></a>구문

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **[**  *expression*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **->**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

이 우선 순위 수준에 있는 연산자는 배열 첨자, 함수 호출, 구조체 및 공용 구조체 멤버 및 후위 증가/감소 연산자입니다.

## <a name="see-also"></a>참조

[C 연산자](../c-language/c-operators.md)
