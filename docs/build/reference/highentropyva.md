---
description: 자세히 알아보기:/HIGHENTROPYVA
title: /HIGHENTROPYVA
ms.date: 06/12/2018
f1_keywords:
- /HIGHENTROPYVA
helpviewer_keywords:
- HIGHENTROPYVA editbin option
- -HIGHENTROPYVA editbin option
- /HIGHENTROPYVA editbin option
ms.assetid: ef4b7c63-440d-40ca-b39d-edefb3217505
ms.openlocfilehash: ae7851bb9160601ef8732120dca12132dbfdee2d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200041"
---
# <a name="highentropyva"></a>/HIGHENTROPYVA

실행 가능 이미지가 높은 엔트로피 64비트 ASLR(주소 공간 레이아웃 불규칙화)을 지원하는지 여부를 지정합니다.

## <a name="syntax"></a>Syntax

> **`/HIGHENTROPYVA`**[**`:NO`**]

## <a name="remarks"></a>설명

이 옵션은 (예: 또는 파일) *실행 가능한 이미지* 파일의 헤더를 수정 *`.dll`* 하 여 *`.exe`* 64 비트 주소 ASLR에 대 한 지원을 표시 합니다. 효과를 적용 하려면 실행 파일 및 실행 파일이 종속 되는 모든 모듈에 대해 옵션을 설정 합니다. 그런 다음 64 비트 ASLR을 지 원하는 운영 체제에서 임의 64 비트 가상 주소를 사용 하 여 로드 시 실행 가능한 이미지의 세그먼트를 기준으로 다시 지정할 수 있습니다. 이처럼 큰 주소 공간을 사용하는 경우 공격자가 특정 메모리 영역의 위치를 추측하기가 어려워집니다.

기본적으로 링커는 **`/HIGHENTROPYVA`** 64 비트 실행 가능 이미지를 사용 하도록 설정 합니다. 이 옵션에는 [`/DYNAMICBASE`](dynamicbase.md) [`/LARGEADDRESSAWARE`](largeaddressaware.md) 64 비트 이미지에 대해 기본적으로 사용 되는 및가 모두 필요 합니다. **`/HIGHENTROPYVA`** 이 옵션은 무시 되는 32 비트 실행 가능 이미지에는 적용 되지 않습니다. 이 옵션을 명시적으로 사용 하지 않도록 설정 하려면를 사용 **`/HIGHENTROPYVA:NO`** 합니다.

## <a name="see-also"></a>참고 항목

[EDITBIN 옵션](editbin-options.md)\
[`/DYNAMICBASE`](dynamicbase.md)\
[`/LARGEADDRESSAWARE`](largeaddressaware.md)\
[Windows ISV 소프트웨어 보안 방어](/previous-versions/bb430720(v=msdn.10))
