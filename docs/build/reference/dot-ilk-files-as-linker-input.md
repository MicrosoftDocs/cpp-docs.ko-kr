---
description: 에 대해 자세히 알아보세요. 링커 입력 파일로 서의 Ilk 파일
title: 링커 입력 파일로 사용하는 .Ilk 파일
ms.date: 11/04/2016
helpviewer_keywords:
- ILK files
- .ilk files
ms.assetid: 7324c104-9e5d-423d-b268-b59f92607bf2
ms.openlocfilehash: 0aaa5fac19cedb8d94fc6dc9ab03a0f23fa0e49b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192735"
---
# <a name="ilk-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Ilk 파일

증분 링크할 때 링크는 첫 번째 증분 링크 중에 생성 된 .ilk 상태 파일을 업데이트 합니다. 이 파일은 .exe 파일 또는 .dll 파일과 동일한 기본 이름을 가지 며 확장명 .ilk를 가집니다. 후속 증분 링크 중에 링크를 통해 .ilk 파일이 업데이트 됩니다. .Ilk 파일이 없으면 LINK에서 전체 링크를 수행 하 고 새 .ilk 파일을 만듭니다. .Ilk 파일을 사용할 수 없는 경우 LINK는 비증분 링크를 수행 합니다. 증분 링크에 대 한 자세한 내용은 [증분 링크 (/INCREMENTAL)](incremental-link-incrementally.md) 옵션을 참조 하세요.

## <a name="see-also"></a>참고 항목

[링크 입력 파일](link-input-files.md)<br/>
[MSVC 링커 옵션](linker-options.md)
