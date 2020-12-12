---
description: '자세한 정보: c + + 개발자 지침에서 잘못 실행 채널에 대 한 지침'
title: 잘못 실행 되는 채널에 대 한 c + + 개발자 지침
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: 41376f02c04a9baf83fec19791d77c169c73fa31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97320081"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>잘못 실행 되는 채널에 대 한 c + + 개발자 지침

이 문서에는 개발자가 c + + 소프트웨어의 잘못 된 실행 쪽 채널 하드웨어 취약점을 식별 하 고 완화할 수 있는 지침이 포함 되어 있습니다. 이러한 취약점은 신뢰 경계를 넘어 중요 한 정보를 공개할 수 있으며, 잘못 된 명령의 잘못 된 실행을 지 원하는 프로세서에서 실행 되는 소프트웨어에 영향을 줄 수 있습니다. 이 취약점의 취약점은 처음에는 2018 년 1 월, 추가 배경 및 설명서에서 확인할 수 [있습니다.](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)

이 문서에서 제공 하는 지침은 다음에서 나타내는 취약성의 클래스와 관련 되어 있습니다.

1. 스펙터 변형 1이 라고도 하는 CVE-2017-5753입니다. 이 하드웨어 취약성 클래스는 조건부 분기 misprediction의 결과로 발생 하는 잘못 된 실행으로 인해 발생할 수 있는 측면 채널과 관련이 있습니다. Visual Studio 2017 (버전 15.5.5부터 시작)의 Microsoft c + + 컴파일러에는 `/Qspectre` CVE-2017-5753와 관련 된 잠재적으로 취약 한 코딩 패턴의 제한 된 집합에 대 한 컴파일 시간 완화를 제공 하는 스위치에 대 한 지원이 포함 되어 있습니다. `/Qspectre`스위치는 Visual Studio 2015 업데이트 3에서 [KB 4338871](https://support.microsoft.com/help/4338871)에도 사용할 수 있습니다. 플래그에 대 한 설명서는 [`/Qspectre`](../build/reference/qspectre.md) 효과 및 사용에 대 한 자세한 정보를 제공 합니다.

2. CVE-2018-3639 [(SSB (잘못 된 저장소 바이패스)](https://aka.ms/sescsrdssb)라고도 함) 이 하드웨어 취약성 클래스는 메모리 액세스 misprediction의 결과로 종속 저장소에 대 한 잘못 된 부하의 잘못 된 실행으로 인해 발생할 수 있는 측면 채널과 관련이 있습니다.

[스펙터 및 멜트다운의 사례는](https://www.youtube.com/watch?v=_4O0zMW-Zu4) 이러한 문제를 발견 한 연구 팀 중 하나에 의해 제공 되는 프레젠테이션에서 찾을 수 있습니다.

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>추론적 실행 측 채널 하드웨어 취약점 이란?

최신 Cpu는 명령에 대 한 잘못 된 실행을 사용 하 여 높은 수준의 성능을 제공 합니다. 예를 들어 CPU가 예측 분기 대상에서 명령을 실행 하는 speculatively를 시작 하 여 실제 분기 대상이 해결 될 때까지 정지를 방지 하는 분기의 목표 (조건부 및 간접)를 예측 하 여이를 수행 하는 경우가 종종 있습니다. 나중에 CPU가 misprediction 발생 했음을 검색 하는 경우 speculatively 계산 된 모든 컴퓨터 상태는 무시 됩니다. 이렇게 하면 mispredicted 추론에 대 한 구조적으로 볼 수 있는 영향이 없습니다.

잘못 된 실행은 아키텍처 측면에서 표시 되는 상태에 영향을 주지 않지만 CPU에서 사용 되는 다양 한 캐시와 같은 비 아키텍처 상태에서 남은 추적을 유지할 수 있습니다. 이는 의도 하지 않은 채널 취약성을 제공할 수 있는 잘못 된 실행의 이러한 잔여 추적입니다. 이를 더 잘 이해 하려면 CVE-2017-5753 (범위 확인 바이패스)의 예를 제공 하는 다음 코드 조각을 참조 하세요.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

이 예제에서는에 `ReadByte` 버퍼, 버퍼 크기 및 해당 버퍼에 대 한 인덱스가 제공 됩니다. 에 지정 된 대로 인덱스 매개 변수는 `untrusted_index` 비관리 프로세스와 같이 낮은 권한의 컨텍스트에서 제공 됩니다. `untrusted_index`가 보다 작은 경우 `buffer_size` 해당 인덱스에 있는 문자를 읽고 `buffer` 사용 하 여에서 참조 하는 메모리의 공유 영역에 대 한 인덱스를 만듭니다 `shared_buffer` .

아키텍처 측면에서이 코드 시퀀스는 항상 보다 작은 것이 보장 되므로 완벽 하 게 안전 `untrusted_index` `buffer_size` 합니다. 그러나 잘못 실행 된 경우 CPU가 조건부 분기를 예측 실패 하 고 `untrusted_index` 가 보다 크거나 같은 경우에도 if 문의 본문을 실행할 수 있습니다 `buffer_size` . 이로 인해 CPU는 (비밀 일 수 있음) 범위를 벗어나 바이트를 speculatively 읽을 수 있습니다 `buffer` . 그런 다음 해당 바이트 값을 사용 하 여 후속 로드의 주소를 계산할 수 있습니다 `shared_buffer` .

CPU가이 misprediction를 검색 하는 동안에는의 범위에서 읽어온 바이트 값에 대 한 정보를 표시 하는 나머지 부작용이 CPU 캐시에 남아 있을 수 있습니다 `buffer` . 이러한 부작용은의 각 캐시 라인에 얼마나 빨리 액세스 되는지 검색 하 여 시스템에서 실행 되는 낮은 권한의 컨텍스트를 통해 검색할 수 있습니다 `shared_buffer` . 이를 수행 하기 위해 수행할 수 있는 단계는 다음과 같습니다.

1. **`ReadByte` `untrusted_index` 보다 `buffer_size` 작은를 사용 하 여를 여러 번 호출** 합니다. 공격 컨텍스트는 `ReadByte` 분기 예측 자가 보다 낮은 수준으로 사용 되지 않도록 교육을 수행 하도록 공격 대상 컨텍스트 (예: RPC를 통해)를 호출할 수 있습니다 `untrusted_index` `buffer_size` .

2. **의 모든 캐시 줄을 `shared_buffer` 플러시합니다**. 공격 컨텍스트는에서 참조 하는 메모리의 공유 영역에 있는 모든 캐시 줄을 플러시합니다 `shared_buffer` . 메모리 영역이 공유 되므로이는 간단 하며와 같은 내장 함수를 사용 하 여 수행할 수 있습니다 `_mm_clflush` .

3. **`ReadByte` `untrusted_index` 보다 `buffer_size` 큰를 사용 하 여를 호출** 합니다. 공격 컨텍스트는 분기를 사용 `ReadByte` 하지 않을 것으로 잘못 예측 하는 공격 컨텍스트를 호출 합니다. 이로 인해 프로세서에서 speculatively가 보다 큰 경우의 본문을 실행 하 여 `untrusted_index` `buffer_size` 의 범위를 벗어난 읽기로 돌아갑니다 `buffer` . 따라서 `shared_buffer` 는 범위를 벗어나는 잠재적 비밀 값을 사용 하 여 인덱싱됩니다. 따라서 CPU에서 각 캐시 줄을 로드 합니다.

4. **에서 각 캐시 줄 `shared_buffer` 을 읽어 가장 빠르게 액세스 하** 는를 확인 합니다. 공격 컨텍스트는의 각 캐시 줄을 읽고 `shared_buffer` 다른 항목 보다 훨씬 빠르게 로드 되는 캐시 줄을 검색할 수 있습니다. 3 단계에서 가져온 것으로 예상 되는 캐시 줄입니다. 이 예제에서 바이트 값과 캐시 줄 간에 1:1 관계가 있으므로 공격자는 범위를 벗어난 읽은 바이트의 실제 값을 유추할 수 있습니다.

위의 단계는 CVE-2017-5753의 인스턴스를 악용 하는 것과 함께 FLUSH + RELOAD 라는 기법을 사용 하는 예를 제공 합니다.

## <a name="what-software-scenarios-can-be-impacted"></a>영향을 받을 수 있는 소프트웨어 시나리오는 무엇입니까?

SDL ( [보안 개발 수명 주기](https://www.microsoft.com/sdl/) )과 같은 프로세스를 사용 하 여 보안 소프트웨어를 개발 하려면 일반적으로 개발자가 응용 프로그램에 존재 하는 신뢰 경계를 식별 해야 합니다. 응용 프로그램이 시스템의 다른 프로세스 또는 커널 모드 장치 드라이버의 경우 관리 되지 않는 사용자 모드 프로세스와 같이 더 낮은 신뢰 컨텍스트에서 제공 된 데이터와 상호 작용할 수 있는 위치에 트러스트 경계가 있습니다. 잘못 된 실행 측 채널과 관련 된 새로운 취약점 클래스는 장치의 코드와 데이터를 격리 하는 기존 소프트웨어 보안 모델의 여러 신뢰 경계와 관련이 있습니다.

다음 표에서는 개발자가 발생 하는 이러한 취약성에 대해 걱정 해야 할 수 있는 소프트웨어 보안 모델을 요약 하 여 보여 줍니다.

|트러스트 경계|설명|
|----------------|----------------|
|가상 머신 경계 |다른 가상 컴퓨터에서 신뢰할 수 없는 데이터를 수신 하는 별도의 가상 컴퓨터에서 워크 로드를 격리 하는 응용 프로그램은 위험이 있을 수 있습니다.|
|커널 경계|관리자가 아닌 사용자 모드 프로세스에서 신뢰할 수 없는 데이터를 받는 커널 모드 장치 드라이버는 위험할 수 있습니다.|
|프로세스 경계 |RPC (원격 프로시저 호출), 공유 메모리 또는 IPC (기타 Inter-Process 통신) 메커니즘과 같이 로컬 시스템에서 실행 되는 다른 프로세스에서 신뢰할 수 없는 데이터를 받는 응용 프로그램은 위험할 수 있습니다.|
|Enclave 경계|Enclave 외부에서 신뢰할 수 없는 데이터를 수신 하는 보안 enclave (예: Intel SGX) 내에서 실행 되는 응용 프로그램은 위험이 있을 수 있습니다.|
|언어 경계|JIT (Just-in-time)를 해석 하는 응용 프로그램은 더 높은 수준의 언어로 작성 된 신뢰할 수 없는 코드를 컴파일하고 실행 하는 것은 위험할 수 있습니다.|

위의 신뢰 경계 중 하나에 노출 된 공격 노출 영역을 가진 응용 프로그램은 공격 노출 영역에서 코드를 검토 하 여 해당 하는 잘못 된 실행 측 채널 취약점을 식별 하 고 완화 해야 합니다. 원격 네트워크 프로토콜과 같은 원격 공격 화면에 노출 되는 트러스트 경계는 잘못 된 실행 측 채널 취약점에 노출 되지 않습니다.

## <a name="potentially-vulnerable-coding-patterns"></a>잠재적으로 취약 한 코딩 패턴

여러 코딩 패턴의 결과로 서의 잘못 된 실행 측 채널 취약성이 발생할 수 있습니다. 이 섹션에서는 잠재적으로 취약 한 코딩 패턴을 설명 하 고 각각에 대 한 예제를 제공 하지만 이러한 테마의 변형이 있을 수 있음을 인식 해야 합니다. 따라서 개발자는 이러한 패턴을 예제로 사용 하는 것이 좋지만 잠재적으로 취약 한 모든 코딩 패턴의 완전 한 목록이 아닙니다. 현재 소프트웨어에 있을 수 있는 것과 동일한 메모리 안전 취약성 클래스는 또한 버퍼 오버런, 범위를 벗어난 배열 액세스, 초기화 되지 않은 메모리 사용, 형식 혼동 등을 포함 하 여 잘못 된 실행 경로를 포함 하 여 존재할 수 있습니다. 공격자가 아키텍처 경로를 따라 메모리 보안 취약성을 악용 하는 데 사용할 수 있는 것과 동일한 기본 형식을 잘못 된 경로에도 적용할 수 있습니다.

일반적으로 조건부 분기 misprediction 관련 된 잘못 된 실행 측 채널은 조건 식이 제어 하거나 신뢰 수준이 낮은 컨텍스트의 영향을 받을 수 있는 데이터에 대해 작동 하는 경우 발생할 수 있습니다. 예를 들어,,, **`if`** **`for`** **`while`** **`switch`** 또는 삼항 문에 사용 되는 조건식이 여기에 포함 될 수 있습니다. 이러한 각 문에 대해 컴파일러는 런타임에 CPU가 분기 대상을 예측할 수 있는 조건부 분기를 생성할 수 있습니다.

각 예제에 대해 개발자가 문제를 완화 하는 데 사용할 수 있는 "추론 장벽" 이라는 구가 포함 된 주석이 삽입 됩니다. 이에 대해서는 완화에 대 한 섹션에서 자세히 설명 합니다.

## <a name="speculative-out-of-bounds-load"></a>잘못 된 경계 로드

이 종류의 코딩 패턴에는 잘못 된 범위의 메모리 액세스를 야기 하는 조건부 분기 misprediction 포함 됩니다.

### <a name="array-out-of-bounds-load-feeding-a-load"></a>배열 범위를 벗어난 부하가 부하를 공급 합니다.

이 코딩 패턴은 CVE-2017-5753 (범위 확인 바이패스)에 대해 원래 설명 된 취약 한 코딩 패턴입니다. 이 문서의 배경 섹션에서는이 패턴에 대해 자세히 설명 합니다.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

마찬가지로 배열 범위를 벗어난 로드는 misprediction로 인 한 종료 조건을 초과 하는 루프와 함께 발생할 수 있습니다. 이 예제에서 식과 연결 된 조건부 분기는 `x < buffer_size` **`for`** 이 보다 크거나 같을 경우 루프 본문을 예측 실패 하 고 speculatively를 실행 하 여 `x` 잘못 된 범위의 부하를 발생 시킬 수 있습니다 `buffer_size` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>배열 범위를 벗어난 부하가 간접 분기를 공급 합니다.

이 코딩 패턴은 조건부 분기 misprediction가 범위를 벗어난 대상 주소에 대 한 간접 분기로 이어지는 함수 포인터의 배열에 대해 범위를 벗어난 액세스를 초래할 수 있는 경우를 포함 합니다. 다음 코드 조각은이를 보여 주는 예제를 제공 합니다.

이 예제에서는 매개 변수를 통해 DispatchMessage에 신뢰할 수 없는 메시지 식별자를 제공 `untrusted_message_id` 합니다. `untrusted_message_id`가 보다 작은 경우 `MAX_MESSAGE_ID` 함수 포인터 및 분기의 배열을 해당 분기 대상으로 인덱싱하는 데 사용 됩니다. 이 코드는 안전 하 게 안전 하지만 CPU가 조건부 분기를 기인한 경우 `DispatchTable` `untrusted_message_id` 해당 값이 보다 크거나 같은 경우에 따라 인덱싱할 수 `MAX_MESSAGE_ID` 있으므로 범위를 벗어난 액세스가 발생 합니다. 이로 인해 배열의 범위를 벗어나 파생 되는 분기 대상 주소에서 잘못 실행 될 수 있습니다. 그러면 speculatively 실행 되는 코드에 따라 정보가 공개 될 수 있습니다.

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

배열 범위를 벗어난 부하가 다른 부하를 공급 하는 경우와 마찬가지로이 상태는 misprediction로 인 한 종료 조건을 초과 하는 루프와 함께 발생할 수도 있습니다.

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>배열 범위를 벗어난 저장소는 간접 분기를 공급 합니다.

이전 예제에서는 잘못 된 범위 외부 부하가 간접 분기 대상에 영향을 줄 수 있는 방법을 보여 주지만, 범위를 벗어난 저장소에서 함수 포인터 또는 반환 주소와 같은 간접 분기 대상을 수정할 수도 있습니다. 이로 인해 공격자가 지정한 주소에서 잘못 실행 될 수 있습니다.

이 예제에서는 신뢰할 수 없는 인덱스가 매개 변수를 통해 전달 됩니다 `untrusted_index` . `untrusted_index`가 배열의 요소 수 `pointers` (256 요소) 보다 작은 경우에는 제공 된 포인터 값 `ptr` 이 배열에 기록 됩니다 `pointers` . 이 코드는 안전 하 게 안전 하지만 CPU가 조건부 분기를 기인한 경우 `ptr` 스택 할당 배열의 범위를 벗어나 speculatively 기록 될 수 있습니다 `pointers` . 이로 인해의 반환 주소가 잘못 손상 될 수 있습니다 `WriteSlot` . 공격자가의 값을 제어할 수 있는 경우가 잘못 된 `ptr` 경로를 따라 반환 될 때 해당 사용자가 임의 주소에서 잘못 된 실행을 일으킬 수 있습니다 `WriteSlot` .

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

마찬가지로 이라는 함수 포인터 지역 변수가 `func` 스택에 할당 된 경우 `func` 에는 조건부 분기 misprediction 발생할 때를 참조 하는 주소를 speculatively 수정할 수 있습니다. 이로 인해 함수 포인터가를 통해 호출 될 때 임의의 주소에서 잘못 실행 될 수 있습니다.

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

이러한 두 예제에는 스택 할당 간접 분기 포인터의 잘못 된 수정이 포함 되어 있습니다. 일부 Cpu에서 전역 변수, 힙 할당 메모리 및 심지어 읽기 전용 메모리에 대해 잘못 된 수정이 발생할 수도 있습니다. 스택에 할당 된 메모리의 경우 Microsoft c + + 컴파일러는 해당 버퍼가 컴파일러 보안 기능의 일부로 보안 쿠키에 인접 하 게 배치 되도록 지역 변수를 다시 정렬 하는 등의 방법으로 스택 할당 간접 분기 대상을 speculatively 수정 하기가 더 어려워집니다 [`/GS`](../build/reference/gs-buffer-security-check.md) .

## <a name="speculative-type-confusion"></a>잘못 되는 형식 혼동

이 범주는 잘못 된 형식 혼동을 줄 수 있는 코딩 패턴을 다룹니다. 이는 잘못 된 형식을 사용 하 여 잘못 된 형식을 사용 하 여 메모리에 액세스 하는 경우에 발생 합니다. 조건부 분기 misprediction와 잘못 된 저장소 바이패스는 모두 잠재적으로 잘못 된 형식 혼동을 일으킬 수 있습니다.

잘못 된 저장소 바이패스의 경우, 컴파일러에서 여러 형식의 변수에 대해 스택 위치를 다시 사용 하는 경우에 발생할 수 있습니다. 이는 형식의 변수에 대 한 아키텍처 저장소를 건너뛸 수 있으므로 `A` `A` 변수를 할당 하기 전에 speculatively의 형식 로드를 실행할 수 있기 때문입니다. 이전에 저장 된 변수가 다른 유형인 경우이로 인해 잘못 된 유형의 혼동에 대 한 조건이 생성 될 수 있습니다.

조건부 분기 misprediction의 경우 다음 코드 조각을 사용 하 여 잘못 된 형식 혼동을 제공할 수 있는 다양 한 조건을 설명 합니다.

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>잘못 된 형식 혼동으로 인해 범위를 벗어난 부하가 발생 합니다.

이 코딩 패턴은 잘못 된 형식 혼동으로 인해 로드 된 값이 후속 로드 주소를 공급 하는 범위를 벗어났거나 형식이 혼동 하는 필드에 액세스할 수 있는 경우를 포함 합니다. 이는 배열 범위를 벗어난 코딩 패턴과 유사 하지만 위에 표시 된 것 처럼 대체 코딩 시퀀스를 통해 매니페스트 됩니다. 이 예제에서 공격 컨텍스트는 `ProcessType` 형식의 개체 `CType1` ( `type` 필드는와 같음)를 사용 하 여 피해자 컨텍스트가 여러 번 실행 될 수 있습니다 `Type1` . 이렇게 하면 첫 번째 문에 대해 사용 되지 않는 조건부 분기를 학습 하는 데 영향을 미칠 수 **`if`** 있습니다. 그러면 공격 컨텍스트는 형식의 개체를 사용 하 여 피해자 컨텍스트를 실행할 수 있습니다 `ProcessType` `CType2` . 이로 인해 첫 번째 문의 조건부 분기가 **`if`** 기인한 하 고 문의 본문을 실행 하 여 **`if`** 형식의 개체를로 캐스팅 하는 경우 잘못 된 형식 혼동을 초래할 수 있습니다 `CType2` `CType1` . `CType2`가 보다 작기 때문에 `CType1` 에 대 한 메모리 액세스로 `CType1::field2` 인해 비밀이 될 수 있는 데이터의 범위를 벗어난 부하가 발생 하 게 됩니다. 이 값은 `shared_buffer` 앞에서 설명한 배열 범위를 벗어난 예제와 마찬가지로에서 관찰 가능한 부작용을 만들 수 있는 로드에 사용 됩니다.

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>간접 분기로 인 한 잘못 된 형식 혼동

이 코딩 패턴은 잘못 된 형식 혼동으로 인해 잘못 된 방식으로 실행 될 수 있는 경우를 포함 합니다. 이 예제에서 공격 컨텍스트는 `ProcessType` 형식의 개체 `CType2` ( `type` 필드는와 같음)를 사용 하 여 피해자 컨텍스트가 여러 번 실행 될 수 있습니다 `Type2` . 이렇게 하면 첫 번째 문에 대해 조건부 분기를 학습 하 **`if`** 고 `else if` 문을 사용 하지 않을 수 있습니다. 그러면 공격 컨텍스트는 형식의 개체를 사용 하 여 피해자 컨텍스트를 실행할 수 있습니다 `ProcessType` `CType1` . 이로 인해 첫 번째 문의 조건부 분기를 **`if`** 예측 하 고 `else if` 문이 예측 되지 않아의 본문을 실행 `else if` 하 고 형식의 개체 `CType1` 를로 캐스팅 `CType2` 하는 경우에는 잘못 된 형식 혼동을 일으킬 수 있습니다. `CType2::dispatch_routine`필드가 **`char`** 배열과 겹치면이로 `CType1::field1` 인해 의도 하지 않은 분기 대상에 대 한 잘못 된 간접 분기가 발생할 수 있습니다. 공격 컨텍스트가 배열에서 바이트 값을 제어할 수 있는 경우 `CType1::field1` 분기 대상 주소를 제어할 수 있습니다.

## <a name="speculative-uninitialized-use"></a>잘못 초기화 되었습니다.

이러한 종류의 코딩 패턴은 잘못 실행 된 메모리에 액세스 하 고이를 사용 하 여 후속 로드 또는 간접 분기를 제공할 수 있는 시나리오를 포함 합니다. 이러한 코딩 패턴이 악용 되기 위해서는 공격자가 사용 중인 컨텍스트를 사용 하 여 초기화 하지 않고도 사용 되는 메모리의 내용을 제어 하거나 영향을 받을 수 있어야 합니다.

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>잘못 초기화 된 잘못 된 사용으로 인해 범위를 벗어난 부하가 발생 합니다.

잘못 초기화 된 잘못 된 사용으로 인해 공격자가 제어 하는 값을 사용 하 여 범위를 벗어난 부하가 발생할 수 있습니다. 아래 예제에서는의 값 `index` 이 `trusted_index` 모든 아키텍처 경로에 할당 되 고 `trusted_index` 보다 작거나 같은 것으로 간주 됩니다 `buffer_size` . 그러나 컴파일러에서 생성 된 코드에 따라 `buffer[index]` 에 대 한 할당 보다 먼저 및 종속 식의 로드를 실행할 수 있도록 하는 잘못 된 저장소 바이패스가 발생할 수 있습니다 `index` . 이 경우에 대해 초기화 되지 않은 값이에 대 한 `index` 오프셋으로 사용 됩니다 .이를 통해 `buffer` 공격자는 경계를 벗어난 중요 한 정보를 읽고의 종속 로드를 통해 측 채널을 통해이를 전달할 수 있습니다 `shared_buffer` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>잘못 초기화 된 잘못 된 사용이 간접 분기에 선행

잘못 초기화 된 잘못 된 사용으로 인해 공격자가 분기 대상을 제어 하는 간접 분기가 될 수 있습니다. 아래 예제에서 `routine` 는 `DefaultMessageRoutine1` `DefaultMessageRoutine` 의 값에 따라 또는에 할당 됩니다 `mode` . 아키텍처 경로에서이는 `routine` 항상 간접 분기 보다 먼저 초기화 됩니다. 그러나 컴파일러에서 생성 된 코드에 따라 `routine` 에 대 한 할당 보다 먼저 간접 분기가 speculatively 실행 되도록 허용 하는 잘못 된 저장소 바이패스가 발생할 수 있습니다 `routine` . 이 경우 공격자는 임의의 주소에서 speculatively 실행 될 수 있으며, 공격자가의 초기화 되지 않은 값에 영향을 주거나이를 제어할 수 있습니다 `routine` .

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>해결 방법 옵션

소스 코드를 변경 하 여 잘못 된 실행 측 채널 취약성을 완화할 수 있습니다. 이러한 변경 내용에는 *추론 장벽을* 추가 하거나 중요 한 정보를 잘못 된 실행에 액세스할 수 없도록 응용 프로그램의 디자인을 변경 하는 등 특정 취약점의 특정 인스턴스를 완화 하는 작업이 포함 될 수 있습니다.

### <a name="speculation-barrier-via-manual-instrumentation"></a>수동 계측을 통해 장벽 추론

개발자는 *추론 장벽을* 수동으로 삽입 하 여 비 아키텍처 경로를 따라 잘못 실행 되는 것을 방지할 수 있습니다. 예를 들어 개발자는 조건부 블록의 시작 부분 (조건부 분기 이후) 이나 중요 한 첫 번째 로드 전에 조건부 블록의 본문에서 위험한 코딩 패턴 앞에 추론 장벽을 삽입할 수 있습니다. 이렇게 하면 조건부 분기 misprediction 실행을 serialize 하 여 비 아키텍처 경로에서 위험한 코드를 실행할 수 없습니다. 추론 장벽 시퀀스는 다음 표에 설명 된 대로 하드웨어 아키텍처에 따라 달라 집니다.

|Architecture|CVE-2017-5753에 대 한 추론 장벽 내장 함수|CVE-2018-3639에 대 한 추론 장벽 내장 함수|
|----------------|----------------|----------------|
|x86/x64|_mm_lfence ()|_mm_lfence ()|
|ARM|현재 사용할 수 없음|__dsb (0)|
|ARM64|현재 사용할 수 없음|__dsb (0)|

예를 들어 다음 코드 패턴은 아래와 같이 내장 함수를 사용 하 여 완화할 수 있습니다 `_mm_lfence` .

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>컴파일러 시간 계측을 통해 장벽 추론

Visual Studio 2017 (버전 15.5.5부터 시작)의 Microsoft c + + 컴파일러에는 `/Qspectre` CVE-2017-5753와 관련 된 잠재적으로 취약 한 코딩 패턴의 제한 된 집합에 대 한 추론 장벽을 자동으로 삽입 하는 스위치에 대 한 지원이 포함 되어 있습니다. 플래그에 대 한 설명서는 [`/Qspectre`](../build/reference/qspectre.md) 효과 및 사용에 대 한 자세한 정보를 제공 합니다. 이 플래그는 잠재적으로 취약 한 모든 코딩 패턴을 포함 하지 않으며, 개발자가이 취약점 클래스에 대 한 포괄적인 완화 수단으로이를 사용 하지 않아야 한다는 점에 유의 해야 합니다.

### <a name="masking-array-indices"></a>배열 인덱스 마스킹

잘못 된 범위를 벗어난 부하가 발생할 수 있는 경우 배열 인덱스를 명시적으로 바인딩하는 논리를 추가 하 여 아키텍처 및 비 아키텍처 경로 둘 다에서 배열 인덱스를 강력 하 게 바인딩할 수 있습니다. 예를 들어 2의 거듭제곱으로 정렬 된 크기에 배열을 할당할 수 있는 경우 단순 마스크를 도입할 수 있습니다. 이는 아래 샘플에서 설명 하며,이는 `buffer_size` 2의 거듭제곱으로 정렬 되어 있다고 가정 합니다. 이렇게 하면 `untrusted_index` `buffer_size` 조건부 분기 misprediction 발생 하 고 `untrusted_index` 보다 크거나 같은 값을 사용 하 여 전달 된 경우에도가 항상 보다 낮습니다 `buffer_size` .

여기에서 수행 되는 인덱스 마스킹은 컴파일러에서 생성 되는 코드에 따라 잘못 된 저장소 바이패스의 영향을 받을 수 있습니다.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>메모리에서 중요 한 정보 제거

잘못 된 실행 측 채널 취약점을 완화 하는 데 사용할 수 있는 다른 방법은 메모리에서 중요 한 정보를 제거 하는 것입니다. 소프트웨어 개발자는 민감한 실행 중에 중요 한 정보에 액세스할 수 없도록 응용 프로그램을 리팩터링할 기회를 찾을 수 있습니다. 이를 위해서는 응용 프로그램의 디자인을 리팩터링하여 중요 한 정보를 별도의 프로세스로 격리할 수 있습니다. 예를 들어 웹 브라우저 응용 프로그램은 각 웹 원본과 연결 된 데이터를 별도의 프로세스로 격리할 수 있으므로 한 프로세스가 잘못 된 실행을 통해 원본 간 데이터에 액세스할 수 없게 됩니다.

## <a name="see-also"></a>참고 항목

[잘못 실행 측면 채널 취약성을 완화 하기 위한 지침](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[추측 실행 측 채널 하드웨어 취약성 완화](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
