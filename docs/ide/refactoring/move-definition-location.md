---
description: '자세한 정보: 정의 위치 이동'
title: 정의 위치 이동
ms.date: 11/16/2016
ms.assetid: c6d507ac-c61e-4da2-95c8-d504b42e2520
ms.openlocfilehash: 5c0ae4ed5e14a50f4d54226fb298c34099c8aec7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318717"
---
# <a name="move-definition-location"></a>정의 위치 이동

**대상:** 함수 정의를 해당 헤더 파일로 즉시 이동할 수 있습니다.

**시기:** 헤더 파일로 이동할 함수가 있는 경우.

**이유:** 함수를 수동으로 이동할 수 있지만, 이 기능이 함수를 자동으로 이동하고, 필요한 경우 헤더 파일을 만듭니다.

**방법:**

1. 이동하려는 함수 위에 텍스트 또는 마우스 커서를 놓습니다.

   ![강조 표시된 코드](images/movedefinition_highlight.png)

1. 다음 작업 중 하나를 수행합니다.
   * **키보드**
     * **Ctrl+.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 상황에 맞는 메뉴에서 **정의 위치 이동** 을 선택합니다.
   * **마우스**
     * 마우스 오른쪽 단추를 클릭하고 **빠른 작업 및 리팩터링** 메뉴를 선택하고, 상황에 맞는 메뉴에서 **정의 위치 이동** 을 선택합니다.

1. 이 함수는 해당 헤더 파일로 이동되며, 팝업 미리 보기 창에 표시됩니다.  헤더 파일이 없는 경우 파일이 생성되어 프로젝트에 배치됩니다.

   ![선언/정의 만들기 결과](images/movedefinition_result.png)
