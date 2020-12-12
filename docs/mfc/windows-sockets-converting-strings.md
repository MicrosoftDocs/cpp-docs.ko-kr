---
description: '자세한 정보: Windows 소켓: 문자열 변환'
title: 'Windows 소켓: 문자열 변환'
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Sockets [MFC], multibyte character string conversion
- sockets [MFC], multibyte character string conversion issues
- string conversion, multibyte character strings
ms.assetid: 9df522b5-6b23-41e0-bb96-e4e623baf141
ms.openlocfilehash: fe8607647192fadc7f0d5d32d7716c222ff9206f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118630"
---
# <a name="windows-sockets-converting-strings"></a>Windows 소켓: 문자열 변환

이 문서 및 두 개의 참조 문서에서는 Windows 소켓 프로그래밍의 몇 가지 문제를 설명합니다. 이 문서에서는 문자열을 변환 하는 방법을 설명 합니다. 다른 문제는 [Windows 소켓: 차단](../mfc/windows-sockets-blocking.md) 및 [Windows 소켓: 바이트 순서](../mfc/windows-sockets-byte-ordering.md)지정에 설명 되어 있습니다.

[Casyncsocket](../mfc/reference/casyncsocket-class.md)클래스를 사용 하거나 클래스에서 파생 하는 경우 이러한 문제를 직접 관리 해야 합니다. 클래스를 사용 하거나 [CSocket](../mfc/reference/csocket-class.md)클래스에서 파생 하는 경우 MFC는 사용자를 위해 관리 합니다.

## <a name="converting-strings"></a>문자열 변환

유니코드 또는 MBCS (멀티 바이트 문자 집합)와 같은 다양 한 와이드 문자 형식으로 저장 된 문자열을 사용 하는 응용 프로그램이 나 이러한 문자열 및 ANSI 문자열을 사용 하는 응용 프로그램 간에 통신 하는 경우에서 변환을 직접 관리 해야 합니다 `CAsyncSocket` . `CArchive`개체와 함께 사용 되는 개체는 `CSocket` [CString](../atl-mfc-shared/reference/cstringt-class.md)클래스의 기능을 통해이 변환을 관리 합니다. 자세한 내용은 Windows SDK에 있는 Windows 소켓 사양을 참조 하십시오.

자세한 내용은 다음을 참조하세요.

- [Windows 소켓: CAsyncSocket 클래스 사용](../mfc/windows-sockets-using-class-casyncsocket.md)

- [Windows 소켓: 소켓과 함께 소켓 사용](../mfc/windows-sockets-using-sockets-with-archives.md)

- [Windows 소켓: 배경](../mfc/windows-sockets-background.md)

- [Windows 소켓: 스트림 소켓](../mfc/windows-sockets-stream-sockets.md)

- [Windows 소켓: 데이터 그램 소켓](../mfc/windows-sockets-datagram-sockets.md)

## <a name="see-also"></a>참고 항목

[MFC의 Windows 소켓](../mfc/windows-sockets-in-mfc.md)
