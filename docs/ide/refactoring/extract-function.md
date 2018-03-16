---
title: "Extract 함수 | Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e31d1249-9705-4511-acbd-9f6fe73bdf2d
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: dbcd323292e301857c65d908047ab14948b86573
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
---
# <a name="extract-function"></a>Extract 함수
**:** 자체 함수로 코드의 일부를 회전할 수 있습니다.

**경우:** 기존 코드의 일부 다른 함수에서 호출 하는 일부 함수에 있어야 합니다.  

**이유:** 해당 코드를 복사하여 붙여넣을 수 있지만 중복이 발생합니다.  다른 함수에서 든 자유롭게 호출할 수 있는 자체 함수로 해당 조각을 리팩터링 하는 것이 좋습니다.

**방법:**

1. 추출할 코드를 강조 표시합니다.

   ![강조 표시된 코드](images/extractfunction_highlight.png)

1. 다음 작업 중 하나를 수행합니다.
   * **키보드**
     * **Ctrl+R**을 누른 다음 **Ctrl+M**을 누릅니다.  바로 가기 키는 선택한 프로필에 따라 다를 수 있습니다.
     * **Ctrl+.**를 눌러 트리거에 **빠른 작업 및 리팩터링** 메뉴와 선택 **함수 추출 (합니다 실험적)** 상황에 맞는 메뉴에서 합니다.
   * **마우스**
     * 선택 **편집 > 리팩터링 > Extract 함수 (실험적)**합니다.
     * 코드를 마우스 오른쪽 단추로 클릭, 선택는 **빠른 작업 및 리팩터링** 메뉴와 선택 **함수 추출 (합니다 실험적)** 상황에 맞는 메뉴에서 합니다.
     * 클릭는 ![전구](images/bulb.png) 선택한 왼쪽된 여백에 표시 되는 아이콘 **함수 추출 (합니다 실험적)** 상황에 맞는 메뉴입니다.

1. 에 **함수/메서드 추출 (합니다 실험적)** 창 च े ं를 입력 합니다. 배치 될 코드를 원하는 위치를 선택 하 고 클릭는 **확인** 단추입니다.  

   ![Extract 함수 함수](images/extractfunction_dialog.png)

1. 새 함수를 만들 수는 사용자가 지정한 해당 헤더 파일에는 함수 프로토타입 고 함수 호출 하는 원본 코드는 변경 합니다.

   ![함수 결과 추출 합니다.](images/extractfunction_result.png)