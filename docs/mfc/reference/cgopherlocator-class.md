---
description: '자세히 알아보기: CGopherLocator 클래스'
title: CGopherLocator 클래스
ms.date: 11/04/2016
f1_keywords:
- CGopherLocator
- AFXINET/CGopherLocator
- AFXINET/CGopherLocator::CGopherLocator
- AFXINET/CGopherLocator::GetLocatorType
helpviewer_keywords:
- CGopherLocator [MFC], CGopherLocator
- CGopherLocator [MFC], GetLocatorType
ms.assetid: 6fcc015f-5ae6-4959-b936-858634c71019
ms.openlocfilehash: f615ce6fbda150d923f6664acff207fdebdbba3f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97184025"
---
# <a name="cgopherlocator-class"></a>CGopherLocator 클래스

Gopher 서버에서 gopher "로케이터"를 가져오고, 로케이터 유형을 결정 하 고, [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)에서 로케이터를 사용할 수 있도록 합니다.

> [!NOTE]
> 클래스 `CGopherConnection` , `CGopherFile` , `CGopherFileFind` `CGopherLocator` 및 해당 멤버는 Windows XP 플랫폼에서 작동 하지 않으므로 더 이상 사용 되지 않지만 이전 플랫폼에서는 계속 작동 합니다.

## <a name="syntax"></a>구문

```
class CGopherLocator : public CObject
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CGopherLocator::CGopherLocator](#cgopherlocator)|`CGopherLocator` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CGopherLocator:: GetLocatorType](#getlocatortype)|Gopher 로케이터를 구문 분석 하 고 해당 특성을 결정 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CGopherLocator:: operator LPCTSTR](#operator_lpctstr)|개체에 저장 된 문자를 `CGopherLocator` C 스타일 문자열로 직접 액세스 합니다.|

## <a name="remarks"></a>설명

응용 프로그램은 해당 서버에서 정보를 검색할 수 있으려면 gopher 서버의 로케이터를 가져와야 합니다. 로케이터를 만든 후에는 로케이터를 불투명 토큰으로 처리 해야 합니다.

각 gopher 로케이터는 찾은 파일 또는 서버의 유형을 결정 하는 특성을 포함 합니다. Gopher 로케이터 형식의 목록은 [Getlocatortype](#getlocatortype) 을 참조 하세요.

응용 프로그램은 일반적으로 [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile) 호출 시 로케이터를 사용 하 여 특정 정보를 검색 합니다.

에서 다른 MFC 인터넷 클래스로 작업 하는 방법에 대 한 자세한 내용은 `CGopherLocator` WinInet을 [사용한 인터넷 프로그래밍](../../mfc/win32-internet-extensions-wininet.md)문서를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

`CGopherLocator`

## <a name="requirements"></a>요구 사항

**헤더:** afxinet.h

## <a name="cgopherlocatorcgopherlocator"></a><a name="cgopherlocator"></a> CGopherLocator::CGopherLocator

이 멤버 함수는 개체를 만들기 위해 호출 됩니다 `CGopherLocator` .

```
CGopherLocator(const CGopherLocator& ref);
```

### <a name="parameters"></a>매개 변수

*ref*<br/>
상수 개체에 대 한 참조 `CGopherLocator` 입니다.

### <a name="remarks"></a>설명

개체를 직접 만들지는 않습니다 `CGopherLocator` . 대신 [CGopherConnection:: CreateLocator](../../mfc/reference/cgopherconnection-class.md#createlocator) 를 호출 하 여 개체에 대 한 포인터를 만들고 반환 `CGopherLocator` 합니다.

## <a name="cgopherlocatorgetlocatortype"></a><a name="getlocatortype"></a> CGopherLocator:: GetLocatorType

이 멤버 함수를 호출 하 여 로케이터 유형을 가져옵니다.

```
BOOL GetLocatorType(DWORD& dwRef) const;
```

### <a name="parameters"></a>매개 변수

*dwRef*<br/>
로케이터 유형을 수신 하는 DWORD에 대 한 참조입니다. 로케이터 형식의 테이블에 대 한 **설명을** 참조 하십시오.

### <a name="return-value"></a>반환 값

성공하면 0이 아니고, 그렇지 않으면 0입니다. 호출에 실패 하면 Win32 함수 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 를 호출 하 여 오류의 원인을 확인할 수 있습니다.

### <a name="remarks"></a>설명

가능한 형식은 다음과 같습니다.

|값|의미|
|-----------|-------------|
|GOPHER_TYPE_TEXT_FILE|ASCII 텍스트 파일입니다.|
|GOPHER_TYPE_DIRECTORY|추가 Gopher 항목의 디렉터리입니다.|
|GOPHER_TYPE_CSO|CSPHONE 책 서버.|
|GOPHER_TYPE_ERROR|오류 조건을 나타냅니다.|
|GOPHER_TYPE_MAC_BINHEX|BINHEX 형식의 Macintosh 파일입니다.|
|GOPHER_TYPE_DOS_ARCHIVE|DOS 보관 파일입니다.|
|GOPHER_TYPE_UNIX_UUENCODED|UUENCODE 파일입니다.|
|GOPHER_TYPE_INDEX_SERVER|인덱스 서버입니다.|
|GOPHER_TYPE_TELNET|텔넷 서버.|
|GOPHER_TYPE_BINARY|이진 파일입니다.|
|GOPHER_TYPE_REDUNDANT|중복 된 서버입니다. 에 포함 된 정보는 주 서버와 중복 됩니다. 주 서버는 GOPHER_TYPE_REDUNDANT 형식이 없는 마지막 디렉터리 항목입니다.|
|GOPHER_TYPE_TN3270|TN3270 서버입니다.|
|GOPHER_TYPE_GIF|GIF 그래픽 파일입니다.|
|GOPHER_TYPE_IMAGE|이미지 파일입니다.|
|GOPHER_TYPE_BITMAP|비트맵 파일입니다.|
|GOPHER_TYPE_MOVIE|동영상 파일입니다.|
|GOPHER_TYPE_SOUND|사운드 파일입니다.|
|GOPHER_TYPE_HTML|HTML 문서입니다.|
|GOPHER_TYPE_PDF|PDF 파일입니다.|
|GOPHER_TYPE_CALENDAR|일정 파일.|
|GOPHER_TYPE_INLINE|인라인 파일입니다.|
|GOPHER_TYPE_UNKNOWN|항목 유형을 알 수 없습니다.|
|GOPHER_TYPE_ASK|Ask + 항목입니다.|
|GOPHER_TYPE_GOPHER_PLUS|Gopher + 항목입니다.|

## <a name="cgopherlocatoroperator-lpctstr"></a><a name="operator_lpctstr"></a> CGopherLocator:: operator LPCTSTR

이 유용한 캐스팅 연산자는 개체에 포함 된 null로 끝나는 C 문자열에 액세스할 수 있는 효율적인 메서드를 제공 합니다 `CGopherLocator` .

```
operator LPCTSTR () const;
```

### <a name="return-value"></a>반환 값

문자열 데이터에 대 한 문자 포인터입니다.

### <a name="remarks"></a>설명

문자는 복사 되지 않습니다. 포인터만 반환 됩니다.

## <a name="see-also"></a>참고 항목

[CObject 클래스](../../mfc/reference/cobject-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind 클래스](../../mfc/reference/cgopherfilefind-class.md)
