---
description: '자세히 알아보기: __cpuid, __cpuidex'
title: __cpuid, __cpuidex
ms.date: 09/02/2019
f1_keywords:
- __cpuid_cpp
- __cpuid
helpviewer_keywords:
- __cpuid intrinsic
- cpuid instruction
- cpuid intrinsic
ms.assetid: f8c344d3-91bf-405f-8622-cb0e337a6bdc
ms.openlocfilehash: 1f3030cc3792911cec8e7a7ef1b17dab0a9a3d6b
ms.sourcegitcommit: 3987d9c39f5a5b4824303a48a6215984ce8949e8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99478138"
---
# <a name="__cpuid-__cpuidex"></a>__cpuid, __cpuidex

**Microsoft 전용**

`cpuid`X86 및 x 64에서 사용할 수 있는 명령을 생성 합니다. 이 명령은 지원되는 기능 및 CPU 형식에 대한 정보의 프로세서를 쿼리합니다.

## <a name="syntax"></a>구문

```C
void __cpuid(
   int cpuInfo[4],
   int function_id
);

void __cpuidex(
   int cpuInfo[4],
   int function_id,
   int subfunction_id
);
```

### <a name="parameters"></a>매개 변수

*cpuInfo*\
제한이 EAX, EBX, ECX 및 EDX에서 반환 된 CPU의 지원 되는 기능에 대 한 정보를 포함 하는 네 개의 정수로 이루어진 배열입니다.

*function_id*\
진행 검색할 정보를 지정 하 고 EAX에 전달 되는 코드입니다.

*subfunction_id*\
진행 검색할 정보를 지정 하 고 ECX로 전달 되는 추가 코드입니다.

## <a name="requirements"></a>요구 사항

|Intrinsic|Architecture|
|---------------|------------------|
|`__cpuid`|x86, x64|
|`__cpuidex`|x86, x64|

**헤더 파일** \<intrin.h>

## <a name="remarks"></a>설명

이 내장 함수는 CpuInfo의 명령에 의해 반환 되는 지원 되는 기능 및 CPU 정보를 저장 합니다. 여기에는 `cpuid` EAX, EBX, ECX 및 EDX 레지스터의 값으로 채워진 4 32 비트 정수의 배열이 해당 순서 대로 저장 됩니다.  반환 되는 정보는 *function_id* 매개 변수로 전달 된 값에 따라 의미가 다릅니다. *Function_id* 의 다양 한 값으로 반환 되는 정보는 프로세서에 따라 다릅니다.

`__cpuid` 내장 함수는 `cpuid` 명령을 호출하기 전에 ECX 레지스터를 지웁니다. `__cpuidex`내장 함수는 명령을 생성 하기 전에 *subfunction_id* 에 대 한 ECX 레지스터의 값을 설정 합니다 `cpuid` . 이를 통해 프로세서에 대 한 추가 정보를 수집할 수 있습니다.

