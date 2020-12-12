---
description: '자세한 정보: 프로젝트 빌드 경고 PRJ0049'
title: 프로젝트 빌드 경고 PRJ0049
ms.date: 11/04/2016
helpviewer_keywords:
- PRJ0049
ms.assetid: 8b38afa1-e080-4efd-ae89-776cfd044413
ms.openlocfilehash: 423b2220cdc80408c71f96c65eb078763291ec3c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97206359"
---
# <a name="project-build-warning-prj0049"></a>프로젝트 빌드 경고 PRJ0049

참조 된 대상 ' \<Reference> '은 (는) .NET Framework 필요 \<MinFrameworkVersion> 하며이 프로젝트의 대상 프레임 워크에서 실행 되지 않습니다.

Visual Studio 2008을 사용 하 여 만든 응용 프로그램은 대상으로 지정 해야 하는 .NET Framework 버전을 지정할 수 있습니다. 대상 버전 보다 이후 버전의 .NET Framework에 종속 된 어셈블리 또는 프로젝트에 대 한 참조를 추가 하는 경우 컴파일 시간에이 경고가 발생 합니다.

### <a name="to-correct-this-warning"></a>이 경고를 해결 하려면

1. 다음 중 하나를 선택합니다.

   - 프로젝트의 **속성 페이지** 대화 상자에서 대상 프레임 워크를 변경 하 여 참조 되는 모든 어셈블리 및 프로젝트의 최소 프레임 워크 버전 보다 나중 이거나 같도록 합니다. 자세한 내용은 [참조 추가](../../build/adding-references-in-visual-cpp-projects.md)를 참조 하세요.

   - 대상 프레임 워크 보다 이후 버전의 프레임 워크 버전을 포함 하는 어셈블리 또는 프로젝트에 대 한 참조를 제거 합니다. 이러한 항목은 프로젝트의 **속성 페이지** 에 경고 아이콘으로 표시 됩니다.

## <a name="see-also"></a>참고 항목

[프로젝트 빌드 오류 및 경고 (PRJxxxx)](../../error-messages/tool-errors/project-build-errors-and-warnings-prjxxxx.md)
