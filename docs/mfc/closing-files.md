---
description: '자세히 알아보기: 파일 닫기'
title: 파일 닫기
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
ms.openlocfilehash: e8d2f0792aeb889c40cb516af259fc2a40890a1a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338387"
---
# <a name="closing-files"></a>파일 닫기

일반적으로 i/o 작업에서 파일을 완료 한 후 파일을 닫아야 합니다.

#### <a name="to-close-a-file"></a>파일을 닫으려면

1. **Close** 멤버 함수를 사용 합니다. 이 함수는 파일 시스템 파일을 닫고 필요한 경우 버퍼를 플러시합니다.

[파일 열기](opening-files.md)에 표시 된 예제와 같이 프레임에서 [CFile](reference/cfile-class.md) 개체를 할당 한 경우 개체가 자동으로 닫히고 범위를 벗어나면 소멸 됩니다. 개체를 삭제 `CFile` 해도 파일 시스템의 물리적 파일은 삭제 되지 않습니다.

## <a name="see-also"></a>참고 항목

[파일](files-in-mfc.md)
