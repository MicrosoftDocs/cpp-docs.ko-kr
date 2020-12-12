---
description: '자세한 정보: 방법: 컨텍스트 클래스를 사용 하 여 협조적 세마포 구현'
title: '방법: 컨텍스트 클래스를 사용하여 공동 작업 세마포 구현'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: d80d364a9dcd27ee7012da5f710d38208c7a9e1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205657"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>방법: 컨텍스트 클래스를 사용하여 공동 작업 세마포 구현

이 항목에서는 concurrency:: Context 클래스를 사용 하 여 협조적 세마포 클래스를 구현 하는 방법을 보여 줍니다.

## <a name="remarks"></a>설명

`Context`클래스를 사용 하 여 현재 실행 컨텍스트를 차단 하거나 생성할 수 있습니다. 현재 컨텍스트를 차단 하거나 생성 하는 것은 리소스를 사용할 수 없기 때문에 현재 컨텍스트를 계속할 수 없는 경우에 유용 합니다. *세마포* 는 현재 실행 컨텍스트가 리소스를 사용할 수 있을 때까지 기다려야 하는 한 가지 상황의 예입니다. 임계 영역 개체와 같은 세마포는 한 컨텍스트에서 코드가 리소스에 단독으로 액세스할 수 있도록 하는 동기화 개체입니다. 그러나 임계 영역 개체와 달리 세마포를 사용 하면 둘 이상의 컨텍스트에서 리소스에 동시에 액세스할 수 있습니다. 최대 컨텍스트 수가 세마포 잠금을 보유 하는 경우 각 추가 컨텍스트는 다른 컨텍스트가 잠금을 해제할 때까지 기다려야 합니다.

### <a name="to-implement-the-semaphore-class"></a>세마포 클래스를 구현 하려면

