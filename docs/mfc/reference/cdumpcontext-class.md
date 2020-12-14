---
description: '자세히 알아보기: CDumpContext 클래스'
title: CDumpContext 클래스
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: 955be92c4a3b08fe6e1d5a947166133143667ac7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184778"
---
# <a name="cdumpcontext-class"></a>CDumpContext 클래스

사용자가 읽을 수 있는 텍스트 형식으로 스트림 지향 진단 출력을 지원합니다.

## <a name="syntax"></a>구문

```
class CDumpContext
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CDumpContext:: CDumpContext](#cdumpcontext)|`CDumpContext` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CDumpContext::D Um Hex](#dumpashex)|표시 된 항목을 16 진수 형식으로 덤프 합니다.|
|[CDumpContext:: Flush](#flush)|덤프 컨텍스트 버퍼의 모든 데이터를 플러시합니다.|
|[CDumpContext:: GetDepth](#getdepth)|덤프의 깊이에 해당 하는 정수를 가져옵니다.|
|[CDumpContext:: HexDump](#hexdump)|16 진수 형식의 배열에 포함 된 바이트를 덤프 합니다.|
|[CDumpContext:: SetDepth](#setdepth)|덤프 수준을 설정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CDumpContext:: operator &lt;&lt;](#operator_lt_lt)|변수 및 개체를 덤프 컨텍스트에 삽입 합니다.|

## <a name="remarks"></a>설명

`CDumpContext` 에 기본 클래스가 없습니다.

[](diagnostic-services.md#afxdump) `CDumpContext` 대부분의 덤프에 대해 미리 선언 된 개체인 afxDump를 사용할 수 있습니다. `afxDump`개체는 MFC 라이브러리의 디버그 버전 에서만 사용할 수 있습니다.

일부 메모리 [진단 서비스](../../mfc/reference/diagnostic-services.md) 는 `afxDump` 출력에 사용 합니다.

Windows 환경에서는 개념적으로 스트림과 비슷한 미리 정의 된 `afxDump` 개체의 출력이 `cerr` windows 함수를 통해 디버거로 라우팅됩니다 `OutputDebugString` .

클래스에는 `CDumpContext` **<<** `CObject` 개체의 데이터를 덤프 하는 포인터에 대 한 오버 로드 된 삽입 () 연산자가 있습니다. 파생 된 개체에 대 한 사용자 지정 덤프 형식이 필요한 경우 [CObject::D ump](../../mfc/reference/cobject-class.md#dump)를 재정의 합니다. 대부분의 Microsoft Foundation 클래스는 재정의 된 `Dump` 멤버 함수를 구현 합니다.

, 및와 같이에서 파생 되지 않은 클래스에 `CObject` `CString` 는, 및와 `CTime` `CTimeSpan` `CDumpContext` 같은 자주 사용 되는 구조와 같이 자체 오버 로드 된 삽입 연산자가 있습니다 `CFileStatus` `CPoint` `CRect` .

클래스 구현에서 [IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic) 또는 [IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial) 매크로를 사용 하는 경우에서 `CObject::Dump` 파생 클래스의 이름을 인쇄 `CObject` 합니다. 그렇지 않으면 인쇄 됩니다 `CObject` .

`CDumpContext`클래스는 라이브러리의 디버그 버전과 릴리스 버전 모두에서 사용할 수 있지만 `Dump` 멤버 함수는 디버그 버전에만 정의 됩니다.   /  `#endif` 사용자 지정 멤버 함수를 포함 하 여 진단 코드를 괄호로 #ifdef _DEBUG 문을 사용 `Dump` 합니다.

사용자 고유의 `CDumpContext` 개체를 만들기 전에 `CFile` 덤프 대상으로 사용 되는 개체를 만들어야 합니다.

에 대 한 자세한 내용은 `CDumpContext` [MFC 응용 프로그램 디버깅](/visualstudio/debugger/mfc-debugging-techniques)을 참조 하세요.

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>상속 계층 구조

`CDumpContext`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a> CDumpContext:: CDumpContext

클래스의 개체를 생성 `CDumpContext` 합니다.

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>매개 변수

*.Pfile*<br/>
덤프 대상인 개체에 대 한 포인터입니다 `CFile` .

### <a name="remarks"></a>설명

`afxDump`개체가 자동으로 생성 됩니다.

덤프 컨텍스트가 활성화 되어 있는 동안에는 내부에 쓰지 마십시오. `CFile` 그렇지 않으면 덤프를 방해 하 게 됩니다. Windows 환경에서 출력은 Windows 함수를 통해 디버거로 라우팅됩니다 `OutputDebugString` .

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a> CDumpContext::D Um Hex

지정 된 형식을 16 진수 숫자로 덤프 합니다.

```
CDumpContext& DumpAsHex(BYTE b);
CDumpContext& DumpAsHex(DWORD dw);
CDumpContext& DumpAsHex(int n);
CDumpContext& DumpAsHex(LONG l);
CDumpContext& DumpAsHex(LONGLONG n);
CDumpContext& DumpAsHex(UINT u);
CDumpContext& DumpAsHex(ULONGLONG n);
CDumpContext& DumpAsHex(WORD w);
```

