---
title: 컴파일러 오류 C2220 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2220
dev_langs:
- C++
helpviewer_keywords:
- C2220
ms.assetid: d610802c-64d7-40ad-a2a6-0ed0b6815a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d23476de35e0af45b46a775683ba8673b4959346
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2220"></a>컴파일러 오류 C2220
개체 파일이 생성 되지 않았습니다 오류로 처리 하는 경고  
  
 [/WX](../../build/reference/compiler-option-warning-level.md) 컴파일러가 모든 경고를 오류로 처리 하도록 지정 합니다. 오류가 발생했기 때문에 개체 또는 실행 파일이 생성되지 않았습니다.  
  
 이 오류만 때 나타나는 **/WX** 플래그가 설정 되 고 컴파일 중 경고가 발생 합니다. 이 오류를 해결하려면 프로젝트에서 모든 경고를 없애야 합니다.  
  
### <a name="to-fix-use-one-of-the-following-techniques"></a>해결하려면 다음 방법 중 하나를 사용합니다.  
  
-   프로젝트에서 경고를 일으키는 문제를 해결합니다.  
  
-   낮은 경고 수준에서 컴파일할-사용 예를 들어 **/W3** 대신 **/W4**합니다.  
  
-   사용 하 여 한 [경고](../../preprocessor/warning.md) pragma를 사용 하지 않도록 설정 하거나 특정 경고를 표시 합니다.  
  
-   사용 하지 않는 **/WX** 컴파일할 수 있습니다.