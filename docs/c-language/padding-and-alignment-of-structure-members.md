---
title: 구조체 멤버 채우기 및 맞춤 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb090fc283da0a8aa86dac524272d308127059ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="padding-and-alignment-of-structure-members"></a>구조체 멤버 채우기 및 맞춤
**ANSI 3.5.2.1** 구조체 멤버의 채우기 및 맞춤과 비트 필드가 저장소 단위 경계에 걸쳐 있을 수 있는지 여부  
  
 구조체 멤버는 선언된 순서에 따라 순차적으로 저장됩니다. 즉, 첫 멤버가 가장 낮은 메모리 주소를 갖고 마지막 멤버가 가장 높은 주소를 갖습니다.  
  
 모든 데이터 개체에는 맞춤 요구 사항이 있습니다. 구조체, 공용 구조체 및 배열을 제외한 모든 데이터에 대한 맞춤 요구 사항은 개체의 크기 또는 현재 압축 크기(/Zp 또는 `pack` pragma 중에서 작은 것으로 지정됨)입니다. 구조체, 공용 구조체 및 배열에 대한 맞춤 요구 사항은 해당 멤버의 최대 맞춤 요구 사항입니다. 다음과 같이 되도록 모든 개체에 오프셋이 할당됩니다.  
  
 *offset*  `%` *alignment-requirement* `==` 0  
  
 정수 계열 형식의 크기가 같으며 다음 비트 필드가 비트 필드의 일반 할당 요구 사항에 따라 적용되는 경계를 벗어나지 않고 현재 할당 단위에 맞는 경우 인접 비트 필드는 동일한 1, 2 또는 4바이트 할당 단위로 압축됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [구조체, 공용 구조체, 열거형 및 비트 필드](../c-language/structures-unions-enumerations-and-bit-fields.md)