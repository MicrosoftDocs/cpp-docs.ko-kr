---
description: '다음에 대 한 자세한 정보: CArchive 클래스'
title: CArchive 클래스
ms.date: 11/04/2016
f1_keywords:
- CArchive
- AFX/CArchive
- AFX/CArchive::CArchive
- AFX/CArchive::Abort
- AFX/CArchive::Close
- AFX/CArchive::Flush
- AFX/CArchive::GetFile
- AFX/CArchive::GetObjectSchema
- AFX/CArchive::IsBufferEmpty
- AFX/CArchive::IsLoading
- AFX/CArchive::IsStoring
- AFX/CArchive::MapObject
- AFX/CArchive::Read
- AFX/CArchive::ReadClass
- AFX/CArchive::ReadObject
- AFX/CArchive::ReadString
- AFX/CArchive::SerializeClass
- AFX/CArchive::SetLoadParams
- AFX/CArchive::SetObjectSchema
- AFX/CArchive::SetStoreParams
- AFX/CArchive::Write
- AFX/CArchive::WriteClass
- AFX/CArchive::WriteObject
- AFX/CArchive::WriteString
- AFX/CArchive::m_pDocument
helpviewer_keywords:
- CArchive [MFC], CArchive
- CArchive [MFC], Abort
- CArchive [MFC], Close
- CArchive [MFC], Flush
- CArchive [MFC], GetFile
- CArchive [MFC], GetObjectSchema
- CArchive [MFC], IsBufferEmpty
- CArchive [MFC], IsLoading
- CArchive [MFC], IsStoring
- CArchive [MFC], MapObject
- CArchive [MFC], Read
- CArchive [MFC], ReadClass
- CArchive [MFC], ReadObject
- CArchive [MFC], ReadString
- CArchive [MFC], SerializeClass
- CArchive [MFC], SetLoadParams
- CArchive [MFC], SetObjectSchema
- CArchive [MFC], SetStoreParams
- CArchive [MFC], Write
- CArchive [MFC], WriteClass
- CArchive [MFC], WriteObject
- CArchive [MFC], WriteString
- CArchive [MFC], m_pDocument
ms.assetid: 9e950d23-b874-456e-ae4b-fe00781a7699
ms.openlocfilehash: bcae8d18503c5ef4acce965f720b947bb1c706ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97118760"
---
# <a name="carchive-class"></a>CArchive 클래스

개체를 삭제 한 후 유지 되는 영구 이진 형식 (일반적으로 디스크 저장소)으로 복잡 한 개체의 네트워크를 저장할 수 있습니다.

## <a name="syntax"></a>구문

