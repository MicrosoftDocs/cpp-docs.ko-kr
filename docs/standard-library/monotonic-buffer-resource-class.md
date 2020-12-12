---
description: Monotonic_buffer_resource 클래스에 대해 자세히 알아보세요.
title: monotonic_buffer_resource 클래스
ms.date: 11/04/2016
f1_keywords:
- memory_resource/std::monotonic_buffer_resource
helpviewer_keywords:
- std::monotonic_buffer_resource
ms.openlocfilehash: b7821dcaf441972eff415da93078ef3d8f0b59ab
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97115016"
---
# <a name="monotonic_buffer_resource-class"></a>monotonic_buffer_resource 클래스

## <a name="syntax"></a>구문

```cpp
class monotonic_buffer_resource : public memory_resource {
    memory_resource *upstream_rsrc; // exposition only
    void *current_buffer; // exposition only
    size_t next_buffer_size; // exposition only

    explicit monotonic_buffer_resource(memory_resource *upstream);
    monotonic_buffer_resource(size_t initial_size, memory_resource *upstream);
    monotonic_buffer_resource(void *buffer, size_t buffer_size, memory_resource *upstream);
    monotonic_buffer_resource()
        : monotonic_buffer_resource(get_default_resource()) {}
    explicit monotonic_buffer_resource(size_t initial_size)
        : monotonic_buffer_resource(initial_size, get_default_resource()) {}
    monotonic_buffer_resource(void *buffer, size_t buffer_size)
        : monotonic_buffer_resource(buffer, buffer_size, get_default_resource()) {}
    monotonic_buffer_resource(const monotonic_buffer_resource&) = delete;
    virtual ~monotonic_buffer_resource();
    monotonic_buffer_resource
        operator=(const monotonic_buffer_resource&) = delete;
    void release();
    memory_resource* upstream_resource() const;
};
```
