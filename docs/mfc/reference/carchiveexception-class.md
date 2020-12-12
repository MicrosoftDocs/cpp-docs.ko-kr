---
description: '자세히 알아보기: CArchiveException 클래스'
title: CArchiveException 클래스
ms.date: 11/04/2016
f1_keywords:
- CArchiveException
- AFX/CArchiveException
- AFX/CArchiveException::CArchiveException
- AFX/CArchiveException::m_cause
- AFX/CArchiveException::m_strFileName
helpviewer_keywords:
- CArchiveException [MFC], CArchiveException
- CArchiveException [MFC], m_cause
- CArchiveException [MFC], m_strFileName
ms.assetid: da31a127-e86c-41d1-b0b6-bed0865b1b49
ms.openlocfilehash: ce8355583e0a7a3fd8a382873a0e4b2a1ea91b83
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185403"
---
# <a name="carchiveexception-class"></a>CArchiveException 클래스

Serialization 예외 상태를 나타냅니다.

## <a name="syntax"></a>구문

```
class CArchiveException : public CException
```

## <a name="members"></a>멤버

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CArchiveException::CArchiveException](#carchiveexception)|`CArchiveException` 개체를 생성합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CArchiveException:: m_cause](#m_cause)|예외 원인을 나타냅니다.|
|[CArchiveException:: m_strFileName](#m_strfilename)|이 예외 조건의 파일 이름을 지정 합니다.|

## <a name="remarks"></a>설명

클래스에는 `CArchiveException` 예외의 원인을 나타내는 공용 데이터 멤버가 포함 되어 있습니다.

`CArchiveException` 개체는 [CArchive](../../mfc/reference/carchive-class.md) 멤버 함수 내에서 생성 및 throw 됩니다. 이러한 개체는 **CATCH** 식의 범위 내에서 액세스할 수 있습니다. 원인 코드는 운영 체제에 독립적입니다. 예외 처리에 대 한 자세한 내용은 [예외 처리 (MFC)](../../mfc/exception-handling-in-mfc.md)를 참조 하세요.

## <a name="inheritance-hierarchy"></a>상속 계층 구조

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CArchiveException`

## <a name="requirements"></a>요구 사항

**헤더:** afx

## <a name="carchiveexceptioncarchiveexception"></a><a name="carchiveexception"></a> CArchiveException::CArchiveException

개체를 생성 `CArchiveException` 하 여 개체의 *원인* 값을 저장 합니다.

```
CArchiveException(
    int cause = CArchiveException::none,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>매개 변수

*cause*<br/>
예외에 대 한 이유를 나타내는 열거형 형식 변수입니다. 열거자 목록은 [m_cause](#m_cause) 데이터 멤버를 참조 하세요.

*lpszArchiveName*<br/>
예외를 발생 시킨 개체의 이름을 포함 하는 문자열을 가리킵니다 `CArchive` .

### <a name="remarks"></a>설명

힙에서 개체를 만들어 `CArchiveException` 직접 throw 하거나 전역 함수 [AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception) 에서이를 처리 하도록 할 수 있습니다.

이 생성자를 직접 사용 하지 마십시오. 대신 전역 함수를 호출 `AfxThrowArchiveException` 합니다.

## <a name="carchiveexceptionm_cause"></a><a name="m_cause"></a> CArchiveException:: m_cause

예외의 원인을 지정 합니다.

```
int m_cause;
```

### <a name="remarks"></a>설명

이 데이터 멤버는 형식의 공용 변수입니다 **`int`** . 해당 값은 열거형 형식에 의해 정의 됩니다 `CArchiveException` . 아래에 열거자와 해당 의미가 나와 있습니다.

- `CArchiveException::none` 오류가 발생 하지 않았습니다.

- `CArchiveException::genericException` 지정 되지 않은 오류입니다.

- `CArchiveException::readOnly` 로드를 위해 열린 보관 파일에 쓰려고 했습니다.

- `CArchiveException::endOfFile` 개체를 읽는 동안 파일의 끝에 도달 했습니다.

- `CArchiveException::writeOnly` 저장을 위해 열린 보관 파일에서 읽으려고 했습니다.

- `CArchiveException::badIndex` 파일 형식이 잘못 되었습니다.

- `CArchiveException::badClass` 개체를 잘못 된 형식의 개체로 읽으려고 했습니다.

- `CArchiveException::badSchema` 다른 버전의 클래스를 사용 하 여 개체를 읽으려고 했습니다.

    > [!NOTE]
    >  이러한 `CArchiveException` 원인 열거자는 `CFileException` 원인 열거자와는 다릅니다.

    > [!NOTE]
    > `CArchiveException::generic`는 사용되지 않습니다. 대신 `genericException`를 사용하세요. 응용 프로그램에서 **제네릭을** 사용 하 고/clr을 사용 하 여 빌드한 경우 쉽게 해독할 수 없는 구문 오류가 발생 합니다.

## <a name="carchiveexceptionm_strfilename"></a><a name="m_strfilename"></a> CArchiveException:: m_strFileName

이 예외 조건의 파일 이름을 지정 합니다.

```
CString m_strFileName;
```

## <a name="see-also"></a>참고 항목

[CException 클래스](../../mfc/reference/cexception-class.md)<br/>
[계층 구조 차트](../../mfc/hierarchy-chart.md)<br/>
[CArchive 클래스](../../mfc/reference/carchive-class.md)<br/>
[AfxThrowArchiveException](../../mfc/reference/exception-processing.md#afxthrowarchiveexception)<br/>
[예외 처리](../../mfc/reference/exception-processing.md)
