---
description: '자세히 알아보기: 파일 읽기 및 쓰기'
title: 파일 읽기 및 쓰기
ms.date: 11/04/2016
helpviewer_keywords:
- CFile class [MFC], objects
- examples [MFC], reading files
- files [MFC], writing to
- examples [MFC], writing to files
- files [MFC], reading
- MFC, file operations
- CFile class [MFC], reading and writing CFile objects
- reading files
- writing to files [MFC]
ms.assetid: cac0c826-ba56-495f-99b3-ce6336f65763
ms.openlocfilehash: 169135f57eaecb52605eca88b7f19e333551f1ad
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248621"
---
# <a name="reading-and-writing-files"></a>파일 읽기 및 쓰기

C 런타임 라이브러리 파일 처리 함수를 사용한 경우 MFC 읽기 및 쓰기 작업은 친숙 하 게 표시 됩니다. 이 문서에서는 개체에서 직접 읽고 개체에 직접 쓰는 방법을 설명 합니다 `CFile` . 또한 [CArchive](../mfc/reference/carchive-class.md) 클래스를 사용 하 여 버퍼링 된 파일 i/o를 수행할 수 있습니다.

#### <a name="to-read-from-and-write-to-the-file"></a>파일을 읽고 파일에 쓰려면

1. `Read`및 `Write` 멤버 함수를 사용 하 여 파일에서 데이터를 읽고 씁니다.

     또는

1. `Seek`멤버 함수는 파일 내의 특정 오프셋으로 이동 하는 데에도 사용할 수 있습니다.

`Read` 버퍼에 대 한 포인터와 읽을 바이트 수를 사용 하 고 읽은 실제 바이트 수를 반환 합니다. EOF (파일 끝)에 도달 하 여 필요한 바이트 수를 읽을 수 없는 경우 실제 읽은 바이트 수가 반환 됩니다. 읽기 오류가 발생 하는 경우 예외가 throw 됩니다. `Write` 는와 비슷하지만 `Read` 쓴 바이트 수는 반환 되지 않습니다. 지정 된 모든 바이트를 쓰지 않는 등 쓰기 오류가 발생 하면 예외가 throw 됩니다. 유효한 개체가 있는 경우 `CFile` 다음 예제와 같이 개체를 읽거나 쓸 수 있습니다.

[!code-cpp[NVC_MFCFiles#2](../atl-mfc-shared/reference/codesnippet/cpp/reading-and-writing-files_1.cpp)]

> [!NOTE]
> 일반적으로 **`try`** / 예외 처리 블록 내에서 입/출력 작업을 수행 해야 합니다 **`catch`** . 자세한 내용은 [예외 처리 (MFC)](../mfc/exception-handling-in-mfc.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[파일](../mfc/files-in-mfc.md)
