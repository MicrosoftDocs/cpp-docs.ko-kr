---
title: "식 계산기 오류 CXX0024 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- CXX0024
dev_langs:
- C++
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c96bd943719afb0d974a5c4386742bea24396fd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="expression-evaluator-error-cxx0024"></a>식 계산기 오류 CXX0024
작업을 해야 l 값  
  
 L-value를 평가 되지 않는 식 l-value를 필요로 하는 작업에 지정 되었습니다.  
  
 L 값 (대입문의 왼쪽에 표시 되기 때문에 이렇게 부름)는 메모리 위치를 참조 하는 식입니다.  
  
 예를 들어 `buffer[count]` 은 올바른 l 값이 특정 메모리 위치를 가리키므로 합니다. 논리 비교 `zed != 0` 메모리 주소로 하지 TRUE 또는 FALSE로 계산 되기 때문에 l 값이 올바르지 않습니다.  
  
 이 오류는 can0024와 동일 합니다.