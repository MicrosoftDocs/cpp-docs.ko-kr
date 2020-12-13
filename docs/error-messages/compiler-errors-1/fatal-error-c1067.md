---
description: '자세한 정보: 심각한 오류 C1067'
title: 심각한 오류 C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: ef50719740de99f85e7e94f99cf0e14531608b22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344421"
---
# <a name="fatal-error-c1067"></a>심각한 오류 C1067

컴파일러 한계: 형식 레코드 크기의 64K 한도를 초과 했습니다.

기호의 데코레이팅된 이름이 247 자를 초과 하는 경우이 오류가 발생할 수 있습니다.  해결 하려면 기호 이름을 짧게 줄입니다.

컴파일러가 디버그 정보를 생성 하는 경우 소스 코드에서 발견 된 형식을 정의 하는 형식 레코드를 내보냅니다.  예를 들어 형식 레코드에는 함수의 단순 구조와 인수 목록이 포함 됩니다.  이러한 형식 레코드 중 일부는 크기가 클 수 있습니다.

모든 형식 레코드 크기에는 64K 제한이 있습니다.  64K 한도를 초과 하면이 오류가 발생 합니다.

C1067는 긴 이름이 있는 기호가 많거나 클래스, 구조체 또는 공용 구조체에 멤버가 너무 많은 경우에도 발생할 수 있습니다.
