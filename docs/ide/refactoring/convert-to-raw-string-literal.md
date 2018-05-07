---
title: 원시 문자열 리터럴로 변환 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: fffbfee4-66ee-42ba-aeb9-df07fb702c51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b98825719e7b3c0d8eb760a2ec50644b5eddd54e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="convert-to-raw-string-literal"></a>원시 문자열 리터럴로 변환
**:** C + + 원시 문자열에는 모든 문자열 리터럴 회전할 수 있습니다.

**경우:** 문자열 이스케이프 된 문자로 이스케이프 된 문자로 처리할 수 없습니다.

**이유:** 이중 이스케이프 문자 이지만 혼란 스 럽 고 읽을 수 없는 문자열에 종종이 리드 수 없습니다.  원시 문자열 리터럴을 사용 하면 문자열을 훨씬 더 쉽게 읽을 수 있습니다.

**방법:**

1. 변환할 이스케이프 된 문자열 텍스트 또는 마우스 커서를 놓습니다.

   ![강조 표시된 코드](images/stringliteral_highlight.png)

1. 다음 작업 중 하나를 수행합니다.
   * **키보드**
     * **Ctrl+.** 를 눌러 트리거에 **빠른 작업 및 리팩터링** 메뉴와 선택 **원시 문자열 리터럴로 변환** 상황에 맞는 메뉴에서 합니다.
   * **마우스**
     * 코드를 마우스 오른쪽 단추로 클릭, 선택는 **빠른 작업 및 리팩터링** 메뉴와 선택 **원시 문자열 리터럴로 변환** 상황에 맞는 메뉴에서 합니다.
     * 클릭는 ![전구](images/bulb.png) 선택한 왼쪽된 여백에 표시 되는 아이콘 **원시 문자열 리터럴로 변환** 상황에 맞는 메뉴입니다.

1. 문자열은 원시 문자열 리터럴은으로 즉시 변환 됩니다.  

   ![원시 문자열 리터럴 결과](images/stringliteral_result.png)