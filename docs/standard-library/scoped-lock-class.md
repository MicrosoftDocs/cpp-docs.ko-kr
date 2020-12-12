---
description: Scoped_lock 클래스에 대해 자세히 알아보세요.
title: scoped_lock 클래스
ms.date: 11/04/2016
f1_keywords:
- mutex/std::scoped_lock
ms.openlocfilehash: 929dadab1f476f4254a46fcd0dbec4b8e162228b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197116"
---
# <a name="scoped_lock-class"></a>scoped_lock 클래스

## <a name="syntax"></a>구문

```cpp
template <class... MutexTypes>
class scoped_lock {
    using mutex_type = Mutex; // If MutexTypes... consists of the single type Mutex
    explicit scoped_lock(MutexTypes&... m);
    explicit scoped_lock(MutexTypes&... m, adopt_lock_t);
    ~scoped_lock();
    scoped_lock(const scoped_lock&) = delete;
    scoped_lock& operator=(const scoped_lock&) = delete;
}
```
