---
title: 참조(C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: a334c7873675183dc06abfc2fe51472190996bf3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351172"
---
# <a name="reference-c-amp"></a>참조(C++ AMP)

이 섹션에서는 C++ Accelerated Massive Parallelism(C++ AMP) 런타임에 대한 참조 정보를 포함하고 있습니다.

> [!NOTE]
>  C++ 언어 표준에는 라이브러리와 같은 구현을 위해 밑줄(`_`) 문자로 시작하는 식별자의 사용이 예약되어 있습니다. 코드에 밑줄로 시작하는 이름을 사용하지 마세요. 해당 이름이 이 규칙을 따르는 코드 요소의 동작은 보장되지 않으며 이후 릴리스에서 변경될 수 있습니다. 이러한 이유로 이 설명서에서는 해당 코드 요소가 생략되었습니다.

## <a name="in-this-section"></a>섹션 내용

[Concurrency 네임스페이스(C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
데이터 병렬 하드웨어에서 C++ 코드를 가속화할 수 있는 클래스와 함수를 제공합니다.

[Concurrency::direct3d 네임스페이스](concurrency-direct3d-namespace.md)<br/>
D3D 상호 운용성을 지원하는 함수를 제공합니다. 중복된 임시 사본을 만들지 않고도 AMP 코드에서 계산하기 위해 D3D 리소스를 원활하게 사용하고 D3D 코드로 AMP에서 만든 리소스의 사용이 가능합니다. C++ AMP를 사용하여 DirectX 응용 프로그램의 계산 집중적인 섹션을 점차적으로 가속화하고 AMP 계산에서 생성된 데이터에 D3D API를 사용합니다.

[Concurrency::fast_math 네임스페이스](concurrency-fast-math-namespace.md)<br/>
함수는 `fast_math` 네임 스페이스는 C99 규격이 아닙니다. 각 함수의 단 정밀도 버전에만 제공 됩니다. 이러한 함수에서 해당 함수 보다 빠르며 DirectX 내장 함수를 사용 합니다 `precise_math` 네임 스페이스 및 액셀러레이터에 대해 확장 된 배정밀도 지원 하지 않아도 되지만 덜 정확 합니다. 두 가지 버전의 C99 코드를 사용 하 여 소스 수준 호환성을 위해 각 함수 버전을 모두 수행 하 고 단 정밀도 값을 반환 합니다.

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)<br/>
그래픽 프로그래밍을 위해 설계된 형식 및 함수를 제공합니다.

[Concurrency::precise_math 네임스페이스](concurrency-precise-math-namespace.md)<br/>
`precise_math` 네임 스페이스의 함수는 C99 규격입니다. 각 함수의 단정밀도 및 배정밀도 버전이 포함됩니다. 단정밀도 기능을 포함한 이러한 기능은 악셀러레이터에서 확장 배정밀도 지원이 필요합니다.

## <a name="related-sections"></a>관련 단원

[C++ AMP(C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++ AMP는 개별 그래픽 카드에서 그래픽 처리 장치(GPU)로 일반적으로 제공되는 데이터 병렬 하드웨어를 활용하여 C++ 코드 실행을 가속화합니다.
