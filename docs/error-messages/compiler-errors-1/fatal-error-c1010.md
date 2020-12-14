---
description: '자세한 정보: 심각한 오류 C1010'
title: 심각한 오류 C1010
ms.date: 09/03/2019
f1_keywords:
- C1010
helpviewer_keywords:
- C1010
ms.assetid: dfd035f1-a7a2-40bc-bc92-dc4d7f456767
ms.openlocfilehash: 2c6d57b2390f727e37d546d7077217e25db40fef
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97262531"
---
# <a name="fatal-error-c1010"></a>심각한 오류 C1010

> 미리 컴파일된 헤더를 찾는 동안 예기치 않은 파일의 끝이 나타났습니다. ' #Include *name*'을 소스에 추가 하는 것을 잊은 경우

## <a name="remarks"></a>설명

[/Yu](../../build/reference/yu-use-precompiled-header-file.md) 로 지정 된 포함 파일은 소스 파일에 나열 되지 않습니다. 이 옵션은 대부분의 Visual Studio c + + 프로젝트 형식에서 기본적으로 사용 하도록 설정 되어 있습니다. 이 옵션으로 지정 된 기본 포함 *파일은 Visual* Studio 2017 이전 버전의 tchar.h 또는 *stdafx.h* 입니다.

Visual Studio 환경에서 다음 방법 중 하나를 사용 하 여이 오류를 해결 합니다.

- 현재 프로젝트에서 파일을 실수로 *삭제 하거나 이름을* 변경 하거나 제거 하지 않았는지 *확인 합니다.* 이전 프로젝트에서는 이러한 파일의 이름을 *stdafx.h* 및 *stdafx.h* 로 지정할 수 있습니다.

- *.Pch* 또는 *stdafx.h* 헤더 파일이 소스 파일의 다른 코드 또는 전처리기 지시문 앞에 포함 되어 있는지 확인 합니다. Visual Studio에서이 헤더 파일은 **미리 컴파일된 헤더 파일** 프로젝트 속성에 의해 지정 됩니다.

- 미리 컴파일된 헤더 사용을 해제할 수 있습니다. 미리 컴파일된 헤더를 해제 하면 빌드 성능에 심각한 영향을 줄 수 있습니다.

### <a name="to-turn-off-precompiled-headers"></a>미리 컴파일된 헤더를 해제 하려면

프로젝트에서 미리 컴파일된 헤더 사용을 해제 하려면 다음 단계를 수행 합니다.

1. **솔루션 탐색기** 창에서 프로젝트 이름을 마우스 오른쪽 단추로 클릭 한 다음 **속성** 을 선택 하 여 프로젝트 **속성 페이지** 대화 상자를 엽니다.

1. **구성** 드롭다운에서 **모든 구성** 을 선택 합니다.

1. **구성 속성**  >  **C/c + +**  >  **미리 컴파일된 헤더** 속성 페이지를 선택 합니다.

1. 속성 목록에서 **미리 컴파일된 헤더** 속성의 드롭다운을 선택한 후 **미리 컴파일된 헤더 사용 안 함** 을 선택 합니다. **확인** 을 선택하여 변경 내용을 저장합니다.

1. **솔루션 탐색기** 창에서 프로젝트의 *.pch. .cpp* 소스 파일을 마우스 오른쪽 단추로 클릭 합니다. 이전 프로젝트에서는 파일의 이름을 *stdafx.h* 로 지정할 수 있습니다. **프로젝트에서 제외** 를 선택 하 여 빌드에서 제거 합니다.

1.   >  작성 하는 각 구성에 대해 **정리 솔루션** 빌드 메뉴 명령을 사용 하 여 중간 빌드 디렉터리에서 *project_name .pch* 파일을 삭제 합니다.

## <a name="see-also"></a>참고 항목

[미리 컴파일된 헤더 파일](../../build/creating-precompiled-header-files.md)\
[/Yc (미리 컴파일된 헤더 파일 만들기)](../../build/reference/yc-create-precompiled-header-file.md)\
[/Yu(미리 컴파일된 헤더 파일 사용)](../../build/reference/yu-use-precompiled-header-file.md)
