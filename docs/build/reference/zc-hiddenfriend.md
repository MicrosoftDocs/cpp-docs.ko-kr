---
title: '/Zc: hiddenFriend (표준 c + + 숨겨진 friend 규칙 적용)'
description: 'Microsoft c + +/Zc: hiddenFriend 컴파일러 옵션에 대 한 자세한 내용은 준수 또는 완화 된 숨겨진 friend 호환성'
ms.date: 01/23/2021
f1_keywords:
- /Zc:hiddenFriend
helpviewer_keywords:
- /Zc:hiddenFriend
- Zc:hiddenFriend
- -Zc:hiddenFriend
ms.openlocfilehash: 5a3487cc4899cf6a07e91dc5ce5b7cd8f8784737
ms.sourcegitcommit: 74e58bee5cffb30b66e17be6dbfde2544369638e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/25/2021
ms.locfileid: "98766870"
---
# <a name="zchiddenfriend-enforce-standard-c-hidden-friend-rules"></a>`/Zc:hiddenFriend` (표준 c + + 숨겨진 friend 규칙 적용)

컴파일러가 숨겨진 friend 함수 또는 함수 템플릿의 c + + 표준 처리를 준수 하도록 지정 합니다.

## <a name="syntax"></a>Syntax

> **`/Zc:hiddenFriend`**\[**`-`**]

## <a name="remarks"></a>설명

**`/Zc:hiddenFriend`** 옵션은 옵션 동작의 하위 집합을 활성화 합니다 [`/permissive-`](permissive-standards-conformance.md) . 숨겨진 친구의 표준을 준수 하도록 컴파일러에 지시 합니다. 컴파일러는 명시적 인스턴스 또는 바깥쪽 클래스 형식의 템플릿 매개 변수에 대해 adl ( [인수 종속 조회](../../cpp/argument-dependent-name-koenig-lookup-on-functions.md) )에 숨겨진 friend만 포함 합니다. 제한 사항을 사용 하면 숨겨진 친구를 사용 하 여 형식에 대 한 작업을 암시적 변환에 적용할 수 있습니다. 이 옵션은 다른 방법으로는 사용할 수 없는 코드의 빌드 속도를 향상 시킬 수 있습니다 [`/permissive-`](permissive-standards-conformance.md) .

*숨겨진 friend* 는 **`friend`** 클래스 또는 클래스 템플릿 정의 내 에서만 선언 된 함수 또는 함수 템플릿입니다. 기본적으로 Microsoft c + + 컴파일러는 숨겨진 friend 선언을 모든 위치에서 오버 로드 확인을 위한 후보로 제거 하지 않습니다. 이러한 레거시 동작으로 인해 숨겨진 friend 함수를 더 많은 컨텍스트에서 가능한 후보로 포함 하 여 컴파일러가 종료 될 수 있습니다.

표준 c + + 숨겨진 friend 동작은에서 기본적으로 사용 하도록 설정 되어 **`/permissive-`** 있습니다. 옵션이 지정 된 경우 레거시 숨겨진 friend 동작을 지정 하려면 **`/permissive-`** 를 사용 **`/Zc:hiddenFriend-`** 합니다. C + + 20 모듈을 사용 하려면 표준 숨겨진 friend 동작이 필요 합니다.

**`/Zc:hiddenFriend`** 이 옵션은 Visual Studio 2019 버전 16.4부터 사용할 수 있습니다.

을 지정 하는 경우의 컴파일러 동작 예제는 **`/Zc:hiddenFriend`** [숨겨진 friend 이름 조회 규칙](./permissive-standards-conformance.md#hidden-friend-name-lookup-rules)을 참조 하세요.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면

1. 프로젝트의 **속성 페이지** 대화 상자를 엽니다. 자세한 내용은 [Visual Studio에서 C++ 컴파일러 및 빌드 속성 설정](../working-with-project-properties.md)을 참조합니다.

1. **구성 속성**  >  **C/c + +**  >  **명령줄** 속성 페이지를 선택 합니다.

1. 또는를 포함 하도록 **추가 옵션** 속성을 수정한 *`/Zc:hiddenFriend`* *`/Zc:hiddenFriend-`* 다음 **확인** 을 선택 합니다.

## <a name="see-also"></a>참고 항목

[`/Zc` 규칙](zc-conformance.md)\
[`/permissive-`](permissive-standards-conformance.md)
