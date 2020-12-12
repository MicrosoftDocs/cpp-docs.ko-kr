---
description: '자세한 정보: CSocketFile 클래스'
title: CSocketFile 클래스
ms.date: 11/04/2016
f1_keywords:
- CSocketFile
- AFXSOCK/CSocketFile
- AFXSOCK/CSocketFile::CSocketFile
helpviewer_keywords:
- CSocketFile [MFC], CSocketFile
ms.assetid: 7924c098-5f72-40d6-989d-42800a47958f
ms.openlocfilehash: 4ca484545e11502a11acf5f27b00ee2df49fc9d6
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97318652"
---
# <a name="csocketfile-class"></a>CSocketFile 클래스

Windows 소켓을 통해 네트워크에서 데이터를 보내고 받는 데 사용되는 `CFile` 개체입니다.

## <a name="syntax"></a>구문

```
class CSocketFile : public CFile
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CSocketFile:: CSocketFile](#csocketfile)|`CSocketFile` 개체를 생성합니다.|

## <a name="remarks"></a>설명

`CSocketFile`이 목적을 위해 개체를 개체에 연결할 수 있습니다 `CSocket` . 또한 일반적으로 개체를 개체에 연결 하 여 `CSocketFile` `CArchive` MFC serialization을 사용 하 여 데이터를 쉽게 보내고 받을 수 있습니다.

데이터를 serialize (전송) 하려면 `CSocketFile` 개체에 데이터를 쓰는 멤버 함수를 호출 하는 보관 파일에 삽입 합니다 `CSocket` . 데이터를 deserialize (수신) 하려면 보관 파일에서 추출 합니다. 이렇게 하면 archive가 멤버 함수를 호출 하 여 `CSocketFile` 개체에서 데이터를 읽습니다 `CSocket` .

> [!TIP]
> 여기에 설명 된 대로를 사용 하는 것 외에도, `CSocketFile` 기본 클래스와 마찬가지로를 사용 하 여 독립 실행형 파일 개체로 사용할 수 있습니다 `CFile` . `CSocketFile`모든 보관 기반 MFC 직렬화 함수와 함께를 사용할 수도 있습니다. `CSocketFile`는의 모든 기능을 지원 하지 않기 때문에 `CFile` 일부 기본 MFC 직렬화 함수는와 호환 되지 않습니다 `CSocketFile` . 이는 특히 클래스에 적용 됩니다 `CEditView` . 를 `CEditView` `CArchive` 사용 하 여 개체에 연결 된 개체를 통해 데이터를 직렬화 할 수 없습니다. `CSocketFile` `CEditView::SerializeRaw` 대신를 사용 하십시오 `CEditView::Serialize` . `SerializeRaw`함수는 파일 개체에와 같이가 없는 함수를 포함 하는 것으로 예상 합니다 `Seek` `CSocketFile` .

및와 함께를 사용 하는 경우에서 `CArchive` `CSocketFile` 요청 된 `CSocket` `CSocket::Receive` 바이트 크기를 대기 하는 루프 ()를 입력 하는 상황이 발생할 수 있습니다 `PumpMessages(FD_READ)` . 이는 Windows 소켓이 FD_READ 알림 당 하나의 수신 호출만 허용 하기 때문 이며, `CSocketFile` `CSocket` FD_READ 당 여러 recv 호출을 허용 하기 때문입니다. 읽을 데이터가 없는 경우 FD_READ 발생 하면 응용 프로그램이 중단 됩니다. 다른 FD_READ를 얻지 못한 경우 응용 프로그램은 소켓을 통한 통신을 중지 합니다.

이 문제는 다음과 같이 해결할 수 있습니다. `OnReceive`소켓 클래스의 메서드에서 `CAsyncSocket::IOCtl(FIONREAD, ...)` `Serialize` 소켓에서 읽을 예상 데이터가 하나의 TCP 패킷 크기를 초과 하는 경우 (일반적으로 1096 바이트 이상 네트워크 미디어의 최대 전송 단위) 메시지 클래스의 메서드를 호출 하기 전에를 호출 합니다. 사용 가능한 데이터의 크기가 필요한 것 보다 작은 경우 모든 데이터를 받을 때까지 기다렸다가 읽기 작업을 시작 합니다.

다음 예제에서 `m_dwExpected` 은 사용자가 받으려는 예상 바이트 수입니다. 코드의 다른 곳에서 선언 하는 것으로 가정 합니다.

[!code-cpp[NVC_MFCSocketThread#4](../../mfc/reference/codesnippet/cpp/csocketfile-class_1.cpp)]

자세한 내용은 [MFC의 Windows 소켓](../../mfc/windows-sockets-in-mfc.md), [Windows 소켓: 보관 파일과 함께 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)및 [windows 소켓 2 API](/windows/win32/WinSock/windows-sockets-start-page-2)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CSocketFile`