```
class CArchive
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CArchive::CArchive](#carchive)|`CArchive` 개체를 만듭니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CArchive:: Abort](#abort)|예외를 throw 하지 않고 아카이브를 닫습니다.|
|[CArchive::Close](#close)|기록 되지 않은 데이터를 플러시하고에서 연결을 끊습니다 `CFile` .|
|[CArchive::Flush](#flush)|보관 버퍼에서 기록 되지 않은 데이터를 플러시합니다.|
|[CArchive:: GetFile](#getfile)|`CFile`이 보관에 대 한 개체 포인터를 가져옵니다.|
|[CArchive::GetObjectSchema](#getobjectschema)|Deserialize 되는 `Serialize` 개체의 버전을 확인 하기 위해 함수에서 호출 됩니다.|
|[CArchive:: IsBufferEmpty](#isbufferempty)|Windows 소켓 수신 프로세스 중 버퍼가 비어 있는지 여부를 확인 합니다.|
|[CArchive::IsLoading](#isloading)|보관 파일이 로드 되 고 있는지 여부를 확인 합니다.|
|[CArchive:: IsStoring](#isstoring)|보관 파일을 저장 하 고 있는지 여부를 확인 합니다.|
|[CArchive::MapObject](#mapobject)|파일에 serialize 되지 않지만 하위 개체에서 참조할 수 있는 개체를 맵에 배치 합니다.|
|[CArchive::Read](#read)|원시 바이트를 읽습니다.|
|[CArchive:: ReadClass](#readclass)|이전에를 사용 하 여 저장 한 클래스 참조를 읽습니다 `WriteClass` .|
|[CArchive::ReadObject](#readobject)|`Serialize`로드에 대 한 개체의 함수를 호출 합니다.|
|[CArchive::ReadString](#readstring)|텍스트 한 줄을 읽습니다.|
|[CArchive:: SerializeClass](#serializeclass)|`CArchive`의 방향에 따라 개체에 대 한 클래스 참조를 읽거나 씁니다 `CArchive` .|
|[CArchive::SetLoadParams](#setloadparams)|로드 배열이 증가 하는 크기를 설정 합니다. 개체를 로드 하거나 `MapObject` 또는를 호출 하기 전에를 호출 해야 합니다 `ReadObject` .|
|[CArchive:: SetObjectSchema](#setobjectschema)|보관 개체에 저장 된 개체 스키마를 설정 합니다.|
|[CArchive:: SetStoreParams 매개 변수](#setstoreparams)|Serialization 프로세스 중에 고유 개체를 식별 하는 데 사용 되는 맵의 블록 크기와 해시 테이블 크기를 설정 합니다.|
|[CArchive::Write](#write)|원시 바이트를 씁니다.|
|[CArchive:: WriteClass](#writeclass)|에 대 한 참조를에 씁니다 `CRuntimeClass` `CArchive` .|
|[CArchive::WriteObject](#writeobject)|`Serialize`저장을 위해 개체의 함수를 호출 합니다.|
|[CArchive::WriteString](#writestring)|텍스트 한 줄을 씁니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CArchive:: operator &lt;&lt;](#operator_lt_lt)|개체 및 기본 형식을 보관 파일에 저장 합니다.|
|[CArchive:: operator &gt;&gt;](#operator_gt_gt)|보관 파일에서 개체 및 기본 형식을 로드 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CArchive:: m_pDocument](#m_pdocument)||

## <a name="remarks"></a>설명

`CArchive` 에 기본 클래스가 없습니다.

나중에 영구적 저장소에서 개체를 로드 하 여 메모리에 reconstituting 수 있습니다. 이러한 데이터를 영구적으로 만드는 프로세스를 "serialization" 이라고 합니다.

보관 개체를 일종의 이진 스트림으로 간주할 수 있습니다. 입/출력 스트림 처럼 보관 파일은 파일과 연결 되며 버퍼링 된 데이터 쓰기 및 저장소에서의 데이터 읽기를 허용 합니다. 입/출력 스트림은 ASCII 문자 시퀀스를 처리 하지만, 아카이브는 이진 개체 데이터를 효율적이 고 nonredundant 형식으로 처리 합니다.

개체를 만들려면 먼저 [CFile](../../mfc/reference/cfile-class.md) 개체를 만들어야 합니다 `CArchive` . 또한 아카이브의 로드/저장소 상태가 파일의 열기 모드와 호환 되는지 확인 해야 합니다. 한 번에 하나의 활성 보관 파일로 제한 됩니다.

개체를 생성 하는 경우에는 `CArchive` `CFile` 열려 있는 파일을 나타내는 클래스 또는 파생 클래스의 개체에 개체를 연결 합니다. 또한 보관을 사용 하 여 로드 하거나 저장할 것인지 여부도 지정 합니다. `CArchive`개체는 기본 형식 뿐만 아니라 serialization을 위해 설계 된 [CObject](../../mfc/reference/cobject-class.md)파생 클래스의 개체도 처리할 수 있습니다. Serializable 클래스는 일반적으로 `Serialize` 멤버 함수를 포함하며, 일반적으로 `CObject` 클래스 아래에 설명된 대로 [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) 및 [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) 매크로를 사용합니다.

오버 로드 된 추출 ( **>>** ) 및 삽입 ( **<<** ) 연산자는 기본 형식 및 파생 클래스를 모두 지 원하는 편리한 보관 프로그래밍 인터페이스입니다 `CObject` .

`CArchive` 에서는 MFC Windows 소켓 클래스인 [CSocket](../../mfc/reference/csocket-class.md) 및 [csocketfile](../../mfc/reference/csocketfile-class.md)을 사용한 프로그래밍도 지원 합니다. [Isbufferempty](#isbufferempty) 멤버 함수는 이러한 사용을 지원 합니다.

에 대 한 자세한 내용은 `CArchive` [Serialization](../../mfc/serialization-in-mfc.md) 및 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CArchive`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="carchiveabort"></a><a name="abort"></a> CArchive:: Abort

예외를 throw 하지 않고이 함수를 호출 하 여 보관 파일을 닫습니다.

```cpp
void Abort ();
```

### <a name="remarks"></a>설명

`CArchive`소멸자는 일반적으로를 호출 하 여 `Close` 연결 된 개체에 저장 되지 않은 모든 데이터를 플러시합니다 `CFile` . 이 경우 예외가 발생할 수 있습니다.

