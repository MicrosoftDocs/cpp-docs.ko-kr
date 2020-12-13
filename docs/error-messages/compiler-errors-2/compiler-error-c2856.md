---
description: '자세한 정보: 컴파일러 오류 C2856'
title: 컴파일러 오류 C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 8594bc5902e13967084aa3695131d616a4cf04da
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97337550"
---
# <a name="compiler-error-c2856"></a>컴파일러 오류 C2856

\#pragma hdrstop은 #if 블록 안에 있을 수 없습니다.

`hdrstop`Pragma는 조건부 컴파일 블록의 본문 안에 배치할 수 없습니다.

`#pragma hdrstop`문을 블록에 포함 되지 않은 영역으로 이동 `#if/#endif` 합니다.
