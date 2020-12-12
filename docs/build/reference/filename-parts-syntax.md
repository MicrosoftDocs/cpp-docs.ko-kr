---
description: Filename-Parts 구문에 대해 자세히 알아보세요.
title: 파일 이름 부분 구문
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, filename-parts
- filename-parts syntax in NMAKE
- NMAKE program, syntax
ms.assetid: 48fe38e0-3f3b-40e6-894c-330ee775a656
ms.openlocfilehash: 436481d52324b4c638b5fa0a9840ce0d9ef654f4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192137"
---
# <a name="filename-parts-syntax"></a>파일 이름 부분 구문

명령의 파일 이름 부분 구문은 첫 번째 종속 파일 이름의 구성 요소를 나타냅니다 (묵시적 종속 파일 일 수 있음). 파일 이름 구성 요소는 디스크에 존재 하지 않고 지정 된 파일의 드라이브, 경로, 기본 이름 및 확장명입니다. **% S을 (를)** 사용 하 여 전체 파일 이름을 표시 합니다. **% &#124;**[*parts*]**F** 를 사용 합니다. (세로 막대 문자는 백분율 기호 뒤에 오는) 파일 이름의 일부를 나타냅니다. 여기서 *부분은* 임의의 순서로 다음 문자를 0 개 이상 사용할 수 있습니다.

|Letter|설명|
|------------|-----------------|
|문자 없음|전체 이름 ( **% s** 과 (와) 같음)|
|**d**|드라이브|
|**®**|경로|
|**f**|파일 기본 이름|
|**e**|파일 확장명|

예를 들어 파일 이름이 c:\prog.exe 경우:

- % s이 (가) c:\prog.exe 됩니다.

- % &#124;F c:\prog.exe 됩니다.

- % &#124;dF는 c입니다.

- % &#124;pF는 c:\

- % &#124;fF를 사용할 수 있습니다.

- % &#124;eF가 exe가 됩니다.

## <a name="see-also"></a>참고 항목

[메이크파일의 명령](commands-in-a-makefile.md)
