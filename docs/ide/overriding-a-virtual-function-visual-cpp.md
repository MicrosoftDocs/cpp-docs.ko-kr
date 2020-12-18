---
description: '자세한 정보: 가상 함수 재정의'
title: 가상 함수 재정의
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.virtualfunc.override
helpviewer_keywords:
- virtual functions, overriding
- base classes, overriding virtual functions defined in
- Properties window, overriding virtual functions in
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
ms.openlocfilehash: d4c800006d5227ed5397c17284c03968a24a3964
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335914"
---
# <a name="override-a-virtual-function"></a>가상 함수 재정의

Visual Studio [속성 창](/visualstudio/ide/reference/properties-window)에서 기본 클래스에 정의된 가상 함수를 재정의할 수 있습니다.

**속성 창에서 가상 함수를 재정의하려면:**

1. 클래스 뷰에서 클래스를 선택합니다.

1. 속성 창에서 **재정의** 단추를 선택합니다.

   > [!NOTE]
   > 클래스 뷰에서 클래스 이름을 선택하거나 원본 창 내에서 선택하면 **재정의** 단추를 사용할 수 있습니다.

   왼쪽 열은 가상 함수를 나열합니다. 가상 함수의 이름이 오른쪽 열에도 나타나면 재정의가 이미 구현된 것입니다.

1. 함수에 재정의가 없는 경우 속성 창에서 오른쪽 열에 있는 셀을 선택하여 \<add>*FuncName* 과 같은 제안된 함수 재정의의 이름을 표시합니다.

1. 제안된 이름을 선택하여 함수의 스텁 코드를 추가합니다.

1. 재정의 함수를 편집하려면 클래스 뷰에서 함수 이름을 두 번 클릭하고 소스 창에서 코드를 편집합니다.

재정의를 제거하려면 오른쪽 열의 재정의 함수 이름을 선택하고 \<delete>*FuncName* 을 선택합니다. 함수의 코드는 주석으로 처리됩니다.