Intel 프로세서에서 사용할 특정 매개 변수 및 이러한 내장 함수에서 반환 되는 값에 대 한 자세한 내용은 `cpuid` [intel 64 및 IA-32 아키텍처 소프트웨어 개발자 수동 볼륨 2: 명령 집합 참조](https://go.microsoft.com/fwlink/p/?LinkID=510021) 및 [Intel 아키텍처 명령 집합 확장 프로그래밍 참조](https://software.intel.com/content/www/us/en/develop/download/intel-architecture-instruction-set-extensions-programming-reference.html)의 지침 설명서를 참조 하세요. Intel 설명서는 *function_id* 에 "리프" 및 "subleaf" 라는 용어를 사용 하 고 EAX 및 ECX에 전달 된 매개 변수를 *subfunction_id* 합니다.

사용할 특정 매개 변수와 AMD 프로세서의 이러한 내장 함수에서 반환 되는 값에 대 한 자세한 내용은 `cpuid` AMD64 아키텍처 프로그래머의 수동 볼륨 3: General-Purpose 및 시스템 지침 및 특정 프로세서 제품군에 대 한 수정 가이드에서 지침에 대 한 설명서를 참조 하세요. 이러한 문서 및 기타 정보에 대 한 링크는 AMD [개발자 가이드, 설명서 & ISA 문서](https://go.microsoft.com/fwlink/p/?LinkId=510023) 페이지를 참조 하세요. AMD 설명서는 *function_id* 에 "function number" 및 "subfunction number" 라는 용어를 사용 하 고 EAX 및 ECX에 전달 된 매개 변수를 *subfunction_id* 합니다.

*Function_id* 인수가 0 인 경우 *cpuInfo*[0]은 프로세서에서 지 원하는 사용 가능한 가장 높은 확장 되지 않은 *function_id* 값을 반환 합니다. 프로세서 제조업체는 *cpuInfo*[1], *cpuInfo*[2] 및 *cpuInfo*[3]로 인코딩됩니다.

특정 명령 집합 확장 및 CPU 기능에 대 한 지원은 상위 *function_id* 값에 대해 반환 된 *cpuInfo* 결과에서 인코딩됩니다. 자세한 내용은 위에 링크되어 있는 설명서와 다음 예제 코드를 참조하세요.

일부 프로세서에서는 확장 함수 CPUID 정보를 지원합니다. 지원 되는 경우 0x80000000의 *function_id* 값을 사용 하 여 정보를 반환할 수 있습니다. 허용 되는 최대 의미 값을 확인 하려면 *function_id* 를 0x80000000로 설정 합니다. 확장 함수에 지원 되는 *function_id* 의 최대값은 *cpuInfo*[0]에 기록 됩니다.

## <a name="example"></a>예제

이 예제에서는 `__cpuid` 및 `__cpuidex` 내장 함수를 통해 제공되는 일부 정보를 보여 줍니다. 앱은 현재 프로세서가 지원하는 명령 집합 확장을 나열합니다. 출력에는 특정 프로세서에 대해 반환될 수 있는 결과가 표시됩니다.

```cpp
// InstructionSet.cpp
// Compile by using: cl /EHsc /W4 InstructionSet.cpp
// processor: x86, x64
// Uses the __cpuid intrinsic to get information about
// CPU extended instruction set support.

#include <iostream>
#include <vector>
#include <bitset>
#include <array>
#include <string>
#include <intrin.h>

class InstructionSet
{
    // forward declarations
    class InstructionSet_Internal;

public:
    // getters
    static std::string Vendor(void) { return CPU_Rep.vendor_; }
    static std::string Brand(void) { return CPU_Rep.brand_; }

    static bool SSE3(void) { return CPU_Rep.f_1_ECX_[0]; }
    static bool PCLMULQDQ(void) { return CPU_Rep.f_1_ECX_[1]; }
    static bool MONITOR(void) { return CPU_Rep.f_1_ECX_[3]; }
    static bool SSSE3(void) { return CPU_Rep.f_1_ECX_[9]; }
    static bool FMA(void) { return CPU_Rep.f_1_ECX_[12]; }
    static bool CMPXCHG16B(void) { return CPU_Rep.f_1_ECX_[13]; }
    static bool SSE41(void) { return CPU_Rep.f_1_ECX_[19]; }
    static bool SSE42(void) { return CPU_Rep.f_1_ECX_[20]; }
    static bool MOVBE(void) { return CPU_Rep.f_1_ECX_[22]; }
    static bool POPCNT(void) { return CPU_Rep.f_1_ECX_[23]; }
    static bool AES(void) { return CPU_Rep.f_1_ECX_[25]; }
    static bool XSAVE(void) { return CPU_Rep.f_1_ECX_[26]; }
    static bool OSXSAVE(void) { return CPU_Rep.f_1_ECX_[27]; }
    static bool AVX(void) { return CPU_Rep.f_1_ECX_[28]; }
    static bool F16C(void) { return CPU_Rep.f_1_ECX_[29]; }
    static bool RDRAND(void) { return CPU_Rep.f_1_ECX_[30]; }

    static bool MSR(void) { return CPU_Rep.f_1_EDX_[5]; }
    static bool CX8(void) { return CPU_Rep.f_1_EDX_[8]; }
    static bool SEP(void) { return CPU_Rep.f_1_EDX_[11]; }
    static bool CMOV(void) { return CPU_Rep.f_1_EDX_[15]; }
    static bool CLFSH(void) { return CPU_Rep.f_1_EDX_[19]; }
    static bool MMX(void) { return CPU_Rep.f_1_EDX_[23]; }
    static bool FXSR(void) { return CPU_Rep.f_1_EDX_[24]; }
    static bool SSE(void) { return CPU_Rep.f_1_EDX_[25]; }
    static bool SSE2(void) { return CPU_Rep.f_1_EDX_[26]; }

    static bool FSGSBASE(void) { return CPU_Rep.f_7_EBX_[0]; }
    static bool BMI1(void) { return CPU_Rep.f_7_EBX_[3]; }
    static bool HLE(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_7_EBX_[4]; }
    static bool AVX2(void) { return CPU_Rep.f_7_EBX_[5]; }
    static bool BMI2(void) { return CPU_Rep.f_7_EBX_[8]; }
    static bool ERMS(void) { return CPU_Rep.f_7_EBX_[9]; }
    static bool INVPCID(void) { return CPU_Rep.f_7_EBX_[10]; }
    static bool RTM(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_7_EBX_[11]; }
    static bool AVX512F(void) { return CPU_Rep.f_7_EBX_[16]; }
    static bool RDSEED(void) { return CPU_Rep.f_7_EBX_[18]; }
    static bool ADX(void) { return CPU_Rep.f_7_EBX_[19]; }
    static bool AVX512PF(void) { return CPU_Rep.f_7_EBX_[26]; }
    static bool AVX512ER(void) { return CPU_Rep.f_7_EBX_[27]; }
    static bool AVX512CD(void) { return CPU_Rep.f_7_EBX_[28]; }
    static bool SHA(void) { return CPU_Rep.f_7_EBX_[29]; }

    static bool PREFETCHWT1(void) { return CPU_Rep.f_7_ECX_[0]; }

    static bool LAHF(void) { return CPU_Rep.f_81_ECX_[0]; }
    static bool LZCNT(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_ECX_[5]; }
    static bool ABM(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[5]; }
    static bool SSE4a(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[6]; }
    static bool XOP(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[11]; }
    static bool TBM(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[21]; }

    static bool SYSCALL(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_EDX_[11]; }
    static bool MMXEXT(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[22]; }
    static bool RDTSCP(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_EDX_[27]; }
    static bool _3DNOWEXT(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[30]; }
    static bool _3DNOW(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[31]; }

private:
    static const InstructionSet_Internal CPU_Rep;

    class InstructionSet_Internal
    {
    public:
        InstructionSet_Internal()
            : nIds_{ 0 },
            nExIds_{ 0 },
            isIntel_{ false },
            isAMD_{ false },
            f_1_ECX_{ 0 },
            f_1_EDX_{ 0 },
            f_7_EBX_{ 0 },
            f_7_ECX_{ 0 },
            f_81_ECX_{ 0 },
            f_81_EDX_{ 0 },
            data_{},
            extdata_{}
        {
            //int cpuInfo[4] = {-1};
            std::array<int, 4> cpui;

            // Calling __cpuid with 0x0 as the function_id argument
            // gets the number of the highest valid function ID.
            __cpuid(cpui.data(), 0);
            nIds_ = cpui[0];

            for (int i = 0; i <= nIds_; ++i)
            {
                __cpuidex(cpui.data(), i, 0);
                data_.push_back(cpui);
            }

            // Capture vendor string
            char vendor[0x20];
            memset(vendor, 0, sizeof(vendor));
            *reinterpret_cast<int*>(vendor) = data_[0][1];
            *reinterpret_cast<int*>(vendor + 4) = data_[0][3];
            *reinterpret_cast<int*>(vendor + 8) = data_[0][2];
            vendor_ = vendor;
            if (vendor_ == "GenuineIntel")
            {
                isIntel_ = true;
            }
            else if (vendor_ == "AuthenticAMD")
            {
                isAMD_ = true;
            }

            // load bitset with flags for function 0x00000001
            if (nIds_ >= 1)
            {
                f_1_ECX_ = data_[1][2];
                f_1_EDX_ = data_[1][3];
            }

            // load bitset with flags for function 0x00000007
            if (nIds_ >= 7)
            {
                f_7_EBX_ = data_[7][1];
                f_7_ECX_ = data_[7][2];
            }

            // Calling __cpuid with 0x80000000 as the function_id argument
            // gets the number of the highest valid extended ID.
            __cpuid(cpui.data(), 0x80000000);
            nExIds_ = cpui[0];

            char brand[0x40];
            memset(brand, 0, sizeof(brand));

            for (int i = 0x80000000; i <= nExIds_; ++i)
            {
                __cpuidex(cpui.data(), i, 0);
                extdata_.push_back(cpui);
            }

            // load bitset with flags for function 0x80000001
            if (nExIds_ >= 0x80000001)
            {
                f_81_ECX_ = extdata_[1][2];
                f_81_EDX_ = extdata_[1][3];
            }

            // Interpret CPU brand string if reported
            if (nExIds_ >= 0x80000004)
            {
                memcpy(brand, extdata_[2].data(), sizeof(cpui));
                memcpy(brand + 16, extdata_[3].data(), sizeof(cpui));
                memcpy(brand + 32, extdata_[4].data(), sizeof(cpui));
                brand_ = brand;
            }
        };

        int nIds_;
        int nExIds_;
        std::string vendor_;
        std::string brand_;
        bool isIntel_;
        bool isAMD_;
        std::bitset<32> f_1_ECX_;
        std::bitset<32> f_1_EDX_;
        std::bitset<32> f_7_EBX_;
        std::bitset<32> f_7_ECX_;
        std::bitset<32> f_81_ECX_;
        std::bitset<32> f_81_EDX_;
        std::vector<std::array<int, 4>> data_;
        std::vector<std::array<int, 4>> extdata_;
    };
};

// Initialize static member data
const InstructionSet::InstructionSet_Internal InstructionSet::CPU_Rep;

// Print out supported instruction set extensions
int main()
{
    auto& outstream = std::cout;

    auto support_message = [&outstream](std::string isa_feature, bool is_supported) {
        outstream << isa_feature << (is_supported ? " supported" : " not supported") << std::endl;
    };

    std::cout << InstructionSet::Vendor() << std::endl;
    std::cout << InstructionSet::Brand() << std::endl;

    support_message("3DNOW",       InstructionSet::_3DNOW());
    support_message("3DNOWEXT",    InstructionSet::_3DNOWEXT());
    support_message("ABM",         InstructionSet::ABM());
    support_message("ADX",         InstructionSet::ADX());
    support_message("AES",         InstructionSet::AES());
    support_message("AVX",         InstructionSet::AVX());
    support_message("AVX2",        InstructionSet::AVX2());
    support_message("AVX512CD",    InstructionSet::AVX512CD());
    support_message("AVX512ER",    InstructionSet::AVX512ER());
    support_message("AVX512F",     InstructionSet::AVX512F());
    support_message("AVX512PF",    InstructionSet::AVX512PF());
    support_message("BMI1",        InstructionSet::BMI1());
    support_message("BMI2",        InstructionSet::BMI2());
    support_message("CLFSH",       InstructionSet::CLFSH());
    support_message("CMPXCHG16B",  InstructionSet::CMPXCHG16B());
    support_message("CX8",         InstructionSet::CX8());
    support_message("ERMS",        InstructionSet::ERMS());
    support_message("F16C",        InstructionSet::F16C());
    support_message("FMA",         InstructionSet::FMA());
    support_message("FSGSBASE",    InstructionSet::FSGSBASE());
    support_message("FXSR",        InstructionSet::FXSR());
    support_message("HLE",         InstructionSet::HLE());
    support_message("INVPCID",     InstructionSet::INVPCID());
    support_message("LAHF",        InstructionSet::LAHF());
    support_message("LZCNT",       InstructionSet::LZCNT());
    support_message("MMX",         InstructionSet::MMX());
    support_message("MMXEXT",      InstructionSet::MMXEXT());
    support_message("MONITOR",     InstructionSet::MONITOR());
    support_message("MOVBE",       InstructionSet::MOVBE());
    support_message("MSR",         InstructionSet::MSR());
    support_message("OSXSAVE",     InstructionSet::OSXSAVE());
    support_message("PCLMULQDQ",   InstructionSet::PCLMULQDQ());
    support_message("POPCNT",      InstructionSet::POPCNT());
    support_message("PREFETCHWT1", InstructionSet::PREFETCHWT1());
    support_message("RDRAND",      InstructionSet::RDRAND());
    support_message("RDSEED",      InstructionSet::RDSEED());
    support_message("RDTSCP",      InstructionSet::RDTSCP());
    support_message("RTM",         InstructionSet::RTM());
    support_message("SEP",         InstructionSet::SEP());
    support_message("SHA",         InstructionSet::SHA());
    support_message("SSE",         InstructionSet::SSE());
    support_message("SSE2",        InstructionSet::SSE2());
    support_message("SSE3",        InstructionSet::SSE3());
    support_message("SSE4.1",      InstructionSet::SSE41());
    support_message("SSE4.2",      InstructionSet::SSE42());
    support_message("SSE4a",       InstructionSet::SSE4a());
    support_message("SSSE3",       InstructionSet::SSSE3());
    support_message("SYSCALL",     InstructionSet::SYSCALL());
    support_message("TBM",         InstructionSet::TBM());
    support_message("XOP",         InstructionSet::XOP());
    support_message("XSAVE",       InstructionSet::XSAVE());
}
```

```Output
GenuineIntel
        Intel(R) Core(TM) i5-2500 CPU @ 3.30GHz
3DNOW not supported
3DNOWEXT not supported
ABM not supported
ADX not supported
AES supported
AVX supported
AVX2 not supported
AVX512CD not supported
AVX512ER not supported
AVX512F not supported
AVX512PF not supported
BMI1 not supported
BMI2 not supported
CLFSH supported
CMPXCHG16B supported
CX8 supported
ERMS not supported
F16C not supported
FMA not supported
FSGSBASE not supported
FXSR supported
HLE not supported
INVPCID not supported
LAHF supported
LZCNT not supported
MMX supported
MMXEXT not supported
MONITOR not supported
MOVBE not supported
MSR supported
OSXSAVE supported
PCLMULQDQ supported
POPCNT supported
PREFETCHWT1 not supported
RDRAND not supported
RDSEED not supported
RDTSCP supported
RTM not supported
SEP supported
SHA not supported
SSE supported
SSE2 supported
SSE3 supported
SSE4.1 supported
SSE4.2 supported
SSE4a not supported
SSSE3 supported
SYSCALL supported
TBM not supported
XOP not supported
XSAVE supported
```

**Microsoft 전용 종료**

## <a name="see-also"></a>참조

[컴파일러 내장 함수](../intrinsics/compiler-intrinsics.md)
