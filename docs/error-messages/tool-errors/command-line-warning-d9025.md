---
description: 자세한 내용은 Command-Line Warning D9025을 (를) 확인 하세요.
title: 명령줄 경고 D9025
ms.date: 11/04/2016
f1_keywords:
- D9025
helpviewer_keywords:
- D9025
ms.assetid: 6edff72c-1508-46c2-99f4-0e4b3c5e60c9
ms.openlocfilehash: 8cec7bdb5f3816c33d395e8ae93a861a29e94c64
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115497"
---
# <a name="command-line-warning-d9025"></a>명령줄 경고 D9025

' 옵션 1 마이그레이션 '를 ' 옵션 2 마이그레이션 '로 재정의 합니다.

*옵션 1 마이그레이션* 옵션이 지정 되었지만 *옵션 2 마이그레이션* 에 의해 재정의 되었습니다. *옵션 2 마이그레이션* 옵션이 사용 되었습니다.

두 옵션에서 모순 또는 호환 되지 않는 지시문을 지정 하는 경우 명령줄에서 가장 오른쪽에 있는 옵션에 지정 되거나 암시 된 지시문이 사용 됩니다.

개발 환경에서 컴파일할 때이 경고가 발생 하 고 충돌 하는 옵션의 출처를 알 수 없는 경우 다음을 고려 하십시오.

- 옵션은 코드에서 지정 하거나 프로젝트의 프로젝트 설정에서 지정할 수 있습니다. 컴파일러의 [명령줄 속성 페이지](../../build/reference/command-line-property-pages.md) 를 살펴보면 **모든 옵션** 필드에 충돌 하는 옵션이 표시 되는 경우 프로젝트의 속성 페이지에서 옵션이 설정 되 고, 그렇지 않은 경우 소스 코드에 옵션이 설정 됩니다.

   프로젝트의 속성 페이지에서 옵션이 설정 된 경우 컴파일러의 전처리기 속성 페이지 (솔루션 탐색기에서 프로젝트 노드를 선택 하 여)를 확인 합니다.  여기에 설정 된 옵션이 표시 되지 않으면 각 소스 코드 파일 (솔루션 탐색기)에 대 한 전처리기 속성 페이지 설정을 확인 하 여 해당 항목에 추가 되지 않았는지 확인 합니다.

   코드에 옵션이 설정 되어 있는 경우 코드 또는 windows 헤더에서 설정할 수 있습니다.  전처리 된 파일 ([/p](../../build/reference/p-preprocess-to-a-file.md))을 만들어 기호를 검색 해 볼 수 있습니다.
