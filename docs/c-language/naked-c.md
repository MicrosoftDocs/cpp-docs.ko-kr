---
description: '자세한 정보: Naked (C)'
title: Naked (C)
ms.date: 11/04/2016
helpviewer_keywords:
- naked keyword [C], storage-class attribute
- naked keyword [C]
- prolog code
- epilog code
ms.assetid: 23b1209b-93ba-46ad-a60f-2327c1933eaf
ms.openlocfilehash: 8d45371f71ccffda2c7505587f0942671d24b047
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97257019"
---
# <a name="naked-c"></a>Naked (C)

**Microsoft 전용**

naked 스토리지 클래스 특성은 Microsoft 전용 C 언어 확장입니다. 컴파일러는 naked 스토리지 클래스 특성으로 선언된 함수의 코드를 프롤로그 및 에필로그 코드 없이 생성합니다. naked 함수는 인라인 어셈블러 코드로 사용자 정의 프롤로그/에필로그 코드 시퀀스를 작성해야 하는 경우 유용합니다. naked 함수는 가상 디바이스 드라이버 작성할 때도 유용합니다.

naked 특성 사용에 대한 자세한 내용은 [Naked 함수](../c-language/naked-functions.md)를 참조하세요.

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[C 확장 스토리지 클래스 특성](../c-language/c-extended-storage-class-attributes.md)
