---
description: '자세한 정보: MFC의 파일'
title: MFC의 파일
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 47fab5876efd7d06ec4364721a09b7ed09da9744
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97155048"
---
# <a name="files-in-mfc"></a>MFC의 파일

MFC 라이브러리 (MFC)에서 클래스 [CFile](reference/cfile-class.md) 은 일반적인 파일 i/o 작업을 처리 합니다. 이 문서 제품군에서는 파일을 열고 닫는 방법 뿐만 아니라 해당 파일에 대 한 데이터를 읽고 쓰는 방법을 설명 합니다. 파일 상태 작업에 대해서도 설명 합니다. 파일에서 데이터를 읽고 쓰는 대체 방법으로 MFC의 개체 기반 serialization 기능을 사용 하는 방법에 대 한 설명은 [serialization](serialization-in-mfc.md)문서를 참조 하세요.

> [!NOTE]
> MFC `CDocument` 개체를 사용 하는 경우 프레임 워크에서 많은 serialization 작업을 수행 합니다. 특히 프레임 워크는 개체를 만들고 사용 합니다 `CFile` . 클래스의 멤버 함수 재정의에서 코드를 작성 하기만 하면 `Serialize` `CDocument` 됩니다.

클래스는 범용 `CFile` 이진 파일 작업에 대 한 인터페이스를 제공 합니다. `CStdioFile` `CMemFile` 에서 파생 된 및 클래스 `CFile` 와 `CSharedFile` 에서 파생 된 클래스는 `CMemFile` 보다 특수화 된 파일 서비스를 제공 합니다.

MFC 파일 처리의 대체 방법에 대 한 자세한 내용은 *런타임 라이브러리 참조* 에서 [파일 처리](../c-runtime-library/file-handling.md) 를 참조 하세요.

파생 클래스에 대 한 자세한 내용은 `CFile` [MFC 계층 구조 차트](hierarchy-chart.md)를 참조 하세요.

## <a name="what-do-you-want-to-do"></a>뭘 하고 싶으세요

*CFile 사용*

- [CFile를 사용 하 여 파일 열기](opening-files.md)

- [CFile를 사용 하 여 파일 읽기 및 쓰기](reading-and-writing-files.md)

- [CFile를 사용 하 여 파일 닫기](closing-files.md)

- [CFile를 사용 하 여 파일 상태 액세스](accessing-file-status.md)

*MFC Serialization 사용 (개체 지 속성)*

- [Serializable 클래스 만들기](serialization-making-a-serializable-class.md)

- [CArchive 개체를 통해 개체를 직렬화 합니다.](serialization-serializing-an-object.md)

- [CArchive 개체 만들기](two-ways-to-create-a-carchive-object.md)

- [CArchive <\< and >> 연산자 사용](using-the-carchive-output-and-input-operators.md)

- [아카이브를 통해 CObjects 및 CObject 파생 개체를 저장 하 고 로드 합니다.](storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>참고 항목

[개념](mfc-concepts.md)<br/>
[일반 MFC 항목](general-mfc-topics.md)<br/>
[CArchive 클래스](reference/carchive-class.md)<br/>
[CObject 클래스](reference/cobject-class.md)
