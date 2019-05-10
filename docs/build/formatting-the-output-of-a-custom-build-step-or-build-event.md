---
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
ms.openlocfilehash: b0e9a7514704742524f97e55c06ef47c7b36631b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195370"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식 지정

사용자 지정 빌드 단계 또는 빌드 이벤트의 출력 형식이 올바르게 지정된 경우, 사용자는 다음과 같은 이점을 얻을 수 있습니다.

- **출력** 창에는 경고 및 오류가 계수됩니다.

- **작업 목록** 창에는 출력이 나타납니다.

- **출력** 창에서 출력을 클릭하면 해당 토픽이 표시됩니다.

- F1 작업은 **작업 목록** 창 또는 **출력** 창에서 활성화됩니다.

출력 형식은 다음과 같아야 합니다.

> {<em>filename</em>**(**<em>line#</em> \[**,** <em>column#</em>]**)** &#124; *toolname*} **:** \[ <em>any text</em> ] {**error** &#124; **warning**} <em>code+number</em>**:**<em>localizable string</em> \[ <em>any text</em> ]

여기서

- {*a* &#124; *b*}는 *a* 또는 *b* 중에서 선택합니다.

- \[<em>item</em>]는 선택적 문자열 또는 매개 변수입니다.

- **볼드**는 리터럴을 나타냅니다.

예를 들어:

> C:\\*sourcefile.cpp*(134): 오류 C2143: 구문 오류: '}' 앞에 ';' 누락
>
> LINK: 치명적인 오류 LNK1104: '*somelib.lib*' 파일을 열 수 없음

## <a name="see-also"></a>참고자료

[사용자 지정 빌드 단계 및 빌드 이벤트 이해](understanding-custom-build-steps-and-build-events.md)