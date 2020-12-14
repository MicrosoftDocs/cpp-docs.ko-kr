---
description: '자세히 알아보기: CMetaFileDC 클래스'
title: CMetaFileDC 클래스
ms.date: 11/04/2016
f1_keywords:
- CMetaFileDC
- AFXEXT/CMetaFileDC
- AFXEXT/CMetaFileDC::CMetaFileDC
- AFXEXT/CMetaFileDC::Close
- AFXEXT/CMetaFileDC::CloseEnhanced
- AFXEXT/CMetaFileDC::Create
- AFXEXT/CMetaFileDC::CreateEnhanced
helpviewer_keywords:
- CMetaFileDC [MFC], CMetaFileDC
- CMetaFileDC [MFC], Close
- CMetaFileDC [MFC], CloseEnhanced
- CMetaFileDC [MFC], Create
- CMetaFileDC [MFC], CreateEnhanced
ms.assetid: ffce60fa-4181-4d46-9832-25e46fad4db4
ms.openlocfilehash: b4b506818b1864c40225055faa2582820f15f423
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336624"
---
# <a name="cmetafiledc-class"></a>CMetaFileDC 클래스

원하는 이미지 또는 텍스트를 만들기 위해 재생할 수 있는 GDI(그래픽 디바이스 인터페이스) 명령 시퀀스가 포함된 Windows 메타파일을 구현합니다.

## <a name="syntax"></a>구문

```
class CMetaFileDC : public CDC
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CMetaFileDC:: CMetaFileDC](#cmetafiledc)|`CMetaFileDC` 개체를 생성합니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CMetaFileDC:: Close](#close)|장치 컨텍스트를 닫고 메타 파일 핸들을 만듭니다.|
|[CMetaFileDC::CloseEnhanced](#closeenhanced)|향상 된 메타 파일 장치 컨텍스트를 닫고 향상 된 메타 파일 핸들을 만듭니다.|
|[CMetaFileDC::Create](#create)|Windows 메타 파일 장치 컨텍스트를 만들어 개체에 연결 `CMetaFileDC` 합니다.|
|[CMetaFileDC::CreateEnhanced](#createenhanced)|확장 형식 메타 파일에 대 한 메타 파일 장치 컨텍스트를 만듭니다.|

## <a name="remarks"></a>설명

Windows 메타 파일을 구현 하려면 먼저 개체를 만듭니다 `CMetaFileDC` . `CMetaFileDC` 생성자를 호출한 다음, Windows 메타 파일 장치 컨텍스트를 만들고 `CMetaFileDC` 개체에 연결하는 [Create](#create) member 함수를 호출합니다.

그런 다음 `CMetaFileDC` 개체를 재생 하려는 CDC GDI 명령의 시퀀스로 보냅니다. 및와 같은 출력을 만드는 GDI 명령만 `MoveTo` `LineTo` 사용할 수 있습니다.

원하는 명령을 메타 파일에 보낸 후에는 `Close` 멤버 함수를 호출 합니다 .이 함수는 메타 파일 장치 컨텍스트를 닫고 메타 파일 핸들을 반환 합니다. 그런 다음 개체를 삭제 `CMetaFileDC` 합니다.

[CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) 는 메타 파일 핸들을 사용 하 여 메타 파일을 반복 해 서 재생할 수 있습니다. 메타 파일을 디스크에 복사 하는 [Copymetafile 파일](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)등의 Windows 함수를 통해 조작할 수도 있습니다.

메타 파일이 더 이상 필요 하지 않은 경우 [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) Windows 함수를 사용 하 여 메모리에서 삭제 합니다.

개체를 구현 하 여 `CMetaFileDC` 와 같이 출력 호출과 특성 GDI 호출을 모두 처리할 수 있습니다 `GetTextExtent` . 이러한 메타 파일은 보다 유연 하며, 일반적으로 출력 및 특성 호출의 혼합으로 구성 된 일반 GDI 코드를 더 쉽게 다시 사용할 수 있습니다. `CMetaFileDC`클래스는 CDC에서 및 라는 두 개의 장치 컨텍스트를 상속 `m_hDC` `m_hAttribDC` 합니다. `m_hDC`장치 컨텍스트는 모든 [cdc](../../mfc/reference/cdc-class.md) gdi 출력 호출을 처리 하 고 `m_hAttribDC` 장치 컨텍스트는 모든 cdc gdi 특성 호출을 처리 합니다. 일반적으로 이러한 두 장치 컨텍스트는 동일한 장치를 참조 합니다. 의 경우 `CMetaFileDC` DC 특성은 기본적으로 NULL로 설정 됩니다.

파일이 아닌 화면, 프린터 또는 장치를 가리키는 두 번째 장치 컨텍스트를 만든 다음 `SetAttribDC` 멤버 함수를 호출 하 여 새 장치 컨텍스트를에 연결 `m_hAttribDC` 합니다. 이제 정보에 대 한 GDI 호출이 새으로 전송 됩니다 `m_hAttribDC` . 출력 GDI 호출은 메타 파일을 나타내는로 이동 합니다 `m_hDC` .

에 대 한 자세한 내용은 `CMetaFileDC` [장치 컨텍스트](../../mfc/device-contexts.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CMetaFileDC`

