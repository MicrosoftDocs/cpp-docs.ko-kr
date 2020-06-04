---
title: 프로젝트 빌드 오류 PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e13236f65aaca778a297cdd2942c07b75dd701d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192499"
---
# <a name="project-build-error-prj0031"></a>프로젝트 빌드 오류 PRJ0031

' File ' 파일에 대 한 사용자 지정 빌드 단계에 대 한 ' Outputs ' 속성은 ' macro_expansion '로 계산 되는 ' macro '를 포함 합니다.

파일에 대 한 사용자 지정 빌드 단계에서 잘못 된 출력이 있습니다 (매크로 평가 문제 때문). 이 오류는 경로 형식이 잘못 된 것을 의미할 수도 있습니다 .이 경우 파일 경로에 잘못 된 문자 또는 문자 조합이 포함 됩니다.

이 오류를 해결 하려면 매크로를 수정 하거나 경로 지정을 수정 합니다. 계산 된 경로는 프로젝트 디렉터리의 절대 경로입니다.
