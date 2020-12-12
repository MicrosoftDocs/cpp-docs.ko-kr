---
description: '자세히 알아보기: 파일 i/o 클래스'
title: 파일 i/o 클래스
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
ms.openlocfilehash: b2a0404864cd63ea3992ebada643b15531bcfc3e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97228016"
---
# <a name="file-io-classes"></a>파일 I/O 클래스

이러한 클래스는 기존 디스크 파일, 메모리 내 파일, 활성 스트림 및 Windows 소켓에 대 한 인터페이스를 제공 합니다. 에서 파생 된 모든 클래스를 `CFile` 개체와 함께 사용 `CArchive` 하 여 serialization을 수행할 수 있습니다.

`CArchive` `CFile` 사용자 고유의 입/출력 처리를 작성 하는 경우, 특히 및 클래스를 사용 합니다. 일반적으로 이러한 클래스에서 파생할 필요가 없습니다. 응용 프로그램 프레임 워크를 사용 하는 경우 문서에서    `CArchive` `Serialize` 내용을 serialize 하는 방법에 대 한 세부 정보를 제공 하기 위해 문서 함수를 재정의 하는 경우 파일 메뉴에서 열기 및 저장 명령의 기본 구현에서는 클래스를 사용 하 여 파일 i/o를 처리 합니다. 파일 클래스 및 serialization에 대 한 자세한 내용은 [MFC의 파일](files-in-mfc.md) 및 [serialization](serialization-in-mfc.md)문서를 참조 하세요.

[CFile](reference/cfile-class.md)<br/>
이진 디스크 파일에 대 한 파일 인터페이스를 제공 합니다.

[CStdioFile](reference/cstdiofile-class.md)<br/>
`CFile`일반적으로 텍스트 모드에서 버퍼링 된 스트림 디스크 파일에 대 한 인터페이스를 제공 합니다.

[CMemFile](reference/cmemfile-class.md)<br/>
`CFile`메모리 내 파일에 대 한 인터페이스를 제공 합니다.

[CSharedFile](reference/csharedfile-class.md)<br/>
`CFile`공유 메모리 내 파일에 대 한 인터페이스를 제공 합니다.

[COleStreamFile](reference/colestreamfile-class.md)<br/>
는 COM 인터페이스를 사용 하 여 `IStream` `CFile` 복합 파일에 대 한 액세스를 제공 합니다.

[CSocketFile](reference/csocketfile-class.md)<br/>
`CFile`Windows 소켓에 대 한 인터페이스를 제공 합니다.

## <a name="related-classes"></a>관련 클래스

[CArchive](reference/carchive-class.md)<br/>
`CFile`Serialization을 통해 개체에 대 한 영구 저장소를 구현 하는 개체를 협력 합니다 ( [CObject:: Serialize](reference/cobject-class.md#serialize)참조).

[CArchiveException](reference/carchiveexception-class.md)<br/>
아카이브 예외입니다.

[CFileException](reference/cfileexception-class.md)<br/>
파일 관련 예외입니다.

[CFileDialog](reference/cfiledialog-class.md)<br/>
파일을 열거나 저장할 때 사용할 표준 대화 상자를 제공 합니다.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
가장 최근에 사용한 (MRU) 파일 목록을 유지 관리 합니다.

## <a name="see-also"></a>참고 항목

[클래스 개요](class-library-overview.md)