## <a name="requirements"></a>요구 사항

**헤더:** afxext.h

## <a name="cmetafiledcclose"></a><a name="close"></a> CMetaFileDC:: Close

메타 파일 장치 컨텍스트를 닫고 [CDC::P laymetafile](../../mfc/reference/cdc-class.md#playmetafile) 멤버 함수를 사용 하 여 메타 파일을 재생 하는 데 사용할 수 있는 Windows 메타 파일 핸들을 만듭니다.

```
HMETAFILE Close();
```

### <a name="return-value"></a>반환 값

함수가 성공 하는 경우 유효한 HMETAFILE 파일입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

Windows 메타 파일 핸들을 사용 하 여 [Copymetafile 파일](/windows/win32/api/wingdi/nf-wingdi-copymetafilew)등의 windows 함수를 사용 하 여 메타 파일을 조작할 수도 있습니다.

Windows [DeleteMetaFile](/windows/win32/api/wingdi/nf-wingdi-deletemetafile) 함수를 호출 하 여 사용 후 메타 파일을 삭제 합니다.

## <a name="cmetafiledccloseenhanced"></a><a name="closeenhanced"></a> CMetaFileDC:: CloseEnhanced

향상 된 메타 파일 장치 컨텍스트를 닫고 향상 된 형식 메타 파일을 식별 하는 핸들을 반환 합니다.

```
HENHMETAFILE CloseEnhanced();
```

### <a name="return-value"></a>반환 값

성공 하는 경우 확장 메타 파일의 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

응용 프로그램은이 함수에서 반환 된 확장 메타 파일 핸들을 사용 하 여 다음 작업을 수행할 수 있습니다.

- 확장 메타 파일에 저장 된 그림 표시

- 확장 메타 파일의 복사본 만들기

- 확장 메타 파일의 개별 레코드 열거, 편집 또는 복사

- 확장 메타 파일 헤더에서 메타 파일 내용에 대 한 선택적 설명을 검색 합니다.

- 향상 된 메타 파일 헤더의 복사본을 검색 합니다.

- 확장 메타 파일의 이진 복사본 검색

- 선택적 색상표의 색 열거

- 향상 된 형식 메타 파일을 Windows 형식 메타 파일로 변환

응용 프로그램에 향상 된 메타 파일 핸들이 더 이상 필요 하지 않은 경우 Win32 함수를 호출 하 여 핸들을 해제 해야 합니다 `DeleteEnhMetaFile` .

## <a name="cmetafiledccmetafiledc"></a><a name="cmetafiledc"></a> CMetaFileDC:: CMetaFileDC

`CMetaFileDC`두 단계로 개체를 생성 합니다.

```
CMetaFileDC();
```

### <a name="remarks"></a>설명

먼저를 호출 하 고, `CMetaFileDC` 를 호출 하 `Create` 여 Windows 메타 파일 장치 컨텍스트를 만들고 개체에 연결 `CMetaFileDC` 합니다.

## <a name="cmetafiledccreate"></a><a name="create"></a> CMetaFileDC:: Create

`CMetaFileDC`두 단계로 개체를 생성 합니다.

```
BOOL Create(LPCTSTR lpszFilename = NULL);
```

### <a name="parameters"></a>매개 변수

*lpszFilename*<br/>
는 null로 끝나는 문자열을 가리킵니다. 만들 메타 파일의 파일 이름을 지정 합니다. *LpszFilename* 가 NULL 이면 새 메모리 내 메타 파일이 만들어집니다.

### <a name="return-value"></a>반환 값

함수가 성공하면 0이 아니고 그렇지 않으면 0입니다.

### <a name="remarks"></a>설명

먼저 생성자 `CMetaFileDC` 를 호출한 다음을 호출 하 여 `Create` Windows 메타 파일 장치 컨텍스트를 만들고 개체에 연결 `CMetaFileDC` 합니다.

## <a name="cmetafiledccreateenhanced"></a><a name="createenhanced"></a> CMetaFileDC:: CreateEnhanced

향상 된 형식 메타 파일에 대 한 장치 컨텍스트를 만듭니다.

```
BOOL CreateEnhanced(
    CDC* pDCRef,
    LPCTSTR lpszFileName,
    LPCRECT lpBounds,
    LPCTSTR lpszDescription);
```

### <a name="parameters"></a>매개 변수

*pDCRef*<br/>
확장 메타 파일에 대 한 참조 장치를 식별 합니다.

*lpszFileName*<br/>
는 null로 끝나는 문자열을 가리킵니다. 만들 확장 메타 파일의 파일 이름을 지정 합니다. 이 매개 변수가 NULL 이면 향상 된 메타 파일은 메모리를 기반으로 하며 개체가 제거 되거나 Win32 함수가 호출 될 때 해당 콘텐츠가 손실 됩니다 `DeleteEnhMetaFile` .

*lpBounds*<br/>
확장 메타 파일에 저장할 그림의 HIMETRIC 단위 (.01 단위)를 지정 하는 [Crect](../../atl-mfc-shared/reference/crect-class.md) 개체 또는 [RECT](/windows/win32/api/windef/ns-windef-rect) 데이터 구조를 가리킵니다.

*lpszDescription*<br/>
그림을 만든 응용 프로그램의 이름 뿐만 아니라 그림의 제목을 지정 하는 0으로 끝나는 문자열을 가리킵니다.

### <a name="return-value"></a>반환 값

성공 하는 경우 확장 메타 파일에 대 한 장치 컨텍스트의 핸들입니다. 그렇지 않으면 NULL입니다.

### <a name="remarks"></a>설명

이 DC는 장치 독립적 그림을 저장 하는 데 사용할 수 있습니다.

Windows에서는 지 *수 매개 변수로 식별 되는 참조* 장치를 사용 하 여 그림이 원래 있었던 장치의 해상도와 단위를 기록 합니다. *Pdce cref* 매개 변수가 NULL 이면 현재 디스플레이 장치를 참조에 사용 합니다.

`RECT` *Lpbounds* 매개 변수에서 가리키는 데이터 구조의 왼쪽 및 상위 멤버는 각각 오른쪽 및 아래 멤버 보다 작아야 합니다. 사각형의 가장자리를 따라 나오는 점이 그림에 포함 되어 있습니다. *Lpbounds* 가 NULL 인 경우 GDI (그래픽 장치 인터페이스)는 응용 프로그램에서 그린 그림을 묶을 수 있는 가장 작은 사각형의 크기를 계산 합니다. 가능 하면 *Lpbounds* 매개 변수를 제공 해야 합니다.

*LpszDescription* 매개 변수에서 가리키는 문자열은 응용 프로그램 이름과 그림 이름 사이에 null 문자를 포함 해야 하 고 두 개의 null 문자 (예: "XYZ Graphics Editor\0Bald Eagle\0\0")로 끝나야 합니다. 여기서 \ 0은 null 문자를 나타냅니다. *LpszDescription* 가 NULL 인 경우에는 확장 메타 파일 헤더에 해당 항목이 없습니다.

응용 프로그램은이 함수에서 만든 DC를 사용 하 여 그래픽 그림을 향상 된 메타 파일에 저장 합니다. 이 DC를 식별 하는 핸들은 모든 GDI 함수에 전달 될 수 있습니다.

응용 프로그램이 확장 된 메타 파일에 사진을 저장 한 후에는 함수를 호출 하 여 출력 장치에 그림을 표시할 수 있습니다 `CDC::PlayMetaFile` . 그림을 표시 하는 경우 Windows는 *Lpbounds* 매개 변수에서 가리키는 사각형과 참조 장치의 해상도 데이터를 사용 하 여 그림의 위치를 조정 하 고 크기를 조정 합니다. 이 함수에서 반환 되는 장치 컨텍스트에는 모든 새 DC와 연결 된 동일한 기본 특성이 포함 됩니다.

응용 프로그램은 Win32 함수를 사용 `GetWinMetaFileBits` 하 여 향상 된 메타 파일을 이전 Windows 메타 파일 형식으로 변환 해야 합니다.

확장 메타 파일의 파일 이름에는를 사용 해야 합니다. EMF 확장.

## <a name="see-also"></a>참고 항목

[CDC 클래스](../../mfc/reference/cdc-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)
