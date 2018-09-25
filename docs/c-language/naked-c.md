---
title: Naked (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dd6665bafb0041989e99a3a766204555f969d16c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062152"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft 전용**

naked 저장소 클래스 특성은 Microsoft 전용 C 언어 확장입니다. 컴파일러는 naked 저장소 클래스 특성으로 선언된 함수의 코드를 프롤로그 및 에필로그 코드 없이 생성합니다. naked 함수는 인라인 어셈블러 코드로 사용자 정의 프롤로그/에필로그 코드 시퀀스를 작성해야 하는 경우 유용합니다. naked 함수는 가상 장치 드라이버 작성할 때도 유용합니다.

naked 특성 사용에 대한 자세한 내용은 [Naked 함수](../c-language/naked-functions.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참고 항목

[C 확장 저장소 클래스 특성](../c-language/c-extended-storage-class-attributes.md)