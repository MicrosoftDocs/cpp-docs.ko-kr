---
title: sample container 구성원 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- container classes
ms.assetid: dc5a1998-a31b-4adf-b888-8abe5b87a4e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7c844416151874714aa86a2ffe9762949c6a62a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/08/2018
---
# <a name="sample-container-members"></a>샘플 컨테이너 멤버

> [!NOTE]
> 이 항목은 C++ 표준 라이브러리에서 사용되는 작동하지 않는 컨테이너 예제로 Visual C++ 설명서에 포함되어 있습니다. 자세한 내용은 [C++ 표준 라이브러리 컨테이너](../standard-library/stl-containers.md)를 참조하세요.

## <a name="reference"></a>참조

## <a name="typedefs"></a>형식 정의

|||
|-|-|
|[const_iterator](../standard-library/container-class-const-iterator.md)|제어되는 시퀀스의 상수 반복기로 사용될 수 있는 개체를 설명합니다.|
|[const_reference](../standard-library/container-class-const-reference.md)|제어되는 시퀀스의 요소에 대한 상수 참조로 사용될 수 있는 개체를 설명합니다.|
|[const_reverse_iterator](../standard-library/container-class-const-reverse-iterator.md)|제어되는 시퀀스의 상수 역방향 반복기로 사용될 수 있는 개체를 설명합니다.|
|[difference_type](../standard-library/container-class-difference-type.md)|제어되는 시퀀스에서 두 요소의 주소 간 차이점을 나타낼 수 있는 개체를 설명합니다.|
|[iterator](../standard-library/container-class-iterator.md)|제어되는 시퀀스의 반복기로 사용될 수 있는 개체를 설명합니다.|
|[reference](../standard-library/container-class-reference.md)|제어되는 시퀀스의 요소에 대한 참조로 사용될 수 있는 개체를 설명합니다.|
|[reverse_iterator](../standard-library/container-class-reverse-iterator.md)|제어되는 시퀀스의 역방향 반복기로 사용될 수 있는 개체를 설명합니다.|
|[size_type](../standard-library/container-class-size-type.md)|제어되는 시퀀스의 길이를 나타낼 수 있는 개체를 설명합니다.|
|[value_type](../standard-library/container-class-value-type.md)|템플릿 매개 변수 **Ty**와 동일한 의미로 사용됩니다.|

## <a name="member-functions"></a>멤버 함수

|||
|-|-|
|[begin](../standard-library/container-class-begin.md)|시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 반복기를 반환합니다.|
|[clear](../standard-library/container-class-clear.md)|[erase](../standard-library/container-class-erase.md)( [begin](../standard-library/container-class-begin.md), [end](../standard-library/container-class-end.md))를 호출합니다.|
|[empty](../standard-library/container-class-empty.md)|빈 제어되는 시퀀스에 대해 **true**를 반환합니다.|
|[end](../standard-library/container-class-end.md)|시퀀스 끝의 바로 다음을 가리키는 반복기를 반환합니다.|
|[erase](../standard-library/container-class-erase.md)|요소를 지웁니다.|
|[max_size](../standard-library/container-class-max-size.md)|개체가 제어할 수 있는 가장 긴 시퀀스의 길이를 제어되는 시퀀스의 길이와 관계없이 상수 시간으로 반환합니다.|
|[rbegin](../standard-library/container-class-rbegin.md)|제어되는 시퀀스의 끝 바로 다음을 가리키는 역방향 반복기를 반환하여 역방향 시퀀스의 시작을 지정합니다.|
|[rend](../standard-library/container-class-rend.md)|구성원 함수는 시퀀스의 첫 번째 요소(또는 빈 시퀀스의 끝 바로 다음)를 가리키는 역방향 반복기를 반환하여 역방향 시퀀스의 끝을 지정합니다.|
|[size](../standard-library/container-class-size.md)|제어되는 시퀀스의 길이를 제어되는 시퀀스의 길이와 관계없이 상수 시간으로 반환합니다.|
|[swap](../standard-library/container-class-swap.md)
