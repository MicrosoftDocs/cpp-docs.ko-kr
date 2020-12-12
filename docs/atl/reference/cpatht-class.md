---
description: '자세한 정보: CPathT 클래스'
title: CPathT 클래스
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: 01657eca0e84a9a3271f7912f565dd1dd2417506
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97141091"
---
# <a name="cpatht-class"></a>CPathT 클래스

이 클래스는 경로를 나타냅니다.

> [!IMPORTANT]
> 이 클래스와 해당 멤버는 Windows 런타임에서 실행 되는 응용 프로그램에서 사용할 수 없습니다.

## <a name="syntax"></a>구문

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>매개 변수

*StringType*<br/>
경로에 사용할 ATL/MFC 문자열 클래스입니다 ( [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)참조).

## <a name="members"></a>멤버

### <a name="public-typedefs"></a>공용 Typedefs

|Name|설명|
|----------|-----------------|
|[CPathT::P CPATHT](#pcxstr)|상수 문자열 형식입니다.|
|[CPathT::P XSTR](#pxstr)|문자열 유형입니다.|
|[CPathT:: XCHAR](#xchar)|문자 형식입니다.|

### <a name="public-constructors"></a>Public 생성자

|이름|설명|
|----------|-----------------|
|[CPathT:: CPathT](#cpatht)|경로에 대 한 생성자입니다.|

### <a name="public-methods"></a>Public 메서드

|이름|설명|
|----------|-----------------|
|[CPathT:: AddBackslash](#addbackslash)|경로에 대 한 올바른 구문을 만들려면이 메서드를 호출 하 여 문자열 끝에 백슬래시를 추가 합니다.|
|[CPathT:: AddExtension](#addextension)|경로에 파일 확장명을 추가 하려면이 메서드를 호출 합니다.|
|[CPathT:: Append](#append)|현재 경로에 문자열을 추가 하려면이 메서드를 호출 합니다.|
|[CPathT:: BuildRoot](#buildroot)|지정 된 드라이브 번호에서 루트 경로를 만들려면이 메서드를 호출 합니다.|
|[CPathT:: 정식화](#canonicalize)|경로를 정규 형식으로 변환 하려면이 메서드를 호출 합니다.|
|[CPathT:: Combine](#combine)|이 메서드를 호출 하 여 디렉터리 이름을 나타내는 문자열과 파일 경로 이름을 나타내는 문자열을 하나의 경로로 연결 합니다.|
|[CPathT:: CommonPrefix](#commonprefix)|지정 된 경로가 현재 경로와 공통 접두사를 공유 하는지 여부를 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: CompactPath](#compactpath)|경로 구성 요소를 줄임표로 바꿔서 지정 된 픽셀 너비에 맞게 파일 경로를 잘라내려면이 메서드를 호출 합니다.|
|[CPathT:: CompactPathEx](#compactpathex)|경로 구성 요소를 줄임표로 바꿔서 지정 된 문자 수에 맞게 파일 경로를 잘라내려면이 메서드를 호출 합니다.|
|[CPathT:: FileExists](#fileexists)|이 메서드를 호출 하 여이 경로 이름에 파일이 있는지 여부를 확인 합니다.|
|[CPathT:: FindExtension](#findextension)|경로 내에서 파일 확장명의 위치를 찾으려면이 메서드를 호출 합니다.|
|[CPathT:: FindFileName](#findfilename)|경로 내에서 파일 이름의 위치를 찾으려면이 메서드를 호출 합니다.|
|[CPathT:: GetDriveNumber](#getdrivenumber)|' A ' 범위 내에 있는 드라이브 문자를 ' Z '로 검색 하 고 해당 드라이브 번호를 반환 하려면이 메서드를 호출 합니다.|
|[CPathT:: GetExtension](#getextension)|경로에서 파일 확장명을 가져오려면이 메서드를 호출 합니다.|
|[CPathT:: IsDirectory](#isdirectory)|경로가 유효한 디렉터리 인지 여부를 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: IsFileSpec](#isfilespec)|경로에서 경로 구분 문자 (예: ': ' 또는 ' ')를 검색 하려면이 메서드를 호출 \\ 합니다. 경로 구분 문자가 없는 경우 경로는 파일 사양 경로로 간주 됩니다.|
|[CPathT:: IsPrefix](#isprefix)|이 메서드를 호출 하 여 경로에 *pszPrefix* 에 의해 전달 된 형식의 올바른 접두사가 포함 되어 있는지 확인 합니다.|
|[CPathT:: IsRelative](#isrelative)|경로가 상대 경로 인지 확인 하려면이 메서드를 호출 합니다.|
|[CPathT::에서는 isroot](#isroot)|경로가 디렉터리 루트 인지 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: IsSameRoot](#issameroot)|다른 경로에 현재 경로를 사용 하는 공통 루트 구성 요소가 있는지 여부를 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: IsUNC](#isunc)|경로가 서버 및 공유에 대 한 유효한 UNC (범용 명명 규칙) 경로 인지 여부를 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: IsUNCServer](#isuncserver)|경로가 서버에 대 한 유효한 UNC (범용 명명 규칙) 경로 인지 여부를 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: IsUNCServerShare](#isuncservershare)|경로가 유효한 UNC (범용 명명 규칙) 공유 경로 \\ \  *서버* \  *공유* 인지 여부를 확인 하려면이 메서드를 호출 합니다.|
|[CPathT:: MakePretty](#makepretty)|경로에 일관 된 모양을 지정 하려면이 메서드를 호출 하 여 경로를 모두 소문자로 변환 합니다.|
|[CPathT:: MatchSpec](#matchspec)|와일드 카드 일치 형식을 포함 하는 문자열의 경로를 검색 하려면이 메서드를 호출 합니다.|
|[CPathT:: QuoteSpaces](#quotespaces)|공백을 포함 하는 경우이 메서드를 호출 하 여 경로를 따옴표로 묶습니다.|
|[CPathT:: RelativePathTo](#relativepathto)|파일이 나 폴더 간에 상대 경로를 만들려면이 메서드를 호출 합니다.|
|[CPathT:: RemoveArgs](#removeargs)|경로에서 모든 명령줄 인수를 제거 하려면이 메서드를 호출 합니다.|
|[CPathT:: RemoveBackslash](#removebackslash)|경로에서 후행 백슬래시를 제거 하려면이 메서드를 호출 합니다.|
|[CPathT:: RemoveBlanks](#removeblanks)|경로에서 선행 및 후행 공백을 모두 제거 하려면이 메서드를 호출 합니다.|
|[CPathT:: RemoveExtension](#removeextension)|경로 (있는 경우)에서 파일 확장명을 제거 하려면이 메서드를 호출 합니다.|
|[CPathT:: RemoveFileSpec](#removefilespec)|경로에서 후행 파일 이름 및 백슬래시를 제거 하려면이 메서드를 호출 합니다 (있는 경우).|
|[CPathT:: RenameExtension](#renameextension)|경로의 파일 이름 확장명을 새 확장명으로 바꾸려면이 메서드를 호출 합니다. 파일 이름에 확장명이 포함 되어 있지 않으면 확장명이 문자열의 끝에 연결 됩니다.|
|[CPathT:: SkipRoot](#skiproot)|드라이브 문자 또는 UNC 서버/공유 경로 부분을 무시 하 고 경로를 구문 분석 하려면이 메서드를 호출 합니다.|
|[CPathT:: StripPath](#strippath)|정규화 된 경로와 파일 이름의 경로 부분을 제거 하려면이 메서드를 호출 합니다.|
|[CPathT:: StripToRoot](#striptoroot)|루트 정보를 제외 하 고 경로의 모든 부분을 제거 하려면이 메서드를 호출 합니다.|
|[CPathT:: UnquoteSpaces](#unquotespaces)|경로의 시작과 끝에서 따옴표를 제거 하려면이 메서드를 호출 합니다.|

### <a name="public-operators"></a>Public 연산자

|Name|설명|
|----------|-----------------|
|[CPathT:: operator const StringType &](#operator_const_stringtype_amp)|이 연산자를 사용 하면 개체를 문자열 처럼 처리할 수 있습니다.|
|[CPathT:: operator CPathT::P CPATHT](#operator_cpatht__pcxstr)|이 연산자를 사용 하면 개체를 문자열 처럼 처리할 수 있습니다.|
|[CPathT:: operator StringType &](#operator_stringtype_amp)|이 연산자를 사용 하면 개체를 문자열 처럼 처리할 수 있습니다.|
|[CPathT:: operator + =](#operator_add_eq)|이 연산자는 경로에 문자열을 추가 합니다.|

### <a name="public-data-members"></a>공용 데이터 멤버

|Name|설명|
|----------|-----------------|
|[CPathT:: m_strPath](#m_strpath)|경로입니다.|

## <a name="remarks"></a>설명

`CPath`, `CPathA` 및 `CPathW` 는 다음과 같이 정의 된의 인스턴스화입니다 `CPathT` .

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>요구 사항

**헤더:** 이 경로 .h

## <a name="cpathtaddbackslash"></a><a name="addbackslash"></a> CPathT:: AddBackslash

경로에 대 한 올바른 구문을 만들려면이 메서드를 호출 하 여 문자열 끝에 백슬래시를 추가 합니다. 경로에 이미 후행 백슬래시가 있으면 백슬래시가 추가 되지 않습니다.

```cpp
void AddBackslash();
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathaddbackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)를 참조 하세요.

## <a name="cpathtaddextension"></a><a name="addextension"></a> CPathT:: AddExtension

경로에 파일 확장명을 추가 하려면이 메서드를 호출 합니다.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>매개 변수

*pszExtension*<br/>
추가할 파일 확장명입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)을 참조 하세요.

## <a name="cpathtappend"></a><a name="append"></a> CPathT:: Append

현재 경로에 문자열을 추가 하려면이 메서드를 호출 합니다.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>매개 변수

*pszMore*<br/>
추가할 문자열입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)를 참조 하세요.

## <a name="cpathtbuildroot"></a><a name="buildroot"></a> CPathT:: BuildRoot

지정 된 드라이브 번호에서 루트 경로를 만들려면이 메서드를 호출 합니다.

```cpp
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>매개 변수

*iDrive*<br/>
드라이브 번호 (0은 A:, 1은 B: 등)입니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)를 참조 하세요.

## <a name="cpathtcanonicalize"></a><a name="canonicalize"></a> CPathT:: 정식화

경로를 정규 형식으로 변환 하려면이 메서드를 호출 합니다.

```cpp
void Canonicalize();
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)를 참조 하세요.

## <a name="cpathtcombine"></a><a name="combine"></a> CPathT:: Combine

이 메서드를 호출 하 여 디렉터리 이름을 나타내는 문자열과 파일 경로 이름을 나타내는 문자열을 하나의 경로로 연결 합니다.

```cpp
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>매개 변수

*pszDir*<br/>
디렉터리 경로입니다.

*pszFile*<br/>
파일 경로입니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)을 참조 하세요.

## <a name="cpathtcommonprefix"></a><a name="commonprefix"></a> CPathT:: CommonPrefix

지정 된 경로가 현재 경로와 공통 접두사를 공유 하는지 여부를 확인 하려면이 메서드를 호출 합니다.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>매개 변수

*pszOther*<br/>
현재 항목과 비교할 경로입니다.

### <a name="return-value"></a>반환 값

공통 접두사를 반환 합니다.

### <a name="remarks"></a>설명

접두사는 "C: \\ \\ ", ".", "...", "... \\ \\ " 형식 중 하나입니다. 자세한 내용은 [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)를 참조 하세요.

## <a name="cpathtcompactpath"></a><a name="compactpath"></a> CPathT:: CompactPath

경로 구성 요소를 줄임표로 바꿔서 지정 된 픽셀 너비에 맞게 파일 경로를 잘라내려면이 메서드를 호출 합니다.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>매개 변수

*hDC*<br/>
글꼴 메트릭에 사용 되는 장치 컨텍스트입니다.

*nWidth*<br/>
문자열이 강제로 적용 되는 너비 (픽셀)입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)를 참조 하세요.

## <a name="cpathtcompactpathex"></a><a name="compactpathex"></a> CPathT:: CompactPathEx

경로 구성 요소를 줄임표로 바꿔서 지정 된 문자 수에 맞게 파일 경로를 잘라내려면이 메서드를 호출 합니다.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>매개 변수

*nMaxChars*<br/>
종료 NULL 문자를 포함 하 여 새 문자열에 포함할 최대 문자 수입니다.

*dwFlags*<br/>
예약되어 있습니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)를 참조 하세요.

## <a name="cpathtcpatht"></a><a name="cpatht"></a> CPathT:: CPathT

생성자입니다.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>매개 변수

*pszPath*<br/>
경로 문자열에 대 한 포인터입니다.

*path*<br/>
경로 문자열입니다.

## <a name="cpathtfileexists"></a><a name="fileexists"></a> CPathT:: FileExists

이 메서드를 호출 하 여이 경로 이름에 파일이 있는지 여부를 확인 합니다.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>반환 값

파일이 있으면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)를 참조 하세요.

## <a name="cpathtfindextension"></a><a name="findextension"></a> CPathT:: FindExtension

경로 내에서 파일 확장명의 위치를 찾으려면이 메서드를 호출 합니다.

```
int FindExtension() const;
```

### <a name="return-value"></a>반환 값

확장 앞에 나오는 "."의 위치를 반환 합니다. 확장을 찾을 수 없는 경우는-1을 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)을 참조 하세요.

## <a name="cpathtfindfilename"></a><a name="findfilename"></a> CPathT:: FindFileName

경로 내에서 파일 이름의 위치를 찾으려면이 메서드를 호출 합니다.

```
int FindFileName() const;
```

### <a name="return-value"></a>반환 값

파일 이름의 위치를 반환 합니다. 파일 이름을 찾을 수 없으면-1을 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)을 참조 하세요.

## <a name="cpathtgetdrivenumber"></a><a name="getdrivenumber"></a> CPathT:: GetDriveNumber

' A ' 범위 내에 있는 드라이브 문자를 ' Z '로 검색 하 고 해당 드라이브 번호를 반환 하려면이 메서드를 호출 합니다.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>반환 값

드라이브에 드라이브 문자가 있으면 드라이브 번호를 0에서 25 사이의 정수로 반환 하 고, 그렇지 않은 경우-1을 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)를 참조 하세요.

## <a name="cpathtgetextension"></a><a name="getextension"></a> CPathT:: GetExtension

경로에서 파일 확장명을 가져오려면이 메서드를 호출 합니다.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>반환 값

파일 확장명을 반환 합니다.

## <a name="cpathtisdirectory"></a><a name="isdirectory"></a> CPathT:: IsDirectory

경로가 유효한 디렉터리 인지 여부를 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>반환 값

경로가 디렉터리 이면 0이 아닌 값을 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)를 참조 하세요.

## <a name="cpathtisfilespec"></a><a name="isfilespec"></a> CPathT:: IsFileSpec

경로에서 경로 구분 문자 (예: ': ' 또는 ' ')를 검색 하려면이 메서드를 호출 \\ 합니다. 경로 구분 문자가 없는 경우 경로는 파일 사양 경로로 간주 됩니다.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>반환 값

경로에 경로 구분 문자가 없으면 TRUE를 반환 하 고, 경로 구분 문자가 있으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)을 참조 하세요.

## <a name="cpathtisprefix"></a><a name="isprefix"></a> CPathT:: IsPrefix

이 메서드를 호출 하 여 경로에 *pszPrefix* 에 의해 전달 된 형식의 올바른 접두사가 포함 되어 있는지 확인 합니다.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>매개 변수

*pszPrefix*<br/>
검색할 접두사입니다. 접두사는 "C: \\ \\ ", ".", "...", "... \\ \\ " 형식 중 하나입니다.

### <a name="return-value"></a>반환 값

경로에 접두사가 포함 되어 있으면 TRUE를, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)를 참조 하세요.

## <a name="cpathtisrelative"></a><a name="isrelative"></a> CPathT:: IsRelative

경로가 상대 경로 인지 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>반환 값

경로가 상대적인 경우 TRUE를 반환 하 고, 절대 경로인 경우 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)를 참조 하세요.

## <a name="cpathtisroot"></a><a name="isroot"></a> CPathT::에서는 isroot

경로가 디렉터리 루트 인지 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>반환 값

경로가 루트 이면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)를 참조 하세요.

## <a name="cpathtissameroot"></a><a name="issameroot"></a> CPathT:: IsSameRoot

다른 경로에 현재 경로를 사용 하는 공통 루트 구성 요소가 있는지 여부를 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>매개 변수

*pszOther*<br/>
다른 경로입니다.

### <a name="return-value"></a>반환 값

두 문자열에 동일한 루트 구성 요소가 있으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)를 참조 하세요.

## <a name="cpathtisunc"></a><a name="isunc"></a> CPathT:: IsUNC

경로가 서버 및 공유에 대 한 유효한 UNC (범용 명명 규칙) 경로 인지 여부를 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>반환 값

경로가 유효한 UNC 경로 이면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)를 참조 하세요.

## <a name="cpathtisuncserver"></a><a name="isuncserver"></a> CPathT:: IsUNCServer

경로가 서버에 대 한 유효한 UNC (범용 명명 규칙) 경로 인지 여부를 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>반환 값

문자열이 서버에 대 한 유효한 UNC 경로 (공유 이름 없음) 이면 TRUE, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)를 참조 하세요.

## <a name="cpathtisuncservershare"></a><a name="isuncservershare"></a> CPathT:: IsUNCServerShare

경로가 유효한 UNC (범용 명명 규칙) 공유 경로 \\ \  *서버* \  *공유* 인지 여부를 확인 하려면이 메서드를 호출 합니다.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>반환 값

경로가 폼 서버 공유에 있으면 TRUE를 반환 하 고, \\ \   \  그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)를 참조 하세요.

## <a name="cpathtm_strpath"></a><a name="m_strpath"></a> CPathT:: m_strPath

경로입니다.

```
StringType m_strPath;
```

### <a name="remarks"></a>설명

`StringType` 는에 대 한 템플릿 매개 변수입니다 `CPathT` .

## <a name="cpathtmakepretty"></a><a name="makepretty"></a> CPathT:: MakePretty

경로에 일관 된 모양을 지정 하려면이 메서드를 호출 하 여 경로를 모두 소문자로 변환 합니다.

```
BOOL MakePretty();
```

### <a name="return-value"></a>반환 값

경로가 변환 되었으면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)를 참조 하세요.

## <a name="cpathtmatchspec"></a><a name="matchspec"></a> CPathT:: MatchSpec

와일드 카드 일치 형식을 포함 하는 문자열의 경로를 검색 하려면이 메서드를 호출 합니다.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>매개 변수

*pszSpec*<br/>
검색할 파일 형식의 null로 끝나는 문자열에 대 한 포인터입니다. 예를 들어 현재 경로에 있는 파일이 DOC 파일 인지 여부를 테스트 하려면 *pszSpec* 을 "* .doc"로 설정 해야 합니다.

### <a name="return-value"></a>반환 값

문자열이 일치 하면 TRUE를 반환 하 고, 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)을 참조 하세요.

## <a name="cpathtoperator-"></a><a name="operator_add_eq"></a> CPathT:: operator + =

이 연산자는 경로에 문자열을 추가 합니다.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>매개 변수

*pszMore*<br/>
추가할 문자열입니다.

### <a name="return-value"></a>반환 값

업데이트 된 경로를 반환 합니다.

## <a name="cpathtoperator-const-stringtype-amp"></a><a name="operator_const_stringtype_amp"></a> CPathT:: operator const StringType &amp;

이 연산자를 사용 하면 개체를 문자열 처럼 처리할 수 있습니다.

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>반환 값

이 개체에서 관리 하는 현재 경로를 나타내는 문자열을 반환 합니다.

## <a name="cpathtoperator-cpathtpcxstr"></a><a name="operator_cpatht__pcxstr"></a> CPathT:: operator CPathT::P CPATHT

이 연산자를 사용 하면 개체를 문자열 처럼 처리할 수 있습니다.

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>반환 값

이 개체에서 관리 하는 현재 경로를 나타내는 문자열을 반환 합니다.

## <a name="cpathtoperator-stringtype-amp"></a><a name="operator_stringtype_amp"></a> CPathT:: operator StringType &amp;

이 연산자를 사용 하면 개체를 문자열 처럼 처리할 수 있습니다.

```
operator StringType&() throw();
```

### <a name="return-value"></a>반환 값

이 개체에서 관리 하는 현재 경로를 나타내는 문자열을 반환 합니다.

## <a name="cpathtpcxstr"></a><a name="pcxstr"></a> CPathT::P CPATHT

상수 문자열 형식입니다.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>설명

`StringType` 는에 대 한 템플릿 매개 변수입니다 `CPathT` .

## <a name="cpathtpxstr"></a><a name="pxstr"></a> CPathT::P XSTR

문자열 유형입니다.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>설명

`StringType` 는에 대 한 템플릿 매개 변수입니다 `CPathT` .

## <a name="cpathtquotespaces"></a><a name="quotespaces"></a> CPathT:: QuoteSpaces

공백을 포함 하는 경우이 메서드를 호출 하 여 경로를 따옴표로 묶습니다.

```cpp
void QuoteSpaces();
```

### <a name="remarks"></a>설명

자세한 내용은 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)를 참조 하세요.

## <a name="cpathtrelativepathto"></a><a name="relativepathto"></a> CPathT:: RelativePathTo

파일이 나 폴더 간에 상대 경로를 만들려면이 메서드를 호출 합니다.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>매개 변수

*pszFrom*<br/>
상대 경로의 시작 부분입니다.

*dwAttrFrom*<br/>
*PszFrom* 의 파일 특성입니다. 이 값에 FILE_ATTRIBUTE_DIRECTORY 포함 된 경우 *pszFrom* 은 디렉터리로 간주 됩니다. 그렇지 않으면 *pszFrom* 는 파일로 가정 합니다.

*pszTo*<br/>
상대 경로의 끝점입니다.

*dwAttrTo*<br/>
*PszTo* 의 파일 특성입니다. 이 값에 FILE_ATTRIBUTE_DIRECTORY 포함 된 경우 *pszTo* 은 디렉터리로 간주 됩니다. 그렇지 않으면 *pszTo* 는 파일로 가정 합니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)를 참조 하세요.

## <a name="cpathtremoveargs"></a><a name="removeargs"></a> CPathT:: RemoveArgs

경로에서 모든 명령줄 인수를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveArgs();
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)를 참조 하세요.

## <a name="cpathtremovebackslash"></a><a name="removebackslash"></a> CPathT:: RemoveBackslash

경로에서 후행 백슬래시를 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveBackslash();
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremovebackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)를 참조 하세요.

## <a name="cpathtremoveblanks"></a><a name="removeblanks"></a> CPathT:: RemoveBlanks

경로에서 선행 및 후행 공백을 모두 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveBlanks();
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)을 참조 하세요.

## <a name="cpathtremoveextension"></a><a name="removeextension"></a> CPathT:: RemoveExtension

경로 (있는 경우)에서 파일 확장명을 제거 하려면이 메서드를 호출 합니다.

```cpp
void RemoveExtension();
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)을 참조 하세요.

## <a name="cpathtremovefilespec"></a><a name="removefilespec"></a> CPathT:: RemoveFileSpec

경로에서 후행 파일 이름 및 백슬래시를 제거 하려면이 메서드를 호출 합니다 (있는 경우).

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)을 참조 하세요.

## <a name="cpathtrenameextension"></a><a name="renameextension"></a> CPathT:: RenameExtension

경로의 파일 이름 확장명을 새 확장명으로 바꾸려면이 메서드를 호출 합니다. 파일 이름에 확장명이 포함 되어 있지 않으면 확장명이 경로 끝에 연결 됩니다.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>매개 변수

*pszExtension*<br/>
"." 문자로 시작 하는 새 파일 이름 확장명입니다.

### <a name="return-value"></a>반환 값

성공 하면 TRUE를 반환 하 고 실패 하면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)를 참조 하세요.

## <a name="cpathtskiproot"></a><a name="skiproot"></a> CPathT:: SkipRoot

드라이브 문자 또는 UNC (범용 명명 규칙) 서버/공유 경로 부분을 무시 하 고 경로를 구문 분석 하려면이 메서드를 호출 합니다.

```
int SkipRoot() const;
```

### <a name="return-value"></a>반환 값

루트 (드라이브 문자 또는 UNC 서버/공유) 뒤에 있는 하위 경로 시작 위치를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)를 참조 하세요.

## <a name="cpathtstrippath"></a><a name="strippath"></a> CPathT:: StripPath

정규화 된 경로와 파일 이름의 경로 부분을 제거 하려면이 메서드를 호출 합니다.

```cpp
void StripPath();
```

### <a name="remarks"></a>설명

자세한 내용은 [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)를 참조 하세요.

## <a name="cpathtstriptoroot"></a><a name="striptoroot"></a> CPathT:: StripToRoot

루트 정보를 제외 하 고 경로의 모든 부분을 제거 하려면이 메서드를 호출 합니다.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>반환 값

경로에서 올바른 드라이브 문자를 찾은 경우 TRUE를 반환 하 고 그렇지 않으면 FALSE를 반환 합니다.

### <a name="remarks"></a>설명

자세한 내용은 [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)를 참조 하세요.

## <a name="cpathtunquotespaces"></a><a name="unquotespaces"></a> CPathT:: UnquoteSpaces

경로의 시작과 끝에서 따옴표를 제거 하려면이 메서드를 호출 합니다.

```cpp
void UnquoteSpaces();
```

### <a name="remarks"></a>설명

자세한 내용은 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)를 참조 하세요.

## <a name="cpathtxchar"></a><a name="xchar"></a> CPathT:: XCHAR

문자 형식입니다.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>설명

`StringType` 는에 대 한 템플릿 매개 변수입니다 `CPathT` .

## <a name="see-also"></a>참고 항목

[클래스](../../atl/reference/atl-classes.md)<br/>
[CStringT 클래스](../../atl-mfc-shared/reference/cstringt-class.md)
