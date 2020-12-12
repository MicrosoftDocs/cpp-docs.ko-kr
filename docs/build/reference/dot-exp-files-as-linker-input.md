---
description: 에 대해 자세히 알아보세요. 링커 입력 파일로 서의 Exp 파일
title: 링커 입력 파일로 사용하는 .Exp 파일
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 03104d6b4265484e54373484b6c9bbdabf0e1afc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192813"
---
# <a name="exp-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Exp 파일

내보내기 (.exp) 파일에는 내보낸 함수 및 데이터 항목에 대 한 정보가 포함 되어 있습니다. LIB는 가져오기 라이브러리를 만들 때 .exp 파일도 만듭니다. 다른 프로그램에 직접 또는 간접적으로 내보내고 가져오는 프로그램을 연결할 때 .exp 파일을 사용 합니다. .Exp 파일을 사용 하 여 링크 하는 경우 LINK에서는 가져오기 라이브러리를 생성 하지 않습니다 .이 라이브러리는 LIB가 이미 생성 된 것으로 가정 하기 때문입니다. .Exp 파일 및 가져오기 라이브러리에 대 한 자세한 내용은 [가져오기 라이브러리 및 내보내기 파일 작업](working-with-import-libraries-and-export-files.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목

[링크 입력 파일](link-input-files.md)<br/>
[MSVC 링커 옵션](linker-options.md)
