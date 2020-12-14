---
description: '자세한 정보: 컴파일러 경고 C4746'
title: 컴파일러 경고 C4746
ms.date: 11/04/2016
f1_keywords:
- C4746
helpviewer_keywords:
- C4746
ms.assetid: 5e79ab46-6031-499a-a986-716c866b6c0e
ms.openlocfilehash: 09c6b6968e7180e19955d84fdb69c9113509c39c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315038"
---
# <a name="compiler-warning-c4746"></a>컴파일러 경고 C4746

' '의 volatile 액세스 \<expression> 에는/volatile: [iso&#124;ms] 설정이 적용 됩니다. __iso_volatile_load/store 내장 함수를 사용 하십시오.

C4746은 volatile 변수에 직접 액세스할 때마다 발생합니다. 이는 개발자가 현재 지정 된 특정 휘발성 모델 ( [/volatile](../../build/reference/volatile-volatile-keyword-interpretation.md) 컴파일러 옵션을 사용 하 여 제어할 수 있음)의 영향을 받는 코드 위치를 식별 하는 데 도움을 주기 위한 것입니다. 특히, /volatile:ms가 사용될 경우에는 컴파일러에서 생성된 하드웨어 메모리 장벽을 찾는데 유용할 수 있습니다.

__iso_volatile_load/store 내장 함수를 사용하면 volatile 모델의 영향을 받지 않고 volatile 메모리에 명시적으로 액세스할 수 있습니다. 이러한 내장 함수를 사용하면 C4746가 트리거되지 않습니다.

기본적으로 이 경고는 해제되어 있습니다. 자세한 내용은 [기본적으로 해제되어 있는 컴파일러 경고](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 를 참조하세요.
