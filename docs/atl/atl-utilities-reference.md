---
description: '자세한 정보: ATL 유틸리티 참조'
title: ATL 유틸리티 참조
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: 8545881c5cd48aaff1bb25448ba443829128dc41
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97148579"
---
# <a name="atl-utilities-reference"></a>ATL 유틸리티 참조

ATL은 [Cpatht](../atl/reference/cpatht-class.md) 및 [말아](../atl/reference/curl-class.md)형식으로 경로 및 url을 조작 하는 코드를 제공 합니다. 스레드 풀 [Cthreadpool](../atl/reference/cthreadpool-class.md)을 응용 프로그램에서 사용할 수 있습니다. 이 코드는 atlpath.h 및 atlutil.h에서 찾을 수 있습니다.

## <a name="classes"></a>클래스

| &nbsp; | &nbsp; |
|--|--|
| [CPathT 클래스](../atl/reference/cpatht-class.md) | 이 클래스는 경로를 나타냅니다. |
| [CDebugReportHook 클래스](../atl/reference/cdebugreporthook-class.md) | 이 클래스를 사용 하 여 디버그 보고서를 명명 된 파이프로 보낼 수 있습니다. |
| [CNonStatelessWorker 클래스](../atl/reference/cnonstatelessworker-class.md) | 스레드 풀에서 요청을 수신 하 고 각 요청에서 만들어지고 소멸 된 작업자 개체에 전달 합니다. |
| [CNoWorkerThread 클래스](../atl/reference/cnoworkerthread-class.md) | `MonitorClass`동적 캐시 유지 관리를 사용 하지 않도록 설정 하려는 경우 클래스를 캐시 하는 템플릿 매개 변수에 대 한 인수로이 클래스를 사용 합니다. |
| [CThreadPool 클래스](../atl/reference/cthreadpool-class.md) | 이 클래스는 작업 항목의 큐를 처리 하는 작업자 스레드 풀을 제공 합니다. |
| [CUrl 클래스](../atl/reference/curl-class.md) | 이 클래스는 URL을 나타냅니다. 이를 통해 기존 URL 문자열을 구문 분석 하거나 처음부터 문자열을 작성 하 든 관계 없이 URL의 각 요소를 개별적으로 조작할 수 있습니다. |
| [CWorkerThread 클래스](../atl/reference/cworkerthread-class.md) | 이 클래스는 작업자 스레드를 만들거나 기존 작업자 스레드를 사용 하 고, 하나 이상의 커널 개체 핸들을 대기 하 고, 핸들 중 하나가 신호를 받으면 지정 된 클라이언트 함수를 실행 합니다. |

## <a name="typedefs"></a>Typedefs

| &emsp; | &emsp; |
|--|--|
| [CPath](../atl/reference/atl-typedefs.md#cpath) | 을 사용 하는 [Cpatht](../atl/reference/cpatht-class.md) 의 특수화입니다 `CString` . |
| [CPathA](../atl/reference/atl-typedefs.md#cpatha) | 을 사용 하는 [Cpatht](../atl/reference/cpatht-class.md) 의 특수화입니다 `CStringA` . |
| [CPathW](../atl/reference/atl-typedefs.md#cpathw) | 을 사용 하는 [Cpatht](../atl/reference/cpatht-class.md) 의 특수화입니다 `CStringW` . |
| [ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port) | 포트 번호를 지정 하기 위해 [말아](../atl/reference/curl-class.md) 에서 사용 하는 형식입니다. |

## <a name="enums"></a>열거형

| &emsp; | &emsp; |
|--|--|
| [ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md) | 이 열거형의 멤버는 [말아](../atl/reference/curl-class.md)가 이해 하는 체계에 대 한 상수를 제공 합니다. |

## <a name="functions"></a>함수

| &emsp; | &emsp; |
|--|--|
| [AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl) | 안전하지 않은 문자와 공백을 이스케이프 시퀀스로 변환하는 등 URL을 정식화하려면 이 함수를 호출합니다. |
| [AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl) | 기본 URL과 상대 URL을 단일 정규 URL로 결합하려면 이 함수를 호출합니다. |
| [AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl) | 모든 안전하지 않은 문자를 이스케이프 시퀀스로 변환하려면 이 함수를 호출합니다. |
| [AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport) | 특정 인터넷 프로토콜 또는 체계와 연결 된 기본 포트 번호를 가져오려면이 함수를 호출 합니다. |
| [AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue) | 16진수의 숫자 값을 가져오려면 이 함수를 호출합니다. |
| [AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar) | URL에서 문자를 안전하게 사용할 수 있는지 확인하려면 이 함수를 호출합니다. |
| [AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl) | 이스케이프된 문자를 원래 값으로 다시 변환하려면 이 함수를 호출합니다. |
| [SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate) | 시스템 시간을 HTTP 헤더에서 사용하기에 적합한 형식의 문자열로 변환하려면 이 함수를 호출합니다. |
| [ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash) | 이 함수는 [PathAddBackslash] (/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha)에 대 한 오버 로드 된 래퍼입니다. |
| ). |
| [ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension) | 이 함수는 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::Append](../atl/reference/atl-path-functions.md#append) | 이 함수는 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot) | 이 함수는 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize) | 이 함수는 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::Combine](../atl/reference/atl-path-functions.md#combine) | 이 함수는 [Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix) | 이 함수는 [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath) | 이 함수는 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex) | 이 함수는 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists) | 이 함수는 [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension) | 이 함수는 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename) | 이 함수는 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber) | 이 함수는 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory) | 이 함수는 [Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec) | 이 함수는 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix) | 이 함수는 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative) | 이 함수는 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot) | 이 함수는 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot) | 이 함수는 [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc) | 이 함수는 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver) | 이 함수는 [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare) | 이 함수는 [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty) | 이 함수는 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)적합 한 오버 로드 된 래퍼입니다. |
| [ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec) | 이 함수는 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces) | 이 함수는 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto) | 이 함수는 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs) | 이 함수는 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash) | 이 함수는 [Pathremovebackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks) | 이 함수는 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension) | 이 함수는 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec) | 이 함수는 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension) | 이 함수는 [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot) | 이 함수는 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath) | 이 함수는 [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot) | 이 함수는 [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)에 대해 오버 로드 된 래퍼입니다. |
| [ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces) | 이 함수는 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)에 대해 오버 로드 된 래퍼입니다. |

## <a name="see-also"></a>참고 항목

[개념](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM 데스크톱 구성 요소](../atl/atl-com-desktop-components.md)
