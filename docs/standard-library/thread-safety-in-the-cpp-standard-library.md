---
description: '자세한 정보: c + + 표준 라이브러리의 스레드 보안'
title: C++ 표준 라이브러리의 스레드 보안
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: ff5d8960b2fc8a79acbfb4fc1d0be508865714e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97289636"
---
# <a name="thread-safety-in-the-c-standard-library"></a>C++ 표준 라이브러리의 스레드 보안

다음 스레드 보안 규칙은 C++ 표준 라이브러리의 모든 클래스에 적용됩니다. 아래에서 설명하는 것처럼 이 라이브러리에는 `shared_ptr`이 포함됩니다.  아래에서 설명 하는 것 처럼 표준 iostream 개체를 비롯 하 여 보다 강력한 보증이 제공 되는 경우와 같이 특히 다중 스레딩을 위한 형식이 제공 됩니다 [\<atomic>](../standard-library/atomic.md) .

개체는 여러 스레드에서 읽기 위해 스레드로부터 안전하게 보호됩니다. 예를 들어 개체 A가 있다고 가정하면 스레드 1과 스레드 2에서 개체 A를 동시에 안전하게 읽을 수 있습니다.

스레드 하나에서 개체에 쓰는 경우 동일하거나 다른 스레드에서 해당 개체에 대한 모든 읽기 및 쓰기가 보호되어야 합니다. 예를 들어 개체 A가 있다고 가정하면 스레드 1이 A에 쓰는 경우 스레드 2는 A에서 읽거나 A에 쓸 수 없어야 합니다.

다른 스레드가 동일한 형식의 다른 인스턴스를 읽거나 이러한 인스턴스에 쓰는 경우에 해당 형식의 인스턴스 하나에 대한 읽기 및 쓰기가 보호됩니다. 예를 들어 형식이 동일한 개체 A와 B가 있다고 가정하면 스레드 1에서 개체 A에 쓰는 중이고 스레드 2에서 개체 B를 읽는 중인 경우 안전합니다.

## <a name="shared_ptr"></a>shared_ptr

개체가 소유권을 공유하는 복사본이더라도 다중 스레드가 여러 [shared_ptr](../standard-library/shared-ptr-class.md) 개체를 동시에 읽고 쓸 수 있습니다.

## <a name="iostream"></a>iostream

표준 iostream 개체 `cin`, `cout`, `cerr`, `clog`, `wcin`, `wcout`, `wcerr` 및 `wclog`는 다중 스레드에서 개체에 쓰기가 보호된다는 점을 제외하면 다른 클래스와 동일한 규칙을 따릅니다. 예를 들어 스레드 1은 스레드 2와 동시에 [cout](../standard-library/iostream.md#cout)에 쓸 수 있습니다. 그러나 이로 인해 두 스레드에서 나온 출력이 섞일 수 있습니다.

> [!NOTE]
> 스트림 버퍼에서의 읽기는 읽기 작업으로 간주되지 않습니다. 대신에 클래스 상태가 변하기 때문에 쓰기 작업으로 간주됩니다.

## <a name="see-also"></a>참고 항목

[C + + 표준 라이브러리 개요](../standard-library/cpp-standard-library-overview.md)
