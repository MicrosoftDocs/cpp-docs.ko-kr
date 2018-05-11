---
title: 만들 선언 / 정의 | Microsoft Docs
ms.custom: ''
ms.date: 11/16/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
ms.assetid: 6b1cdcb2-765e-4b93-8cef-92b861f64eba
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60d583ec47a3f9c5b61599a5945e3cfa0d375b1d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/04/2018
---
# <a name="create-declaration--definition"></a>선언/정의 만들기
**:** 즉시 선언 또는 함수 정의 생성할 수 있습니다.

**경우:** delcaration, 또는 그 반대로 필요로 하는 함수가 있습니다.  

**이유:** 선언/정의 수동으로 만들 수 있지만이 만들 자동으로 필요한 경우 헤더/코드 파일을 만드는 합니다.

**방법:**

1. 함수 선언 또는 정의 만들기를 통해 텍스트 또는 마우스 커서를 놓습니다.

   ![강조 표시된 코드](images/createdefinition_highlight.png)

1. 다음 작업 중 하나를 수행합니다.
   * **키보드**
     * **Ctrl+.** 를 눌러 트리거에 **빠른 작업 및 리팩터링** 메뉴와 선택 **만들 선언 / 정의** 상황에 맞는 메뉴에서 합니다.
   * **마우스**
     * 마우스 오른쪽 단추로 클릭 하 고 선택 된 **빠른 작업 및 리팩터링** 메뉴를 선택 **만들 선언 / 정의** 상황에 맞는 메뉴에서 합니다.

1. 함수 선언/정의 팝업 미리 보기 창에 표시 되는 원본 또는 헤더 파일에서 생성 됩니다.  원본이 나 헤더 파일이 없는 경우 것도 만들어지고 됩니다는 프로젝트에 배치 합니다.

   ![선언을 정의 /](images/createdefinition_result.png)
