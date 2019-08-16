---
title: ATL 경로 함수
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497978"
---
# <a name="atl-path-functions"></a>ATL 경로 함수

ATL은 [Cpatht](cpatht-class.md)형식의 경로를 조작 하기 위한 npath 클래스를 제공 합니다. 이 코드는이 코드를 찾을 수 없습니다. h.

### <a name="related-classes"></a>관련 클래스

|||
|-|-|
|[CPathT 클래스](cpatht-class.md)|이 클래스는 경로를 나타냅니다.|

### <a name="related-typedefs"></a>관련 형식 정의

|||
|-|-|
|`CPath`|을 사용 하 `CString`는 [cpatht](cpatht-class.md) 의 특수화입니다.|
|`CPathA`|을 사용 하 `CStringA`는 [cpatht](cpatht-class.md) 의 특수화입니다.|
|`CPathW`|을 사용 하 `CStringW`는 [cpatht](cpatht-class.md) 의 특수화입니다.|

### <a name="functions"></a>함수

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|이 함수는 [Pathaddbackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::AddExtension](#addextension)|이 함수는 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::Append](#append)|이 함수는 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::BuildRoot](#buildroot)|이 함수는 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::Canonicalize](#canonicalize)|이 함수는 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::Combine](#combine)|이 함수는 [Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::CommonPrefix](#commonprefix)|이 함수는 [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::CompactPath](#compactpath)|이 함수는 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::CompactPathEx](#compactpathex)|이 함수는 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::FileExists](#fileexists)|이 함수는 [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::FindExtension](#findextension)|이 함수는 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::FindFileName](#findfilename)|이 함수는 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::GetDriveNumber](#getdrivenumber)|이 함수는 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsDirectory](#isdirectory)|이 함수는 [Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsFileSpec](#isfilespec)|이 함수는 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsPrefix](#isprefix)|이 함수는 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsRelative](#isrelative)|이 함수는 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsRoot](#isroot)|이 함수는 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsSameRoot](#issameroot)|이 함수는 [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsUNC](#isunc)|이 함수는 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsUNCServer](#isuncserver)|이 함수는 [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::IsUNCServerShare](#isuncservershare)|이 함수는 [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::MakePretty](#makepretty)|이 함수는 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)적합 한 오버 로드 된 래퍼입니다.|
|[ATLPath::MatchSpec](#matchspec)|이 함수는 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::QuoteSpaces](#quotespaces)|이 함수는 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RelativePathTo](#relativepathto)|이 함수는 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RemoveArgs](#removeargs)|이 함수는 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RemoveBackslash](#removebackslash)|이 함수는 [Pathremovebackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RemoveBlanks](#removeblanks)|이 함수는 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RemoveExtension](#removeextension)|이 함수는 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RemoveFileSpec](#removefilespec)|이 함수는 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::RenameExtension](#renameextension)|이 함수는 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::SkipRoot](#skiproot)|이 함수는 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::StripPath](#strippath)|이 함수는 [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::StripToRoot](#striptoroot)|이 함수는 [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)에 대해 오버 로드 된 래퍼입니다.|
|[ATLPath::UnquoteSpaces](#unquotespaces)|이 함수는 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)에 대해 오버 로드 된 래퍼입니다.|

## <a name="requirements"></a>요구 사항

**헤더:** 이 경로 .h

## <a name="addbackslash"></a> ATLPath::AddBackSlash

이 함수는 [Pathaddbackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathaddbackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw) 를 참조 하세요.

## <a name="addextension"></a> ATLPath::AddExtension

이 함수는 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) 을 참조 하세요.

## <a name="append"></a> ATLPath::Append

이 함수는 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) 를 참조 하세요.

## <a name="buildroot"></a> ATLPath::BuildRoot

이 함수는 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw) 를 참조 하세요.

## <a name="canonicalize"></a> ATLPath::Canonicalize

이 함수는 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) 를 참조 하십시오.

## <a name="combine"></a> ATLPath::Combine

이 함수는 [Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>설명

자세한 내용은 PathCombine을 참조 하십시오.

## <a name="commonprefix"></a> ATLPath::CommonPrefix

이 함수는 [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) 를 참조 하세요.

## <a name="compactpath"></a> ATLPath::CompactPath

이 함수는 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw) 를 참조 하세요.

## <a name="compactpathex"></a> ATLPath::CompactPathEx

이 함수는 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw) 를 참조 하세요.

## <a name="fileexists"></a> ATLPath::FileExists

이 함수는 [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) 를 참조 하세요.

## <a name="findextension"></a> ATLPath::FindExtension

이 함수는 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) 을 참조 하세요.

## <a name="findfilename"></a> ATLPath::FindFileName

이 함수는 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 을 참조 하십시오.

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

이 함수는 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw) 를 참조 하세요.

## <a name="isdirectory"></a>  ATLPath::IsDirectory

이 함수는 [Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)에 대해 오버 로드 된 래퍼입니다.

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 PathIsDirectory를 참조 하세요.

## <a name="isfilespec"></a> ATLPath::IsFileSpec

이 함수는 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) 을 참조 하세요.

## <a name="isprefix"></a> ATLPath::IsPrefix

이 함수는 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw) 를 참조 하세요.

## <a name="isrelative"></a> ATLPath::IsRelative

이 함수는 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) 을 참조 하세요.

## <a name="isroot"></a> ATLPath::IsRoot

이 함수는 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw) 를 참조 하세요.

## <a name="issameroot"></a> ATLPath::IsSameRoot

이 함수는 [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) 를 참조 하세요.

## <a name="isunc"></a> ATLPath::IsUNC

이 함수는 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw) 를 참조 하세요.

## <a name="isuncserver"></a> ATLPath::IsUNCServer

이 함수는 [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw) 를 참조 하세요.

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

이 함수는 [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew) 를 참조 하세요.

## <a name="makepretty"></a> ATLPath::MakePretty

이 함수는 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)적합 한 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) 을 참조 하세요.

## <a name="matchspec"></a> ATLPath::MatchSpec

이 함수는 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) 을 참조 하십시오.

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

이 함수는 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw) 를 참조 하세요.

## <a name="relativepathto"></a> ATLPath::RelativePathTo

이 함수는 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow) 를 참조 하세요.

## <a name="removeargs"></a> ATLPath::RemoveArgs

이 함수는 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) 를 참조 하세요.

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

이 함수는 [Pathremovebackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremovebackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw) 를 참조 하세요.

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

이 함수는 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw) 을 참조 하세요.

## <a name="removeextension"></a> ATLPath::RemoveExtension

이 함수는 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) 을 참조 하세요.

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

이 함수는 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) 을 참조 하세요.

## <a name="renameextension"></a> ATLPath::RenameExtension

이 함수는 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) 를 참조 하세요.

## <a name="skiproot"></a> ATLPath::SkipRoot

이 함수는 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw) 를 참조 하세요.

## <a name="strippath"></a> ATLPath::StripPath

이 함수는 [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) 를 참조 하세요.

## <a name="striptoroot"></a> ATLPath::StripToRoot

이 함수는 [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) 를 참조 하세요.

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

이 함수는 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)에 대해 오버 로드 된 래퍼입니다.

### <a name="syntax"></a>구문

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>설명

자세한 내용은 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw) 를 참조 하세요.