### <a name="return-value"></a>반환 값

`CDumpContext` 개체에 대한 참조입니다.

### <a name="remarks"></a>설명

지정 된 형식의 항목을 16 진수 숫자로 덤프 하려면이 멤버 함수를 호출 합니다. 배열을 덤프 하려면 [CDumpContext:: HexDump](#hexdump)를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a> CDumpContext:: Flush

버퍼에 남아 있는 모든 데이터가 덤프 컨텍스트에 첨부 된 파일에 기록 되도록 합니다.

```cpp
void Flush();
```

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a> CDumpContext:: GetDepth

전체 또는 단순 덤프가 처리 중인지 여부를 확인 합니다.

```
int GetDepth() const;
```

### <a name="return-value"></a>반환 값

로 설정 된 덤프의 깊이입니다 `SetDepth` .

### <a name="example"></a>예제

  [Setdepth](#setdepth)의 예제를 참조 하세요.

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a> CDumpContext:: HexDump

16 진수 숫자로 포맷 된 바이트 배열을 덤프 합니다.

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>매개 변수

*lpszLine*<br/>
새 줄의 시작 부분에 출력할 문자열입니다.

*pby*<br/>
덤프할 바이트를 포함 하는 버퍼에 대 한 포인터입니다.

*nBytes*<br/>
덤프할 바이트 수입니다.

*nWidth*<br/>
줄 단위로 덤프 된 최대 바이트 수입니다 (출력 줄의 너비가 아님).

### <a name="remarks"></a>설명

단일 특정 항목 형식을 16 진수로 덤프 하려면 [CDumpContext::D Um hex](#dumpashex)를 호출 합니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a> CDumpContext:: operator &lt;&lt;

덤프 컨텍스트에 지정 된 데이터를 출력 합니다.

```
CDumpContext& operator<<(const CObject* pOb);
CDumpContext& operator<<(const CObject& ob);
CDumpContext& operator<<(LPCTSTR lpsz);
CDumpContext& operator<<(const void* lp);
CDumpContext& operator<<(BYTE by);
CDumpContext& operator<<(WORD w);
CDumpContext& operator<<(DWORD dw);
CDumpContext& operator<<(int n);
CDumpContext& operator<<(double d);
CDumpContext& operator<<(float f);
CDumpContext& operator<<(LONG l);
CDumpContext& operator<<(UINT u);
CDumpContext& operator<<(LPCWSTR lpsz);
CDumpContext& operator<<(LPCSTR lpsz);
CDumpContext& operator<<(LONGLONG n);
CDumpContext& operator<<(ULONGLONG n);
CDumpContext& operator<<(HWND h);
CDumpContext& operator<<(HDC h);
CDumpContext& operator<<(HMENU h);
CDumpContext& operator<<(HACCEL h);
CDumpContext& operator<<(HFONT h);
```

### <a name="return-value"></a>반환 값

`CDumpContext` 참조입니다. 반환 값을 사용 하 여 한 줄의 소스 코드에 여러 삽입을 작성할 수 있습니다.

### <a name="remarks"></a>설명

삽입 연산자는 `CObject` 포인터 및 대부분의 기본 형식에 대해 오버 로드 됩니다. 문자에 대 한 포인터는 문자열 내용의 덤프를 발생 합니다. 에 대 한 포인터는 **`void`** 주소에 대 한 16 진수 덤프만 발생 합니다. 을 (를) 만들면 64 비트의 부호 있는 정수에 대 한 덤프가 생성 됩니다. ULONGLONG는 64 비트 부호 없는 정수의 덤프를 생성 합니다.

클래스의 구현에서 IMPLEMENT_DYNAMIC 또는 IMPLEMENT_SERIAL 매크로를 사용 하는 경우를 통해 삽입 연산자 `CObject::Dump` 가 파생 클래스의 이름을 인쇄 `CObject` 합니다. 그렇지 않으면 인쇄 됩니다 `CObject` . 클래스의 함수를 재정의 하는 경우 `Dump` 16 진수 덤프 대신 개체의 내용에 대 한 보다 의미 있는 출력을 제공할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a> CDumpContext:: SetDepth

덤프의 깊이를 설정 합니다.

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>매개 변수

*nNewDepth*<br/>
새 깊이 값입니다.

### <a name="remarks"></a>설명

다른 개체에 대 한 포인터를 포함 하지 않는 기본 형식 또는 단순을 덤프 하는 경우 `CObject` 값이 0 이면 충분 합니다. 0 보다 큰 값은 모든 개체를 재귀적으로 덤프 하는 심층 덤프를 지정 합니다. 예를 들어 컬렉션의 심층 덤프는 컬렉션의 모든 요소를 덤프 합니다. 파생 클래스에서 다른 특정 깊이 값을 사용할 수 있습니다.

> [!NOTE]
> 전체 덤프에서는 순환 참조가 검색 되지 않으며 무한 루프가 발생할 수 있습니다.

### <a name="example"></a>예제

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>참고 항목

[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CFile 클래스](../../mfc/reference/cfile-class.md)<br/>
[CObject 클래스](../../mfc/reference/cobject-class.md)
