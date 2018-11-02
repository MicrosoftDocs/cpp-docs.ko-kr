---
title: 링커 입력 파일로 사용하는 .Pdb 파일
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 23974a9e20f8259c3a38af15664d328ded7ff7d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628896"
---
# <a name="pdb-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Pdb 파일

/Zi 옵션을 사용 하 여 컴파일된 파일 (.obj) 프로그램 데이터베이스 (PDB)의 이름을 포함 하는 개체입니다. 개체의 링커에 PDB 파일 이름을 지정 하지 않으면 필요한 경우 PDB를 찾을 포함 된 이름을 사용 하는 링크입니다. 이에 적용 됩니다을 라이브러리에 포함 된 디버깅 가능한 개체 디버깅 가능한 라이브러리에 대 한 PDB 링커 라이브러리와 함께 사용할 수 있어야 합니다.

또한 링크.exe 파일이 나.dll 파일에 대 한 디버깅 정보를 저장 하는 PDB를 사용 합니다. 프로그램을 다시 구성 하는 경우 링크 PDB를 업데이트 하기 때문에 프로그램의 PDB는 출력 파일과 입력된 파일입니다.

## <a name="see-also"></a>참고 항목

[LINK 입력 파일](../../build/reference/link-input-files.md)<br/>
[링커 옵션](../../build/reference/linker-options.md)