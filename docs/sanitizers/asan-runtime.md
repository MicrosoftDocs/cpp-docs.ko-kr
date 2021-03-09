---
title: AddressSanitizer 런타임
description: Microsoft C/c + + 용 AddressSanitizer 런타임에 대 한 기술 설명입니다.
ms.date: 03/02/2021
helpviewer_keywords:
- AddressSanitizer runtime
- Address Sanitizer runtime
- clang_rt.asan
- Clang runtime
- ASan runtime
ms.openlocfilehash: 6ab27365ba6841dd5314f1eac65abd71b7d4170d
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471180"
---
# <a name="addresssanitizer-runtime"></a>AddressSanitizer 런타임

AddressSanitizer 런타임 라이브러리는 메모리 액세스 검사를 사용 하도록 설정 하는 일반적인 메모리 할당 함수 및 작업을 차단 합니다. 컴파일러가 생성할 수 있는 다양 한 형식의 실행 파일을 지 원하는 여러 가지 런타임 라이브러리가 있습니다. 컴파일 시간에 옵션을 전달 하는 한 컴파일러와 링커는 적절 한 런타임 라이브러리를 자동으로 연결 합니다 [`/fsanitize=address`](../build/reference/fsanitize.md) . 링크 타임에 옵션을 사용 하 여 기본 동작을 재정의할 수 있습니다 **`/NODEFAULTLIB`** . 자세한 내용은 [AddressSanitizer 언어, 빌드 및 디버깅 참조](./asan-building.md)의 [링크](./asan-building.md#linker) 에 대 한 섹션을 참조 하세요.

다음은 AddressSanitizer 런타임에 연결 하기 위한 런타임 라이브러리의 인벤토리입니다 *`{arch}`* . 여기서는 *`i386`* 또는 *`x86_64`* 입니다.

> [!NOTE]
> 이러한 라이브러리는 아키텍처 이름에 대해 Clang 규칙을 유지 합니다. MSVC 규칙은 일반적으로 i386 및 x86_64이 아닌 x86 및 x 64입니다. 동일한 아키텍처를 참조 합니다.

| CRT 옵션 | DLL 또는 EXE | 디버그? | AddressSanitizer runtime 이진 파일 라이브러리 |
|--|--|--|--|
| MT | EXE | 아니요 | *`clang_rt.asan-{arch}`*, *`clang_rt.asan_cxx-{arch}`* |
| MT | DLL | 아니요 | *`clang_rt.asan_dll_thunk-{arch}`* |
| MD | 다음 중 하나 | 아니요 | *`clang_rt.asan_dynamic-{arch}`*, *`clang_rt.asan_dynamic_runtime_thunk-{arch}`* |
| MT | EXE | YES | *`clang_rt.asan_dbg-{arch}`*, *`clang_rt.asan_dbg_cxx-{arch}`* |
| MT | DLL | YES | *`clang_rt.asan_dbg_dll_thunk-{arch}`* |
| MD | 다음 중 하나 | YES | *`clang_rt.asan_dbg_dynamic-{arch}`*, *`clang_rt.asan_dbg_dynamic_runtime_thunk-{arch}`* |

를 사용 하 여 컴파일할 때 `cl /fsanitize=address` 컴파일러는 [섀도 바이트](./asan-shadow-bytes.md)를 관리 하 고 확인 하는 명령을 생성 합니다. 프로그램은이 계측을 사용 하 여 스택, 힙 또는 전역 범위에서 메모리 액세스를 확인 합니다. 컴파일러는 스택 및 전역 변수를 설명 하는 메타 데이터도 생성 합니다. 이 메타 데이터를 사용 하면 런타임 시 소스 코드의 함수 이름, 줄 및 열에 대 한 정확한 오류 진단을 생성할 수 있습니다. 컴파일러 검사 및 런타임 라이브러리는 결합 되어 런타임에 발생 하는 경우 많은 형식의 [메모리 안전 버그](./asan-error-examples.md) 를 정확 하 게 진단할 수 있습니다.

## <a name="function-interception"></a>함수 가로채기

AddressSanitizer는 다양 한 핫 패치 기술을 통해 가로채기 기능을 전달 합니다. 이러한 기술은 [소스 코드 자체 내에서 가장 잘 설명](https://github.com/llvm/llvm-project/blob/1a2eaebc09c6a200f93b8beb37130c8b8aab3934/compiler-rt/lib/interception/interception_win.cpp#L11)되어 있습니다.

런타임 라이브러리는 일반적인 메모리 관리 및 메모리 조작 함수를 대부분 가로챕니다. 목록에 대해서는 [가로채기 함수 목록 AddressSanitizer](#intercepted_functions)을 참조 하세요. 할당 인터셉터는 각 할당 호출과 관련 된 메타 데이터 및 섀도 바이트를 관리 합니다. 또는와 같은 CRT 함수를 `malloc` 호출할 때마다 `delete` 인터셉터는 AddressSanitizer 영역에서 특정 값을 설정 하 여 이러한 힙 위치에 현재 액세스할 수 있는지 여부와 할당 범위를 나타냅니다. 이러한 섀도 바이트를 사용 하면 컴파일러에서 [섀도 바이트](./asan-shadow-bytes.md) 를 검사 하 여 로드 또는 저장소가 유효한 지 여부를 확인할 수 있습니다.

가로채기는 성공 하지 못할 수 있습니다. 함수 프롤로그가 너무 짧아서를 쓸 수 없는 경우 `jmp` 가로채기가 실패할 수 있습니다. 가로채기 오류가 발생 하면 프로그램은를 throw `debugbreak` 하 고 중지 합니다. 디버거를 연결 하면 가로채기 문제의 원인이 명확 하 게 됩니다. 이 문제가 발생 하는 경우 [버그를 보고](https://aka.ms/feedback/report?space=62)합니다.

> [!NOTE]
> 사용자는 필요에 따라 환경 변수를 값으로 설정 하 여 실패 한 가로채기를 계속 해 서 계속할 수 있습니다 `ASAN_WIN_CONTINUE_ON_INTERCEPTION_FAILURE` . 가로채기 실패를 계속 하면 해당 함수에 대 한 버그 보고서가 누락 될 수 있습니다.

## <a name="custom-allocators-and-the-addresssanitizer-runtime"></a>사용자 지정 할당자 및 AddressSanitizer 런타임

AddressSanitizer 런타임은 일반 할당자 인터페이스,, `malloc` / `free` `new` / `delete` , `HeapAlloc` / `HeapFree` (via `RtlAllocateHeap` / `RtlFreeHeap` )에 대 한 인터셉터를 제공 합니다. 많은 프로그램은 한 가지 이유 또는 다른 목적으로 사용자 지정 할당자를 사용 합니다. 예를 들어 `dlmalloc` 또는 인터페이스 및를 사용 하는 솔루션을 사용 하는 프로그램이 `std::allocator` `VirtualAlloc()` 있습니다. 컴파일러가 사용자 지정 할당자에 대 한 섀도 메모리 관리 호출을 자동으로 추가할 수 없습니다. [제공 된 수동 손상 인터페이스](#poisoning)를 사용 하는 것은 사용자의 책임입니다. 이 API를 통해 이러한 할당자는 기존 AddressSanitizer 런타임 및 [섀도 바이트](./asan-shadow-bytes.md) 규칙에 맞게 제대로 작동할 수 있습니다.

## <a name="manual-addresssanitizer-poisoning-interface"></a><a name="poisoning"></a> 수동 AddressSanitizer 손상 인터페이스

Enlightening에 대 한 인터페이스는 간단 하지만 사용자에 게 맞춤 제한을 적용 합니다. 사용자는를 가져와 이러한 프로토타입을 가져올 수 있습니다 [`sanitizer/asan_interface.h`](https://github.com/llvm/llvm-project/blob/main/compiler-rt/include/sanitizer/asan_interface.h) . 인터페이스 함수 프로토타입은 다음과 같습니다.

```cpp
void __asan_poison_memory_region(void const volatile *addr, size_t size);
void __asan_unpoison_memory_region(void const volatile *addr, size_t size);
```

편의를 위해 [AddressSanitizer 인터페이스 헤더 파일](https://github.com/llvm/llvm-project/blob/main/compiler-rt/include/sanitizer/asan_interface.h) 은 래퍼 매크로를 제공 합니다. 이러한 매크로는 컴파일 중에 AddressSanitizer 기능을 사용할 수 있는지 여부를 확인 합니다. 필요 하지 않은 경우 소스 코드에서 손상 함수 호출을 생략할 수 있습니다. 위의 함수를 직접 호출 하는 것 보다 이러한 매크로를 선호 해야 합니다.

```cpp
#define ASAN_POISON_MEMORY_REGION(addr, size)
#define ASAN_UNPOISON_MEMORY_REGION(addr, size)
```

## <a name="alignment-requirements-for-addresssanitizer-poisoning"></a>AddressSanitizer 손상에 대 한 맞춤 요구 사항

섀도 바이트의 수동 손상으로 인해 맞춤 요구 사항을 고려해 야 합니다. 섀도 바이트가 섀도 메모리의 바이트 경계에서 종료 되도록 필요한 경우 사용자가 안쪽 여백을 추가 해야 합니다. AddressSanitizer 섀도 메모리의 각 비트는 응용 프로그램 메모리의 단일 바이트 상태를 인코딩합니다. 이 인코딩은 안쪽 여백을 포함 하 여 각 할당의 총 크기를 8 바이트 경계에 맞춰야 함을 의미 합니다. 맞춤 요구 사항이 충족 되지 않으면 잘못 된 버그 보고가 발생할 수 있습니다. 잘못 된 보고는 누락 된 보고서 (거짓 부정)로 매니페스트 하거나 오류가 아닌 경우 (가양성) 보고할 수 있습니다.

맞춤 요구 사항 및 잠재적인 문제에 대 한 예시는 제공 된 [asan 맞춤 예](https://github.com/mcgov/asan_alignment_example)를 참조 하세요. 하나는 수동 섀도 메모리 손상으로 발생할 수 있는 문제를 보여 주는 작은 프로그램입니다. 두 번째는 인터페이스를 사용 하는 수동 손상의 예제 구현입니다 `std::allocator` .

## <a name="run-time-options"></a>런타임 옵션

Microsoft C/c + + (MSVC)는 [llvm 프로젝트 리포지토리에서 Clang AddressSanitizer runtime](https://github.com/llvm/llvm-project)을 기반으로 하는 런타임을 사용 합니다. 따라서 대부분의 런타임 옵션은 두 버전 간에 공유 됩니다. [공용 Clang 런타임 옵션의 전체 목록은 여기에서 사용할 수](https://github.com/google/sanitizers/wiki/SanitizerCommonFlags)있습니다. 다음 섹션에서는 몇 가지 차이점을 설명 합니다. 예상 대로 작동 하지 않는 옵션을 검색 하는 경우 [버그를 보고](https://aka.ms/feedback/report?space=62)합니다.

### <a name="unsupported-addresssanitizer-options"></a>지원 되지 않는 AddressSanitizer 옵션

- detect_container_overflow
- unmap_shadow_on_exit

> [!NOTE]
> AddressSanitizer runtime 옵션이 원하는 `halt_on_error` 대로 작동 하지 않습니다. Clang 및 MSVC 런타임 라이브러리 모두에서 대부분의 오류 형식은 대부분의 메모리 손상 오류를 포함 하 여 **비연속적 아닌** 것으로 간주 됩니다.

자세한 내용은 [Clang 12.0의 차이점](./asan.md#differences) 섹션을 참조 하세요.

### <a name="msvc-specific-addresssanitizer-runtime-options"></a>MSVC 특정 AddressSanitizer 런타임 옵션

- `windows_hook_legacy_allocators` 부울로 설정 하 여 `true` 및 할당자 가로채기를 사용 하도록 설정 [`GlobalAlloc`](/windows/win32/api/winbase/nf-winbase-globalalloc) [`LocalAlloc`](/windows/win32/api/winbase/nf-winbase-localalloc) 합니다.

> [!NOTE]
> `windows_hook_legacy_allocators`이 문서를 작성 했을 때 공개 llvm 런타임에이 옵션을 사용할 수 없습니다. 이 옵션은 궁극적으로 공용 프로젝트에 다시 기여 될 수 있습니다. 그러나 코드 검토와 커뮤니티 승인에 따라 다릅니다.
>
> 이전에 `windows_hook_rtl_allocators` AddressSanitizer이 실험적 인 옵트인 (opt in) 기능이 실험적 인 옵션은 이제 기본적으로 사용 하도록 설정 되어 있습니다.

## <a name="addresssanitizer-list-of-intercepted-functions-windows"></a><a name="intercepted_functions"></a> AddressSanitizer 가로채기 함수 목록 (Windows)

AddressSanitizer 런타임 핫 패치는 런타임에 메모리 안전성 검사를 사용 하도록 설정 하는 다양 한 함수를 사용 합니다. 다음은 AddressSanitizer 런타임이 모니터링 하는 함수에 대 한 완전 하지 않은 목록입니다.

### <a name="default-interceptors"></a>기본 인터셉터

- [`__C_specific_handler` (x 64에만 해당)](/windows/win32/devnotes/--c-specific-handler2)
- [`_aligned_free`](../c-runtime-library/reference/aligned-free.md)
- [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md)
- [`_aligned_msize`](../c-runtime-library/reference/aligned-msize.md)
- [`_aligned_realloc`](../c-runtime-library/reference/aligned-realloc.md)
- [`_calloc_base`](../c-runtime-library/reference/calloc.md)
- [`_calloc_crt`](../c-runtime-library/reference/calloc.md)
- [`_calloc_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/calloc-dbg.md)
- [`_except_handler3` (x 86에만 해당)](../c-runtime-library/except-handler3.md)
- [ `_except_handler4` (x 86에만 해당)](../c-runtime-library/internal-crt-globals-and-functions.md) (문서화 되지 않음)
- [`_expand`](../c-runtime-library/reference/expand.md)
- `_expand_base` 나오지
- [`_expand_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/expand-dbg.md)
- [`_free_base`](../c-runtime-library/internal-crt-globals-and-functions.md) 나오지
- [`_free_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/free-dbg.md)
- [`_malloc_base`](../c-runtime-library/internal-crt-globals-and-functions.md) 나오지
- `_malloc_crt` 나오지
- [`_malloc_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/malloc-dbg.md)
- [`_msize`](../c-runtime-library/reference/msize.md)
- `_msize_base` 나오지
- [`_msize_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/msize-dbg.md)
- [`_realloc_base`](../c-runtime-library/internal-crt-globals-and-functions.md) 나오지
- `_realloc_crt` 나오지
- [`_realloc_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/realloc-dbg.md)
- [`_recalloc`](../c-runtime-library/reference/recalloc.md)
- `_recalloc_base` 나오지
- `_recalloc_crt` 나오지
- [`_recalloc_dbg` (디버그 런타임 전용)](../c-runtime-library/reference/recalloc-dbg.md)
- [`_strdup`](../c-runtime-library/reference/strdup-wcsdup-mbsdup.md)
- [`atoi`](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)
- [`atol`](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)
- [`calloc`](../c-runtime-library/reference/calloc.md)
- [`CreateThread`](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createthread)
- [`free`](../c-runtime-library/reference/free.md)
- [`frexp`](../c-runtime-library/reference/frexp.md)
- [`longjmp`](../c-runtime-library/reference/longjmp.md)
- [`malloc`](../c-runtime-library/reference/malloc.md)
- [`memchr`](../c-runtime-library/reference/memchr-wmemchr.md)
- [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md)
- [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md)
- [`memmove`](../c-runtime-library/reference/memmove-wmemmove.md)
- [`memset`](../c-runtime-library/reference/memset-wmemset.md)
- [`RaiseException`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)
- [`realloc`](../c-runtime-library/reference/realloc.md)
- [`RtlAllocateHeap`](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-rtlallocateheap)
- [`RtlCreateHeap`](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-rtlcreateheap)
- [`RtlDestroyHeap`](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-rtlcreateheap)
- [`RtlFreeHeap`](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-rtlfreeheap)
- [`RtlRaiseException`](/windows/win32/api/rtlsupportapi/nf-rtlsupportapi-rtlraiseexception)
- `RtlReAllocateHeap` 나오지
- `RtlSizeHeap` 나오지
- [`SetUnhandledExceptionFilter`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-setunhandledexceptionfilter)
- [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md)
- [`strchr`](../c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l.md)
- [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)
- [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)
- [`strcspn`](../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)
- [`strdup`](../c-runtime-library/reference/strdup-wcsdup.md)
- [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
- [`strncat`](../c-runtime-library/reference/strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)
- [`strncmp`](../c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)
- [`strncpy`](../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)
- [`strnlen`](../c-runtime-library/reference/strnlen-strnlen-s.md)
- [`strpbrk`](../c-runtime-library/reference/strpbrk-wcspbrk-mbspbrk-mbspbrk-l.md)
- [`strspn`](../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)
- [`strstr`](../c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l.md)
- [`strtok`](../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md)
- [`strtol`](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)
- [`wcslen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)
- [`wcsnlen`](../c-runtime-library/reference/strnlen-strnlen-s.md)

### <a name="optional-interceptors"></a>선택적 인터셉터

여기에 나열 된 인터셉터는 AddressSanitizer 런타임 옵션을 사용 하도록 설정한 경우에만 설치 됩니다. `windows_hook_legacy_allocators` `true` 레거시 할당자 가로채기를 사용 하려면로 설정 합니다.
`set ASAN_OPTIONS=windows_hook_legacy_allocators=true`

- [`GlobalAlloc`](/windows/win32/api/winbase/nf-winbase-globalalloc)
- [`GlobalFree`](/windows/win32/api/winbase/nf-winbase-GlobalFree)
- [`GlobalHandle`](/windows/win32/api/winbase/nf-winbase-GlobalHandle)
- [`GlobalLock`](/windows/win32/api/winbase/nf-winbase-GlobalLock)
- [`GlobalReAlloc`](/windows/win32/api/winbase/nf-winbase-GlobalReAlloc)
- [`GlobalSize`](/windows/win32/api/winbase/nf-winbase-GlobalSize)
- [`GlobalUnlock`](/windows/win32/api/winbase/nf-winbase-GlobalUnlock)
- [`LocalAlloc`](/windows/win32/api/winbase/nf-winbase-LocalAlloc)
- [`LocalFree`](/windows/win32/api/winbase/nf-winbase-LocalFree)
- [`LocalHandle`](/windows/win32/api/winbase/nf-winbase-LocalHandle)
- [`LocalLock`](/windows/win32/api/winbase/nf-winbase-LocalLock)
- [`LocalReAlloc`](/windows/win32/api/winbase/nf-winbase-LocalReAlloc)
- [`LocalSize`](/windows/win32/api/winbase/nf-winbase-LocalSize)
- [`LocalUnlock`](/windows/win32/api/winbase/nf-winbase-LocalUnlock)

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 섀도 바이트](./asan-shadow-bytes.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
