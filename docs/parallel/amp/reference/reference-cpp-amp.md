---
description: '자세한 정보: 참조 (C++ AMP)'
title: 참조(C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::Reference (C++ AMP)
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, reference
ms.assetid: 372a8aed-8a53-48c9-996f-9c3cf09c9fa8
ms.openlocfilehash: 043522d7524078c3c7fec956021fdd7a86347169
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97327637"
---
# <a name="reference-c-amp"></a>참조(C++ AMP)

이 섹션에는 C++ Accelerated Massive Parallelism (C++ AMP) 런타임에 대 한 참조 정보가 포함 되어 있습니다.

> [!NOTE]
> C++ 언어 표준에는 라이브러리와 같은 구현을 위해 밑줄(`_`) 문자로 시작하는 식별자의 사용이 예약되어 있습니다. 코드에 밑줄로 시작하는 이름을 사용하지 마세요. 해당 이름이 이 규칙을 따르는 코드 요소의 동작은 보장되지 않으며 이후 릴리스에서 변경될 수 있습니다. 이러한 이유로 이 설명서에서는 해당 코드 요소가 생략되었습니다.

## <a name="in-this-section"></a>섹션 내용

[동시성 네임 스페이스 (C++ AMP)](concurrency-namespace-cpp-amp.md)<br/>
데이터 병렬 하드웨어에서 c + + 코드의 가속을 사용할 수 있는 클래스와 함수를 제공 합니다.

[Concurrency::direct3d 네임스페이스](concurrency-direct3d-namespace.md)<br/>
는 D3D 상호 운용성을 지 원하는 함수를 제공 합니다. 중복 된 중간 복사본을 만들지 않고 AMP 코드에서 계산을 위해 D3D 리소스를 원활 하 게 사용 하 고 D3D 코드의 AMP에서 만든 리소스를 사용할 수 있습니다. C++ AMP를 사용 하 여 DirectX 응용 프로그램의 계산 집약적인 섹션을 점차적으로 가속화 하 고 AMP 계산에서 생성 된 데이터에 대해 D3D API를 사용할 수 있습니다.

[Concurrency::fast_math 네임스페이스](concurrency-fast-math-namespace.md)<br/>
`fast_math`네임 스페이스의 함수는 C99 규격이 아닙니다. 각 함수의 단 정밀도 버전만 제공 됩니다. 이러한 함수는 DirectX 내장 함수를 사용 합니다 .이 함수는 네임 스페이스의 해당 함수 보다 빠르지만 `precise_math` 액셀러레이터에 대 한 확장 된 배정밀도 지원이 필요 하지 않지만 정확도가 떨어집니다. C99 코드와의 소스 수준 호환성을 위한 각 함수에는 두 가지 버전이 있습니다. 두 버전 모두 단일 전체 자릿수 값을 사용 하 고 반환 합니다.

[Concurrency::graphics 네임스페이스](concurrency-graphics-namespace.md)<br/>
그래픽 프로그래밍을 위해 디자인 된 형식 및 함수를 제공 합니다.

[동시성::p recise_math 네임 스페이스](concurrency-precise-math-namespace.md)<br/>
`precise_math`네임 스페이스의 함수는 C99 규격입니다. 각 함수의 단 정밀도와 배정밀도 버전이 모두 포함 됩니다. 단 정밀도 함수를 포함 하는 이러한 함수에는 액셀러레이터에 대 한 확장 된 배정밀도 지원이 필요 합니다.

## <a name="related-sections"></a>관련 단원

[C++ AMP(C++ Accelerated Massive Parallelism)](../../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
C++ AMP는 개별 그래픽 카드의 GPU (그래픽 처리 장치)로 일반적으로 존재 하는 데이터 병렬 하드웨어를 활용 하 여 c + + 코드의 실행 속도를 가속화 합니다.
