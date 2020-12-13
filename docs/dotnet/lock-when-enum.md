---
description: '다음에 대 한 자세한 정보: 열거형 lock_when'
title: lock_when 열거형
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::lock_when
- msclr.lock_when
- lock_when
helpviewer_keywords:
- lock_when enum
ms.assetid: 6b87bbe9-63cd-450d-a02e-bb91ffd0dcea
ms.openlocfilehash: 5fcc0e428056f5076803ec1ba82bb20207e37189
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344486"
---
# <a name="lock_when-enum"></a>lock_when 열거형

지연 된 잠금을 지정 합니다.

## <a name="syntax"></a>구문

```
enum lock_when {
   lock_later
};
```

## <a name="remarks"></a>설명

[Lock:: lock](./lock-class.md#lock)에 전달 될 때 `lock_later` 잠금이 현재 수행 되지 않도록 지정 합니다.

## <a name="example"></a>예제

이 예제에서는 여러 스레드 간에 클래스의 단일 인스턴스를 사용 합니다.  클래스는 자체에 대 한 잠금을 사용 하 여 내부 데이터에 대 한 액세스가 각 스레드에 일치 하는지 확인 합니다.  주 응용 프로그램 스레드는 클래스의 동일한 인스턴스에 대 한 잠금을 사용 하 여 모든 작업자 스레드가 존재 하는지 정기적으로 확인 하 고 모든 작업자 스레드가 작업을 완료할 때까지 종료 될 때까지 기다립니다.

```cpp
// msl_lock_lock_when.cpp
// compile with: /clr
#include <msclr/lock.h>

using namespace System;
using namespace System::Threading;
using namespace msclr;

ref class CounterClass {
private:
   int Counter;

public:
   property int ThreadCount;

   // function called by multiple threads, use lock to keep Counter consistent
   // for each thread
   void UseCounter() {
      try {
         lock l(this); // wait infinitely

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         for (int i = 0; i < 10; i++) {
            Counter++;
            Thread::Sleep(10);
         }

         Console::WriteLine("In thread {0}, Counter = {1}", Thread::CurrentThread->ManagedThreadId,
            Counter);

         Counter = 0;
         // lock is automatically released when it goes out of scope and its destructor is called
      }
      catch (...) {
         Console::WriteLine("Couldn't acquire lock!");
      }

      ThreadCount--;
   }
};

int main() {
   // create a few threads to contend for access to the shared data
   CounterClass^ cc = gcnew CounterClass;
   array<Thread^>^ tarr = gcnew array<Thread^>(5);
   ThreadStart^ startDelegate = gcnew ThreadStart(cc, &CounterClass::UseCounter);
   for (int i = 0; i < tarr->Length; i++) {
      tarr[i] = gcnew Thread(startDelegate);
      cc->ThreadCount++;
      tarr[i]->Start();
   }

   // keep our main thread alive until all worker threads have completed
   lock l(cc, lock_later); // don't lock now, just create the object
   while (true) {
      if (l.try_acquire(50)) { // try to acquire lock, don't throw an exception if can't
         if (0 == cc->ThreadCount) {
            Console::WriteLine("All threads completed.");
            break; // all threads are gone, exit while
         }
         else {
            Console::WriteLine("{0} threads exist, continue waiting...", cc->ThreadCount);
            l.release(); // some threads exist, let them do their work
         }
      }
   }
}
```

```Output
In thread 3, Counter = 0
In thread 3, Counter = 10
In thread 5, Counter = 0
In thread 5, Counter = 10
In thread 7, Counter = 0
In thread 7, Counter = 10
In thread 4, Counter = 0
In thread 4, Counter = 10
In thread 6, Counter = 0
In thread 6, Counter = 10
All threads completed.
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\lock.h>

Msclr **네임 스페이스**

## <a name="see-also"></a>참고 항목

[lock](../dotnet/lock.md)
