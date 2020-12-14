---
description: '자세한 정보: Module-Definition 문의 규칙'
title: 모듈 정의 문의 규칙
ms.date: 11/04/2016
f1_keywords:
- .def
helpviewer_keywords:
- module definition files, statement syntax
- module definition files
ms.assetid: f65cd3a7-65d7-4d06-939f-a8b1ecd50f2d
ms.openlocfilehash: bca1f279a9a93690edeaabc2264d1cfe869b3e80
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97225000"
---
# <a name="rules-for-module-definition-statements"></a>모듈 정의 문의 규칙

다음 구문 규칙은 .def 파일의 모든 문에 적용 됩니다. 특정 문에 적용 되는 다른 규칙은 각 문으로 설명 됩니다.

- 문, 특성 키워드 및 사용자 지정 식별자는 대/소문자를 구분 합니다.

- 공백이 나 세미콜론을 포함 하는 긴 파일 이름 (;) 따옴표 (")로 묶어야 합니다.

- 하나 이상의 공백, 탭 또는 줄 바꿈 문자를 사용 하 여 문 키워드와 인수를 구분 하 고 서로 다른 문을 사용 합니다. 콜론 (:) 인수를 지정 하는 등호 (=)는 0 개 이상의 공백, 탭 또는 줄 바꿈 문자로 둘러싸여 있습니다.

- **이름** 또는 **라이브러리** 문이 사용 되는 경우 다른 모든 문 앞에와 야 합니다.

- **섹션과** **내보내기** 문은 .def 파일에 두 번 이상 나타날 수 있습니다. 각 문은 하나 이상의 공백, 탭 또는 줄 바꿈 문자로 구분 되어야 하는 여러 사양을 사용할 수 있습니다. Statement 키워드는 첫 번째 사양 앞에 한 번만 표시 되어야 하며 각 추가 사양 전에 반복 될 수 있습니다.

- 많은 문에는 동일한 링크 명령줄 옵션이 있습니다. 자세한 내용은 해당 링크 옵션에 대 한 설명을 참조 하십시오.

- .Def 파일의 주석은 세미콜론 (;) 각 주석 줄의 시작 부분에 있습니다. 주석은 문과 함께 줄을 공유할 수 없지만 여러 줄 문의 사양 사이에 나타날 수 있습니다. (**섹션과** **내보내기** 는 여러 줄 문입니다.)

- 숫자 인수는 base 10 또는 16 진수로 지정 됩니다.

- 문자열 인수가 [예약어](reserved-words.md)와 일치 하는 경우 큰따옴표 (")로 묶어야 합니다.

## <a name="see-also"></a>참고 항목

[모듈 정의 (. Def) 파일](module-definition-dot-def-files.md)
