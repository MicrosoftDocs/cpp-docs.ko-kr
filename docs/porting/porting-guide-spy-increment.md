---
description: '자세한 정보: 포팅 가이드: Spy + +'
title: '포팅 가이드: Spy++'
ms.date: 10/23/2019
ms.assetid: e558f759-3017-48a7-95a9-b5b779d5e51d
ms.openlocfilehash: 7c417a6f313ba6f77e0330bd9511b40c8e1285b2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97331266"
---
# <a name="porting-guide-spy"></a>포팅 가이드: Spy++

이 포팅 사례 연구는 일반적인 포팅 프로젝트, 발생할 수 있는 문제 유형 및 포팅 문제를 다루기 위한 몇 가지 일반적인 팁과 트릭에 대한 아이디어를 제공하도록 설계되었습니다. 프로젝트 포팅 경험은 코드의 세부 사항에 따라 달라지므로 결정적인 포팅 가이드는 아닙니다.

## <a name="spy"></a>Spy++

Spy++는 Windows 데스크톱의 사용자 인터페이스 요소에 대해 모든 종류의 정보를 제공하는 널리 사용되는 Windows 데스크톱용 GUI 진단 도구입니다. 창의 전체 계층 구조를 표시하고 각 창과 컨트롤에 대한 메타데이터에 액세스할 수 있게 합니다. 이 유용한 애플리케이션은 수년 동안 Visual Studio와 함께 제공되었습니다. Visual C++ 6.0에서 마지막으로 컴파일된 이전 버전이 Visual Studio 2015로 이식되었습니다. Visual Studio 2017 또는 Visual Studio 2019 환경은 거의 동일 해야 합니다.

이 사례가 특히 Visual C++ 6.0 이후 Visual C++의 각 릴리스로 업데이트되지 않은 오래된 프로젝트에 대해 MFC 및 Win32 API를 사용하는 Windows 데스크톱 애플리케이션을 포팅하는 일반적인 경우라고 간주했습니다.

## <a name="step-1-converting-the-project-file"></a><a name="convert_project_file"></a> 1단계. 프로젝트 파일 변환

프로젝트 파일인 Visual C++ 6.0의 이전 .dsw 파일 두 개는 추가로 주의가 필요한 문제없이 쉽게 변환되었습니다. 한 프로젝트는 Spy++ 애플리케이션입니다. 다른 프로젝트는 지원 DLL인 C로 작성된 SpyHk입니다. 보다 복잡한 프로젝트는 [여기](../porting/visual-cpp-porting-and-upgrading-guide.md)서 설명한 것처럼 쉽게 업그레이드되지 않을 수도 있습니다.

두 프로젝트를 업그레이드한 후 솔루션은 다음과 같았습니다.