## <a name="requirements"></a>요구 사항

**헤더:** afxsock

## <a name="csocketfilecsocketfile"></a><a name="csocketfile"></a> CSocketFile:: CSocketFile

`CSocketFile` 개체를 생성합니다.

```
explicit CSocketFile(
    CSocket* pSocket,
    BOOL bArchiveCompatible = TRUE);
```

### <a name="parameters"></a>매개 변수

*pSocket*<br/>
개체에 연결할 소켓 `CSocketFile` 입니다.

*bArchiveCompatible*<br/>
파일 개체가 개체와 함께 사용 되는지 여부를 지정 합니다 `CArchive` . `CSocketFile`특정 제한 사항과 함께 독립 실행형 개체와 마찬가지로 독립 실행형 방식으로 개체를 사용 하려는 경우에만 FALSE를 전달 합니다 `CFile` . 이 플래그는 `CArchive` 개체에 연결 된 개체가 읽기 위해 버퍼를 관리 하는 방식을 변경 `CSocketFile` 합니다.

### <a name="remarks"></a>설명

개체가 범위를 벗어나면 개체의 소멸자가 소켓 개체에서 자신을 분리 하거나 삭제 합니다.

> [!NOTE]
> 는 `CSocketFile` 개체 없이 (제한 된) 파일로도 사용할 수 있습니다 `CArchive` . 기본적으로 `CSocketFile` 생성자의 *bArchiveCompatible* 매개 변수는 TRUE입니다. 이는 파일 개체를 보관에 사용할 수 있도록 지정 합니다. Archive 없이 file 개체를 사용 하려면 *bArchiveCompatible* 매개 변수에서 FALSE를 전달 합니다.

"보관 호환" 모드에서 `CSocketFile` 개체는 더 나은 성능을 제공 하 고 "교착 상태"의 위험을 줄입니다. 교착 상태는 송신 및 수신 소켓이 모두 대기 중이거나 공용 리소스인 경우에 발생 합니다. 이 상황은 개체가 개체를 사용 하는 `CArchive` 방식으로 작동 하는 경우에 발생할 수 있습니다 `CSocketFile` `CFile` . 에서 `CFile` 보관은 요청 된 것 보다 더 짧은 바이트를 수신 하는 경우 파일의 끝에 도달한 것으로 간주할 수 있습니다.

그러나를 사용 하는 경우 `CSocketFile` 데이터는 메시지를 기반으로 합니다. 버퍼는 여러 메시지를 포함할 수 있으므로 요청 된 바이트 수를 초과 하면 파일의 끝을 의미 하지 않습니다. 이 경우 응용 프로그램은에서와 같이 차단 하지 않으며 `CFile` 버퍼가 비어 있을 때까지 버퍼에서 메시지를 계속 읽을 수 있습니다. [CArchive:: IsBufferEmpty](../../mfc/reference/carchive-class.md#isbufferempty) 함수는 이러한 경우 보관의 버퍼 상태를 모니터링 하는 데 유용 합니다.

을 사용 하는 방법에 대 한 자세한 내용은 `CSocketFile` [windows 소켓:](../../mfc/windows-sockets-using-sockets-with-archives.md) 아카이브를 [사용 하는 소켓의 예:](../../mfc/windows-sockets-example-of-sockets-using-archives.md)보관을 사용 하는 소켓의 예 문서를 참조 하세요.

## <a name="see-also"></a>참고 항목

[CFile 클래스](../../mfc/reference/cfile-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CAsyncSocket 클래스](../../mfc/reference/casyncsocket-class.md)<br/>
[CSocket 클래스](../../mfc/reference/csocket-class.md)
