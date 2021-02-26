---
title: C++ 문서의 새로운 기능
description: Microsoft C/C++ 컴파일러, ATL/MFC, C 런타임, 표준 라이브러리 문서에 대한 새로운 문서 및 문서 업데이트입니다.
ms.date: 02/17/2021
ms.openlocfilehash: b15d286eb7bd2951ab2b8101a752de2beb57f4a4
ms.sourcegitcommit: e99db7c3b5f25ece0e152165066c926751a7c2ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100643575"
---
# <a name="microsoft-c-docs-whats-new-for-visual-studio-168"></a>Microsoft C++ 문서: Visual Studio 16.8의 새로운 기능

이 문서에는 Visual Studio 16.8에 대한 문서의 주요 변경 내용 중 일부가 나열되어 있습니다. 

Visual Studio의 새로운 기능에 대한 자세한 내용은 [Visual Studio의 새로운 C++ 기능](what-s-new-for-visual-cpp-in-visual-studio.md)을 참조하세요.

최신 C++ 규칙 상태는 [Visual Studio의 C++ 규칙 향상](cpp-conformance-improvements.md)을 참조하세요.

## <a name="c-language"></a>C 언어

### <a name="new-articles"></a>새 문서

- [`_Noreturn` 키워드 및 `noreturn` 매크로(C11)](../c-language/noreturn.md)
- [_Static_assert 키워드 및 static_assert 매크로(C11)](../c-language/static-assert-c.md)

### <a name="updated-articles"></a>업데이트된 문서

- [C 명령줄 인수 구문 분석](../c-language/parsing-c-command-line-arguments.md) - C 인수를 구문 분석하는 규칙에 대한 예외 문서화
- [형식 한정자](../c-language/type-qualifiers.md) - `restrict` 추가됨
- [C 할당 연산자](../c-language/c-assignment-operators.md) - C17에 대한 어휘 문법 업데이트
- [C 키워드](../c-language/c-keywords.md) - C17에 대한 어휘 문법 업데이트
- [C 어휘 문법](../c-language/lexical-grammar.md) - C17에 대한 어휘 문법 업데이트
- [선언 요약](../c-language/summary-of-declarations.md) - C17에 대한 어휘 문법 업데이트
- [식 요약](../c-language/summary-of-expressions.md) - C17에 대한 어휘 문법 업데이트
- [C 열거형 선언](../c-language/c-enumeration-declarations.md) - 어휘 문법 수정됨
- [C 문 요약](../c-language/summary-of-statements.md) - `__leave`, `__try` 키워드에 대해 업데이트됨

## <a name="c-runtime-library"></a>C 런타임 라이브러리

### <a name="new-articles"></a>새 문서

- [형식-제네릭 수학](../c-runtime-library/tgmath.md)

### <a name="updated-articles"></a>업데이트된 문서

- [`qsort`](../c-runtime-library/reference/qsort.md) - 안정성에 대한 참고 사항 추가됨
- [`_cwait`](../c-runtime-library/reference/cwait.md) - 코드 예제 수정됨
- [함수 패밀리 개요](../c-runtime-library/function-family-overviews.md) - 연산자 `new` 및 `delete` 추가됨
- [`round, roundf, roundl`](../c-runtime-library/reference/round-roundf-roundl.md) - 반올림 코드 예제에 대한 명확한 설명 제공됨
- [호환성](../c-runtime-library/compatibility.md) - C99 규칙 참고 사항 추가됨
- [`realloc`](../c-runtime-library/reference/realloc.md) - C99 규칙 참고 사항 추가됨
- [CRT 라이브러리 기능](../c-runtime-library/crt-library-features.md) - C99 규칙 참고 사항 추가됨
- [`assert Macro, _assert, _wassert`](../c-runtime-library/reference/assert-macro-assert-wassert.md) - 어설션 동작에 대한 명확한 설명 제공됨
- [`vsnprintf_s, _vsnprintf_s, _vsnprintf_s_l, _vsnwprintf_s, _vsnwprintf_s_l`](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md) - 반환 값에 대한 명확한 설명 제공됨
- [`setlocale, _wsetlocale`](../c-runtime-library/reference/setlocale-wsetlocale.md) - C 런타임 UTF-8 지원 정보 추가됨

## <a name="cc-preprocessor-reference"></a>C/C++ 전처리기 참조

### <a name="updated-articles"></a>업데이트된 문서

- [미리 정의된 매크로](../preprocessor/predefined-macros.md) - 16.8 릴리스 정보, C11/C17 `/std` 지원 및 SDK 설치 문서로 업데이트됨
- [MSVC 새 전처리기 개요](../preprocessor/preprocessor-experimental-overview.md) - 전처리기 콘텐츠 업데이트됨

