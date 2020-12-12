---
description: '자세한 정보: 유니코드 및 MBCS'
title: 유니코드 및 멀티바이트 문자 집합(MBCS)
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
ms.openlocfilehash: 4fc5afc447612a3f08067185072cd4f116ab80c3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97114977"
---
# <a name="unicode-and-mbcs"></a>유니코드 및 멀티바이트 문자 집합(MBCS)

Microsoft Foundation Classes (MFC) 라이브러리, Visual C++에 대 한 C 런타임 라이브러리 및 Visual C++ 개발 환경을 사용 하 여 국제 프로그래밍을 지원할 수 있습니다. DSVM에서 제공하는 기능은 다음과 같습니다.

- Windows의 유니코드 표준에 대 한 지원. 유니코드는 현재의 표준이며 어디에서든 항상 사용 가능해야 합니다.

   유니코드는 16 비트 문자 인코딩입니다. 모든 언어에 대해 충분 한 인코딩을 제공 합니다. 모든 ASCII 문자는 유니코드에 확장 문자로 포함 됩니다.

- 모든 플랫폼에서 DBCS (더블 바이트 문자 집합) 라고 하는 MBCS (멀티 바이트 문자 집합) 형식 지원.

   DBCS 문자는 1 또는 2 바이트로 구성 됩니다. 일부 바이트 범위는 선행 바이트로 사용 하도록 따로 설정 되어 있습니다. 선행 바이트는이를 지정 하 고 다음 트레일 바이트는 단일 2 바이트 와이드 문자를 구성 합니다. 선행 바이트 바이트를 추적 해야 합니다. 특정 멀티바이트 문자 집합에서 선행 바이트는 후행 바이트와 마찬가지로 특정 범위 내에 속합니다. 이러한 범위가 겹치면 지정 된 바이트가 선행 바이트 또는 후행 바이트로 작동 하는지 여부를 확인 하기 위해 컨텍스트를 평가 해야 할 수 있습니다.

- 국제 시장을 위해 작성 된 응용 프로그램의 MBCS 프로그래밍을 간소화 하는 도구에 대 한 지원.

   MBCS를 사용 하는 Windows 운영 체제 버전에서 실행 하는 경우 통합 된 소스 코드 편집기, 디버거 및 명령줄 도구를 비롯 한 Visual C++ 개발 시스템은 완전히 MBCS를 사용할 수 있습니다. 자세한 내용은 [Visual C++의 MBCS 지원](../text/mbcs-support-in-visual-cpp.md)을 참조 하세요.

> [!NOTE]
> 이 설명서에서는 MBCS를 사용 하 여 멀티 바이트 문자에 대 한 모든 비유니코드 지원을 설명 합니다. Visual C++에서 MBCS는 항상 DBCS를 의미 합니다. 2 바이트 보다 큰 문자 집합은 지원 되지 않습니다.

정의에 따라 ASCII 문자 집합은 모든 멀티 바이트 문자 집합의 하위 집합입니다. 많은 멀티바이트 문자 집합에서 0x00 - 0x7F 범위의 각 문자는 ASCII 문자 집합에 동일한 값을 가진 문자와 같습니다. 예를 들어, ASCII 및 MBCS 문자열 모두에서 1 바이트 NULL 문자 (' \ 0 ')는 값 0x00을 가지 며 종료 NULL 문자를 나타냅니다.

## <a name="see-also"></a>참고 항목

[텍스트 및 문자열](../text/text-and-strings-in-visual-cpp.md)<br/>
[국제 활성화](../text/international-enabling.md)
