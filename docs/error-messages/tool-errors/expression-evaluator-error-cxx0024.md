---
description: '자세한 정보: 식 계산기 오류 CXX0024'
title: 식 계산기 오류 CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: cb40199c217180b08e62d89dee551130eefefc35
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228081"
---
# <a name="expression-evaluator-error-cxx0024"></a>식 계산기 오류 CXX0024

연산에 l-value가 필요 합니다.

L-value로 계산 되지 않는 식이 l-value를 필요로 하는 작업에 대해 지정 되었습니다.

L-value (대입 문의 왼쪽에 표시 되기 때문에 호출 됨)는 메모리 위치를 참조 하는 식입니다.

예를 들어 `buffer[count]` 는 특정 메모리 위치를 가리키기 때문에 유효한 l-value입니다. 논리적 비교는 `zed != 0` 메모리 주소가 아니라 TRUE 또는 FALSE로 계산 되기 때문에 유효한 l-value가 아닙니다.

이 오류는 CAN0024와 동일 합니다.
