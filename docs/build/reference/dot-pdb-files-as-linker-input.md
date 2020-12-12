---
description: 에 대해 자세히 알아보세요. 링커 입력 파일로 서의 Pdb 파일
title: 링커 입력 파일로 사용하는 .Pdb 파일
ms.date: 11/04/2016
helpviewer_keywords:
- .pdb files, as linker input
- PDB files, as linker input
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
ms.openlocfilehash: 713d42e7e95b5d1e7e3b1f9be21203b75569cdbe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201159"
---
# <a name="pdb-files-as-linker-input"></a>링커 입력 파일로 사용하는 .Pdb 파일

/Zi 옵션을 사용 하 여 컴파일된 개체 (.obj) 파일에는 PDB (프로그램 데이터베이스)의 이름이 포함 됩니다. 링커에 대 한 개체의 PDB 파일 이름을 지정 하지 않습니다. LINK는 포함 된 이름을 사용 하 여 필요한 경우 PDB를 찾습니다. 이는 라이브러리에 포함 된 디버깅 가능한 개체에도 적용 됩니다. 디버깅할 수 있는 라이브러리에 대 한 PDB는 라이브러리와 함께 링커에서 사용할 수 있어야 합니다.

또한이 링크는 PDB를 사용 하 여 .exe 파일이 나 .dll 파일에 대 한 디버깅 정보를 저장 합니다. 프로그램의 PDB는 프로그램이 프로그램을 다시 작성할 때 PDB를 업데이트 하기 때문에 출력 파일 및 입력 파일입니다.

## <a name="see-also"></a>참고 항목

[링크 입력 파일](link-input-files.md)<br/>
[MSVC 링커 옵션](linker-options.md)