![Spy&#43;&#43; 솔루션](../porting/media/spyxxsolution.PNG "Spy&#43;&#43; 솔루션")

하나는 많은 C++ 파일을 포함하고 다른 하나는 C로 작성된 DLL을 포함하는 두 개의 프로젝트가 있습니다.

## <a name="step-2-header-file-problems"></a><a name="header_file_problems"></a> 2단계. 헤더 파일 문제

새로 변환된 프로젝트를 빌드할 때 첫 번째로 발견하는 사항 중 하나는 대체로 프로젝트에서 사용하는 헤더 파일이 없다는 것입니다.

Spy++에서 찾을 수 없는 파일 중 하나는 verstamp.h였습니다. 인터넷 검색을 통해 이 파일이 오래된 데이터 기술인 DAO SDK에서 제공된 것을 확인했습니다. 해당 헤더 파일에서 사용된 기호를 찾아 파일이 정말 필요한지 또는 해당 기호가 다른 곳에서 정의되었는지 확인하고 싶었으므로 헤더 파일 선언을 주석으로 처리하고 다시 컴파일했습니다. 필요한 기호는 VER_FILEFLAGSMASK 하나뿐이었습니다.

```Output
1>C:\Program Files (x86)\Windows Kits\8.1\Include\shared\common.ver(212): error RC2104: undefined keyword or key name: VER_FILEFLAGSMASK
```

사용 가능한 포함 파일에서 기호를 찾는 가장 쉬운 방법은 **파일에서 찾기** (**Ctrl** + **Shift** + **F**)를 사용 하 고 **Visual C++ 포함 디렉터리** 를 지정 하는 것입니다. ntverp.h에서 해당 기호를 찾았습니다. verstamp.h 포함 파일을 ntverp.h로 바꾼 후 이 오류가 사라졌습니다.

## <a name="step-3-linker-outputfile-setting"></a><a name="linker_output_settings"></a> 3 단계. 링커 OutputFile 설정

이전 프로젝트는 업그레이드한 후 문제가 발생할 수 있는 위치에 파일이 배치된 경우가 있습니다. 이 경우 Visual Studio에서 프로젝트 폴더 중 하나가 아니라 여기에 배치된 일부 헤더 파일을 찾을 수 있도록 프로젝트 속성의 **포함** 경로에 `$(SolutionDir)`을 추가해야 합니다.

MSBuild는 **OutputFile** 속성이 **TargetPath** 및 **TargetName** 값과 일치 하지 불만 MSB8012를 발급 합니다.

```Output
warning MSB8012: TargetPath(...\spyxx\spyxxhk\.\..\Debug\SpyxxHk.dll) does not match the Linker's OutputFile property value (...\spyxx\Debug\SpyHk55.dll). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).warning MSB8012: TargetName(SpyxxHk) does not match the Linker's OutputFile property value (SpyHk55). This may cause your project to build incorrectly. To correct this, please make sure that $(OutDir), $(TargetName) and $(TargetExt) property values match the value specified in %(Link.OutputFile).
```

**Link.OutputFile** 은 빌드 출력(예: EXE, DLL)이며, 일반적으로 `$(TargetDir)$(TargetName)$(TargetExt)`에서 생성되고 경로, 파일 이름 및 확장명을 제공합니다. 이는 이전 Visual C++ 빌드 도구(vcbuild.exe)에서 새 빌드 도구(MSBuild.exe)로 프로젝트를 마이그레이션하는 경우의 일반적인 오류입니다. Visual Studio 2010에서 빌드 도구가 변경되었으므로 2010 이전 프로젝트를 2010 이상 버전으로 마이그레이션할 때마다 이 문제가 발생할 수 있습니다. 기본적인 문제는 다른 프로젝트 설정을 기반으로 하는 값을 결정 하는 것이 항상 가능한 것은 아니기 때문에 프로젝트 마이그레이션 마법사가 **OutputFile** 값을 업데이트 하지 않는다는 것입니다. 따라서 일반적으로 수동으로 설정해야 합니다. 자세한 내용은 Visual C++ 블로그에서 이 [게시물](https://devblogs.microsoft.com/cppblog/visual-studio-2010-c-project-upgrade-guide/)을 참조하세요.

이 경우 변환된 프로젝트의 **Link.OutputFile** 속성이 구성에 따라 Spy++ 프로젝트에 대한 .\Debug\Spyxx.exe 및 .\Release\Spyxx.exe로 설정되었습니다. **모든 구성** 에 대해 이러한 하드 코딩된 값을 `$(TargetDir)$(TargetName)$(TargetExt)`로 바꾸는 것이 가장 좋습니다. 작동 하지 않는 경우 해당 위치에서 사용자 지정 하거나 해당 값이 설정 된 **일반** 섹션의 속성을 변경할 수 있습니다 (속성은 **출력 디렉터리**, **대상 이름** 및 **대상 확장명**). 보려는 속성이 매크로를 사용하는 경우 드롭다운 목록에서 **편집** 을 선택하여 매크로 대체가 수행된 최종 문자열을 보여 주는 대화 상자를 표시할 수 있습니다. **매크로** 단추를 선택하여 사용 가능한 모든 매크로 및 현재 값을 볼 수 있습니다.

## <a name="step-4-updating-the-target-windows-version"></a><a name="updating_winver"></a> 4 단계. 대상 Windows 버전 업데이트

다음 오류는 WINVER 버전이 MFC에서 더 이상 지원되지 않음을 나타냅니다. Windows XP에 대한 WINVER은 0x0501입니다.

```Output
C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxv_w32.h(40): fatal error C1189: #error:  MFC does not support WINVER less than 0x0501.  Please change the definition of WINVER in your project properties or precompiled header.
```

Windows XP는 Microsoft에서 더 이상 지원되지 않으므로 Visual Studio에서 대상으로 지정할 수는 있지만 애플리케이션에서 지원을 단계적으로 중단하고 사용자가 새 버전의 Windows를 채택하도록 장려해야 합니다.

오류를 제거하려면 **프로젝트 속성** 설정을 현재 대상으로 지정하려는 가장 낮은 Windows 버전으로 업데이트하여 WINVER을 정의합니다. 다양한 Windows 릴리스에 대한 값 테이블은 [여기](/windows/win32/WinProg/using-the-windows-headers)서 확인할 수 있습니다.

*Stdafx.h* 파일에 이러한 매크로 정의 중 일부가 포함 되어 있습니다.

```cpp
#define WINVER       0x0500  // these defines are set so that we get the
#define _WIN32_WINNT 0x0500  // maximum set of message/flag definitions,
#define _WIN32_IE    0x0400  // from both winuser.h and commctrl.h.
```

WINVER을 Windows 7으로 설정하겠습니다. 값 자체가 아닌 (_WIN32_WINNT_WIN7) 매크로를 사용 하는 경우 나중에 코드를 더 쉽게 읽을 수 있습니다 (0x0601).

```cpp
#define WINVER _WINNT_WIN32_WIN7 // Minimum targeted Windows version is Windows 7
```

## <a name="step-5-linker-errors"></a><a name="linker_errors"></a> 5 단계. 링커 오류

이렇게 변경하면 SpyHk(DLL) 프로젝트가 빌드되지만 링커 오류가 발생합니다.

```Output
LINK : warning LNK4216: Exported entry point _DLLEntryPoint@12
```

DLL에 대한 진입점을 내보내면 안 됩니다. 진입점은 DLL을 메모리에 처음 로드할 때 로더에서 호출되는 용도로만 사용되므로 다른 호출자를 위한 내보내기 테이블에 포함되면 안 됩니다. 지시문이 연결 되어 있지 않은지 확인 하기만 하면 **`__declspec(dllexport)`** 됩니다. spyxxhk.c의 두 위치, 즉 `DLLEntryPoint`의 선언과 정의에서 제거해야 합니다. 이전에도 이 지시문을 사용하는 것은 타당하지 않았지만 이전 버전의 링커 및 컴파일러에서 문제로 플래그를 지정하지 않았습니다. 최신 버전의 링커에서는 경고를 제공합니다.

```cpp
// deleted __declspec(dllexport)
BOOL WINAPI DLLEntryPoint(HINSTANCE hinstDLL,DWORD fdwReason, LPVOID lpvReserved);
```

C DLL 프로젝트인 SpyHK.dll이 이제 오류 없이 빌드되고 연결됩니다.

## <a name="step-6-more-outdated-header-files"></a><a name="outdated_header_files"></a> 6 단계. 더 오래된 헤더 파일

이 시점에서 기본 실행 파일 프로젝트인 Spyxx에서 작업을 시작합니다.

몇 개의 다른 포함 파일(ctl3d.h 및 penwin.h)을 찾을 수 없습니다. 인터넷을 검색 하 여 헤더에 포함 된 항목을 식별 하는 것이 도움이 될 수 있지만 정보가 도움이 되지 않는 경우도 있습니다. ctl3d.h는 Exchange Development Kit의 일부이고 Windows 95에서 특정 스타일의 컨트롤에 대한 지원을 제공했으며, penwin.h는 사용되지 않는 API인 창 펜 컴퓨팅과 관련이 있는 것을 확인했습니다. 이 경우 `#include` 줄을 주석으로 처리하고, verstamp.h와 동일한 방식으로 정의되지 않은 기호를 처리합니다. 3D 컨트롤 또는 펜 컴퓨팅과 관련된 모든 항목이 프로젝트에서 제거되었습니다.

단계적으로 제거 중인 많은 컴파일 오류가 있는 프로젝트의 경우 `#include` 지시문을 제거할 때 바로 오래된 API의 모든 사용을 찾는 것은 비현실적입니다. 즉시 감지하지 못하고 나중에 WM_DLGBORDER이 정의되지 않았다는 오류가 발생했습니다. 이는 실제로 ctl3d.h에서 제공되는, 정의되지 않은 많은 기호 중 하나일 뿐입니다. 오래된 API와 관련이 있음을 확인한 후 코드에서 해당 참조를 모두 제거했습니다.

## <a name="step-7-updating-old-iostreams-code"></a><a name="updating_iostreams_code"></a> 7 단계. 이전 iostreams 코드 업데이트

다음 오류는 iostreams를 사용하는 이전 C++ 코드에서 일반적으로 발생합니다.

```Output
mstream.h(40): fatal error C1083: Cannot open include file: 'iostream.h': No such file or directory
```

문제는 이전 iostreams 라이브러리가 제거 및 대체된 것입니다. 이전 iostreams를 최신 표준으로 바꾸어야 합니다.

```cpp
#include <iostream.h>
#include <strstrea.h>
#include <iomanip.h>
```

다음은 업데이트된 포함 파일입니다.

```cpp
#include <iostream>
#include <sstream>
#include <iomanip>
```

이렇게 변경하면 더 이상 사용되는 `ostrstream`에서 문제가 발생합니다. 적절한 대체 항목은 ostringstream입니다. **`typedef`** `ostrstream` 최소한 시작 부분에서 코드를 너무 많이 수정 하지 않도록에 대 한를 추가 해 봅니다.

```cpp
typedef std::basic_ostringstream<TCHAR> ostrstream;
```

현재 프로젝트는 MBCS (멀티 바이트 문자 집합)를 사용 하 여 빌드되기 때문에 **`char`** 적절 한 문자 데이터 형식입니다. 그러나 코드를 UTF-16 유니코드로 업데이트 하기 위해 `TCHAR` **`char`** **`wchar_t`** 프로젝트 설정의 **문자 집합** 속성이 MBCS 또는 유니코드로 설정 되었는지에 따라 또는로 확인 되는로 업데이트 합니다.

다른 몇 가지 코드 부분도 업데이트해야 합니다.  기본 클래스는로 대체 `ios` `ios_base` 되었으며 ostream은 basic_ostream를 사용 하 여 바뀌었습니다 \<T> . 두 개의 추가 typedef를 추가하면 이 섹션이 컴파일됩니다.

```cpp
typedef std::basic_ostream<TCHAR> ostream;
typedef ios_base ios;
```

이러한 typedef를 사용하는 것은 임시 솔루션일 뿐입니다. 더 영구적인 솔루션을 위해 이름이 바뀌었거나 오래된 API에 대한 각 참조를 업데이트할 수 있습니다.

다음 오류는 다음과 같습니다.

```Output
error C2039: 'freeze': is not a member of 'std::basic_stringbuf<char,std::char_traits<char>,std::allocator<char>>'
```

다음 문제는에 `basic_stringbuf` 메서드가 없는 것입니다 `freeze` . `freeze` 메서드는 이전 `ostream`에서 메모리 누수를 방지하는 데 사용됩니다. 이제 새를 사용 하 고 있기 때문에 필요 하지 않습니다 `ostringstream` . `freeze`에 대한 호출을 삭제할 수 있습니다.

```cpp
//rdbuf()->freeze(0);
```

인접한 줄에서 다음 두 오류가 발생했습니다. 첫 번째 불만는 `ends` `iostream` 문자열에 null 종결자를 추가 하는 이전 라이브러리의 IO 조작자 인을 사용 하는 것입니다. 이러한 오류 중 두 번째는 메서드의 출력을 `str` 비 const 포인터에 할당할 수 없음을 설명 합니다.

```cpp
// Null terminate the string in the buffer and
// get a pointer to it.
//
*this << ends;
LPSTR psz = str();
```

```Output
2>mstream.cpp(167): error C2065: 'ends': undeclared identifier2>mstream.cpp(168): error C2440: 'initializing': cannot convert from 'std::basic_string<char,std::char_traits<char>,std::allocator<char>>' to 'LPSTR'
```

새 스트림 라이브러리를 사용할 경우 문자열이 항상 null로 종료되기 때문에 `ends`가 필요하지 않으므로 해당 줄을 제거할 수 있습니다. 두 번째 문제에 대 한 문제는 이제 `str()` 문자열의 문자 배열에 대 한 포인터를 반환 하지 않고 형식을 반환 한다는 것입니다 `std::string` . 두 번째 문제에 대한 솔루션은 형식을 `LPCSTR`로 변경하고 `c_str()` 메서드를 사용하여 포인터를 요청하는 것입니다.

```cpp
//*this << ends;
LPCTSTR psz = str().c_str();
```

오랫동안 해결되지 않은 오류가 이 코드에서 발생했습니다.

```cpp
MOUT << _T(" chUser:'") << chUser
<< _T("' (") << (INT)(UCHAR)chUser << _T(')');
```

MOUT 매크로는 `mstream` 형식의 개체인 `*g_pmout`로 확인됩니다. `mstream` 클래스는 표준 출력 문자열 클래스 `std::basic_ostream<TCHAR>`에서 파생됩니다. 그러나 유니코드로 변환하기 위해 삽입한 문자열 리터럴 앞뒤의 \_T로 인해 **operator <<** 에 대한 오버로드 확인이 실패하고 다음 오류 메시지가 표시됩니다.

```Output
1>winmsgs.cpp(4612): error C2666: 'mstream::operator <<': 2 overloads have similar conversions
1>  c:\source\spyxx\spyxx\mstream.h(120): note: could be 'mstream &mstream::operator <<(ios &(__cdecl *)(ios &))'
1>  c:\source\spyxx\spyxx\mstream.h(118): note: or       'mstream &mstream::operator <<(ostream &(__cdecl *)(ostream &))'
1>  c:\source\spyxx\spyxx\mstream.h(116): note: or       'mstream &mstream::operator <<(ostrstream &(__cdecl *)(ostrstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(114): note: or       'mstream &mstream::operator <<(mstream &(__cdecl *)(mstream &))'
1>  c:\source\spyxx\spyxx\mstream.h(109): note: or       'mstream &mstream::operator <<(LPTSTR)'
1>  c:\source\spyxx\spyxx\mstream.h(104): note: or       'mstream &mstream::operator <<(TCHAR)'
1>  c:\source\spyxx\spyxx\mstream.h(102): note: or       'mstream &mstream::operator <<(DWORD)'
1>  c:\source\spyxx\spyxx\mstream.h(101): note: or       'mstream &mstream::operator <<(WORD)'
1>  c:\source\spyxx\spyxx\mstream.h(100): note: or       'mstream &mstream::operator <<(BYTE)'
1>  c:\source\spyxx\spyxx\mstream.h(95): note: or       'mstream &mstream::operator <<(long)'
1>  c:\source\spyxx\spyxx\mstream.h(90): note: or       'mstream &mstream::operator <<(unsigned int)'
1>  c:\source\spyxx\spyxx\mstream.h(85): note: or       'mstream &mstream::operator <<(int)'
1>  c:\source\spyxx\spyxx\mstream.h(83): note: or       'mstream &mstream::operator <<(HWND)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1132): note: or       'CDumpContext &operator <<(CDumpContext &,COleSafeArray &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1044): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1042): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1037): note: or       'CArchive &operator <<(CArchive &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1035): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::COleDateTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1030): note: or       'CArchive &operator <<(CArchive &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(1028): note: or       'CDumpContext &operator <<(CDumpContext &,COleCurrency)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(955): note: or       'CArchive &operator <<(CArchive &,ATL::CComBSTR)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(951): note: or       'CArchive &operator <<(CArchive &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxdisp.h(949): note: or       'CDumpContext &operator <<(CDumpContext &,COleVariant)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(248): note: or       'CArchive &operator <<(CArchive &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(247): note: or       'CArchive &operator <<(CArchive &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(246): note: or       'CArchive &operator <<(CArchive &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(242): note: or       'CDumpContext &operator <<(CDumpContext &,const RECT &)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(241): note: or       'CDumpContext &operator <<(CDumpContext &,POINT)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afxwin.h(240): note: or       'CDumpContext &operator <<(CDumpContext &,SIZE)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1639): note: or       'CArchive &operator <<(CArchive &,const CObject *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1425): note: or       'CArchive &operator <<(CArchive &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1423): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTime)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1418): note: or       'CArchive &operator <<(CArchive &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\atlmfc\include\afx.h(1416): note: or       'CDumpContext &operator <<(CDumpContext &,ATL::CTimeSpan)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(694): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const char *)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(741): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,char)'
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(866): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const _Elem *)'
1>          with
1>          [
1>              _Elem=wchar_t
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(983): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>,wchar_t[10]>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &&,const _Ty (&))'
1>          with
1>          [
1>              _Ty=wchar_t [10]
1>          ]
1>  C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\include\ostream(1021): note: or       'std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &std::operator <<<wchar_t,std::char_traits<wchar_t>>(std::basic_ostream<wchar_t,std::char_traits<wchar_t>> &,const std::error_code &)'
1>  winmsgs.cpp(4612): note: while trying to match the argument list '(CMsgStream, const wchar_t [10])'
```

**operator <<** 정의가 너무 많아서 이러한 종류의 오류는 위협적일 수 있습니다. 사용 가능한 오버로드를 자세히 살펴보면 대부분 관련이 없는 것을 확인할 수 있으며, `mstream` 클래스 정의를 자세히 살펴본 후 이 경우에 호출되어야 한다고 생각하는 다음 함수를 식별했습니다.

```cpp
mstream& operator<<(LPTSTR psz)
{
  return (mstream&)ostrstream::operator<<(psz);
}
```

이 함수가 호출되지 않은 것은 긴 오류 메시지의 마지막 줄에서 볼 수 있듯이 문자열 리터럴이 `const wchar_t[10]` 형식이어서 const 이외의 포인터로 자동 변환되지 않았기 때문입니다. 그러나 해당 연산자는 입력 매개 변수를 수정하면 안 되므로 더 적절한 매개 변수 형식은 `LPCTSTR`(MBCS로 컴파일하는 경우 `const char*` 및 유니코드로 컴파일하는 경우 `const wchar_t*`)이 아니라 `LPTSTR`(MBCS로 컴파일하는 경우 `char*` 및 유니코드로 컴파일하는 경우 `wchar_t*`)입니다. 이렇게 변경하면 이 오류가 수정됩니다.

이러한 형식의 변환은 덜 엄격한 이전 컴파일러에서 허용되었지만 최근의 규칙 변경에 따라 보다 올바른 코드가 필요합니다.

## <a name="step-8-the-compilers-more-strict-conversions"></a><a name="stricter_conversions"></a> 8 단계. 컴파일러의 보다 엄격한 변환

다음과 같은 많은 오류도 발생합니다.

```Output
error C2440: 'static_cast': cannot convert from 'UINT (__thiscall CHotLinkCtrl::* )(CPoint)' to 'LRESULT (__thiscall CWnd::* )(CPoint)'
```

단순히 매크로인 메시지 맵에서 오류가 발생합니다.

```cpp
BEGIN_MESSAGE_MAP(CFindToolIcon, CWnd)
// other messages omitted...
ON_WM_NCHITTEST() // Error occurs on this line.
END_MESSAGE_MAP()
```

이 매크로의 정의로 이동하면 `OnNcHitTest` 함수를 참조하는 것을 확인할 수 있습니다.

```cpp
#define ON_WM_NCHITTEST() \
{ WM_NCHITTEST, 0, 0, 0, AfxSig_l_p, \
(AFX_PMSG)(AFX_PMSGW) \
(static_cast< LRESULT (AFX_MSG_CALL CWnd::*)(CPoint) > (&ThisClass :: OnNcHitTest)) },
```

문제는 멤버 함수 형식에 대한 포인터의 불일치와 관련이 있습니다. 이 문제는 클래스 형식으로에서로 변환 하는 것 `CHotLinkCtrl` `CWnd` 이 아닙니다 .이는 유효한 파생 된 기본 변환 이기 때문입니다. 문제는 반환 형식 UINT 및 LRESULT입니다. LRESULT는 대상 이진 형식에 따라 64비트 포인터 또는 32비트 포인터인 LONG_PTR로 확인되므로 UINT는 이 형식으로 변환되지 않습니다. 이 문제는 Visual Studio 2005에서 64비트 호환성 변경의 일부로 많은 메시지 맵 메서드의 반환 형식이 UINT에서 LRESULT로 변경되었기 때문에 2005 이전에 작성된 코드를 업그레이드하는 경우에 자주 발생합니다. 다음 코드에서 반환 형식을 UINT에서 LRESULT로 변경합니다.

```cpp
afx_msg UINT OnNcHitTest(CPoint point);
```

변경한 후의 코드는 다음과 같습니다.

```cpp
afx_msg LRESULT OnNcHitTest(CPoint point);
```

CWnd에서 파생 된 서로 다른 클래스에이 함수가 모두 10 회 발생 하므로 **정의로 이동** (키보드: **f12**) 및 **선언으로** 이동 (키보드: **Ctrl** + **F12**)을 사용 하 여 편집기의 함수에 커서를 놓고 **기호 찾기** 도구 창에서 이동 하는 것이 좋습니다. 일반적으로 **정의로 이동** 이 둘 중에서 더 유용합니다. **선언으로 이동** 은 friend 클래스 선언이나 정방향 참조와 같은 정의하는 클래스 선언 이외의 선언을 찾습니다.

## <a name="step-9-mfc-changes"></a><a name="mfc_changes"></a> 9 단계. MFC 변경

그다음 오류도 변경된 선언 형식과 관련이 있으며 매크로에서도 발생합니다.

```Output
error C2440: 'static_cast': cannot convert from 'void (__thiscall CFindWindowDlg::* )(BOOL,HTASK)' to 'void (__thiscall CWnd::* )(BOOL,DWORD)'
```

문제는 `CWnd::OnActivateApp`의 두 번째 매개 변수가 HTASK에서 DWORD로 변경된 것입니다. 이 변경은 Visual Studio 2002 릴리스, Visual Studio .NET에서 발생했습니다.

```cpp
afx_msg void OnActivateApp(BOOL bActive, HTASK hTask);
```

파생 클래스에서 OnActivateApp의 선언을 다음과 같이 적절하게 업데이트해야 합니다.

```cpp
afx_msg void OnActivateApp(BOOL bActive, DWORD dwThreadId);
```

이 시점에서 프로젝트를 컴파일할 수 있습니다. 그러나 작업할 몇 가지 경고가 있으며, MBCS에서 유니코드로 변환 또는 보안 CRT 함수를 사용한 보안 향상 등 업그레이드의 선택적 부분이 있습니다.

## <a name="step-10-addressing-compiler-warnings"></a><a name="compiler_warnings"></a> 10 단계. 컴파일러 경고 처리

경고의 전체 목록을 가져오려면 현재 컴파일의 경고 보고서만 가져오기 때문에 일반 빌드 대신 솔루션에 대해 **모두 다시 빌드** 를 수행하여 이전에 컴파일된 모든 항목이 다시 컴파일되도록 해야 합니다. 다른 질문은 현재 경고 수준을 수락할지 또는 더 높은 경고 수준을 사용할지 여부입니다.  많은 코드, 특히 이전 코드를 포팅하는 경우 더 높은 경고 수준을 사용하는 것이 적합할 수 있습니다.  기본 경고 수준으로 시작한 후 경고 수준을 높여 모든 경고를 가져올 수도 있습니다. `/Wall`을 사용하는 경우 시스템 헤더 파일의 일부 경고를 가져오므로 대체로 `/W4`를 사용하여 시스템 헤더에 대한 경고를 가져오지 않고 코드에 대한 경고를 최대한 가져옵니다. 경고를 오류로 표시하려는 경우 `/WX` 옵션을 추가합니다. 이러한 설정은 **프로젝트 속성** 대화 상자의 **c/c + +** 섹션에 있습니다.

`CSpyApp` 클래스의 메서드 중 하나는 더 이상 지원되지 않는 함수에 대한 경고를 생성합니다.

```cpp
void SetDialogBkColor() {CWinApp::SetDialogBkColor(::GetSysColor(COLOR_BTNFACE));}
```

경고는 다음과 같습니다.

```Output
warning C4996: 'CWinApp::SetDialogBkColor': CWinApp::SetDialogBkColor is no longer supported. Instead, handle WM_CTLCOLORDLG in your dialog
```

WM_CTLCOLORDLG 메시지는 Spy++ 코드에서 이미 처리되었으므로 더 이상 필요하지 않은 `SetDialogBkColor`에 대한 참조만 삭제하면 변경은 완료됩니다.

그다음 경고는 변수 이름을 주석으로 처리하여 수정했습니다. 다음 경고가 표시되었습니다.

```Output
warning C4456: declaration of 'lpszBuffer' hides previous local declaration
```

이 경고를 생성하는 코드는 매크로를 포함합니다.

```cpp
DECODEPARM(CB_GETLBTEXT)
{
  P2WPOUT();

  P2LPOUTPTRSTR;
  P2IFDATA()
  {
    PARM(lpszBuffer, PPACK_STRINGORD, ED2);

    INDENT();

    P2IFISORD(lpszBuffer)
    {
      P2OUTORD(lpszBuffer);
    }
    else
    {
      PARM(lpszBuffer, LPTSTR, ED2);
      P2OUTS(lpszBuffer);
    }
  }
}
```

이 코드와 같이 매크로를 많이 사용하면 코드를 유지 관리하기 어려워집니다. 이 경우 매크로가 변수 선언을 포함합니다. PARM 매크로는 다음과 같이 정의됩니다.

```cpp
#define PARM(var, type, src)type var = (type)src
```

따라서 `lpszBuffer` 변수가 동일한 함수에서 두 번 선언됩니다. 이 문제는 코드에서 매크로를 사용하지 않는 경우와 같이(간단하게 두 번째 형식 선언 제거) 간단하게 수정할 수 없습니다. 매크로 코드를 일반 코드로 다시 작성할지(시간이 걸리고 오류가 발생할 가능성이 있는 작업), 또는 경고를 사용하지 않도록 설정할지 결정해야 합니다.

이 경우 경고를 사용하지 않도록 설정합니다. 다음과 같이 pragma를 추가하면 됩니다.

```cpp
#pragma warning(disable : 4456)
```

경고를 사용하지 않도록 설정할 때 유용한 정보를 제공할 수 있는 경고가 표시되도록 경고를 생성하는 코드에만 설정이 적용되도록 제한하는 것이 좋습니다. 경고를 생성하는 줄 바로 뒤에 경고를 복원하는 코드를 추가하거나, 이 경고가 매크로에서 발생하므로 매크로에서 작동하는 **__pragma** 키워드를 사용합니다(`#pragma`는 매크로에서 작동하지 않음).

```cpp
#define PARM(var, type, src)__pragma(warning(disable : 4456))  \
type var = (type)src \
__pragma(warning(default : 4456))
```

그다음 경고는 일부 코드 수정이 필요합니다. Win32 API `GetVersion`(및 `GetVersionEx`)은 사용되지 않습니다.

```Output
warning C4996: 'GetVersion': was declared deprecated
```

다음 코드에서는 버전을 가져오는 방법을 보여 줍니다.

```cpp
// check Windows version and set m_bIsWindows9x/m_bIsWindows4x/m_bIsWindows5x flags accordingly.
DWORD dwWindowsVersion = GetVersion();
```

이 코드 뒤에는 dwWindowsVersion 값을 검사하여 Windows 95에서 실행 중인지 여부 및 Windows NT 버전을 확인하는 많은 코드가 있습니다. 모두 오래된 코드이므로 코드를 제거하고 해당 변수에 대한 참조를 모두 처리합니다.

[Operating system version changes in Windows 8.1 and Windows Server 2012 R2](/windows/win32/w8cookbook/operating-system-version-changes-in-windows-8-1)(Windows 8.1 및 Windows Server 2012 R2의 운영 체제 버전 변경 내용) 문서에서 이 상황을 설명합니다.

`IsWindows9x`, `IsWindows4x` 및 `IsWindows5x` 운영 체제 버전을 쿼리하는 `CSpyApp` 클래스에 메서드가 있습니다. 이 오래된 애플리케이션에서 사용하는 기술과 관련해서 지원하려는 Windows 버전(Windows 7 이상)이 모두 Windows NT 5에 가깝다는 가정에서 시작하는 것이 좋습니다. 이러한 메서드는 이전 운영 체제의 제한 사항을 처리하는 데 사용됩니다. 따라서 `IsWindows5x`에 대해 TRUE를 반환하고 다른 값에 대해 FALSE를 반환하도록 해당 메서드를 변경했습니다.

```cpp
BOOL IsWindows9x() {/*return(m_bIsWindows9x);*/ return FALSE;  }
BOOL IsWindows4x() {/*return(m_bIsWindows4x);*/ return FALSE;  }
BOOL IsWindows5x() {/*return(m_bIsWindows5x);*/ return TRUE;  }
```

이렇게 하면 내부 변수가 직접 사용된 위치가 몇 개밖에 남지 않습니다. 해당 변수를 제거했으므로 명시적으로 처리해야 하는 몇 개의 오류가 발생합니다.

```Output
error C2065: 'm_bIsWindows9x': undeclared identifier
```

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(m_bIsWindows9x || hToolhelp32 != NULL);
}
```

메서드 호출로 바꾸거나, TRUE를 전달하고 Windows 9x에 대한 이전 특수 사례를 제거할 수 있습니다.

```cpp
void CSpyApp::OnUpdateSpyProcesses(CCmdUI *pCmdUI)
{
  pCmdUI->Enable(TRUE /*!m_bIsWindows9x || hToolhelp32 != NULL*/);
}
```

기본 수준(3)에서 최종 경고는 비트 필드와 관련이 있습니다.

```Output
treectl.cpp(1656): warning C4463: overflow; assigning 1 to bit-field that can only hold values from -1 to 0
```

이 경고를 트리거하는 코드는 다음과 같습니다.

```cpp
m_bStdMouse = TRUE;
```

`m_bStdMouse` 선언은 비트 필드임을 나타냅니다.

```cpp
class CTreeListBox : public CListBox
{
  DECLARE_DYNCREATE(CTreeListBox)

  CTreeListBox();

  private:
  int ItemFromPoint(const CPoint& point);

  class CTreeCtl* m_pTree;
  BOOL m_bGotMouseDown : 1;
  BOOL m_bDeferedDeselection : 1;
  BOOL m_bStdMouse : 1;
```

이 코드는 기본 제공 bool 형식이 Visual C++에서 지원되기 전에 작성되었습니다. 이러한 코드에서 BOOL은 **`typedef`** 에 대 한입니다 **`int`** . 형식은 **`int`** **`signed`** 형식이 고,의 비트 표현은 **`signed int`** 첫 번째 비트를 부호 비트로 사용 하는 것 이므로 int 형식의 비트 필드는 의도 한 것이 아닌 0 또는-1을 나타내는 것으로 해석 될 수 있습니다.

코드에서는 비트 필드인 이유를 알 수 없습니다. 의도가 개체 크기를 작게 유지하는 것인가요, 또는 개체의 이진 레이아웃이 사용되는 곳이 있나요? 비트 필드의 사용 이유를 찾지 못했기 때문에 일반 BOOL 멤버로 변경했습니다. 비트 필드를 사용하여 개체 크기를 작게 유지하는 것은 효과가 보장되지 않습니다. 컴파일러가 형식을 레이아웃하는 방식에 따라 달라집니다.

전체에서 표준 형식을 사용 하는 **`bool`** 것이 도움이 될 수 있습니다. BOOL 형식과 같은 이전 코드 패턴은 대부분 표준 c + +에서 해결 된 문제를 해결 하기 위해 고안 되었으므로 BOOL에서 기본 제공 형식으로 변경 하는 것 **`bool`** 은 새 버전에서 코드를 처음 실행 한 후에 수행 해야 하는 변경의 한 가지 예입니다.

기본 수준(수준 3)에서 표시되는 모든 경고를 처리한 후 몇 가지 추가 경고를 catch하기 위해 수준 4로 변경했습니다. 처음 표시되는 경고는 다음과 같습니다.

```Output
warning C4100: 'nTab': unreferenced formal parameter
```

이 경고를 생성하는 코드는 다음과 같습니다.

```cpp
virtual void OnSelectTab(int nTab) {};
```

무해한 것처럼 보이지만 `/W4` 및 `/WX` 집합에서 오류 없는 컴파일을 원했기 때문에 변수 이름을 주석으로 처리하고 읽기 쉽도록 그대로 두었습니다.

```cpp
virtual void OnSelectTab(int /*nTab*/) {};
```

표시된 다른 경고는 일반적인 코드 정리에 유용했습니다. **`int`** 또는에서 **`unsigned int`** WORD (의 typedef)로의 암시적 변환이 많습니다 **`unsigned short`** . 이러한 변환으로 인해 데이터가 손실될 수 있습니다. 이 경우에 WORD로 캐스트를 추가했습니다.

이 코드에 대해 표시된 다른 수준 4 경고는 다음과 같습니다.

```Output
warning C4211: nonstandard extension used: redefined extern to static
```

이 문제는 변수가 처음으로 선언 된 **`extern`** 후 나중에 선언 될 때 발생 합니다 **`static`** . 이러한 두 스토리지 클래스 지정자의 의미는 양립할 수 없지만 Microsoft 확장으로 허용됩니다. 코드를 다른 컴파일러로 이식 가능하게 하거나 `/Za`(ANSI 호환성)를 사용하여 컴파일하려는 경우 일치하는 스토리지 클래스 지정자를 포함하도록 선언을 변경합니다.

## <a name="step-11-porting-from-mbcs-to-unicode"></a><a name="porting_to_unicode"></a> 11 단계. MBCS에서 유니코드로 포팅

Windows 환경에서 유니코드를 말할 때는 일반적으로 UTF-16을 의미합니다. Linux와 같은 다른 운영 체제는 UTF-8을 사용하지만 Windows는 일반적으로 사용하지 않습니다. MBCS 버전의 MFC는 Visual Studio 2013 및 2015에서 사용되지 않았지만, Visual Studio 2017에서는 더 이상 사용되지 않습니다. Visual Studio 2013 또는 2015를 사용하는 경우, 실제로 MBCS 코드를 UTF-16 유니코드로 포팅하는 단계를 수행하기 전에, 다른 작업을 수행하거나 편리한 시간까지 포팅을 연기하기 위해 MBCS가 사용되지 않는다는 경고를 일시적으로 제거하는 것이 좋습니다. 현재 코드는 MBCS를 사용하며, 계속 MBCS를 사용하려면 ANSI/MBCS 버전의 MFC를 설치해야 합니다. 비교적 큰 MFC 라이브러리는 **C++ 설치를 사용하는 기본 Visual Studio 데스크톱 개발** 에 포함되지 않으므로 설치 관리자의 선택적 구성 요소에서 선택해야 합니다. [MFC MBCS DLL 추가 기능](../mfc/mfc-mbcs-dll-add-on.md)을 참조하세요. 이를 다운로드 하 고 Visual Studio를 다시 시작한 후에는 MBCS 버전의 MFC를 컴파일 및 연결 하 고, Visual Studio 2013 또는 2015를 사용 하는 경우 MBCS에 대 한 경고를 제거할 수 있습니다. 또한 프로젝트 속성의 **전처리기** 섹션에서 또는 *stdafx.h* 헤더 파일이 나 기타 공용 헤더 파일의 시작 부분에서 미리 정의 된 매크로 목록에 NO_WARN_MBCS_MFC_DEPRECATION를 추가 해야 합니다.

이제 일부 링커 오류가 있습니다.

```Output
fatal error LNK1181: cannot open input file 'mfc42d.lib'
```

mfc의 오래된 정적 라이브러리 버전이 링커 입력에 포함되어 있으므로 LNK1181이 발생합니다. 이는 MFC를 동적으로 연결할 수 있기 때문에 더 이상 필요 하지 않으므로 프로젝트 속성의 **링커** 섹션에 있는 **입력** 속성에서 mfc 정적 라이브러리를 모두 제거 하면 됩니다. 또한 이 프로젝트는 `/NODEFAULTLIB` 옵션을 사용하며, 대신 모든 라이브러리 종속성을 나열합니다.

```
msvcrtd.lib;msvcirtd.lib;kernel32.lib;user32.lib;gdi32.lib;advapi32.lib;Debug\SpyHk55.lib;%(AdditionalDependencies)
```

이제 실제로 이전 MBCS(멀티바이트 문자 집합) 코드를 유니코드로 업데이트하겠습니다. Windows 데스크톱 플랫폼에 깊이 연결된 Windows 애플리케이션이므로 Windows에서 사용하는 UTF-16 유니코드로 포팅하겠습니다. 플랫폼 간 코드를 작성하거나 Windows 애플리케이션을 다른 플랫폼으로 포팅하는 경우 다른 운영 체제에서 널리 사용되는 UTF-8로 포팅하는 것이 좋습니다.

UTF-16 유니코드로 포팅하는 경우 MBCS로 컴파일하는 옵션을 원하는지 여부를 결정해야 합니다.  MBCS를 지 원하는 옵션을 사용 하려면 TCHAR.H 매크로를 문자 형식으로 사용 해야 합니다 .이 문자 형식은 **`char`** **`wchar_t`** \_ mbcs 또는 \_ UNICODE가 컴파일 중에 정의 되었는지 여부에 따라 또는로 확인 됩니다. 및 관련 된 Api 대신 TCHAR.H와 다양 한 Api의 TCHAR.H로 전환 하면 **`wchar_t`** \_ 유니코드 대신 mbcs 매크로를 정의 하 여 코드의 mbcs 버전으로 돌아갈 수 있습니다 \_ . TCHAR 외에도 널리 사용되는 typedef, 매크로 및 함수의 다양한 TCHAR 버전이 있습니다. 예를 들어 LPCSTR 대신 LPCTSTR을 사용합니다. 프로젝트 속성 대화 상자의 **구성 속성** 아래, **일반** 섹션에서 **문자 집합** 속성을 **MBCS 문자 집합 사용** 에서 **유니코드 문자 집합 사용** 으로 변경합니다. 이 설정은 컴파일하는 동안 미리 정의되는 매크로에 영향을 줍니다. UNICODE 매크로와 \_UNICODE 매크로가 둘 다 있습니다. 프로젝트 속성은 두 매크로에 일관되게 적용됩니다. Windows 헤더는 unicode를 사용하고 MFC와 같은 Visual C++ 헤더는 \_UNICODE를 사용하지만 하나가 정의될 때 다른 하나도 항상 정의됩니다.

TCHAR를 사용하여 MBCS에서 UTF-16 유니코드로 포팅하는 방법에 대한 유용한 [가이드](/previous-versions/cc194801(v=msdn.10))가 있습니다. 이 경로를 선택합니다. 먼저, **문자 집합** 속성을 **유니코드 문자 집합 사용** 으로 변경하고 프로젝트를 다시 빌드합니다.

코드에는 궁극적으로 유니코드를 지원하기 위해 이미 TCHAR를 사용 중인 부분도 있고 그렇지 않은 부분도 있습니다. 의 인 CHAR 인스턴스를 검색 하 여 대부분을 **`typedef`** **`char`** tchar.h로 바꿉니다. 또한 `sizeof(CHAR)`를 찾았습니다. CHAR에서 TCHAR로 변경할 때마다 일반적으로 문자열의 문자 수를 확인하는 데 주로 사용되는 `sizeof(TCHAR)`로 변경해야 했습니다. 여기서 잘못된 형식을 사용해도 컴파일러 오류가 생성되지 않으므로 이 경우에 약간 주의할 가치가 있습니다.

이 형식의 오류는 유니코드로 전환한 직후에 일반적으로 발생합니다.

```Output
error C2664: 'int wsprintfW(LPWSTR,LPCWSTR,...)': cannot convert argument 1 from 'CHAR [16]' to 'LPWSTR'
```

이를 생성 하는 코드의 예는 다음과 같습니다.

```cpp
wsprintf(szTmp, "%d.%2.2d.%4.4d", rmj, rmm, rup);
```

오류를 제거하기 위해 문자열 앞뒤에 \_T를 넣습니다.

```cpp
wsprintf(szTmp, _T("%d.%2.2d.%4.4d"), rmj, rmm, rup);
```

\_T 매크로는 **`char`** **`wchar_t`** MBCS 또는 UNICODE 설정에 따라 문자열 리터럴을 문자열 또는 문자열로 만드는 효과를 가집니다. Visual Studio에서 모든 문자열을 T로 바꾸려면 \_ 먼저 **빠른 바꾸기** (키보드: **ctrl** + **F**) 상자 또는 **파일에서 바꾸기** (키보드: **ctrl** + **Shift** + **H**)를 열고 **정규식 사용** 확인란을 선택 합니다. `((\".*?\")|('.+?'))`를 검색 텍스트로 입력하고 `_T($1)`를 바꿀 텍스트로 입력합니다. \_일부 문자열 주위에 t 매크로가 이미 있는 경우이 절차에서 다시 추가 하 고를 사용 하는 \_ 경우와 같이 t를 사용 하지 않는 경우를 사용 하는 경우를 사용 하는 것이 `#include` 좋습니다. 따라서 **모두 바꾸기** 대신 **다음 바꾸기** 를 사용 하는 것이 좋습니다.

이 특정 함수 [wsprintf](/windows/win32/api/winuser/nf-winuser-wsprintfw)는 실제로 Windows 헤더에서 정의되며, 해당 설명서에서 가능한 버퍼 오버런으로 인해 사용하지 않도록 권장합니다. `szTmp` 버퍼에 대한 크기가 지정되지 않으므로 함수에서 버퍼가 기록되는 모든 데이터를 포함할 수 있는지 확인할 방법이 없습니다. 보안 CRT로 포팅하는 방법에 대한 다음 섹션을 참조하세요. 여기서는 다른 유사한 문제를 해결합니다. 결국 [_stprintf_s](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)로 바꾸었습니다.

유니코드로 변환할 때 표시 되는 또 다른 일반적인 오류는 다음과 같습니다.

```Output
error C2440: '=': cannot convert from 'char *' to 'TCHAR *'
```

이 오류를 생성하는 코드는 다음과 같습니다.

```cpp
pParentNode->m_szText = new char[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

`_tcscpy`문자열을 복사 하기 위한 tchar.h strcpy 함수를 사용 하는 경우에도 할당 된 버퍼는 **`char`** 버퍼 였습니다. 이 코드는 TCHAR로 쉽게 변경됩니다.

```cpp
pParentNode->m_szText = new TCHAR[strTitle.GetLength() + 1];
_tcscpy(pParentNode->m_szText, strTitle);
```

마찬가지로, 컴파일러 오류가 발생할 경우 LPSTR(긴 문자열 포인터) 및 LPCSTR(긴 상수 문자열 포인터)를 LPTSTR(긴 TCHAR 문자열 포인터) 및 LPCTSTR(긴 상수 TCHAR 문자열 포인터)로 각각 변경했습니다. 각 상황을 개별적으로 검사해야 했으므로 전체 검색 및 바꾸기를 사용하여 이러한 바꾸기를 수행하지는 않았습니다. **`char`** 접미사를 포함 하는 windows 구조를 사용 하는 특정 windows 메시지를 처리 하는 경우와 같이 버전이 필요한  경우도 있습니다. Windows API에서 접미사 **A** 는 ASCII 또는 ANSI를 의미하고(MBCS에도 적용됨), 접미사 **W** 는 와이드 문자 또는 UTF-16 유니코드를 의미합니다. 이 명명 패턴은 Windows 헤더에서 사용되지만, Spy++ 코드에서 MBCS 버전에서만 이미 정의된 함수의 유니코드 버전을 추가해야 하는 경우에도 따랐습니다.

올바르게 확인되는 버전을 사용하기 위해 형식을 바꾸어야 하는 경우도 있었습니다(예: WNDCLASSA 대신 WNDCLASS 사용).

대부분의 경우 `GetClassName`(`GetClassNameA` 대신)과 같은 Win32 API의 제네릭 버전(매크로)을 사용해야 했습니다. 메시지 처리기 switch 문에서 일부 메시지는 MBCS 또는 유니코드 특정이고, 두 경우 모두 MBCS 버전을 명시적으로 호출하도록 코드를 변경해야 했습니다. 일반적으로 명명된 함수를 **A** 및 **W** 특정 함수로 바꾸고 UNICODE 정의 여부에 따라 올바른 **A** 또는 **W** 이름으로 확인되는 제네릭 이름에 대한 매크로를 추가했기 때문입니다.  코드의 많은 부분에서, 유니코드를 정의 하기 위해 전환할 때 \_ 이제 **는** 버전이 필요한 경우에도 W 버전이 선택 됩니다.

특별한 조치가 필요한 몇 개의 위치가 있습니다. `WideCharToMultiByte` 또는 `MultiByteToWideChar`를 사용하려면 자세히 살펴보아야 할 수 있습니다. 다음은 `WideCharToMultiByte`가 사용된 한 가지 예제입니다.

```cpp
BOOL C3dDialogTemplate::GetFont(CString& strFace, WORD& nFontSize)
{
  ASSERT(m_hTemplate != NULL);

  DLGTEMPLATE* pTemplate = (DLGTEMPLATE*)GlobalLock(m_hTemplate);
  if ((pTemplate->style & DS_SETFONT) == 0)
  {
    GlobalUnlock(m_hTemplate);
    return FALSE;
  }

  BYTE* pb = GetFontSizeField(pTemplate);
  nFontSize = *(WORD*)pb;
  pb += sizeof (WORD);
  WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
  strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
  strFace.ReleaseBuffer();
  GlobalUnlock(m_hTemplate);
  return TRUE;
}
```

이 작업을 처리하려면 작업이 수행된 이유가 `CString`의 내부 버퍼, `strFace`에 글꼴 이름을 나타내는 와이드 문자열을 복사하기 위한 것임을 이해해야 했습니다. 이 예제는 와이드 문자 `CString` 문자열과 마찬가지로 멀티바이트 `CString` 문자열을 위한 약간 다른 코드가 필요했으므로 이 경우 `#ifdef`를 추가했습니다.

```cpp
#ifdef _MBCS
WideCharToMultiByte(CP_ACP, 0, (LPCWSTR)pb, -1,
strFace.GetBufferSetLength(LF_FACESIZE), LF_FACESIZE, NULL, NULL);
strFace.ReleaseBuffer();
#else
wcscpy(strFace.GetBufferSetLength(LF_FACESIZE), (LPCWSTR)pb);
strFace.ReleaseBuffer();
#endif
```

물론, 실제로 `wcscpy` 대신 보다 안전한 버전인 `wcscpy_s`를 사용해야 합니다. 다음 섹션에서 이 작업을 처리합니다.

작업을 검사하기 위해 **문자 집합** 을 **멀티바이트 문자 집합 사용** 으로 다시 설정하고 유니코드 및 MBCS를 사용하여 코드가 컴파일되는지 확인해야 합니다. 당연히 이러한 모든 변경 후에는 다시 컴파일된 앱에서 전체 테스트 과정을 실행해야 합니다.

이 Spy++ 솔루션을 작업할 때 평균적인 C++ 개발자가 코드를 유니코드로 변환하는 데 약 2일이 걸렸습니다. 다시 테스트하는 시간은 여기에 포함되지 않았습니다.

## <a name="step-12-porting-to-use-the-secure-crt"></a><a name="porting_to_secure_crt"></a> 12 단계. 보안 CRT를 사용하도록 포팅

보안 버전 ( **_s** 접미사가 있는 버전)을 사용 하도록 코드를 이식 하는 것은 다음에 있습니다. 이 경우 일반적인 전략은 함수를 **_s** 버전으로 바꾼 후 일반적으로 필요한 추가 버퍼 크기 매개 변수를 추가 하는 것입니다. 대부분의 경우 크기가 알려져 있으므로 이 작업은 간단합니다. 크기를 즉시 사용할 수 없는 경우에는 CRT 함수를 사용 하는 함수에 매개 변수를 더 추가 하거나 대상 버퍼의 사용을 검사 하 고 적절 한 크기 제한을 확인 해야 합니다.

Visual C++에서는 크기 매개 변수를 많이 추가하지 않고 쉽게 코드 보안을 설정하는 트릭을 제공하며, 템플릿 오버로드를 사용하여 수행됩니다. 이러한 오버로드는 템플릿이므로 C가 아니라 C++로 컴파일하는 경우에만 사용할 수 있습니다. Spyxxhk는 C 프로젝트이므로 트릭이 작동하지 않습니다.  그러나 Spyxx는 C 프로젝트가 아니므로 트릭을 사용할 수 있습니다. 트릭은 stdafx.h와 같은 프로젝트의 각 파일에서 컴파일되는 위치에 다음과 같은 줄을 추가하는 것입니다.

```cpp
#define _CRT_SECURE_TEMPLATE_OVERLOADS 1
```

이렇게 정의하면 버퍼가 배열일 때마다 원시 포인터 대신 해당 크기가 배열 형식에서 유추되고, 사용자가 제공하지 않아도 크기 매개 변수로 사용됩니다. 이는 코드를 다시 작성하는 복잡성을 줄이는 데 도움이 됩니다. 함수 이름을 **_s** 버전으로 바꾸어야 하지만 검색 및 바꾸기 작업으로 수행할 수 있는 경우가 많습니다.

일부 함수의 반환 값이 변경됩니다. 예를 들어 `_itoa_s`(및 `_itow_s`와 매크로 `_itot_s`)는 문자열 대신 오류 코드(`errno_t`)를 반환합니다. 따라서 이러한 경우 `_itoa_s`에 대한 호출을 별도 줄로 이동하고 버퍼의 식별자로 바꾸어야 합니다.

몇 가지 일반적인 사례: `memcpy`의 경우 `memcpy_s`로 전환하면 복사되는 구조의 크기가 추가되는 경우가 많습니다. 마찬가지로, 대부분의 문자열과 버퍼의 경우 배열 또는 버퍼의 크기가 버퍼 선언에서 또는 버퍼가 원래 할당된 위치를 찾아 쉽게 확인됩니다. 일부 상황에서는 실제로 사용할 수 있는 버퍼 크기를 확인 해야 하며, 수정 중인 함수 범위에서 해당 정보를 사용할 수 없는 경우 추가 매개 변수로 추가 해야 하 고 정보를 제공 하도록 호출 코드를 수정 해야 합니다.

이러한 기술을 통해 안전한 CRT 함수를 사용하도록 코드를 변환하는 데 약 반나절이 걸렸습니다. 템플릿 오버로드를 선택하지 않고 크기 매개 변수를 수동으로 추가하는 경우 두세 배의 시간이 걸릴 것입니다.

## <a name="step-13-zcforscope--is-deprecated"></a><a name="deprecated_forscope"></a> 13 단계. /Zc:forScope가 사용되지 않음

Visual C++ 6.0 이후 컴파일러는 루프에서 선언된 변수의 범위를 루프 범위로 제한하는 현재 표준을 준수합니다. 컴파일러 옵션 [/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)(프로젝트 속성의 **루프 범위 강제 규칙**)는 이를 오류로 보고할지 여부를 제어합니다. 부합되도록 코드를 업데이트하고 루프 바깥쪽에 선언을 추가해야 합니다. 코드 변경을 방지하기 위해 C++ 프로젝트 속성의 **언어** 섹션에서 해당 설정을 `No (/Zc:forScope-)`로 변경할 수 있습니다. 그러나 Visual C++의 이후 릴리스에서 `/Zc:forScope-`가 제거될 수도 있으므로 결국 표준에 맞게 코드를 변경해야 합니다.

이러한 문제는 비교적 쉽게 해결되지만, 코드에 따라 많은 코드에 영향을 줄 수 있습니다. 다음은 일반적인 문제입니다.

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  for (int n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

위 코드는 오류를 생성합니다.

```Output
'n': undeclared identifier
```

이 오류는 컴파일러가 더 이상 C++ 표준을 준수하지 않는 코드를 허용하는 컴파일러 옵션 사용을 중단했기 때문에 발생합니다. 표준에서 루프 내의 변수 선언은 해당 범위가 루프로만 제한되므로 루트 바깥쪽에 루프 카운터를 사용하는 일반적인 방식의 경우에도 다음 수정된 코드와 같이 루프 카운터를 루프 바깥쪽으로 이동해야 합니다.

```cpp
int CPerfTextDataBase::NumStrings(LPCTSTR mszStrings) const
{
  int n;
  for (n = 0; mszStrings[0] != 0; n++)
  mszStrings = _tcschr(mszStrings, 0) + 1;
  return(n);
}
```

## <a name="summary"></a>요약

원래 Visual C++ 6.0 코드에서 최신 컴파일러로 Spy++를 포팅하는 데 약 1주 동안 20시간의 코딩 시간이 소요되었습니다. Visual Studio 6.0에서 Visual Studio 2015로 8개 제품 릴리스가 직접 업그레이드되었습니다. 이 방법은 현재 큰 프로젝트와 작은 프로젝트의 업그레이드에 모두 권장되는 방법입니다.

## <a name="see-also"></a>참고 항목

[포팅 및 업그레이드: 예제 및 사례 연구](../porting/porting-and-upgrading-examples-and-case-studies.md)<br/>
[이전 사례 연구: COM Spy](../porting/porting-guide-com-spy.md)
