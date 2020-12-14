---
description: '자세한 정보: 리소스 컴파일러 심각한 오류 RC1052'
title: 리소스 컴파일러 심각한 오류 RC1052
ms.date: 11/04/2016
f1_keywords:
- RC1052
helpviewer_keywords:
- RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
ms.openlocfilehash: 41ef30cfde7d463337b1747b3f6141866e39e3be
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255082"
---
# <a name="resource-compiler-fatal-error-rc1052"></a>리소스 컴파일러 심각한 오류 RC1052

컴파일러 한계: #if 또는 #ifdef 블록이 너무 많이 중첩되었습니다.

프로그램에서 `#if` 및 `#ifdef` 지시문에 대해 허용 가능한 최대 중첩 수준이 초과되었습니다.

이 오류는 전처리기 지시문을 사용하는 포함 파일에 의해 발생할 수 있습니다.

이 문제를 해결하려면 리소스 파일에서 중첩된 `#if` 및 `#ifdef` 지시문의 수를 줄입니다. 리소스 파일에 포함된 헤더 파일에 의해 문제가 발생하는 경우 헤더 파일에 중첩된 `#if` 및 `#ifdef` 지시문의 수를 줄입니다. 이렇게 할 수 없는 경우에는 포함된 기존 헤더 파일에서 전처리기를 실행하여 새 헤더 파일을 만든 다음 리소스 파일에 포함할 수 있습니다. 자세한 내용은 [/p (파일로 전처리)](../../build/reference/p-preprocess-to-a-file.md) 컴파일러 옵션을 참조 하세요.
