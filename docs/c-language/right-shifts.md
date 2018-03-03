---
title: "오른쪽 이동 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 307cf91bf86f2912ad6cafa7e89f48e614c3865a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="right-shifts"></a>오른쪽 시프트
음수 값 부호 있는 정수 계열 형식의 오른쪽 시프트 결과  
  
 음수 값을 오른쪽으로 이동하면 절대값의 반을 정수로 내림한 값이 생성됩니다. 예를 들어 부호 있는 `short` 값 –253(16진수 0xFF03, 이진수 11111111 00000011)을 오른쪽으로 1비트 이동하면 –127(16진수 0xFF81, 이진수 11111111 10000001)이 생성됩니다. 양수 253을 오른쪽으로 시프트하면 +126이 생성됩니다.  
  
 오른쪽으로 시프트하면 부호 있는 정수 형식의 부호 비트는 유지됩니다. 부호 있는 정수가 오른쪽으로 이동하면 최상위 비트는 설정된 상태로 유지됩니다. 예를 들어 0xF0000000이 부호 있는 `int`인 경우 오른쪽 시프트는 0xF8000000을 생성합니다. 음의 `int`를 오른쪽으로 32번 시프트하면 0xFFFFFFFF가 생성됩니다.  
  
 부호 없는 정수가 오른쪽으로 이동하면 최상위 비트는 해제됩니다. 예를 들어 0xF000에 부호가 없는 경우 결과는 0x7800입니다. `unsigned` 또는 양의 `int`를 오른쪽으로 32번 이동하면 0x00000000이 생성됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [정수](../c-language/integers.md)