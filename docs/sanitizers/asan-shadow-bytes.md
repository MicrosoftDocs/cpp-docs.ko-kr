---
title: AddressSanitizer 섀도 바이트
description: 컴파일러가 생성 한 코드 및 AddressSanitizer 런타임에 의해 작성 되 고 읽은 섀도 바이트에 대 한 기술 설명입니다.
ms.date: 03/02/2021
helpviewer_keywords:
- Shadow bytes
- AddressSanitizer shadow bytes
- Address Sanitizer shadow bytes
- ASan shadow bytes
ms.openlocfilehash: 89c3051d2e68d579f2f187fcd12b45ff52cd8a58
ms.sourcegitcommit: 6ed44d9c3fb32e965e363b9c69686739a90a2117
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102471177"
---
# <a name="addresssanitizer-shadow-bytes"></a>AddressSanitizer 섀도 바이트

섀도 바이트의 개념과의 런타임 구현에서 이러한 바이트를 사용 하는 방법을 간략하게 요약 합니다 [`/fsanitize=address`](../build/reference/fsanitize.md) . 자세한 내용은 [내용이 필요한 종이](https://www.usenix.org/system/files/conference/atc12/atc12-final39.pdf) 및 [AddressSanitizer 알고리즘](https://github.com/google/sanitizers/wiki/AddressSanitizerAlgorithm)을 참조 하세요.

## <a name="core-concept"></a>핵심 개념

응용 프로그램의 가상 주소 공간에서 **8 바이트** 마다 **섀도 바이트 하나** 를 사용 하 여 설명할 수 있습니다.

섀도 바이트 1 개는 현재 다음과 같이 액세스할 수 있는 바이트 수를 나타냅니다.

- 0은 8 바이트를 모두 의미 합니다.
- 1-7은 1 ~ 7 바이트를 의미 합니다.
- 음수는 런타임에 보고 진단에 사용할 컨텍스트를 인코딩합니다.

### <a name="shadow-byte-legend"></a>그림자 바이트 범례

모든 음수가 정의 되는 다음 섀도 바이트 범례를 고려 하십시오.

:::image type="content" source="./media/asan-shadow-byte-legend.png" alt-text="AddressSanitizer 그림자-바이트 범례의 스크린샷":::

## <a name="mapping---describing-your-address-space"></a>매핑-주소 공간을 설명 합니다.

응용 프로그램의 가상 주소 공간에서 8 바이트 마다 "0-mod-8"이 정렬 되어 있으므로 가상 주소 공간에서 해당 슬롯을 설명 하는 섀도 바이트에 매핑할 수 있습니다.  이 매핑은 **간단한 shift 및 add** 를 사용 하 여 수행할 수 있습니다.

X 86:

```cpp
char shadow_byte_value = *((Your_Address >> 3) + 0x30000000)
```

X 64에서:

```cpp
char shadow_byte_value = *((Your_Address >> 3) + _asan_runtime_assigned_offset)
```

## <a name="code-generation---tests"></a>코드 생성-테스트

컴파일러가 생성 하는 코드, 정적 데이터 또는 런타임에서 특정 섀도 바이트를 작성할 수 있는 방법을 고려 합니다. 이 의사 코드는 모든 로드 또는 저장소 이전에 확인을 생성할 수 있는 방법을 보여 줍니다.

```cpp
ShadowAddr = (Addr >> 3) + Offset;
if (*ShadowAddr != 0) {
    ReportAndCrash(Addr);
}
```

8 바이트 보다 작은 메모리 참조를 계측할 때 계측은 약간 더 복잡 합니다. 그림자 값이 양수인 경우 (8 바이트 단어의 첫 k 바이트만 액세스할 수 있음), 주소의 마지막 3 비트를 k와 비교 해야 합니다.

```cpp
ShadowAddr = (Addr >> 3) + Offset;
k = *ShadowAddr;
if (k != 0 && ((Addr & 7) + AccessSize > k)) {
    ReportAndCrash(Addr);
}
```

런타임과 컴파일러에서 생성 된 코드는 모두 섀도 바이트를 씁니다. 이러한 섀도 바이트는 범위 종료 또는 저장소가 해제 될 때 액세스를 허용 하거나 취소 합니다. 위의 검사는 응용 프로그램의 주소 공간에서 8 바이트 "슬롯"을 설명 하는 읽기 섀도 바이트를 프로그램 실행의 특정 시간에 확인 합니다. 이러한 명시적으로 생성 된 검사 외에도 런타임은 CRT에서 많은 함수를 가로채 나 ("후크") 한 후 섀도 바이트를 확인 합니다.

자세한 내용은 차단 되는 [함수](./asan-runtime.md#default-interceptors)목록을 참조 하세요.

## <a name="setting-shadow-bytes"></a>섀도 바이트 설정

컴파일러가 생성 하는 코드와 AddressSanitizer 런타임은 섀도 바이트를 쓸 수 있습니다. 예를 들어 컴파일러는 내부 범위에 정의 된 stack 지역에 고정 크기의 액세스를 허용 하도록 섀도 바이트를 설정할 수 있습니다. 런타임에서는 데이터 섹션의 전역 변수를 섀도 바이트로 묶을 수 있습니다.

## <a name="see-also"></a>참고 항목

[AddressSanitizer 개요](./asan.md)\
[알려진 문제 AddressSanitizer](./asan-known-issues.md)\
[AddressSanitizer 빌드 및 언어 참조](./asan-building.md)\
[AddressSanitizer 런타임 참조](./asan-runtime.md)\
[AddressSanitizer 클라우드 또는 분산 테스트](./asan-offline-crash-dumps.md)\
[AddressSanitizer 디버거 통합](./asan-debugger-integration.md)\
[AddressSanitizer 오류 예](./asan-error-examples.md)
