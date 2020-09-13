---
title: ARM64 내장 함수
description: Visual Studio의 Microsoft c + + 컴파일러에서 지 원하는 ARM64 내장 함수 목록입니다.
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
helpviewer_keywords:
- __break ARM64 intrinsic
- __addx18byte ARM64 intrinsic
- __addx18word ARM64 intrinsic
- __addx18dword ARM64 intrinsic
- __addx18qword ARM64 intrinsic
- __cas8 ARM64 intrinsic
- __cas16 ARM64 intrinsic
- __cas32 ARM64 intrinsic
- __cas64 ARM64 intrinsic
- __casa8 ARM64 intrinsic
- __casa16 ARM64 intrinsic
- __casa32 ARM64 intrinsic
- __casa64 ARM64 intrinsic
- __casl8 ARM64 intrinsic
- __casl16 ARM64 intrinsic
- __casl32 ARM64 intrinsic
- __casl64 ARM64 intrinsic
- __casal8 ARM64 intrinsic
- __casal16 ARM64 intrinsic
- __casal32 ARM64 intrinsic
- __casal64 ARM64 intrinsic
- __crc32b ARM64 intrinsic
- __crc32h ARM64 intrinsic
- __crc32w ARM64 intrinsic
- __crc32d ARM64 intrinsic
- __crc32cb ARM64 intrinsic
- __crc32ch ARM64 intrinsic
- __crc32cw ARM64 intrinsic
- __crc32cd ARM64 intrinsic
- __getReg ARM64 intrinsic
- __getRegFp ARM64 intrinsic
- __getCallerReg ARM64 intrinsic
- __getCallerRegFp ARM64 intrinsic
- __hlt ARM64 intrinsic
- __incx18byte ARM64 intrinsic
- __incx18word ARM64 intrinsic
- __incx18dword ARM64 intrinsic
- __incx18qword ARM64 intrinsic
- __ldar8 ARM64 intrinsic
- __ldar16 ARM64 intrinsic
- __ldar32 ARM64 intrinsic
- __ldar64 ARM64 intrinsic
- __ldapr8 ARM64 intrinsic
- __ldapr16 ARM64 intrinsic
- __ldapr32 ARM64 intrinsic
- __ldapr64 ARM64 intrinsic
- __prefetch2 ARM64 intrinsic
- __readx18byte ARM64 intrinsic
- __readx18word ARM64 intrinsic
- __readx18dword ARM64 intrinsic
- __readx18qword ARM64 intrinsic
- __setReg ARM64 intrinsic
- __setRegFp ARM64 intrinsic
- __setCallerReg ARM64 intrinsic
- __setCallerRegFp ARM64 intrinsic
- __stlr8 ARM64 intrinsic
- __stlr16 ARM64 intrinsic
- __stlr32 ARM64 intrinsic
- __stlr64 ARM64 intrinsic
- __swp8 ARM64 intrinsic
- __swp16 ARM64 intrinsic
- __swp32 ARM64 intrinsic
- __swp64 ARM64 intrinsic
- __swpa8 ARM64 intrinsic
- __swpa16 ARM64 intrinsic
- __swpa32 ARM64 intrinsic
- __swpa64 ARM64 intrinsic
- __swpl8 ARM64 intrinsic
- __swpl16 ARM64 intrinsic
- __swpl32 ARM64 intrinsic
- __swpl64 ARM64 intrinsic
- __swpal8 ARM64 intrinsic
- __swpal16 ARM64 intrinsic
- __swpal32 ARM64 intrinsic
- __swpal64 ARM64 intrinsic
- __sys ARM64 intrinsic
- __svc ARM64 intrinsic
- __writex18byte ARM64 intrinsic
- __writex18word ARM64 intrinsic
- __writex18dword ARM64 intrinsic
- __writex18qword ARM64 intrinsic
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 13358458bf9abcf0bc6e38ca115b537abc99300a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039757"
---
# <a name="arm64-intrinsics"></a>ARM64 내장 함수

