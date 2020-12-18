---
description: '자세한 정보: 순수 가상 구현'
title: 순수 가상 구현
ms.date: 11/16/2016
ms.assetid: ea9b4719-34a3-474a-b4ec-05b1859f80f1
ms.openlocfilehash: b35ebba556ed9bae6ded649caca000b7d3554480
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318756"
---
# <a name="implement-pure-virtuals"></a>순수 가상 구현

**대상:** 클래스의 모든 순수 가상 메서드를 구현하는 데 필요한 코드를 즉시 생성할 수 있습니다.

**시기:** 순수 가상 함수가 있는 클래스에서 상속받으려는 경우.

**이유:** 모든 순수 가상 함수를 하나씩 수동으로 구현할 수 있지만 이 기능은 모든 메서드 시그니처를 자동으로 생성합니다.

**방법:**

1. 기본 클래스의 순수 가상 함수를 구현할 클래스 위에 텍스트 또는 마우스 커서를 놓습니다.

   ![강조 표시된 코드](images/virtuals_highlight.png)

1. 다음 작업 중 하나를 수행합니다.
   * **키보드**
     * **Ctrl+.** 를 눌러 상황에 맞는 메뉴에서 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 **'*ClassName*' 클래스의 모든 순수 가상 구현** 을 선택합니다. 여기서 *ClassName* 은 선택된 클래스의 이름입니다.
   * **마우스**
     * 상황에 맞는 메뉴에서 마우스 오른쪽 단추를 클릭하고, **빠른 작업 및 리팩터링** 메뉴를 선택하고, **'*ClassName*' 클래스의 모든 순수 가상 구현** 을 선택합니다. 여기서 *ClassName* 은 선택된 클래스의 이름입니다.

1. 순수 가상 메서드 시그니처가 자동으로 만들어지고 구현할 준비가 됩니다.

   ![순수 가상 구현 결과](images/virtuals_result.png)