이러한 예외를 catch 할 때를 사용 하는 것이 좋습니다 `Abort` . 이렇게 하면 삭제 `CArchive` 개체가 추가 예외를 발생 시 키 지 않습니다. 예외를 처리할 때 `CArchive::Abort` 는 [CArchive:: Close](#close)와 달리 오류를 무시 하므로에서 오류 발생 시 예외를 throw 하지 않습니다 `Abort` .

힙에서 개체를 할당 하는 데를 사용한 경우에는 **`new`** `CArchive` 파일을 닫은 후에 삭제 해야 합니다.

### <a name="example"></a>예제

  [CArchive:: WriteClass](#writeclass)의 예제를 참조 하세요.

## <a name="carchivecarchive"></a><a name="carchive"></a> CArchive:: CArchive

개체를 생성 `CArchive` 하 고 개체를 로드 하거나 저장 하는 데 사용 되는지 여부를 지정 합니다.

```
CArchive(
    CFile* pFile,
    UINT nMode,
    int nBufSize = 4096,
    void* lpBuf = NULL);
```

### <a name="parameters"></a>매개 변수

*.Pfile*<br/>
`CFile`영구 데이터의 최종 원본 또는 대상인 개체에 대 한 포인터입니다.

*nMode*<br/>
개체를 보관 대상에서 로드 하거나 보관에 저장할지 여부를 지정 하는 플래그입니다. *Nmode* 매개 변수의 값은 다음 중 하나 여야 합니다.

- `CArchive::load` 보관 파일에서 데이터를 로드 합니다. `CFile`읽기 권한만 필요 합니다.

- `CArchive::store` 보관 파일에 데이터를 저장 합니다. `CFile`쓰기 권한이 필요 합니다.

- `CArchive::bNoFlushOnDelete``Flush`보관 소멸자가 호출 될 때 아카이브가 자동으로 호출 되지 않도록 합니다. 이 플래그를 설정 하는 경우 `Close` 소멸자가 호출 되기 전에를 명시적으로 호출 해야 합니다. 이렇게 하지 않으면 데이터가 손상 됩니다.

*nBufSize*<br/>
내부 파일 버퍼의 크기 (바이트)를 지정 하는 정수입니다. 기본 버퍼 크기는 4096 바이트입니다. 큰 개체를 정기적으로 보관 하는 경우 파일 버퍼 크기의 배수가 되는 더 큰 버퍼 크기를 사용 하는 경우 성능이 향상 됩니다.

*lpBuf*<br/>
*NBufSize* 크기의 사용자 제공 버퍼에 대 한 선택적 포인터입니다. 이 매개 변수를 지정 하지 않으면 archive는 로컬 힙에서 버퍼를 할당 하 고 개체가 제거 될 때이를 해제 합니다. 보관은 사용자가 제공한 버퍼를 해제 하지 않습니다.

### <a name="remarks"></a>설명

아카이브를 만든 후에는이 사양을 변경할 수 없습니다.

`CFile`보관 파일을 닫을 때까지 작업을 사용 하 여 파일의 상태를 변경할 수 없습니다. 이러한 작업을 수행 하면 보관 파일의 무결성이 손상 됩니다. Serialization 중에는 [getfile](#getfile) 멤버 함수에서 아카이브의 파일 개체를 가져온 다음 [CFile:: getfile](../../mfc/reference/cfile-class.md#getposition) 함수를 사용 하 여 언제 든 지 파일 포인터의 위치에 액세스할 수 있습니다. 파일 포인터의 위치를 가져오기 전에 [CArchive:: Flush](#flush) 를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#12](../../mfc/codesnippet/cpp/carchive-class_1.cpp)]

## <a name="carchiveclose"></a><a name="close"></a> CArchive:: Close

버퍼에 남아 있는 모든 데이터를 플러시하고, 아카이브를 닫고, 파일에서 보관 파일의 연결을 끊습니다.

```cpp
void Close();
```

### <a name="remarks"></a>설명

보관에 대 한 추가 작업은 허용 되지 않습니다. 아카이브를 닫은 후 동일한 파일에 대해 다른 보관 파일을 만들거나 파일을 닫을 수 있습니다.

멤버 함수를 `Close` 사용 하면 모든 데이터가 보관 파일에서 파일로 전송 되 고 보관 파일을 사용할 수 없게 됩니다. 파일에서 저장소 매체로의 전송을 완료 하려면 먼저 [CFile:: Close](../../mfc/reference/cfile-class.md#close) 를 사용 하 고 개체를 삭제 해야 합니다. `CFile`

### <a name="example"></a>예제

  [CArchive:: WriteString](#writestring)의 예제를 참조 하세요.

## <a name="carchiveflush"></a><a name="flush"></a> CArchive:: Flush

보관 버퍼에 남아 있는 모든 데이터를 파일에 기록 하도록 합니다.

```cpp
void Flush();
```

### <a name="remarks"></a>설명

멤버 함수는 `Flush` 모든 데이터가 보관 파일에서 파일로 전송 되도록 합니다. 파일에서 저장소 매체로의 전송을 완료 하려면 [CFile:: Close](../../mfc/reference/cfile-class.md#close) 를 호출 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#13](../../mfc/codesnippet/cpp/carchive-class_2.cpp)]

## <a name="carchivegetfile"></a><a name="getfile"></a> CArchive:: GetFile

`CFile`이 보관에 대 한 개체 포인터를 가져옵니다.

```
CFile* GetFile() const;
```

### <a name="return-value"></a>반환 값

사용 중인 개체에 대 한 상수 포인터 `CFile` 입니다.

### <a name="remarks"></a>설명

를 사용 하기 전에 보관 파일을 플러시해야 합니다 `GetFile` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#14](../../mfc/codesnippet/cpp/carchive-class_3.cpp)]

## <a name="carchivegetobjectschema"></a><a name="getobjectschema"></a> CArchive:: GetObjectSchema

함수에서이 함수를 호출 `Serialize` 하 여 현재 deserialize 되 고 있는 개체의 버전을 확인 합니다.

```
UINT GetObjectSchema();
```

### <a name="return-value"></a>반환 값

Deserialization을 수행 하는 동안 읽을 개체의 버전입니다.

### <a name="remarks"></a>설명

개체를 로드 하는 경우에만이 함수를 호출할 수 `CArchive` 있습니다. [CArchive:: isloading](#isloading) 는 0이 아닌 값을 반환 합니다. 함수에서 첫 번째 호출 이어야 하 `Serialize` 고 한 번만 호출 해야 합니다. 반환 값 (UINT)-1은 버전 번호를 알 수 없음을 나타냅니다.

`CObject`파생 클래스는 스키마 버전 자체와 함께 (비트 **or**)를 사용 하 여 (IMPLEMENT_SERIAL 매크로에서) 빌딩 블록인 개체를 만들 수 VERSIONABLE_SCHEMA 있습니다. 즉, `Serialize` 멤버 함수가 여러 버전을 읽을 수 있는 개체를 만들 수 있습니다. 기본 프레임 워크 기능 (VERSIONABLE_SCHEMA 없음)은 버전이 일치 하지 않을 때 예외를 throw 하는 것입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#15](../../mfc/codesnippet/cpp/carchive-class_4.cpp)]

## <a name="carchiveisbufferempty"></a><a name="isbufferempty"></a> CArchive:: IsBufferEmpty

보관 개체의 내부 버퍼가 비어 있는지 여부를 확인 하려면이 멤버 함수를 호출 합니다.

```
BOOL IsBufferEmpty() const;
```

### <a name="return-value"></a>반환 값

보관의 버퍼가 비어 있는 경우 0이 아닌 값입니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 함수는 MFC Windows 소켓 클래스를 사용한 프로그래밍을 지원 하기 위해 제공 됩니다 `CSocketFile` . 개체와 연결 된 아카이브에는 사용할 필요가 없습니다 `CFile` .

개체와 연결 된 보관 파일에를 사용 하는 이유는 `IsBufferEmpty` `CSocketFile` 보관의 버퍼에 둘 이상의 메시지나 레코드가 포함 될 수 있다는 것입니다. 메시지 하나를 받은 후를 사용 `IsBufferEmpty` 하 여 버퍼가 비어 있을 때까지 데이터를 계속 수신 하는 루프를 제어 해야 합니다. 자세한 내용은 `IsBufferEmpty`를 사용하는 방법을 보여 주는 클래스 `CAsyncSocket`의 [Receive](../../mfc/reference/casyncsocket-class.md#receive) 멤버 함수를 참조하세요.

자세한 내용은 [Windows 소켓: 아카이브가 포함 된 소켓 사용](../../mfc/windows-sockets-using-sockets-with-archives.md)을 참조 하세요.

## <a name="carchiveisloading"></a><a name="isloading"></a> CArchive:: IsLoading

보관 파일이 데이터를 로드 하 고 있는지 여부를 확인 합니다.

```
BOOL IsLoading() const;
```

### <a name="return-value"></a>반환 값

보관 파일이 현재 로드에 사용 되 고 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `Serialize` 보관 된 클래스의 함수에 의해 호출 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#16](../../mfc/codesnippet/cpp/carchive-class_5.cpp)]

## <a name="carchiveisstoring"></a><a name="isstoring"></a> CArchive:: IsStoring

보관 파일이 데이터를 저장 하 고 있는지 여부를 확인 합니다.

```
BOOL IsStoring() const;
```

### <a name="return-value"></a>반환 값

보관이 현재 저장에 사용 되 고 있는 경우 0이 아닙니다. 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

이 멤버 함수는 `Serialize` 보관 된 클래스의 함수에 의해 호출 됩니다.

`IsStoring`보관 함의 상태가 0이 아닌 경우 상태는 0 이며 그 `IsLoading` 반대의 경우도 마찬가지입니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#17](../../mfc/codesnippet/cpp/carchive-class_6.cpp)]

## <a name="carchivemapobject"></a><a name="mapobject"></a> CArchive:: MapObject

이 멤버 함수를 호출 하 여 파일에는 serialize 되지 않지만 하위 개체에서 참조할 수 있는 개체를 맵에 삽입할 수 있습니다.

```cpp
void MapObject(const CObject* pOb);
```

### <a name="parameters"></a>매개 변수

*pOb*<br/>
저장 되는 개체에 대 한 상수 포인터입니다.

### <a name="remarks"></a>설명

예를 들어 문서를 직렬화 할 수는 없지만 문서에 포함 된 항목은 serialize 할 수 있습니다. 을 호출 하 여 `MapObject` 해당 항목 또는 하위 개체가 문서를 참조할 수 있습니다. 또한 serialize 된 하위 항목은 *m_pDocument* 뒤로 포인터를 serialize 할 수 있습니다.

`MapObject`개체에서를 저장 하 고 로드할 때를 호출할 수 있습니다 `CArchive` . `MapObject` 직렬화 및 deserialization을 수행 하는 동안 개체에 의해 유지 관리 되는 내부 데이터 구조에 지정 된 개체를 추가 `CArchive` 하지만 [ReadObject](#readobject) 및 [WriteObject](#writeobject)와는 달리 개체에서 serialize를 호출 하지 않습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#18](../../mfc/codesnippet/cpp/carchive-class_7.h)]

[!code-cpp[NVC_MFCSerialization#19](../../mfc/codesnippet/cpp/carchive-class_8.cpp)]

[!code-cpp[NVC_MFCSerialization#20](../../mfc/codesnippet/cpp/carchive-class_9.h)]

[!code-cpp[NVC_MFCSerialization#21](../../mfc/codesnippet/cpp/carchive-class_10.cpp)]

## <a name="carchivem_pdocument"></a><a name="m_pdocument"></a> CArchive:: m_pDocument

NULL로 설정 합니다. 기본적으로에 대 한이 포인터는 `CDocument` 인스턴스의 사용자가 원하는 모든 항목으로 설정할 수 있습니다 `CArchive` .

```
CDocument* m_pDocument;
```

### <a name="remarks"></a>설명

이 포인터는 serialize 되는 모든 개체에 대 한 serialization 프로세스에 대 한 추가 정보를 전달 하는 데 주로 사용 됩니다. 이렇게 하려면 `CDocument` 문서 내의 개체가 필요한 경우 문서에 액세스할 수 있는 방식으로 serialize 되는 문서 (파생 클래스)를 사용 하 여 포인터를 초기화 합니다. 이 포인터는 serialization 중에도 개체에 사용 됩니다 `COleClientItem` .

사용자가 파일 열기 또는 저장 명령을 실행 하는 경우 프레임 워크는 serialize 되는 문서에 *m_pDocument* 을 설정 합니다. 파일 열기 또는 저장 이외의 이유로 개체 연결 및 포함 (OLE) 컨테이너 문서를 serialize 하는 경우 명시적으로 *m_pDocument* 설정 해야 합니다. 예를 들어 컨테이너 문서를 클립보드로 serialize 할 때이 작업을 수행 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#35](../../mfc/codesnippet/cpp/carchive-class_11.cpp)]

## <a name="carchiveoperator-ltlt"></a><a name="operator_lt_lt"></a> CArchive:: operator &lt;&lt;

지정 된 개체나 기본 형식을 보관 파일에 저장 합니다.

```
friend CArchive& operator<<(
    CArchive& ar,
    const CObject* pOb);

throw(
    CArchiveException*,
    CFileException*);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator<<(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator<<(
    const ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator<<(BYTE by);
CArchive& operator<<(WORD w);
CArchive& operator<<(LONG l);
CArchive& operator<<(DWORD dw);
CArchive& operator<<(float f);
CArchive& operator<<(double d);
CArchive& operator<<(int i);
CArchive& operator<<(short w);
CArchive& operator<<(char ch);
CArchive& operator<<(wchar_t ch);
CArchive& operator<<(unsigned u);
CArchive& operator<<(bool b);
CArchive& operator<<(ULONGLONG dwdw);
CArchive& operator<<(LONGLONG dwdw);
```

### <a name="return-value"></a>반환 값

`CArchive`한 줄에 여러 삽입 연산자를 사용할 수 있도록 하는 참조입니다.

### <a name="remarks"></a>설명

위의 마지막 두 버전은 64 비트 정수를 저장 하는 데 특히 적합 합니다.

클래스 구현에서 IMPLEMENT_SERIAL 매크로를 사용한 경우에 대해 오버 로드 된 삽입 연산자가 `CObject` 보호 된를 호출 합니다 `WriteObject` . 그런 다음이 함수는 `Serialize` 클래스의 함수를 호출 합니다.

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) 삽입 연산자 (<<)는 진단 덤프를 지원 하 고 보관 파일에 저장 합니다.

### <a name="example"></a>예제

이 예에서는 `CArchive` 및 형식과 함께 << 삽입 연산자를 사용 하는 방법을 보여 줍니다 **`int`** **`long`** .

[!code-cpp[NVC_MFCSerialization#31](../../mfc/codesnippet/cpp/carchive-class_12.cpp)]

### <a name="example"></a>예제

이 예제 2에서는 형식에 << 삽입 연산자를 사용 하는 방법을 보여 줍니다 `CArchive` `CStringT` .

[!code-cpp[NVC_MFCSerialization#32](../../mfc/codesnippet/cpp/carchive-class_13.cpp)]

## <a name="carchiveoperator-gtgt"></a><a name="operator_gt_gt"></a> CArchive:: operator &gt;&gt;

보관에서 표시 된 개체 또는 기본 형식을 로드 합니다.

```
friend CArchive& operator>>(
    CArchive& ar,
    CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

friend CArchive& operator>>(
    CArchive& ar,
    const CObject *& pOb);

throw(
    CArchiveException*,
    CFileException*,
    CMemoryException*);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    const RECT& rect);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    POINT point);

CArchive& AFXAPI operator>>(
    CArchive& ar,
    SIZE size);

template<typename BaseType,
    class StringTraits> CArchive& operator>>(
    ATL::CStringT<BaseType,
    StringTraits>& str);

CArchive& operator>>(BYTE& by);
CArchive& operator>>(WORD& w);
CArchive& operator>>(int& i);
CArchive& operator>>(LONG& l);
CArchive& operator>>(DWORD& dw);
CArchive& operator>>(float& f);
CArchive& operator>>(double& d);
CArchive& operator>>(short& w);
CArchive& operator>>(char& ch);
CArchive& operator>>(wchar_t& ch);
CArchive& operator>>(unsigned& u);
CArchive& operator>>(bool& b);
CArchive& operator>>(ULONGLONG& dwdw);
CArchive& operator>>(LONGLONG& dwdw);
```

### <a name="return-value"></a>반환 값

`CArchive`한 줄에 여러 추출 연산자를 사용할 수 있도록 하는 참조입니다.

### <a name="remarks"></a>설명

위의 마지막 두 버전은 64 비트 정수를 로드 하는 데 특히 적합 합니다.

클래스 구현에서 IMPLEMENT_SERIAL 매크로를 사용한 경우에 대해 오버 로드 된 추출 연산자는 `CObject` protected 함수를 호출 합니다 `ReadObject` (0이 아닌 런타임 클래스 포인터 사용). 그런 다음이 함수는 `Serialize` 클래스의 함수를 호출 합니다.

[CStringT](../../atl-mfc-shared/reference/cstringt-class.md) 추출 연산자 (>>)는 보관 파일에서 로드를 지원 합니다.

### <a name="example"></a>예제

이 예에서는 형식에 >> 추출 연산자를 사용 하는 방법을 보여 줍니다 `CArchive` **`int`** .

[!code-cpp[NVC_MFCSerialization#33](../../mfc/codesnippet/cpp/carchive-class_14.cpp)]

### <a name="example"></a>예제

이 예에서는 삽입 및 추출 연산자를 사용 하 여> <하는 방법을 보여 줍니다 `CArchive` \< and > `CStringT` .

[!code-cpp[NVC_MFCSerialization#34](../../mfc/codesnippet/cpp/carchive-class_15.cpp)]

## <a name="carchiveread"></a><a name="read"></a> CArchive:: Read

보관 파일에서 지정 된 바이트 수를 읽습니다.

```
UINT Read(void* lpBuf, UINT nMax);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
보관 파일에서 읽은 데이터를 받을 사용자 제공 버퍼에 대 한 포인터입니다.

*nMax*<br/>
보관 파일에서 읽을 바이트 수를 지정 하는 부호 없는 정수입니다.

### <a name="return-value"></a>반환 값

실제로 읽은 바이트 수를 포함 하는 부호 없는 정수입니다. 반환 값이 요청 된 수보다 적으면 파일의 끝에 도달 했습니다. 파일 끝 조건에서는 예외가 throw 되지 않습니다.

### <a name="remarks"></a>설명

아카이브는 바이트를 해석 하지 않습니다.

함수 내에서 멤버 함수를 사용 하 여 `Read` `Serialize` 개체에 포함 된 일반 구조를 읽을 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#24](../../mfc/codesnippet/cpp/carchive-class_16.cpp)]

## <a name="carchivereadclass"></a><a name="readclass"></a> CArchive:: ReadClass

[Writeclass](#writeclass)를 사용 하 여 이전에 저장 된 클래스에 대 한 참조를 읽으려면이 멤버 함수를 호출 합니다.

```
CRuntimeClass* ReadClass(
    const CRuntimeClass* pClassRefRequested = NULL,
    UINT* pSchema = NULL,
    DWORD* pObTag = NULL);
```

### <a name="parameters"></a>매개 변수

*pClassRefRequested*<br/>
요청 된 클래스 참조에 해당 하는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 포인터입니다. NULL일 수 있습니다.

*pSchema*<br/>
이전에 저장 한 런타임 클래스의 스키마에 대 한 포인터입니다.

*pObTag*<br/>
개체의 고유 태그를 참조 하는 숫자입니다. [ReadObject](#readobject)구현에서 내부적으로 사용 됩니다. 고급 프로그래밍에만 노출 됩니다. *Pobtag* 는 일반적으로 NULL 이어야 합니다.

### <a name="return-value"></a>반환 값

[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

*Pclassrefrequested* 된가 NULL이 아닌 경우에는 `ReadClass` 보관 된 클래스 정보가 런타임 클래스와 호환 되는지 확인 합니다. 호환 되지 않는 경우는 `ReadClass` [CArchiveException](../../mfc/reference/carchiveexception-class.md)을 throw 합니다.

런타임 클래스는 [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) 및 [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)를 사용 해야 합니다. 그렇지 않으면 `ReadClass` [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)이 throw 됩니다.

*Pschema* 가 NULL 인 경우에는 [CArchive:: GetObjectSchema](#getobjectschema);를 호출 하 여 저장 된 클래스의 스키마를 검색할 수 있습니다. 그렇지 않으면 <strong>\*</strong> *pschema* 에 이전에 저장 한 런타임 클래스의 스키마가 포함 됩니다.

클래스 참조의 읽기 및 쓰기를 모두 처리 하는 `ReadClass` 대신 [SerializeClass](#serializeclass)를 사용할 수 있습니다.

### <a name="example"></a>예제

  [CArchive:: WriteClass](#writeclass)의 예제를 참조 하세요.

## <a name="carchivereadobject"></a><a name="readobject"></a> CArchive:: ReadObject

보관에서 개체 데이터를 읽고 해당 형식의 개체를 생성 합니다.

```
CObject* ReadObject(const CRuntimeClass* pClass);
```

### <a name="parameters"></a>매개 변수

*pClass*<br/>
읽을 것으로 간주 되는 개체에 해당 하는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 상수 포인터입니다.

### <a name="return-value"></a>반환 값

[Cobject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)를 사용 하 여 올바른 파생 클래스로 안전 하 게 캐스팅 해야 하는 [cobject](../../mfc/reference/cobject-class.md) 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 `CArchive` **>>** [CObject](../../mfc/reference/cobject-class.md) 포인터에 대해 오버 로드 된 추출 () 연산자에 의해 호출 됩니다. `ReadObject`그러면는 `Serialize` 보관 된 클래스의 함수를 호출 합니다.

[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) 매크로가 가져오는 0이 아닌 *pclass* 매개 변수를 제공 하는 경우 함수는 보관 된 개체의 런타임 클래스를 확인 합니다. 여기서는 클래스의 구현에서 IMPLEMENT_SERIAL 매크로를 사용 했다고 가정 합니다.

### <a name="example"></a>예제

  [CArchive:: WriteObject](#writeobject)의 예제를 참조 하세요.

## <a name="carchivereadstring"></a><a name="readstring"></a> CArchive:: ReadString

이 멤버 함수를 호출 하 여 개체와 연결 된 파일에서 버퍼로 텍스트 데이터를 읽습니다 `CArchive` .

```
BOOL ReadString(CString& rString);
LPTSTR ReadString(LPTSTR lpsz, UINT nMax);
```

### <a name="parameters"></a>매개 변수

*rString*<br/>
CArchive 개체와 연결 된 파일에서 결과 문자열을 읽은 후 결과 문자열을 포함 하는 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 에 대 한 참조입니다.

*lpsz*<br/>
Null로 종료 되는 텍스트 문자열을 받을 사용자 제공 버퍼에 대 한 포인터를 지정 합니다.

*nMax*<br/>
읽을 최대 문자 수를 지정 합니다. 는 *lpsz* 버퍼의 크기 보다 하나 작아야 합니다.

### <a name="return-value"></a>반환 값

BOOL을 반환 하는 버전에서 성공 하면 TRUE입니다. 그렇지 않으면 FALSE입니다.

을 반환 하는 버전에서 `LPTSTR` 텍스트 데이터를 포함 하는 버퍼에 대 한 포인터입니다. 파일의 끝에 도달한 경우 NULL입니다.

### <a name="remarks"></a>설명

*N 일별 최대* 매개 변수를 사용 하는 멤버 함수 버전에서 버퍼는 최대 *n 일별 최대* 문자 제한을 포함 합니다. 읽기는 캐리지 리턴-줄 바꿈 쌍으로 중지 됩니다. 후행 줄 바꿈 문자는 항상 제거 됩니다. 두 경우 모두 null 문자 (' \ 0 ')가 추가 됩니다.

[CArchive:: Read](#read) 는 텍스트 모드 입력에도 사용할 수 있지만 캐리지 리턴-줄 바꿈 쌍에서는 종료 되지 않습니다.

### <a name="example"></a>예제

  [CArchive:: WriteString](#writestring)의 예제를 참조 하세요.

## <a name="carchiveserializeclass"></a><a name="serializeclass"></a> CArchive:: SerializeClass

기본 클래스의 버전 정보를 저장 하 고 로드 하려면이 멤버 함수를 호출 합니다.

```cpp
void SerializeClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>매개 변수

*pClassRef*<br/>
기본 클래스에 대 한 런타임 클래스 개체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`SerializeClass` 의 방향에 따라 클래스에 대 한 참조를 개체에 읽거나 씁니다 `CArchive` `CArchive` . 를 사용 `SerializeClass` 하 여 기본 클래스 개체를 serialize 하는 편리한 방법으로 [readclass](#readclass) 및 [writeclass](#writeclass) 대신를 사용 합니다 .이 경우에는 `SerializeClass` 더 작은 코드와 더 작은 매개 변수가 필요 합니다.

와 마찬가지로는 `ReadClass` `SerializeClass` 보관 된 클래스 정보가 런타임 클래스와 호환 되는지 확인 합니다. 호환 되지 않는 경우는 `SerializeClass` [CArchiveException](../../mfc/reference/carchiveexception-class.md)을 throw 합니다.

런타임 클래스는 [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) 및 [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)를 사용 해야 합니다. 그렇지 않으면 `SerializeClass` [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)이 throw 됩니다.

[RUNTIME_CLASS](../../mfc/reference/run-time-object-model-services.md#runtime_class) 매크로를 사용 하 여 *pRuntimeClass* 매개 변수의 값을 검색 합니다. 기본 클래스는 [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) 매크로를 사용 해야 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#25](../../mfc/codesnippet/cpp/carchive-class_17.h)]

## <a name="carchivesetloadparams"></a><a name="setloadparams"></a> CArchive:: SetLoadParams

`SetLoadParams`보관에서 많은 수의 파생 개체를 읽으려고 할 때를 호출 `CObject` 합니다.

```cpp
void SetLoadParams(UINT nGrowBy = 1024);
```

### <a name="parameters"></a>매개 변수

*nGrowBy*<br/>
크기 증가가 필요한 경우 할당할 요소 슬롯의 최소 개수입니다.

### <a name="remarks"></a>설명

`CArchive` 는 로드 배열을 사용 하 여 보관에 저장 된 개체에 대 한 참조를 확인 합니다. `SetLoadParams` 로드 배열이 증가 하는 크기를 설정할 수 있습니다.

`SetLoadParams`개체가 로드 된 후 또는 [mapobject](#mapobject) 또는 [ReadObject](#readobject) 가 호출 된 후에는를 호출 하면 안 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivesetobjectschema"></a><a name="setobjectschema"></a> CArchive:: SetObjectSchema

보관 개체에 저장 된 개체 스키마를 *Nschema* 로 설정 하려면이 멤버 함수를 호출 합니다.

```cpp
void SetObjectSchema(UINT nSchema);
```

### <a name="parameters"></a>매개 변수

*nSchema*<br/>
개체의 스키마를 지정 합니다.

### <a name="remarks"></a>설명

[GetObjectSchema](#getobjectschema) 에 대 한 다음 호출에서는 *nschema* 에 저장 된 값을 반환 합니다.

`SetObjectSchema`파생 클래스의 함수에서 특정 버전을 강제로 읽도록 하려는 경우와 같이 고급 버전 관리에 사용 `Serialize` 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#27](../../mfc/codesnippet/cpp/carchive-class_19.cpp)]

## <a name="carchivesetstoreparams"></a><a name="setstoreparams"></a> CArchive:: SetStoreParams 매개 변수

`SetStoreParams`보관에 많은 수의 파생 개체를 저장할 때 사용 `CObject` 합니다.

```cpp
void SetStoreParams(UINT nHashSize = 2053, UINT nBlockSize = 128);
```

### <a name="parameters"></a>매개 변수

*nHashSize*<br/>
인터페이스 포인터 맵에 대 한 해시 테이블의 크기입니다. 는 소수 여야 합니다.

*nBlockSize*<br/>
매개 변수 확장을 위한 메모리 할당 세분성을 지정 합니다. 최상의 성능을 위해 2의 거듭제곱 이어야 합니다.

### <a name="remarks"></a>설명

`SetStoreParams` serialization 프로세스 중에 고유 개체를 식별 하는 데 사용 되는 맵의 블록 크기와 해시 테이블 크기를 설정할 수 있습니다.

`SetStoreParams`개체가 저장 된 후 또는 [Mapobject](#mapobject) 또는 [WriteObject](#writeobject) 가 호출 된 후에는를 호출 하면 안 됩니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#26](../../mfc/codesnippet/cpp/carchive-class_18.h)]

## <a name="carchivewrite"></a><a name="write"></a> CArchive:: Write

보관에 지정 된 바이트 수를 씁니다.

```cpp
void Write(const void* lpBuf, INT nMax);
```

### <a name="parameters"></a>매개 변수

*lpBuf*<br/>
보관 파일에 쓸 데이터를 포함 하는 사용자 제공 버퍼에 대 한 포인터입니다.

*nMax*<br/>
보관에 쓸 바이트 수를 지정 하는 정수입니다.

### <a name="remarks"></a>설명

아카이브는 바이트의 형식을 지정 하지 않습니다.

`Write`함수 내에서 멤버 함수를 사용 `Serialize` 하 여 개체에 포함 된 일반 구조를 작성할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#23](../../mfc/codesnippet/cpp/carchive-class_20.cpp)]

## <a name="carchivewriteclass"></a><a name="writeclass"></a> CArchive:: WriteClass

`WriteClass`파생 클래스를 serialize 하는 동안 기본 클래스의 버전과 클래스 정보를 저장 하는 데 사용 합니다.

```cpp
void WriteClass(const CRuntimeClass* pClassRef);
```

### <a name="parameters"></a>매개 변수

*pClassRef*<br/>
요청 된 클래스 참조에 해당 하는 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 구조체에 대 한 포인터입니다.

### <a name="remarks"></a>설명

`WriteClass` 기본 클래스에 대 한 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 에 대 한 참조를에 씁니다 `CArchive` . [CArchive:: ReadClass](#readclass) 를 사용 하 여 참조를 검색 합니다.

`WriteClass` 보관 된 클래스 정보가 런타임 클래스와 호환 되는지 확인 합니다. 호환 되지 않는 경우는 `WriteClass` [CArchiveException](../../mfc/reference/carchiveexception-class.md)을 throw 합니다.

런타임 클래스는 [DECLARE_SERIAL](../../mfc/reference/run-time-object-model-services.md#declare_serial) 및 [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)를 사용 해야 합니다. 그렇지 않으면 `WriteClass` [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)이 throw 됩니다.

클래스 참조의 읽기 및 쓰기를 모두 처리 하는 `WriteClass` 대신 [SerializeClass](#serializeclass)를 사용할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#28](../../mfc/codesnippet/cpp/carchive-class_21.cpp)]

## <a name="carchivewriteobject"></a><a name="writeobject"></a> CArchive:: WriteObject

지정 된를 `CObject` 보관에 저장 합니다.

```cpp
void WriteObject(const CObject* pOb);
```

### <a name="parameters"></a>매개 변수

*pOb*<br/>
저장 되는 개체에 대 한 상수 포인터입니다.

### <a name="remarks"></a>설명

이 함수는 일반적으로 `CArchive` **<<** 에 대해 오버 로드 된 삽입 () 연산자에 의해 호출 됩니다 `CObject` . `WriteObject`그러면는 `Serialize` 보관 된 클래스의 함수를 호출 합니다.

보관을 사용 하도록 설정 하려면 IMPLEMENT_SERIAL 매크로를 사용 해야 합니다. `WriteObject` 압축에 ASCII 클래스 이름을 씁니다. 이 클래스 이름은 나중에 로드 프로세스 중에 유효성이 검사 됩니다. 특수 인코딩 스키마는 클래스의 여러 개체에 대해 클래스 이름이 불필요 하 게 중복 되는 것을 방지 합니다. 또한이 체계는 둘 이상의 포인터를 대상으로 하는 개체의 중복 저장소를 방지 합니다.

ASCII 클래스 이름의 현재 상태를 포함 하 여 정확한 개체 인코딩 메서드는 구현 세부 정보 이며 이후 버전의 라이브러리에서 변경 될 수 있습니다.

> [!NOTE]
> 모든 개체의 생성, 삭제 및 업데이트를 완료 한 후 보관 하기 시작 합니다. 보관을 개체 수정과 함께 사용 하는 경우 보관 파일이 손상 됩니다.

### <a name="example"></a>예제

클래스에 대 한 정의는 `CAge` [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist)의 예제를 참조 하세요.

[!code-cpp[NVC_MFCSerialization#29](../../mfc/codesnippet/cpp/carchive-class_22.cpp)]

## <a name="carchivewritestring"></a><a name="writestring"></a> CArchive:: WriteString

이 멤버 함수를 사용 하 여 버퍼의 데이터를 개체에 연결 된 파일에 쓸 수 `CArchive` 있습니다.

```cpp
void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>매개 변수

*lpsz*<br/>
Null로 끝나는 텍스트 문자열을 포함 하는 버퍼에 대 한 포인터를 지정 합니다.

### <a name="remarks"></a>설명

종결 null 문자 (' \ 0 ')는 파일에 기록 되지 않습니다. 또는는 자동으로 작성 되는 줄 바꿈이 아닙니다.

`WriteString` 는 디스크 전체 상태를 포함 하 여 여러 조건에 대 한 응답으로 예외를 throw 합니다.

`Write` 도 사용할 수 있지만 null 문자를 종료 하는 대신 요청 된 바이트 수를 파일에 씁니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFCSerialization#30](../../mfc/codesnippet/cpp/carchive-class_23.cpp)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFile 클래스](../../mfc/reference/cfile-class.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[CSocket 클래스](../../mfc/reference/csocket-class.md)<br/>
[CSocketFile 클래스](../../mfc/reference/csocketfile-class.md)
