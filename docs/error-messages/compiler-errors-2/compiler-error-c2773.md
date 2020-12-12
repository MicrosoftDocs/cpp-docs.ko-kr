---
description: '자세한 정보: 컴파일러 오류 C2773'
title: 컴파일러 오류 C2773
ms.date: 11/04/2016
f1_keywords:
- C2773
helpviewer_keywords:
- C2773
ms.assetid: 8d564b26-1623-4d92-aabc-dff33f7b1145
ms.openlocfilehash: 4530257adab91abec8a1fa87f8625ef6dbd7bb04
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97298242"
---
# <a name="compiler-error-c2773"></a>컴파일러 오류 C2773

\#import 및 #using는 c + + 컴파일러 에서만 사용할 수 있습니다.

C 컴파일러는 전처리기 지시문을 인식 하지 않습니다 `#import` . 소스를 c + +로 컴파일합니다. 필요한 경우 [/tp](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) 를 사용 합니다.