## <a name="code-quality"></a>코드 품질

### <a name="new-articles"></a>새 문서

- [C33001](../code-quality/c33001.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가
- [C33004](../code-quality/c33004.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가
- [C33005](../code-quality/c33005.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가
- [C33010](../code-quality/c33010.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가
- [C33011](../code-quality/c33011.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가
- [C33020](../code-quality/c33020.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가
- [C33022](../code-quality/c33022.md) - VC 코드 분석 - 16.8의 새 규칙에 대해 추가

### <a name="updated-articles"></a>업데이트된 문서

- [`C6262`](../code-quality/c6262.md) - cpp-docs.zh-tw 문제 20 해결
- [`C26497 USE_CONSTEXPR_FOR_FUNCTION`](../code-quality/c26497.md) - C26497에 예제 추가됨
- [`C26496 USE_CONST_FOR_VARIABLE`](../code-quality/c26496.md) - C26496에 예제 추가됨
- [`C26495 MEMBER_UNINIT`](../code-quality/c26495.md) - C26495의 예제 및 링크 업데이트됨
- [`C26483 STATIC_INDEX_OUT_OF_RANGE`](../code-quality/c26483.md) - C26483에 예제 추가됨
- [`C26462 USE_CONST_POINTER_FOR_VARIABLE`](../code-quality/c26462.md) - C26462에 설명 및 예제 추가됨
- [`C26461 USE_CONST_POINTER_ARGUMENTS:`](../code-quality/c26461.md) - C26461에 설명 및 예제 추가됨
- [`C26460 USE_CONST_REFERENCE_ARGUMENTS`](../code-quality/c26460.md) - C26460에 설명 및 예제 추가됨
- [`C26440 DECLARE_NOEXCEPT`](../code-quality/c26440.md) - C26440에 대해 예제 및 핵심 지침 링크 추가됨
- [`C26439 SPECIAL_NOEXCEPT`](../code-quality/c26439.md) - C26439에 대해 예제 및 핵심 지침 링크 추가됨
- [`C26436 NEED_VIRTUAL_DTOR`](../code-quality/c26436.md) - C26436에 예제 및 핵심 지침 링크 추가됨
- [`C26408 NO_MALLOC_FREE`](../code-quality/c26408.md) - C26408에 예제 및 핵심 지침 링크 추가됨
- [`C26401 DONT_DELETE_NON_OWNER`](../code-quality/c26401.md) - C26401에 예제 및 핵심 지침 링크 추가됨
- [`C26494 VAR_USE_BEFORE_INIT`](../code-quality/c26494.md) - C26494에 예제 추가됨
- [`C26493 NO_CSTYLE_CAST`](../code-quality/c26493.md) - C26493에 예제 추가됨
- [`C26492 NO_CONST_CAST`](../code-quality/c26492.md) - C26492에 예제 추가됨
- [`C26490 NO_REINTERPRET_CAST`](../code-quality/c26490.md) - C26490에 예제 추가됨
- [`C26482 NO_DYNAMIC_ARRAY_INDEXING`](../code-quality/c26482.md) - C26482에 예제 추가됨
- [`C26471 NO_REINTERPRET_CAST_FROM_VOID_PTR`](../code-quality/c26471.md) - C26471에 예제 추가됨
- [`C26466 NO_STATIC_DOWNCAST_POLYMORPHIC`](../code-quality/c26466.md) - C26466에 예제 추가됨
- [`C26465 NO_CONST_CAST_UNNECESSARY`](../code-quality/c26465.md) - C26465에 예제 추가됨
- [`C26447 DONT_THROW_IN_NOEXCEPT`](../code-quality/c26447.md) -C26447에 예제 추가 중
- [`C26446 USE_GSL_AT`](../code-quality/c26446.md) - C26446에 대한 예제 추가됨
- [`C26434 DONT_HIDE_METHODS`](../code-quality/c26434.md) - C26434에 대한 예제 추가됨
- [`C26432 DEFINE_OR_DELETE_SPECIAL_OPS`](../code-quality/c26432.md) - C26432에 대한 예제 추가됨
- [`C26402 DONT_HEAP_ALLOCATE_MOVABLE_RESULT`](../code-quality/c26402.md) - C26402에 대한 예제 추가됨
- [`C26409 NO_NEW_DELETE`](../code-quality/c26409.md) - C26409에 대한 예제 추가됨
- [`C26474 NO_IMPLICIT_CAST`](../code-quality/c26474.md) -기본/파생된 사례를 명확히 설명하도록 C26474 업데이트됨
## <a name="linux-with-microsoft-c-in-visual-studio"></a>Visual Studio에서 Microsoft C++를 사용하는 Linux

### <a name="new-articles"></a>새 문서

- [Visual Studio에서 Linux CMake 프로젝트 구성](../linux/cmake-linux-configure.md)

### <a name="updated-articles"></a>업데이트된 문서

- [Visual Studio에서 Linux MSBuild C++ 프로젝트 만들기](../linux/create-a-new-linux-project.md) - Linux 프로젝트 만들기에 대한 지침 업데이트됨
- [ConnectionManager 참조](../linux/connectionmanager-reference.md) - 수정, 정리에 대한 명령 추가됨
- [Visual Studio에서 Linux CMake 프로젝트 구성](../linux/cmake-linux-configure.md) - 최신 UI를 반영하도록 업데이트됨
- [Linux MSBuild 프로젝트 배포, 실행, 디버그](../linux/deploy-run-and-debug-your-linux-project.md) - `GDB Path` 추가됨

## <a name="cc-compiler-and-tools-errors-and-warnings"></a>C/C++ 컴파일러와 도구 오류 및 경고

### <a name="new-articles"></a>새 문서

- [컴파일러 경고(수준 4) C4388](../error-messages/compiler-warnings/c4388.md) - 경고 C4388 추가됨, 16.7 경고 업데이트됨

### <a name="updated-articles"></a>업데이트된 문서

- [컴파일러 경고(수준 3) C4018](../error-messages/compiler-warnings/compiler-warning-level-3-c4018.md) - 16.7 경고 업데이트됨
- [컴파일러 경고(수준 4) C4389](../error-messages/compiler-warnings/compiler-warning-level-4-c4389.md) - 16.7 경고 업데이트됨
- [컴파일러 버전별 컴파일러 버전](../error-messages/compiler-warnings/compiler-warnings-by-compiler-version.md) - 16.7 경고 업데이트됨
- [컴파일러 경고 C4800 ~ C5999](../error-messages/compiler-warnings/compiler-warnings-c4800-through-c4999.md) - 16.7 경고 업데이트됨
- [컴파일러 오류 C3381](../error-messages/compiler-errors-2/compiler-error-c3381.md) -cpp-docs 2493 해결, 설명 및 예제 업데이트

## <a name="cc-compiler-intrinsics-and-assembly-language"></a>C/C++ 컴파일러 내장 함수 및 어셈블리 언어

### <a name="updated-articles"></a>업데이트된 문서

- [Visual Studio의 C++ 규칙 향상](../overview/cpp-conformance-improvements.md) - 16.8 릴리스 정보로 업데이트됨
- [Microsoft C/C++ 도움말 및 커뮤니티](../overview/visual-cpp-help-and-community.md) - DevCom 및 Microsoft Docs Q&A 링크 업데이트됨
- [Visual Studio의 C++](../overview/visual-cpp-in-visual-studio.md) - DevCom 및 Microsoft Docs Q&A 링크 업데이트됨
- [Microsoft C++ 언어 규칙 테이블](../overview/visual-cpp-language-conformance.md) - C++20 라이브러리 규칙 테이블 업데이트됨, 16.7에 대한 언어 기능 테이블 업데이트

## <a name="c-in-visual-studio"></a>Visual Studio의 C++

### <a name="updated-articles"></a>업데이트된 문서

- [`__restrict`](../cpp/extension-restrict.md)
- [if-else 문(C++)](../cpp/if-else-statement-cpp.md) - `if/else` 문법에 대한 설명 추가됨
- [`union`](../cpp/unions.md) - 코드 조각 수정됨

## <a name="cc-projects-and-build-systems"></a>C/C++ 프로젝트 및 빌드 시스템

### <a name="new-articles"></a>새 문서

- [`.vcxproj` 파일 및 와일드카드](../build/reference/vcxproj-files-and-wildcards.md)
- [`/headerUnit`(헤더 단위 IFC 사용)](../build/reference/headerunit.md)
- [`/module:exportHeader`(헤더 단위 만들기)](../build/reference/module-exportheader.md)
- [`/module:reference`(명명된 모듈 IFC 사용)](../build/reference/module-reference.md)
- [`/translateInclude`(include 지시문을 import 지시문으로 변환)](../build/reference/translateinclude.md)
- [`/Zc:preprocessor`(전처리기 규칙 모드 사용)](../build/reference/zc-preprocessor.md)

### <a name="updated-articles"></a>업데이트된 문서

- [`/permissive-`(표준 준수)](../build/reference/permissive-standards-conformance.md) - 16.8 릴리스 정보로 업데이트됨
- [`/clr`(공용 언어 런타임 컴파일)](../build/reference/clr-common-language-runtime-compilation.md) - `/clr`에 대한 설명 추가됨
- [pgosweep](../build/pgosweep.md) - pgosweep 옵션 더 추가됨
- [`__declspec(dllimport)`을 사용하여 데이터 가져오기](../build/importing-data-using-declspec-dllimport.md) - 예제 업데이트됨

## <a name="c-porting-and-upgrade-guide"></a>C++ 포팅 및 업그레이드 가이드

### <a name="updated-articles"></a>업데이트된 문서

- [방법: 유니버설 Windows 플랫폼 앱에서 기존 C++ 코드 사용](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md) - 명확한 설명을 위해 재작성하고 예제 업데이트함

## <a name="c-standard-library-stl-reference"></a>C++ 표준 라이브러리(STL) 참조

### <a name="new-articles"></a>새 문서

- [`<bit>`](../standard-library/bit.md)
- [`<bit>` 함수](../standard-library/bit-functions.md)
- [`endian` 열거형](../standard-library/bit-enum.md)

### <a name="updated-articles"></a>업데이트된 문서

- [`<ios>` typedef](../standard-library/ios-typedefs.md) - GitHub #2514별 예제 업데이트됨
- [`basic_string` 클래스](../standard-library/basic-string-class.md) - `_starts_with()`, `ends_with()` 추가됨
- [`ios_base Class`](../standard-library/ios-base-class.md)
- [`map` 클래스](../standard-library/map-class.md)
- [`multimap` 클래스](../standard-library/multimap-class.md) - `contains()` 추가됨
- [`multiset` 클래스](../standard-library/multiset-class.md) - `contains()` 추가됨
- [`set` 클래스](../standard-library/set-class.md) - `contains()` 추가됨
- [`unordered_map` 클래스](../standard-library/unordered-map-class.md) - `contains()` 추가됨
- [`unordered_multimap` 클래스](../standard-library/unordered-multimap-class.md) - `contains()` 추가됨
- [`unordered_multiset` 클래스](../standard-library/unordered-multiset-class.md) - `contains()` 추가됨
- [`unordered_set` 클래스](../standard-library/unordered-set-class.md) - `contains()` 추가됨
- [`basic_string_view` 클래스](../standard-library/basic-string-view-class.md) - `starts_with()`, `ends_with()` 추가됨
- [`<bit>` 함수](../standard-library/bit-functions.md) - `nodiscard` 구문 업데이트됨

## <a name="community-contributors"></a>커뮤니티 기여자

이 기간 동안 C++, C, 어셈블러 문서에 기여한 사용자는 다음과 같습니다. 감사합니다! 기여 방법을 알아보려면 [Microsoft Docs 기여자 가이드 개요](https://docs.microsoft.com/contribute/)를 참조하세요.

- [yecril71pl](https://github.com/yecril71pl) - Christopher Yeleighton(4)
- [definedrisk](https://github.com/definedrisk) - Ben(3)
- [BeardedFish](https://github.com/BeardedFish) - Darian B. (1)
- [codevenkat](https://github.com/codevenkat)(1)
- [eltociear](https://github.com/eltociear) - Ikko Ashimine (1)
- [fsb4000](https://github.com/fsb4000) - Igor Zhukov(1)
- [Jaiganeshkumaran](https://github.com/Jaiganeshkumaran) - Jaiganesh Kumaran(1)
- [jogo-](https://github.com/jogo-)(1)
- [justanotheranonymoususer](https://github.com/justanotheranonymoususer)(1)
- [matrohin](https://github.com/matrohin) - Dmitry Matrokhin(1)
- [mhemmit](https://github.com/mhemmit)(1)
- [MSDN-WhiteKnight](https://github.com/MSDN-WhiteKnight) - MSDN.WhiteKnight(1)
- [OdinTemple](https://github.com/OdinTemple) - Odin Temple(1)
- [r00tdr4g0n](https://github.com/r00tdr4g0n) - r00tdr4g0n(1)
- [sebkraemer](https://github.com/sebkraemer) - Sebastian Krämer(1)
- [vtjnash](https://github.com/vtjnash) - Jameson Nash(1)
- [Youssef1313](https://github.com/Youssef1313) - Youssef Victor (1)
- [zecozephyr](https://github.com/zecozephyr) - Jonathan Bailey(1)