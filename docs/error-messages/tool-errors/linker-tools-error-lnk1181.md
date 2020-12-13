---
description: '자세한 정보: 링커 도구 오류 LNK1181'
title: 링커 도구 오류 LNK1181
ms.date: 08/22/2018
f1_keywords:
- LNK1181
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
ms.openlocfilehash: bda05d15597d6ed82b12145d380bbe40483d7623
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341687"
---
# <a name="linker-tools-error-lnk1181"></a>링커 도구 오류 LNK1181

' filename ' 입력 파일을 열 수 없습니다.

링커가 `filename` 없거나 경로를 찾을 수 없어서 링커가 찾을 수 없습니다.

오류 LNK1181의 몇 가지 일반적인 원인은 다음과 같습니다.

- `filename` 는 링커 줄에서 추가 종속성으로 참조 되지만 파일이 존재 하지 않습니다.

- 를 포함 하는 디렉터리를 지정 하는 **/libpath** 문이 `filename` 없습니다.

위의 문제를 해결 하려면 링커 줄에서 참조 되는 파일이 시스템에 있는지 확인 합니다.  또한 링커 종속 파일을 포함 하는 각 디렉터리에 대해 **/libpath** 문이 있는지 확인 합니다.

자세한 내용은 [링커 입력 파일로 사용할 .Lib 파일](../../build/reference/dot-lib-files-as-linker-input.md)을 참조 하세요.

LNK1181의 또 다른 가능한 원인은 공백이 포함 된 긴 파일 이름을 따옴표로 묶지 않았기 때문입니다.  이 경우 링커에서는 첫 번째 공간까지 파일 이름만 인식 한 다음 .obj의 파일 확장명을 가정 합니다.  이러한 상황을 해결 하는 방법은 긴 파일 이름 (경로 + 파일 이름)을 따옴표로 묶는 것입니다.

[/P (파일에 대 한 전처리)](../../build/reference/p-preprocess-to-a-file.md) 옵션을 사용 하 여 컴파일하면 .obj 파일 생성을 억제 LNK1181 수 있습니다.

## <a name="see-also"></a>참고 항목

[/LIBPATH (추가 Libpath)](../../build/reference/libpath-additional-libpath.md)
