---
description: '자세한 정보: 리소스 컴파일러 오류 RC2144'
title: 리소스 컴파일러 오류 RC2144
ms.date: 11/04/2016
f1_keywords:
- RC2144
helpviewer_keywords:
- RC2144
ms.assetid: 1b3ff39a-92cd-4a04-b1a3-b1fa6a805813
ms.openlocfilehash: 8b40f989e4319b16a9a983f5e4e377aeb357e8f7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97133512"
---
# <a name="resource-compiler-error-rc2144"></a>리소스 컴파일러 오류 RC2144

주 언어 ID가 숫자가 아닙니다.

주 언어 ID는 16진수 언어 ID여야 합니다. 유효한 언어 ID 목록은 [런타임 라이브러리 참조](../../c-runtime-library/locale-names-languages-and-country-region-strings.md) 에서 *언어 및 국가/지역 문자열* 을 참조하세요.

도구를 사용하여 리소스를 .RC 파일에 추가한 다음 해당 파일에서 삭제한 경우에도 이 오류가 발생할 수 있습니다. 이 문제를 해결하려면 텍스트 편집기에서 .RC 파일을 열고 사용하지 않는 리소스를 수동으로 정리합니다.