1. 이라는 클래스를 선언 `semaphore` 합니다. **`public`** 및 **`private`** 섹션을이 클래스에 추가 합니다.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. **`private`** 클래스의 섹션에서 세마포 `semaphore` 수를 포함 하는 [std:: atomic](../../standard-library/atomic-structure.md) 변수와 세마포를 얻기 위해 대기 해야 하는 컨텍스트가 포함 된 [concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) 개체를 선언 합니다.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. **`public`** 클래스의 섹션에서 `semaphore` 생성자를 구현 합니다. 생성자는 동시에 **`long long`** 잠금을 보유할 수 있는 최대 컨텍스트 수를 지정 하는 값을 사용 합니다.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. **`public`** 클래스의 섹션에서 `semaphore` 메서드를 구현 `acquire` 합니다. 이 메서드는 원자 단위 연산으로 세마포 수를 감소 시킵니다. 세마포 수가 음수가 되 면 현재 컨텍스트를 대기 큐의 끝에 추가 하 고 [concurrency:: context:: Block](reference/context-class.md#block) 메서드를 호출 하 여 현재 컨텍스트를 차단 합니다.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. **`public`** 클래스의 섹션에서 `semaphore` 메서드를 구현 `release` 합니다. 이 메서드는 원자 단위 연산으로 세마포 수를 증가 시킵니다. 증분 작업 전에 세마포 수가 음수 이면 잠금을 기다리는 컨텍스트가 하나 이상 있습니다. 이 경우 대기 큐의 맨 앞에 있는 컨텍스트를 차단 해제 합니다.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>예제

`semaphore`이 예제의 클래스는 `Context::Block` `Context::Yield` 런타임에서 다른 작업을 수행할 수 있도록 및 메서드가 실행을 생성 하기 때문에 협조적으로 동작 합니다.

`acquire`메서드는 카운터를 감소 시키지만 다른 컨텍스트에서 메서드를 호출 하기 전에 대기 큐에 컨텍스트를 추가 하는 작업이 완료 되지 않을 수 있습니다 `release` . 이를 고려 하기 위해 `release` 메서드는 [concurrency:: context:: Yield](reference/context-class.md#yield) 메서드를 호출 하는 spin 루프를 사용 하 여 `acquire` 메서드가 컨텍스트 추가를 완료할 때까지 기다립니다.

메서드는 메서드를 `release` `Context::Unblock` 호출 하기 전에 메서드를 호출할 수 있습니다 `acquire` `Context::Block` . 런타임에서 이러한 메서드를 순서에 관계 없이 호출할 수 있으므로 이러한 경합 상태를 방지할 필요가 없습니다. 메서드가 `release` `Context::Unblock` 동일한 컨텍스트에 대해를 호출 하기 전에 메서드를 호출 하면 `acquire` `Context::Block` 해당 컨텍스트는 차단 해제 된 상태로 유지 됩니다. 런타임에서는에 대 한 각 호출이 `Context::Block` 에 대 한 해당 호출과 일치 해야 합니다 `Context::Unblock` .

다음 예제에서는 전체 클래스를 보여 줍니다 `semaphore` . `wmain`함수는이 클래스의 기본 사용법을 보여 줍니다. `wmain`함수는 [concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) 알고리즘을 사용 하 여 세마포에 대 한 액세스가 필요한 몇 가지 작업을 만듭니다. 3 개의 스레드가 언제 든 지 잠금을 보유할 수 있으므로 일부 작업은 다른 작업이 완료 될 때까지 대기 하 고 잠금을 해제 해야 합니다.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

이 예제에서는 다음 샘플 출력을 생성 합니다.

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

클래스에 대 한 자세한 내용은 `concurrent_queue` [병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)를 참조 하세요. 알고리즘에 대 한 자세한 내용은 `parallel_for` [병렬 알고리즘](../../parallel/concrt/parallel-algorithms.md)을 참조 하세요.

## <a name="compiling-the-code"></a>코드 컴파일

예제 코드를 복사 하 여 Visual Studio 프로젝트에 붙여넣거나 라는 파일에 붙여 넣은 `cooperative-semaphore.cpp` 후 Visual Studio 명령 프롬프트 창에서 다음 명령을 실행 합니다.

> **cl.exe/EHsc cooperative-semaphore**

## <a name="robust-programming"></a>강력한 프로그래밍

RAII ( *Resource 취득-초기화* ) 패턴을 사용 하 여 개체에 대 한 액세스를 지정 된 범위로 제한할 수 있습니다 `semaphore` . RAII 패턴에서 데이터 구조가 스택에 할당 됩니다. 해당 데이터 구조는 생성 될 때 리소스를 초기화 하거나 획득 하 고, 데이터 구조가 소멸 될 때 해당 리소스를 소멸 하거나 해제 합니다. RAII 패턴은 바깥쪽 범위가 끝나기 전에 소멸자가 호출 되도록 합니다. 따라서 예외가 throw 되거나 함수에 여러 문이 포함 된 경우 리소스가 올바르게 관리 됩니다 **`return`** .

다음 예제에서는 `scoped_lock` 클래스의 섹션에서 정의 되는 이라는 클래스를 정의 합니다 **`public`** `semaphore` . `scoped_lock`클래스는 [concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) 및 [concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) 클래스와 유사 합니다. 클래스의 생성자는 `semaphore::scoped_lock` 지정 된 개체에 대 한 액세스 권한을 얻고 `semaphore` 소멸자는 해당 개체에 대 한 액세스 권한을 해제 합니다.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
다음 예제에서는 `parallel_for` RAII를 사용 하 여 함수가 반환 되기 전에 세마포가 해제 되도록 알고리즘에 전달 되는 작업 함수의 본문을 수정 합니다. 이 방법을 사용 하면 작업 함수가 예외를 안전 하 게 처리할 수 있습니다.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>참고 항목

[컨텍스트](../../parallel/concrt/contexts.md)<br/>
[병렬 컨테이너 및 개체](../../parallel/concrt/parallel-containers-and-objects.md)
