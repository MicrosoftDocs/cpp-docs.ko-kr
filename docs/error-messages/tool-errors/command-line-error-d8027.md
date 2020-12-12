---
description: 자세한 내용은 Command-Line Error D8027을 (를) 확인 하세요.
title: 명령줄 오류 D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: 80d0812571043249616108e99e763b105b527475
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115653"
---
# <a name="command-line-error-d8027"></a>명령줄 오류 D8027

' component '를 실행할 수 없습니다.

컴파일러가 지정 된 컴파일러 구성 요소나 링커를 실행할 수 없습니다.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>다음과 같은 가능한 원인을 확인하여 수정하려면

1. 메모리가 부족 하 여 구성 요소를 로드할 수 없습니다. NMAKE가 컴파일러를 호출한 경우 메이크파일 외부에서 컴파일러를 실행 합니다.

1. 현재 운영 체제에서 구성 요소를 실행할 수 없습니다. 경로가 운영 체제에 적합 한 실행 파일을 가리키는지 확인 합니다.

1. 구성 요소가 손상 되었습니다. 설치 프로그램을 사용 하 여 배포 디스크에서 구성 요소를 다시 복사 합니다.

1. 옵션을 잘못 지정 했습니다. 예를 들어:

    ```
    cl /B1 file1.c
    ```
