---
description: '자세한 정보: 사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식 지정'
title: 사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식 지정
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: c2631e3c6cbd8e66d88527ff75ff7bcac9869b4f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97156426"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식 지정

사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식이 올바르게 지정된 경우, 사용자는 다음과 같은 이점을 얻을 수 있습니다.

- **출력** 창에는 경고 및 오류가 계수됩니다.

- **작업 목록** 창에는 출력이 나타납니다.

- **출력** 창에서 출력을 클릭하면 해당 토픽이 표시됩니다.

- F1 작업은 **작업 목록** 창 또는 **출력** 창에서 활성화됩니다.

출력 형식은 다음과 같아야 합니다.

> {<em>파일 이름</em> **(** <em>줄#</em> \[ **,** <em>열#</em>] **)** &#124; *도구 이름*} **:** \[ <em>텍스트</em> ] {**오류** &#124; **경고**} <em>코드+수</em> **:** <em>지역화 가능한 문자열</em> \[ <em>텍스트</em> ]

여기서

- {*a* &#124; *b*}는 *a* 또는 *b* 중에서 선택합니다.

- \[<em>item</em>]는 선택적 문자열 또는 매개 변수입니다.

- **볼드** 는 리터럴을 나타냅니다.

예를 들어:

> C:\\*sourcefile.cpp*(134): 오류 C2143: 구문 오류: '}' 앞에 ';' 누락
>
> LINK: 치명적인 오류 LNK1104: '*somelib.lib*' 파일을 열 수 없음

## <a name="see-also"></a>참조

[사용자 지정 빌드 단계 및 빌드 이벤트 이해](understanding-custom-build-steps-and-build-events.md)