Microsoft c + + 컴파일러 (MSVC)는 ARM64 아키텍처에서 다음 내장 함수를 사용할 수 있도록 합니다. ARM에 대 한 자세한 내용은 [Arm 개발자 설명서](https://developer.arm.com/docs) 웹 사이트의 아키텍처 및 소프트웨어 개발 도구 섹션을 참조 하세요.

## <a name="neon"></a><a name="top"></a> NEON

ARM64에 대 한 NEON vector 명령 집합 확장은 SIMD (Single Instruction Multiple Data) 기능을 제공 합니다. X86 및 x64 아키텍처 프로세서에 공통적인 MMX 및 SSE 벡터 명령 집합에 있는 것과 유사 합니다.

헤더 파일 arm64_neon에 제공 된 대로 NEON 내장 함수가 지원 됩니다 *.* NEON 내장 함수에 대 한 MSVC 지원은 arm 정보 센터 웹 사이트의 [ARM NEON 내장 참조](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf) 에 설명 된 ARM64 컴파일러의 경우와 유사 합니다.

## <a name="arm64-specific-intrinsics-listing"></a><a name="A"></a> ARM64 내장 목록

|함수 이름|명령|함수 프로토타입|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int)|
|__addx18byte||void __addx18byte (부호 없는 long, 부호 없는 문자)|
|__addx18word||void __addx18word (부호 없는 long, 부호 없는 short)|
|__addx18dword||void __addx18dword (unsigned long, unsigned long)|
|__addx18qword||void __addx18qword (unsigned long, unsigned __int64)|
|__cas8|CASB|unsigned __int8 __cas8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__cas16|등록기|unsigned __int16 __cas16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__cas32|CAS|unsigned __int32 __cas32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__cas64|CAS|unsigned __int64 __cas64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casa8|CASAB|unsigned __int8 __casa8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casa16|CASAH|unsigned __int16 __casa16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casa32|CASA|unsigned __int32 __casa32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casa64|CASA|unsigned __int64 __casa64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casl8|CASLB|unsigned __int8 __casl8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casl16|CASLH|unsigned __int16 __casl16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casl32|CASL|unsigned __int32 __casl32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casl64|CASL|unsigned __int64 __casl64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__casal8|CASALB|unsigned __int8 __casal8 (unsigned __int8 volatile * _Target, unsigned __int8 _Comp, unsigned __int8 _Value)|
|__casal16|CASALH|unsigned __int16 __casal16 (unsigned __int16 volatile * _Target, unsigned __int16 _Comp, unsigned __int16 _Value)|
|__casal32|CASAL|unsigned __int32 __casal32 (unsigned __int32 volatile * _Target, unsigned __int32 _Comp, unsigned __int32 _Value)|
|__casal64|CASAL|unsigned __int64 __casal64 (unsigned __int64 volatile * _Target, unsigned __int64 _Comp, unsigned __int64 _Value)|
|__crc32b|CRC32B|unsigned __int32 __crc32b (서명 되지 않은 __int32, 부호 없는 __int32)|
|__crc32h|CRC32H|unsigned __int32 __crc32h (서명 되지 않은 __int32, 부호 없는 __int32)|
|__crc32w|CRC32W|unsigned __int32 __crc32w (서명 되지 않은 __int32, 부호 없는 __int32)|
|__crc32d|CRC32X|unsigned __int32 __crc32d (서명 되지 않은 __int32, 부호 없는 __int64)|
|__crc32cb|CRC32CB|unsigned __int32 __crc32cb (서명 되지 않은 __int32, 부호 없는 __int32)|
|__crc32ch|CRC32CH|unsigned __int32 __crc32ch (서명 되지 않은 __int32, 부호 없는 __int32)|
|__crc32cw|CRC32CW|unsigned __int32 __crc32cw (서명 되지 않은 __int32, 부호 없는 __int32)|
|__crc32cd|CRC32CX|unsigned __int32 __crc32cd (서명 되지 않은 __int32, 부호 없는 __int64)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 명령 스트림에 메모리 장벽 작업을 삽입합니다. 매개 변수 `_Type`은 장벽이 적용하는 제한의 종류를 지정 합니다.<br /><br /> 적용할 수 있는 제한의 종류에 대 한 자세한 내용은 [메모리 장벽 제한](#BarrierRestrictions)을 참조 하세요.|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 명령 스트림에 메모리 장벽 작업을 삽입합니다. 매개 변수 `_Type`은 장벽이 적용하는 제한의 종류를 지정 합니다.<br /><br /> 적용할 수 있는 제한의 종류에 대 한 자세한 내용은 [메모리 장벽 제한](#BarrierRestrictions)을 참조 하세요.|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 명령 스트림에 메모리 장벽 작업을 삽입합니다. 매개 변수 `_Type`은 장벽이 적용하는 제한의 종류를 지정 합니다.<br /><br /> 적용할 수 있는 제한의 종류에 대 한 자세한 내용은 [메모리 장벽 제한](#BarrierRestrictions)을 참조 하세요.|
|__getReg||unsigned __int64 __getReg (int)|
|__getRegFp||double __getRegFp (int)|
|__getCallerReg||unsigned __int64 __getCallerReg (int)|
|__getCallerRegFp||double __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt (unsigned int, ...)|
|__incx18byte||void __incx18byte (부호 없는 long)|
|__incx18word||void __incx18word (부호 없는 long)|
|__incx18dword||void __incx18dword (부호 없는 long)|
|__incx18qword||void __incx18qword (부호 없는 long)|
|__iso_volatile_load16||__int16 \_ _iso_volatile_load16 (const volatile \_ _int16 \* )<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_load32||__int32 \_ _iso_volatile_load32 (const volatile \_ _int32 \* )<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_load64||__int64 \_ _iso_volatile_load64 (const volatile \_ _int64 \* )<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_load8||__int8 \_ _iso_volatile_load8 (const volatile \_ _int8 \* )<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_store16||void __iso_volatile_store16 (휘발성 \_ _int16 \* , \_ _int16)<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_store32||void __iso_volatile_store32 (휘발성 \_ _int32 \* , \_ _int32)<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_store64||void __iso_volatile_store64 (휘발성 \_ _int64 \* , \_ _int64)<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__iso_volatile_store8||void __iso_volatile_store8 (휘발성 \_ _int8 \* , \_ _int8)<br /><br /> 자세한 내용은 [__iso_volatile_load/store 내장 함수](#IsoVolatileLoadStore)를 참조 하세요.|
|__ldar8|LDARB|unsigned __int8 __ldar8 (서명 되지 않은 __int8 volatile * _Target)|
|__ldar16|LDARH|unsigned __int16 __ldar16 (서명 되지 않은 __int16 volatile * _Target)|
|__ldar32|LDAR|unsigned __int32 __ldar32 (서명 되지 않은 __int32 volatile * _Target)|
|__ldar64|LDAR|unsigned __int64 __ldar64 (서명 되지 않은 __int64 volatile * _Target)|
|__ldapr8|LDAPRB|unsigned __int8 __ldapr8 (서명 되지 않은 __int8 volatile * _Target)|
|__ldapr16|LDAPRH|unsigned __int16 __ldapr16 (서명 되지 않은 __int16 volatile * _Target)|
|__ldapr32|LDAPR|unsigned __int32 __ldapr32 (서명 되지 않은 __int32 volatile * _Target)|
|__ldapr64|LDAPR|unsigned __int64 __ldapr64 (서명 되지 않은 __int64 volatile * _Target)|
|__mulh||\__int64 __mulh ( \_ _int64, \_ _int64)|
|__prefetch|PRFM|void __cdecl \_ _prefetch (const void \* )<br /><br /> `PRFM` `PLDL1KEEP` 지정 된 주소 또는 그 근처의 메모리를 곧 액세스할 수 있는 시스템의 프리페치 작업에 메모리 힌트를 제공 합니다. 일부 시스템은 런타임 성능을 향상시키기 위해 해당 메모리 액세스 패턴을 최적화하도록 선택할 수 있습니다. 그러나 C++ 언어의 관점에서 함수는 눈에 띄는 효과가 없고 아무 작업도 하지 않을 수 있습니다.|
|__prefetch2|PRFM|void __cdecl \_ _prefetch (const void \* , uint8_t prfop)<br /><br /> 지정 된 `PRFM` 주소 또는 그 근처의 메모리를 곧 액세스할 수 있는 시스템에 제공 된 프리페치 작업에 메모리 힌트를 제공 합니다. 일부 시스템은 런타임 성능을 향상시키기 위해 해당 메모리 액세스 패턴을 최적화하도록 선택할 수 있습니다. 그러나 C++ 언어의 관점에서 함수는 눈에 띄는 효과가 없고 아무 작업도 하지 않을 수 있습니다.|
|__readx18byte||unsigned char __readx18byte (부호 없는 long)|
|__readx18word||unsigned short __readx18word (unsigned long)|
|__readx18dword||unsigned long __readx18dword (부호 없는 long)|
|__readx18qword||unsigned __int64 __readx18qword (부호 없는 long)|
|__setReg||void __setReg (int, unsigned __int64)|
|__setRegFp||void __setRegFp (int, double)|
|__setCallerReg||void __setCallerReg (int, unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, double)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert (int, const char \* )|
|__stlr8|STLRB|void __stlr8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__stlr16|STLRH|void __stlr16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__stlr32|STLR|void __stlr32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__stlr64|STLR|void __stlr64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swp8|SWPB|unsigned __int8 __swp8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swp16|SWPH|unsigned __int16 __swp16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swp32|SWP|unsigned __int32 __swp32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swp64|SWP|unsigned __int64 __swp64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpa8|SWPAB|unsigned __int8 __swpa8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpa16|SWPAH|unsigned __int16 __swpa16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpa32|SWPA|unsigned __int32 __swpa32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpa64|SWPA|unsigned __int64 __swpa64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpl8|SWPLB|unsigned __int8 __swpl8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpl16|SWPLH|unsigned __int16 __swpl16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpl32|SWPL|unsigned __int32 __swpl32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpl64|SWPL|unsigned __int64 __swpl64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__swpal8|SWPALB|unsigned __int8 __swpal8 (unsigned __int8 volatile * _Target, unsigned __int8 _Value)|
|__swpal16|SWPALH|unsigned __int16 __swpal16 (unsigned __int16 volatile * _Target, unsigned __int16 _Value)|
|__swpal32|SWPAL|unsigned __int32 __swpal32 (unsigned __int32 volatile * _Target, unsigned __int32 _Value)|
|__swpal64|SWPAL|unsigned __int64 __swpal64 (unsigned __int64 volatile * _Target, unsigned __int64 _Value)|
|__sys|시스템|unsigned int __sys (int, __int64)|
|__svc|SVC|unsigned int __svc (unsigned int, ...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte (부호 없는 long, 부호 없는 문자)|
|__writex18word||void __writex18word (부호 없는 long, 부호 없는 short)|
|__writex18dword||void __writex18dword (unsigned long, unsigned long)|
|__writex18qword||void __writex18qword (unsigned long, unsigned __int64)|
|__umulh||unsigned \_ _int64 __umulh (서명 되지 않은 \_ _int64, 부호 없는 \_ _int64)|
|_CopyDoubleFromInt64||이중 _CopyDoubleFromInt64 ( \_ _int64)|
|_CopyFloatFromInt32||float _CopyFloatFromInt32 ( \_ _int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||unsigned int _CountLeadingOnes64 (unsigned \_ _int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||unsigned int _CountLeadingSigns64 ( \_ _int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||unsigned int _CountLeadingZeros64 (unsigned \_ _int64)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \_ _int64)|

[[맨 위로](#top)이동]

### <a name="memory-barrier-restrictions"></a><a name="BarrierRestrictions"></a> 메모리 장벽 제한

내장 함수 `__dmb` (데이터 메모리 장벽), `__dsb` (데이터 동기화 장벽) 및 `__isb` (명령 동기화 장벽)에서는 다음의 미리 정의 된 값을 사용 하 여 공유 도메인 및 작업의 영향을 받는 액세스의 종류를 기준으로 메모리 장벽 제한을 지정 합니다.

|제한 값|Description|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|전체 시스템, 읽기 및 쓰기|
|_ARM64_BARRIER_ST|전체 시스템, 쓰기 전용|
|_ARM64_BARRIER_LD|전체 시스템, 읽기 전용|
|_ARM64_BARRIER_ISH|내부 공유 가능, 읽기 및 쓰기|
|_ARM64_BARRIER_ISHST|내부 공유 가능, 쓰기 전용|
|_ARM64_BARRIER_ISHLD|내부 공유 가능, 읽기 전용|
|_ARM64_BARRIER_NSH|공유 불가, 읽기 및 쓰기|
|_ARM64_BARRIER_NSHST|공유 불가, 쓰기 전용|
|_ARM64_BARRIER_NSHLD|공유 불가능, 읽기 전용입니다.|
|_ARM64_BARRIER_OSH|외부 공유 가능, 읽기 및 쓰기|
|_ARM64_BARRIER_OSHST|외부 공유 가능, 쓰기 전용|
|_ARM64_BARRIER_OSHLD|외부 공유 가능, 읽기 전용|

`__isb`내장 함수에서는 현재 유효한 제한만 _ARM64_BARRIER_SY 되며 다른 모든 값은 아키텍처에서 예약 됩니다.

### <a name="__iso_volatile_loadstore-intrinsics"></a><a name="IsoVolatileLoadStore"></a> __iso_volatile_load/store 내장 함수

이러한 내장 함수는 컴파일러 최적화가 적용 되지 않는 로드 및 저장소를 명시적으로 수행 합니다.

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>매개 변수

*위치*\
읽거나 쓸 메모리 위치의 주소입니다.

*Value*\
지정 된 메모리 위치에 쓸 값입니다 (매장 내장 함수에만 해당).

#### <a name="return-value-load-intrinsics-only"></a>반환 값 (load 내장 함수 전용)

*위치*에 지정 된 메모리 위치의 값입니다.

#### <a name="remarks"></a>설명

`__iso_volatile_load8/16/32/64`및 내장 함수를 사용 `__iso_volatile_store8/16/32/64` 하 여 컴파일러 최적화가 적용 되지 않는 메모리 액세스를 명시적으로 수행할 수 있습니다. 컴파일러는 이러한 작업의 상대적 순서를 제거 하거나, sya tize를 제거 하거나, 변경할 수 없습니다. 그러나 암시적 하드웨어 메모리 장벽을 생성 하지 않습니다. 따라서 하드웨어는 여러 스레드 간의 식별할 수 있는 메모리 액세스를 여전히 다시 정렬할 수 있습니다. 보다 정확 하 게 말하자면 이러한 내장 함수는 **/volatile: iso**에서 컴파일된 다음 식과 같습니다.

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

내장 함수가 휘발성 포인터를 취하여 휘발성 변수를 수용합니다. 그러나 휘발성 포인터를 인수로 사용 하는 것은 요구 사항이 나 권장 사항이 없습니다. 이러한 작업의 의미 체계는 보통 비휘발성 형식이 사용 되는 경우와 동일 합니다.

**/Volatile: iso** 명령줄 인수에 대 한 자세한 내용은 [/volatile (volatile 키워드 해석)](../build/reference/volatile-volatile-keyword-interpretation.md)를 참조 하세요.

## <a name="arm64-support-for-intrinsics-from-other-architectures"></a><a name="I"></a> 다른 아키텍처의 내장 함수에 대 한 ARM64 지원

다음 표에서는 ARM64 플랫폼에서 지원 되는 다른 아키텍처의 내장 함수를 보여 줍니다. ARM64에 내장 된의 동작이 다른 하드웨어 아키텍처의 동작과 다른 경우 추가 세부 정보가 표시 됩니다.

|함수 이름|함수 프로토타입|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \* )|
|__debugbreak|void (void __cdecl \_ _debugbreak (void)|
|__fastfail|__declspec (noreturn) void \_ _fastfail (부호 없는 정수)|
|__nop|void __nop(void)|
|__yield|void __yield (void) **참고:**  ARM64 플랫폼에서이 함수는 yield 명령을 생성 합니다. 이 명령은 스레드가 프로그램에 부정적인 영향을 주지 않고 일시적으로 실행에서 일시 중단 될 수 있는 작업 (예: spinlock)을 수행 하 고 있음을 나타냅니다. 이렇게 하면 CPU가 실행 주기 동안 다른 작업을 실행할 수 있습니다.|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|unsigned char _BitScanForward (unsigned long \* _Index, unsigned long _Mask)|
|_BitScanForward64|unsigned char _BitScanForward64 (unsigned long \* _Index, unsigned __int64 _Mask)|
|_BitScanReverse|unsigned char _BitScanReverse (unsigned long \* _Index, unsigned long _Mask)|
|_BitScanReverse64|unsigned char _BitScanReverse64 (unsigned long \* _Index, unsigned __int64 _Mask)|
|_bittest|unsigned char _bittest (long const \* , long)|
|_bittest64|unsigned char _bittest64 (__int64 const \* , __int64)|
|_bittestandcomplement|unsigned char _bittestandcomplement (long \* , long)|
|_bittestandcomplement64|unsigned char _bittestandcomplement64 (__int64 \* , __int64)|
|_bittestandreset|unsigned char _bittestandreset (long \* , long)|
|_bittestandreset64|unsigned char _bittestandreset64 (__int64 \* , __int64)|
|_bittestandset|unsigned char _bittestandset (long \* , long)|
|_bittestandset64|unsigned char _bittestandset64 (__int64 \* , __int64)|
|_byteswap_uint64|unsigned __int64 \_ _cdecl _byteswap_uint64 (부호 없는 \_ _int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable (void) **참고:**  ARM64 플랫폼에서이 함수는 명령을 생성 하며 `MSR DAIFCLR,#2` 내장 함수로만 사용할 수 있습니다.|
|_enable|void __cdecl _enable (void) **참고:**  ARM64 플랫폼에서이 함수는 명령을 생성 하며 `MSR DAIFSET,#2` 내장 함수로만 사용할 수 있습니다.|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|unsigned __int64 \_ _cdecl _rotl64 (unsigned \_ _int64 _Value, int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|unsigned __int64 \_ _cdecl _rotr64 (unsigned \_ _int64 _Value, int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[맨 위로](#top)이동]

## <a name="interlocked-intrinsics"></a>연동 내장 함수

Interlocked 내장 함수는 원자성 읽기-수정-쓰기 작업을 수행하는데 사용되는 내장 함수 집합입니다. 일부 내장 함수는 모든 플랫폼에 공통적입니다. 많은 수가 있으므로 여기에 별도로 나열 됩니다. 해당 정의는 대체로 중복 되기 때문에 일반적인 용어로 생각 하는 것이 더 쉽습니다. 내장 함수의 이름을 사용해 정확한 동작을 파악할 수 있습니다.

다음 표에는 비 bittest 연동 내장 함수에 대 한 ARM64 지원이 요약 되어 있습니다. 테이블의 각 셀은 `_Interlocked`에 행의 가장 왼쪽 셀에 작업 이름 및 열의 맨 위 셀에 형식 이름을 추가하여 파생된 이름을 뜻합니다. 예를 들어 행과 열이 교차 하는 셀은 `Xor` `8` 에 해당 하 `_InterlockedXor8` 고 완전 하 게 지원 됩니다. 대부분의 지원되는 함수에는 옵션 접미사 `_acq`, `_rel`, 및 `_nf`가 제공됩니다. `_acq` 접미사는 "acquire" 의미를 나타내며 `_rel` 접미사는 "release" 의미를 나타냅니다. `_nf`또는 "no fence" 접미사는 ARM 및 ARM64에 고유 하며 다음 섹션에서 설명 합니다.

|작업(Operation)|8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|추가|없음|없음|전체|전체|없음|없음|
|and|전체|전체|전체|전체|없음|없음|
|CompareExchange|전체|전체|전체|전체|전체|전체|
|감소|없음|전체|전체|전체|없음|없음|
|Exchange|전체|전체|전체|전체|없음|전체|
|ExchangeAdd|전체|전체|전체|전체|없음|없음|
|ID 증가값|없음|전체|전체|전체|없음|없음|
|Or|전체|전체|전체|전체|없음|없음|
|Xor|전체|전체|전체|전체|없음|없음|

키:

- **Full**: 일반,, `_acq` `_rel` 및 양식을 지원 `_nf` 합니다.

- **없음**: 지원 되지 않음

### <a name="_nf-no-fence-suffix"></a><a name="nf_suffix"></a> _nf (fence 없음) 접미사

`_nf`또는 "no fence" 접미사는 다른 세 가지 형태 (일반, 및)와는 달리 작업을 일종의 장벽으로 작동 하지 않음을 나타냅니다 `_acq` `_rel` . 한 가지 가능한 형태는 `_nf` 여러 스레드에서 동시에 업데이트 되는 통계 카운터를 유지 관리 하는 것입니다. 하지만 여러 스레드가 실행 되는 동안에는 해당 값을 사용 하지 않습니다.

### <a name="list-of-interlocked-intrinsics"></a>연동 내장 함수 목록

|함수 이름|함수 프로토타입|
|-------------------|------------------------|
|_InterlockedAdd|long _InterlockedAdd (long _volatile \* , long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAdd_acq|long _InterlockedAdd_acq (long volatile \* , long)|
|_InterlockedAdd_nf|long _InterlockedAdd_nf (long volatile \* , long)|
|_InterlockedAdd_rel|long _InterlockedAdd_rel (long volatile \* , long)|
|_InterlockedAnd|long _InterlockedAnd (long volatile \* , long)|
|_InterlockedAnd16|short _InterlockedAnd16 (짧은 휘발성 \* , short)|
|_InterlockedAnd16_acq|short _InterlockedAnd16_acq (짧은 휘발성 \* , short)|
|_InterlockedAnd16_nf|short _InterlockedAnd16_nf (짧은 휘발성 \* , short)|
|_InterlockedAnd16_rel|short _InterlockedAnd16_rel (짧은 휘발성 \* , short)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedAnd8|문자 _InterlockedAnd8 (문자 휘발성 \* , 문자)|
|_InterlockedAnd8_acq|문자 _InterlockedAnd8_acq (문자 휘발성 \* , 문자)|
|_InterlockedAnd8_nf|문자 _InterlockedAnd8_nf (문자 휘발성 \* , 문자)|
|_InterlockedAnd8_rel|문자 _InterlockedAnd8_rel (문자 휘발성 \* , 문자)|
|_InterlockedAnd_acq|long _InterlockedAnd_acq (long volatile \* , long)|
|_InterlockedAnd_nf|long _InterlockedAnd_nf (long volatile \* , long)|
|_InterlockedAnd_rel|long _InterlockedAnd_rel (long volatile \* , long)|
|_InterlockedCompareExchange|long __cdecl _InterlockedCompareExchange (long volatile \* , long, long)|
|_InterlockedCompareExchange_acq|long _InterlockedCompareExchange_acq (long volatile \* , long, long)|
|_InterlockedCompareExchange_nf|long _InterlockedCompareExchange_nf (long volatile \* , long, long)|
|_InterlockedCompareExchange_rel|long _InterlockedCompareExchange_rel (long volatile \* , long, long)|
|_InterlockedCompareExchange16|short _InterlockedCompareExchange16 (짧은 volatile \* , short, short)|
|_InterlockedCompareExchange16_acq|short _InterlockedCompareExchange16_acq (짧은 volatile \* , short, short)|
|_InterlockedCompareExchange16_nf|short _InterlockedCompareExchange16_nf (짧은 volatile \* , short, short)|
|_InterlockedCompareExchange16_rel|short _InterlockedCompareExchange16_rel (짧은 volatile \* , short, short)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel ( \_ _int64 volatile \* , \_ _int64, \_ _int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char volatile \* , char, char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char volatile \* , char, char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (char volatile \* , char, char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (char volatile \* , char, char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \* , void \* , void \* )|
|_InterlockedCompareExchange128|unsigned char _InterlockedCompareExchange128 ( \_ _int64 휘발성 \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 \_ _ExchangeLow _int64 \* )|
|_InterlockedCompareExchange128_acq|unsigned char _InterlockedCompareExchange128_acq ( \_ _int64 휘발성 \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 \_ _ExchangeLow _int64 \* )|
|_InterlockedCompareExchange128_nf|unsigned char _InterlockedCompareExchange128_nf ( \_ _int64 휘발성 \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 \_ _ExchangeLow _int64 \* )|
|_InterlockedCompareExchange128_rel|unsigned char _InterlockedCompareExchange128_rel ( \_ _int64 휘발성 \* _Destination, \_ _int64 _ExchangeHigh, \_ _int64 \_ _ExchangeLow _int64 \* )|
|_InterlockedDecrement|long __cdecl _InterlockedDecrement (긴 휘발성 \* )|
|_InterlockedDecrement16|short _InterlockedDecrement16 (짧은 휘발성 \* )|
|_InterlockedDecrement16_acq|short _InterlockedDecrement16_acq (짧은 휘발성 \* )|
|_InterlockedDecrement16_nf|short _InterlockedDecrement16_nf (짧은 휘발성 \* )|
|_InterlockedDecrement16_rel|short _InterlockedDecrement16_rel (짧은 휘발성 \* )|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf ( \_ _int64 volatile \* )|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel ( \_ _int64 volatile \* )|
|_InterlockedDecrement_acq|long _InterlockedDecrement_acq (긴 휘발성 \* )|
|_InterlockedDecrement_nf|long _InterlockedDecrement_nf (긴 휘발성 \* )|
|_InterlockedDecrement_rel|long _InterlockedDecrement_rel (긴 휘발성 \* )|
|_InterlockedExchange|long __cdecl _InterlockedExchange (long 휘발성 \* _Target, long)|
|_InterlockedExchange_acq|long _InterlockedExchange_acq (긴 휘발성 \* _Target, long)|
|_InterlockedExchange_nf|long _InterlockedExchange_nf (긴 휘발성 \* _Target, long)|
|_InterlockedExchange_rel|long _InterlockedExchange_rel (긴 휘발성 \* _Target, long)|
|_InterlockedExchange16|short _InterlockedExchange16 (short volatile \* _Target, short)|
|_InterlockedExchange16_acq|short _InterlockedExchange16_acq (short volatile \* _Target, short)|
|_InterlockedExchange16_nf|short _InterlockedExchange16_nf (short volatile \* _Target, short)|
|_InterlockedExchange16_rel|short _InterlockedExchange16_rel (short volatile \* _Target, short)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 ( \_ _int64 휘발성 \* _Target, \_ _int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq ( \_ _int64 휘발성 \* _Target, \_ _int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf ( \_ _int64 휘발성 \* _Target, \_ _int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel ( \_ _int64 휘발성 \* _Target, \_ _int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char volatile \* _Target, char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char volatile \* _Target, char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char volatile \* _Target, char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char volatile \* _Target, char)|
|_InterlockedExchangeAdd|long __cdecl _InterlockedExchangeAdd (long 휘발성 \* , long)|
|_InterlockedExchangeAdd16|short _InterlockedExchangeAdd16 (짧은 휘발성 \* , short)|
|_InterlockedExchangeAdd16_acq|short _InterlockedExchangeAdd16_acq (짧은 휘발성 \* , short)|
|_InterlockedExchangeAdd16_nf|short _InterlockedExchangeAdd16_nf (짧은 휘발성 \* , short)|
|_InterlockedExchangeAdd16_rel|short _InterlockedExchangeAdd16_rel (짧은 휘발성 \* , short)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedExchangeAdd8|문자 _InterlockedExchangeAdd8 (문자 휘발성 \* , 문자)|
|_InterlockedExchangeAdd8_acq|문자 _InterlockedExchangeAdd8_acq (문자 휘발성 \* , 문자)|
|_InterlockedExchangeAdd8_nf|문자 _InterlockedExchangeAdd8_nf (문자 휘발성 \* , 문자)|
|_InterlockedExchangeAdd8_rel|문자 _InterlockedExchangeAdd8_rel (문자 휘발성 \* , 문자)|
|_InterlockedExchangeAdd_acq|long _InterlockedExchangeAdd_acq (long volatile \* , long)|
|_InterlockedExchangeAdd_nf|long _InterlockedExchangeAdd_nf (long volatile \* , long)|
|_InterlockedExchangeAdd_rel|long _InterlockedExchangeAdd_rel (long volatile \* , long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _Target, void \* )|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* _Target, void \* )|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _Target, void \* )|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* _Target, void \* )|
|_InterlockedIncrement|long __cdecl _InterlockedIncrement (긴 휘발성 \* )|
|_InterlockedIncrement16|short _InterlockedIncrement16 (짧은 휘발성 \* )|
|_InterlockedIncrement16_acq|short _InterlockedIncrement16_acq (짧은 휘발성 \* )|
|_InterlockedIncrement16_nf|short _InterlockedIncrement16_nf (짧은 휘발성 \* )|
|_InterlockedIncrement16_rel|short _InterlockedIncrement16_rel (짧은 휘발성 \* )|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf ( \_ _int64 volatile \* )|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel ( \_ _int64 volatile \* )|
|_InterlockedIncrement_acq|long _InterlockedIncrement_acq (긴 휘발성 \* )|
|_InterlockedIncrement_nf|long _InterlockedIncrement_nf (긴 휘발성 \* )|
|_InterlockedIncrement_rel|long _InterlockedIncrement_rel (긴 휘발성 \* )|
|_InterlockedOr|long _InterlockedOr (long volatile \* , long)|
|_InterlockedOr16|short _InterlockedOr16 (짧은 휘발성 \* , short)|
|_InterlockedOr16_acq|short _InterlockedOr16_acq (짧은 휘발성 \* , short)|
|_InterlockedOr16_nf|short _InterlockedOr16_nf (짧은 휘발성 \* , short)|
|_InterlockedOr16_rel|short _InterlockedOr16_rel (짧은 휘발성 \* , short)|
|_InterlockedOr64|__int64 _InterlockedOr64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedOr8|문자 _InterlockedOr8 (문자 휘발성 \* , 문자)|
|_InterlockedOr8_acq|문자 _InterlockedOr8_acq (문자 휘발성 \* , 문자)|
|_InterlockedOr8_nf|문자 _InterlockedOr8_nf (문자 휘발성 \* , 문자)|
|_InterlockedOr8_rel|문자 _InterlockedOr8_rel (문자 휘발성 \* , 문자)|
|_InterlockedOr_acq|long _InterlockedOr_acq (long volatile \* , long)|
|_InterlockedOr_nf|long _InterlockedOr_nf (long volatile \* , long)|
|_InterlockedOr_rel|long _InterlockedOr_rel (long volatile \* , long)|
|_InterlockedXor|long _InterlockedXor (long volatile \* , long)|
|_InterlockedXor16|short _InterlockedXor16 (짧은 휘발성 \* , short)|
|_InterlockedXor16_acq|short _InterlockedXor16_acq (짧은 휘발성 \* , short)|
|_InterlockedXor16_nf|short _InterlockedXor16_nf (짧은 휘발성 \* , short)|
|_InterlockedXor16_rel|short _InterlockedXor16_rel (짧은 휘발성 \* , short)|
|_InterlockedXor64|__int64 _InterlockedXor64 ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel ( \_ _int64 volatile \* , \_ _int64)|
|_InterlockedXor8|문자 _InterlockedXor8 (문자 휘발성 \* , 문자)|
|_InterlockedXor8_acq|문자 _InterlockedXor8_acq (문자 휘발성 \* , 문자)|
|_InterlockedXor8_nf|문자 _InterlockedXor8_nf (문자 휘발성 \* , 문자)|
|_InterlockedXor8_rel|문자 _InterlockedXor8_rel (문자 휘발성 \* , 문자)|
|_InterlockedXor_acq|long _InterlockedXor_acq (long volatile \* , long)|
|_InterlockedXor_nf|long _InterlockedXor_nf (long volatile \* , long)|
|_InterlockedXor_rel|long _InterlockedXor_rel (long volatile \* , long)|

[[맨 위로](#top)이동]

### <a name="_interlockedbittest-intrinsics"></a>_interlockedbittest 내장 함수

일반 연동 비트 테스트 내장 함수는 모든 플랫폼에 공통적입니다. ARM64는 `_acq` , `_rel` 및 `_nf` 변형을 추가 합니다 .이는이 문서의 앞부분에 있는 [_nf (fence 없음) 접미사](#nf_suffix) 에 설명 된 대로 작업의 장애물 의미 체계를 수정 합니다.

|함수 이름|함수 프로토타입|
|-------------------|------------------------|
|_interlockedbittestandreset|unsigned char _interlockedbittestandreset (long volatile \* , long)|
|_interlockedbittestandreset_acq|unsigned char _interlockedbittestandreset_acq (long volatile \* , long)|
|_interlockedbittestandreset_nf|unsigned char _interlockedbittestandreset_nf (long volatile \* , long)|
|_interlockedbittestandreset_rel|unsigned char _interlockedbittestandreset_rel (long volatile \* , long)|
|_interlockedbittestandreset64|unsigned char _interlockedbittestandreset64 (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_acq|unsigned char _interlockedbittestandreset64_acq (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_nf|unsigned char _interlockedbittestandreset64_nf (__int64 volatile \* , __int64)|
|_interlockedbittestandreset64_rel|unsigned char _interlockedbittestandreset64_rel (__int64 volatile \* , __int64)|
|_interlockedbittestandset|unsigned char _interlockedbittestandset (long volatile \* , long)|
|_interlockedbittestandset_acq|unsigned char _interlockedbittestandset_acq (long volatile \* , long)|
|_interlockedbittestandset_nf|unsigned char _interlockedbittestandset_nf (long volatile \* , long)|
|_interlockedbittestandset_rel|unsigned char _interlockedbittestandset_rel (long volatile \* , long)|
|_interlockedbittestandset64|unsigned char _interlockedbittestandset64 (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_acq|unsigned char _interlockedbittestandset64_acq (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_nf|unsigned char _interlockedbittestandset64_nf (__int64 volatile \* , __int64)|
|_interlockedbittestandset64_rel|unsigned char _interlockedbittestandset64_rel (__int64 volatile \* , __int64)|

[[맨 위로](#top)이동]

## <a name="see-also"></a>참고 항목

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)\
[ARM 내장 함수](arm-intrinsics.md)\
[ARM 어셈블러 참조](../assembler/arm/arm-assembler-reference.md)\
[C + + 언어 참조](../cpp/cpp-language-reference.md)
